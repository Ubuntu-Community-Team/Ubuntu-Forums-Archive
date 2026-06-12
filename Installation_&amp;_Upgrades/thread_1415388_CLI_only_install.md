---
title: "CLI only install"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by sideaway on 2010-02-24
I have a very old computer... It's a Compaq Armada 1592DT. 200mhz w/ 92mb ram. I want a CLI installation of Ubuntu to run it. Note, it does not have an ethernet port, I have USB dongle that has an ethernet adaptor. Which I've used with Puppy linux, but I can't get it to work with the alternative install CD, so the CLI installation from there is impossible.

I have 32 bit versions of nearly every Ubuntu _*desktop*_ version from 6.06 up to 9.10 (including some alphas for 10.04), I'm using 6.06 because it's the oldest supported version. Is there a way to install a CLI only installation from this live CD?

---

### Post by wojox on 2010-02-24
Download and burn the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") . At the BOOT: prompt type cli

---

### Post by sideaway on 2010-02-24
I tried the 6.06 mini iso, it won't install without an internet connection.

---

### Post by lisati on 2010-02-24
> **sideaway said:**
> I have a very old computer... It's a Compaq Armada 1592DT. 200mhz w/ 92mb ram. I want a CLI installation of Ubuntu to run it. Note, it does not have an ethernet port, I have USB dongle that has an ethernet adaptor. Which I've used with Puppy linux, but I can't get it to work with the alternative install CD, so the CLI installation from there is impossible.

I have 32 bit versions of nearly every Ubuntu _*desktop*_ version from 6.06 up to 9.10 (including some alphas for 10.04), I'm using 6.06 because it's the oldest supported version. Is there a way to install a CLI only installation from this live CD?

I have an old machine that has a CLI-only installation of 6.06. I can't remember the exact details, but I think there was an option available by pressing F4 before installing.

---

### Post by sideaway on 2010-02-24
Thanks lisati, I'm gonna try again. I tried a server version of 8.10, but it could not find or mount the CD drive, even saved the output of ls /dev and could not find my cdrom.

Ok I'm currently looking at the graphical interface of 6.06, all the options I have go from f1-6; help, language, keymap, VGA, accessibility, advanced options.

---

### Post by ajgreeny on 2010-02-24
You may need the Alternate Install CD, if you have no web connection.  With that CD you can choose all manner of different installation options.

---

### Post by sideaway on 2010-02-24
Is that just the Mini.iso? Because I have that, but it refuses to progress without a working internet connection.

---

### Post by sisco311 on 2010-02-24
You can use debootstrap to install Ubuntu from PuppyLinux:
[uhelp]8.04/installation-guide/i386/linux-upgrade.html[/uhelp].

I would go with the latest stable version (9.10), since the core of the system (usually) becomes faster with each new release.

You may also want to check out:  [thread=882596]HOWTO: Ubuntu CLI versions & Framebuffer Programs[/thread]

---

### Post by sisco311 on 2010-02-24
> **sideaway said:**
> Is that just the Mini.iso? Because I have that, but it refuses to progress without a working internet connection.

Nope, you can use the Alternate CD to install Ubuntu without a working internet connection,

---

### Post by robert shearer on 2010-02-24
Compaq Armada 1592DT. 200mhz w/ 92mb ram  
I have two of these bought for .20 cents apiece ! and have tried numerous distros.

The bios setting resides on a small partition on the hard drive.
Back it up and/or leave it there for future access.
I removed it on one before I tried to change the boot order and can no longer access this to allow it to boot from cd.

Have to move the hard-drive to the other, load the os, then move it back. Lots of dismantling.

Mine only had 4Gb hard drives (2Gb and 1Gb partitions for the fat16 max file limit and the small bios partition)

So far Puppy has been the most featured and usable of the distros with a gui.

However, I did try and was impressed with the remix of Hardy here...

 [http://kmandla.wordpress.com/projects/ubuntu-gtk12-remix/](http://kmandla.wordpress.com/projects/ubuntu-gtk12-remix/)

Which is a combination of a few gui apps and many cli apps.
May be worth a try ? and installs from cd.

---

### Post by sideaway on 2010-02-25
Hey thanks mate!

Found a mirror to download 6.06 alt CD. Got a server installation... it gets to GRUB, tried to boot, does approximately 2 lines of white text then just restarts... any ideas?

I think I've deleted the BIOS partition (long time ago from fiddling), but thankfully it automatically tries to boot from CD atm... I too found puppy the most useable, Turbopup w/ Dillo has resulted in the most success, but I want a Ubuntu CLI to learn more about the command line, nano, scripts and compiling etc, just general computer use w/o a GUI.

---

### Post by robert shearer on 2010-02-25
It probably stops with a line that mentions 'initramfs'.

(just a guess but it may mean initializing ram file-system, jump in and correct me anyone !)

This usually indicates too low a memory for the install to proceed though could be slow rather than stopped.

With such an old processor and low ram it might take several hours-to-days to complete.

You could just leave it a while (hours +) and see what happens or bail and try the GTK-remix I linked.

At the link page read through to the end for an overview and other download sites for the iso.

Cheers and happy experiments. :)

---

