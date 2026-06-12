---
title: "Koala and Windows7 dual boot issues"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Coolaaron88 on 2009-07-26
I ended up booting up into Windows7 and uninstalling ubuntu. I burned karmic koala onto a cd and did an install of karmic which went well until the attempted boot up of ubuntu which was stopped by the error "no wubildr". After that error my computer reboots and starts up to the boot screen where the same thing happens again so I have that issues at the moment. I also run a 64 bit machine with AMD as well. I really wanna get it running. Any solutions?

---

### Post by jfernyhough on 2009-07-26
Boot with the Karmic LiveCD, open a Terminal, and reinstall GRUB:

$ sudo grub-install --recheck /dev/sda

(/dev/sda assumes you have one HDD)

The option --recheck will do as it says; it will detect what OS you have. The old config is probably looking for a Wubi installation, which I presume you no longer have.

---

### Post by Coolaaron88 on 2009-07-26
Well I tried doing that and I got this back:

ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

Im so confused as to why this is happening.

---

### Post by psyke83 on 2009-07-26
> **Coolaaron88 said:**
> Well I tried doing that and I got this back:

ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

Im so confused as to why this is happening.

Let's get this clear first: did you install Karmic to a dedicated partition (i.e. a real installation), or did you use Wubi?

If you used Wubi, GRUB or GRUB2 isn't used in the same way; the Windows bootloader is utilized.

**If** and **only if** you performed a real installation:

The instructions by jfernyhough are too simplistic and don't take some issues into account. You must follow the "If you messed up" section on the [Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") page.

This was [discussed recently]("http://ubuntuforums.org/showthread.php?t=1223207") - always do a search.

---

### Post by jfernyhough on 2009-07-26
How did you install Karmic? Directly into a partition by booting from the CD or by using Wubi from within Windows?

---

### Post by Coolaaron88 on 2009-07-26
I installed Karmic through wubi in windows.

---

### Post by jfernyhough on 2009-07-26
If it were me I'd go back, install a Jaunty Wubi, then if you really wanted dist-upgrade to Karmic ($ update-manager -d). Seeing as this is Alpha 3 Wubi likely isn't well tested (plus I'm outside my knowledge area - I've never used Wubi).

Does GRUB2 even know how to boot a Wubi install?

--edit
Re-read psyke's post, so no, GRUB(2) can't boot Wubi.

---

### Post by Coolaaron88 on 2009-07-26
Apparently not unfortunately, I did an upgrade from jaunty to karmic before but it was really laggy and I couldn't really move around to see what the problem was. So I tried doing a fresh install and thats what led me here. Ill install a fresh jaunty and then upgrade afterward. Hopefully that will fix my issue. Thanks for all the support. I will reply with how it went.

---

### Post by Coolaaron88 on 2009-07-26
OK I can announce that the upgrade to Koala from Jaunty was successful. No lag and now Im just at the mercy of all the bugs that exist now. Thank everyone.

---

### Post by ranch hand on 2009-07-27
From what I was reading earlier today, wubi is not ready to use for 9.10 yet at all.

This is for folks that may have come in late to this thread.

---

### Post by Coolaaron88 on 2009-07-27
> **ranch hand said:**
> From what I was reading earlier today, wubi is not ready to use for 9.10 yet at all.

This is for folks that may have come in late to this thread.
Thanks for that heads up. I got around that problem but its good to know.

---

