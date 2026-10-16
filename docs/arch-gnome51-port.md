# Experimental GNOME 51 AnLand port (Arch ARM64)

This is an **experimental build only**. It never touches the existing `anland-gnome-packages` Release.

- AnLand source fork: `vildangil/anland`, branch `port/gnome-51` (based on upstream `legacy`, not upstream `main`).
- Patch base: Mutter 50.5. Target: GNOME Mutter 51.1, checked against immutable upstream tag commit `9134e3a5869ce232bf95b77519005865747ba603`.
- Current Arch Linux ARM GNOME Shell requires `libmutter-51.so`.
- Source `PKGBUILD` targets `51.1`; new `mutter.patch` is **not yet complete**. Source and patch checksums are `SKIP` on the experimental branch only; fix these before any production release.
- The rebase script first applies the old AnLand patch to Mutter 50.5, then performs a three-way merge against 51.1. Conflicts are retained as Actions artifacts (`rebase-conflicts.diff`, `conflict-files.txt`).
- If rebase succeeds, it builds the Arch ARM64 packages and tests that they can be installed together with the current `gnome-shell` package, all within Docker. Successful compilation and pacman dependency resolution **do not** yet prove that rendering, input, or the Android host AnLand daemon work.

Go to **Actions → Experiment - Arch GNOME 51 AnLand port → Run workflow**. The first run is also requested automatically when this workflow first lands on `main`. Do not select these artifacts as DroidSpaces production packages until the GNOME Shell and Android runtime tests pass.

Use the normal package workflow and update the RootFS builder's `wayland_package_repository` only after that verification.
