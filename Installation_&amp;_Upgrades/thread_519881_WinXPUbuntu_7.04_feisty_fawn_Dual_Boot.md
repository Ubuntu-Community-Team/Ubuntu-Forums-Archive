---
title: "WinXP/Ubuntu 7.04 feisty fawn Dual Boot"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by phearsome on 2007-08-07
Hello.
I recently bought a new Hard drive for my old laptop.
I decided to dual boot Ubuntu feisty fawn and windows xp on it.
40gb Ubuntu 40gb windows xp
I started by installing Ubuntu through a boot server (well, my brother did it for me), and it was working perfectly fine. 
UNTIL I installed Windows.
Windows completely took over the computer, and now I am unable to access Ubuntu.
A friend of mine told me I needed to get an Ubuntu CD, but I don't have any CD-R's and I really don't feel like waiting 6-10 weeks.
Is there any other way for me to fix this problem?
Grateful for any help, thanks in advance. :)

---

### Post by jnorthr on 2007-08-07
When you say you are unable to access ubuntu, what do you mean /? Please describe your condition more clearly. If you power off and power on your machine, do you receive a supergrub menu screen before windows loads ? This supergrub menu will allow you to select the operating system you wish to start. If you are not given this choice when you reboot, then the windows installation may have toasted the master boot record, by over-writing the small program written into track 1 of your boot disk. If this is your situation you may still be able to regain access to both ubuntu and wondows if you can acquire a supergrub partition manager. This is something like the M/s dos fdisk command. You may need to find someone who can burn you either a supergrub cd or the full ubuntu live cd. From that you can then access the partition tables, restore supergrub to the first sector in your disk and proceed from there without the need to fully reinstall either ubuntu or windows.

---

### Post by phearsome on 2007-08-07
I don't even know what supergrub is so I bet the problem lies there :) I'll look it up tyvm

---

### Post by CowzRule on 2007-08-07
You should have installed Windows first. When you installed Windows after Ubuntu, Windows over wrote Grub. You need to restore Grub. Just do a search on how to restore grub. You'll get hits on doing so with a live cd and with a floppy called Super Grub Disk. See [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/") for info about the Super Grub Disk.

---

