---
title: "Reinstalling Windows after Ubuntu"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Dan++ on 2008-05-25
I have three drives: 2x 80GB HDDs and one 500GB (which stores all of my documents).

I installed Ubuntu a few days ago on my second drive which was previously the D: drive for Windows XP, and for a couple of days I was dual-booting just fine. Until one day when I realised Windows had been wiped completely from the first 80GB HD, C. My theory is that I was attempting to mount it and did something crazy, or when I was learning how to format my USB memory stick in BASH, I accidentally wiped the C drive too.

This wasn't a big issue, because no documents were on there, only programs, so I thought "I'll reinstall at some point". So now I'm trying to reinstall. Unfortunately, during the installation process, it tried to do a chkdsk of the Z drive (the 500GB one) and when it got to stage 2 of that process, kept looping through "Deleting the index $0 at file 25" over and over and over.

I restarted and it went back into Windows installation and got to this stage and kept looping again.

So I thought, "I'll find out how to fix this problem from Ubuntu" and followed [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")* to get GRUB back so I could boot up Ubuntu. I followed it and it returned all the expected messages, rebooted and Windows booted up without any warning and did it's whole shpiel again with index $0 at file 25.

Basically, I'm a bit screwed at the moment. :( Any ideas?

I'd appreciate it massively. Thank you :)

*by the way, I wanted to overwrite the Windows bootloader so that's what I did, rather than any other section, although I did try "quick start" at first in my confusion.

---

### Post by Partyboi2 on 2008-05-25
What options did you use with chkdsk? Have you tried
```
chkdsk /F /V /R 
```

---

### Post by meierfra. on 2008-05-25
Maybe grub got installed onto a different drive than you think. See what happens if you boot from the other drives.

If that did not solve your problem, boot from a Live CD and post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

Also go to Places->Computer and double click the icon for your ubuntu partition. Navigate to /boot  and then to /boot/grub. Open the file menu.lst and post the content.

---

