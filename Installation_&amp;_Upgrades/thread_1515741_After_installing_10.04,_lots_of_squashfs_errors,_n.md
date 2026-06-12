---
title: "After installing 10.04, lots of squashfs errors, no end"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by rpoupore on 2010-06-22
I'm a newbie to Linux and Ubuntu. I got some help getting past a problem with my NVIDIA problem (thanks, Cariboo907!) and saw how ubuntu Desktop edition looks and works from the LiveCD. I wanted to use my Linksys USB wireless adapter, but couldn't write to the CD, so I decided to install 10.04.  I guess I stupidly decided to get rid of the Windows XP partition so Ubuntu could use the entire 250 GB hard drive.

After the install and repartitioning was complete, I eagerly pressed the restart button, and haven't been able to get past SQUASHFS errors since then. 

1. Restart from successful Live CD start
The error messages scroll off the screen at the top. I'm looking at it now (from a restart when I had booted from LiveCD).

"file: error while loading shared libraries: /usr/lib/libmagic.so.1: cannot read file data: Input/output error." followed by lots of squashfs errors.

I think this is from restarting rather than cold booting. System must be looking to load from CD (which I removed).

2. Full reboot after powering off.
error message displays for about 1/2 second: what I can read is:
"nForce2_smbus 0000:00:01a  Error probing SMB1"  (this is close but not fully accurate, the last three words are correct)
and then the Monitor is Working Out of Scan Range message.

This is the second time I've done the full install. Any ideas how to capture the log of the start up? or how to get it to boot from the disk?

---

### Post by rpoupore on 2010-06-24
bump --
the PC is a Compaq Presario SR1950NX Media Center

I'm guessing that having Ubuntu repartition the disk is part of the problem. Booting from Live CD, I can examine the 250GB drive and its contents. The hidden System Recovery partition is gone.

Is there a way to capture a log of boot messages? I'm assuming that the quiet splash parameter is about suppressing these message from going to the screen.

Thanks

---

### Post by dino99 on 2010-06-24
why are you using squashfs ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by rpoupore on 2010-06-24
Dino99 -
thanks for the link, I'll check out the hot-to.

You asked why I'm using squashfs. I have no idea. I installed 10.04 to my hard drive (launched the install from the Live CD Ubuntu menu)

I assumed the "fs" meant "file system", but I didn't choose it.

Just trying to install Ubuntu 10.04 as my singe booting OS on my old desktop. Eventually I'd like to have it run as a file/print server on my home wireless network. Until then, I want to use it to learn about Linux/Ubuntu.

---

### Post by rpoupore on 2010-06-24
hi dino99 - THANKS!  Progress but not total success!
your link to more info got me a bit closer!  Holding Shift down after bios process got me to the Grub menu. 

After first boot attempt resulted in "Monitor is working out of scan range" message, I tried to edit the boot commands. The option the caliboo97 pointed me to was "NOMODESET"

After that had same result, I tried putting NOMODESET in different lines. Also deleted "quiet splash" so I could see some feedback. 

Can't get past the Out of Scan Range problem, possibly because I don't know where to insert NOMODEST (no jokes please!).

Any related suggestions?

If I get past this problem, is there a way to save the boot command file, so it will boot up naturally into Ubuntu without shift key and editing?

---

### Post by rpoupore on 2010-06-25
I'm going to mark this as SOLVED even though I still have problems. I'll create a new report for those.


I think I figured out where those SQUASHFS error messages were coming from. I was running off the Live CD, and wanted to reboot to the hard disk to test out something. I popped out the CD and rebooted. When the PC was shutting down, it was trying to shut down the system from the CD, and couldn't find the files. The CD uses SQUASHFS to manage the read-only files on the CD in a compressed format for booting.

---

