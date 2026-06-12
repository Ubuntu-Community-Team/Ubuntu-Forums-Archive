---
title: "libGL error: failed to load driver: swrast"
date: 2021-01-15
forum: Installation &amp; Upgrades
---

### Post by realt3ch on 2021-01-15
Helo!

Iam trying to run android emulator and it throws error for swrast. This started after upgrade to 20.04.

Error message when running emulator from console:
$ ./emulator -avd Moises_6
emulator: Android emulator version 30.3.5.0 (build_id 7033400) (CL:N/A)
handleCpuAcceleration: feature check for hvf
libGL error: MESA-LOADER: failed to open swrast (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: swrast
Segmentation fault (core dumped)


Thanks!

---

### Post by realt3ch on 2021-01-16
:)

---

### Post by realt3ch on 2021-01-16
so what help is this:

$ export LIBGL_DRIVERS_PATH=/usr/lib/x86_64-linux-gnu/dri
$ export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/

or for X apps should be set here (system wide):
nano /etc/environment

---

