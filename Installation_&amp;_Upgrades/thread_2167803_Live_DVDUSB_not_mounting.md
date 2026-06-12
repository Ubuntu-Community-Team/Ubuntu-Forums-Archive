---
title: "Live DVD/USB not mounting"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by Samuel_Lee on 2013-08-15
Hey all, newbie here.
I've just tried out Linux Mint 15, and I like it but I kinda want to install Ubuntu 13 over it
but I cannot seem to get the Live DVD nor the USB installer to run!

It says:

Error: Unable to Mount PENDRIVE
Error mounting /dev/sdb1 at /media/family/PENDRIVE: Command-line
`mount -t "vfat" -o
"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush"
"/dev/sdb1" "/media/family/PENDRIVE"' exited with non-zero exit status
32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The Desktop I'm using is a Dell Inspiron 620.
And because of current slow internet (will upgrade soon), I haven't had the chance to do any updates or anything, if that helps.
Thank You!!!!!

---

### Post by Bucky Ball on 2013-08-15
Welcome to the forums.

Apologies if this is a silly question, but are you booting from the USB dongle and not trying to launch while running Mint? ;)

---

### Post by Samuel_Lee on 2013-08-15
is there a way to launch it while running mint? haha sorry im so new to this
well when i just insert the Live DVD or the USB thats the that error message that pops out.
when i try double clicking it, the same message pops out.

---

### Post by Bucky Ball on 2013-08-15
> **Samuel_Lee said:**
> is there a way to launch it while running mint?

Absolutely not. Not the intention. Are you setting the BIOS or the boot device to be the CD then booting the machine directly from the CD/DVD?

DO NOT attempt to run this from an already running install. If you are sticking it in while you are in Linux Mint, you are doing it wrong and you will not get anything happening. We can't help with this as there is no fix or issue. It is simply the wrong procedure.

Boot the machine, press whatever key you need to to get to the BIOS (or sometimes F12 or another key will let you just select the boot device) then boot from the CD, NOT into Mint. If you are not booting directly from the CD when you start you machine, then you should be. 

Apologies if you are already doing this. Please confirm either way and also, boot directly from the CD/DVD and confirm this is the error message you are getting DIRECTLY from a CD boot, not when inserting and attempting to launch in Mint. 

Let us know.

PS: This: 'Error mounting /dev/sdb1 at /media/family/PENDRIVE: Command-line' suggest you are trying to do this while in Mint. It is looking for a mount point in Mint at /media/family/PENDRIVE, and that looks like where you are trying to mount it. If you actually created that mount point manually, you might be able to mount the USB dongle, but that still wouldn't let you install Ubuntu. As I say, need to boot from the CD. Not designed to install this way (and there's no way you can install over a system that is already running!).

---

### Post by Samuel_Lee on 2013-08-15
it works!
Thank you so much for you help!

---

### Post by Bucky Ball on 2013-08-16
All good and great that you got it going! ;)

To help others with the same probs, could you please mark thread as solved by following the link in my signature.

Don't hesitate to post in the appropriate sub-forum and using a descriptive title for any futher support requests. Good luck and enjoy the OS, the learning curve and the forums!

---

