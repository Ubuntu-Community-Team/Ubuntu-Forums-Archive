---
title: "How do I remount Ubuntu arm 22.04 -rw from -ro"
date: 2023-02-09
forum: Installation &amp; Upgrades
---

### Post by kudzu9999 on 2023-02-09
Unable to mount Rasberry Pi Arm -rw starts as -ro and I can"t change it.

---

### Post by TheFu on 2023-02-10
Usually when storage is put into read-only mode, that happened because it is flash and the OS is trying to prevent worst things from happening.  In short, if it is flash memory, it is about to fail.  Stop.  Immediately.  Replace the storage.

If it isn't flash storage, you can just mount it with the remount,rw options using the normal 'mount' command.  If it refuses, it is going bad and you have hours or less time remaining before all access is lost.

---

### Post by MAFoElffen on 2023-02-10
When mine would do that on my RaspPi, I would remove the MicroSD Card, make a backup of it on my laptop... Then check/repair the errors with fschk. This would happen occasionally. Enough that I converted it to USB NVMe SSD boot to avoid MicroSD cards.

I think both I and TheFu are USB boot on ours. I have very much not regretted going that way for mine. Has saved me lots of work and stress.

---

