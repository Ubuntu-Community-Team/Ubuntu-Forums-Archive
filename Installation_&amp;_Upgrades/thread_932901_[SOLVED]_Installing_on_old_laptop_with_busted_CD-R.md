---
title: "[SOLVED] Installing on old laptop with busted CD-ROM"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by HDave on 2008-09-28
Hi - I am a fairly experienced (and very happy) Ubuntu user.  I would like to install Ubuntu on an old Viao laptop we have at home.  It currently has Windows XP on it, but it is so screwed up from mis-fired MS updates, that it barely works.  Plus after a year of looking over my shoulder, the wife is finally will to try Linux.

My problem is this.  The CD-ROM drive is 100% dead, and the BIOS on the thing is so old it doesn't have the option to boot from a USB stick (I have a 8.04 live USB stick).

It will read a USB drive once I am booted into windows.  Is there a way to install Ubuntu from a running Windows session from a USB drive?  I could go either dual-boot, or wiping out Windows...don't care.

---

### Post by Pumalite on 2008-09-28
Try:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by HDave on 2008-10-01
Thanks for the link.  I had heard of Wubi, but didn't really understand the intent.  Apparently, it creates a big file on the windows c: drive that acts as a loopback device for an ext3 Ubuntu install...it also touches the windows boot.ini to inject Ubuntu in there.

At any rate, it worked great.  I put the Wubi installer on the machine via a USB stick, run the program from Windows, and viola - 3 hours late it was perfectly installed.

There was only one hiccup, however.  After it installed and rebooted, I was dropped into busybox.  Frustrated, I went to another computer and found this [thread]("http://ubuntuforums.org/showthread.php?p=5633657").  Apparently when Windows shuts down abnormally (and when doesn't it) the hard drive can't be mounted.

I am debating filing a WUBI bug to have them provide an option for /etc/fstab to force mount the drive if it is flagged as being messed up by Windows.

Overall, I couldn't be happier...thanks for the lead.

---

### Post by Pumalite on 2008-10-01
You are welcome. Good luck!

---

