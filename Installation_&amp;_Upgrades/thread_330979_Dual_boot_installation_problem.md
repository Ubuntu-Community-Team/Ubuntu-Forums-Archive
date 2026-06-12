---
title: "Dual boot installation problem"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by ceestand on 2007-01-03
I am attempting to install Ubuntu 6.10 desktop onto a Dell box with Windows XP SP2 already installed on it. I reinstalled over the Dell-configured installation, so there is only the base OS now. The single SCSI HDD has an ~80GB NTFS partition with WinXP on it, and the rest ~80GB is unallocated which I intended to install Ubuntu onto.

I burned a "bootable disc" in Nero and when I start up the box with the CD inside, it says booting from CD, then starting Caldera DOS. It then goes to another screen and hangs, advising me to hit Control-Alt-Delete to restart or hit any other key to close the offending application and resume; Neither of which works. Supposedly EMM386.EXE is throwing the error.

The error screen is like, if not exactly, the one reported in this post: [http://www.ubuntuforums.org/showthread.php?t=9276](http://www.ubuntuforums.org/showthread.php?t=9276)
The difference is I am running off an Intel chip.

I tried burning another disc using the built-in windows burner, but there I get "Boot from CD" and then it just loads Windows.

---

### Post by encompass on 2007-01-04
What is the image that your trying to burn... does it end with iso and have you checked it with md5sum?

---

### Post by ceestand on 2007-01-04
Thanks Encompass, it turns out I just was incorrectly burning the disc. In Nero, I should have chosen to burn a "Disk Image" instead of "Bootable Disk" Comes up fine now.

---

