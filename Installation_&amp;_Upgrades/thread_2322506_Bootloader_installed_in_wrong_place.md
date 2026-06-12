---
title: "Bootloader installed in wrong place"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by Hopeatykki on 2016-04-28
So I tried installing Ubuntu on my old laptop. Everything went normally except that letters were missing from some word like the font would be corrupted. Oh well, I continued and boom, "where to install bootloader". I supposed it was same as where to install Ubuntu so I put sda1 (or something like that.) Next, just a line popping in and out after reboot. How can I reinstall bootloader or is my laptop worth nothing now?

---

### Post by Impavidus on 2016-04-28
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). If it doesn't work, post the link it gives you here.

The correct place to install the boot loader was probably sda, that is, the drive, not the partition boot sector.

---

### Post by Bucky Ball on 2016-04-28
> **Impavidus said:**
> Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). If it doesn't work, post the link it gives you here.

The correct place to install the boot loader was probably sda, that is, the drive, not the partition boot sector.

+1. The sda1 partition now, obviously, has the grub. Run the bootinfo and post the link that gives you here before running a recommended repair of Boot Repair, please. ;)

(You could also try 'Advanced Repair' in BR and install grub to the correct place, sda, and see if that makes a difference.)

If it is an old laptop you would be much better served by going for a lighter flavour. I suggest Xubuntu-core, Lubuntu or Xubuntu. Much smoother ride. Sounds like your machine is not coping with Ubuntu's graphics demands. 

Not sure what you're trying to install, but 16.04 LTS has just been released and has five years support so probably the place to start.

---

### Post by ka55o5 on 2016-04-28
> **Bucky Ball said:**
> [..] Xubuntu-core, Lubuntu or Xubuntu.
Ofc., BUT - was Ubuntu installed alongside of Windows and/or some other operating system?.. Because the automatic installer, setup, should have NO problems. What you needed to had done, was: install to the HDD **without** creating any partitions, whatsoever (it'll partition the drive, all on its own :))

---

### Post by Hopeatykki on 2016-05-20
I was trying to install the newest one and not alongside windows, I installed a distro over win7 a long time ago.

---

### Post by Hopeatykki on 2016-05-20
> **Impavidus said:**
> Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). If it doesn't work, post the link it gives you here.

The correct place to install the boot loader was probably sda, that is, the drive, not the partition boot sector.

I tried booting it with boot-repair (using 8GB Sony USB stick) but it says "Operating System not found" or something like that. Same thing trying to boot with ubuntu iso installed on the stick. I can get into GRUB but choosing Ubuntu will make the screen say "Gave up waiting for root device." Same with recovery mode but takes longer and shows a wall of code.

---

### Post by oldfred on 2016-05-20
Did you install Boot-Repair into the installer you used to install Ubuntu?
That often is the easiest way to get a working boot.

And you probably have an old copy of grub in MBR, that then cannot find the old install to boot.
If flash drive is correctly configured, it should boot directly.

---

### Post by Hopeatykki on 2016-05-21
> **oldfred said:**
> Did you install Boot-Repair into the installer you used to install Ubuntu?
That often is the easiest way to get a working boot.

And you probably have an old copy of grub in MBR, that then cannot find the old install to boot.
If flash drive is correctly configured, it should boot directly.

I installed Boot-Repair on the USB stick, the same I used to try and install Ubuntu, which didn't work out.

---

### Post by oldfred on 2016-05-21
You may need to redo flash drive then. It sounds like it is not booting and you are just booting hard drive's old grub.

---

