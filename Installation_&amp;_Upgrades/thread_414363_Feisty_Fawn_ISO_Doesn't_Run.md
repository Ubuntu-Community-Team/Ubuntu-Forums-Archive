---
title: "Feisty Fawn ISO Doesn't Run"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by nakile on 2007-04-19
I have 5.10 installed along with Windows XP, but I'm planing on just overwriting it (5.10) with Feisty Fawn because I never use it and have very few important things on there.

I burned the Feisty ISO correctly and everything, boot order is set to CD drive first and all. But I put the disc in, and it goes right to GRUB with no care for the CD at all.

I have a Dell Inspiron 5100, by the way.

---

### Post by bwhite82 on 2007-04-19
Try hitting F12 right when you turn the PC on (while the load bar is being displayed, this goes quickly), it should take you to a boot menu, select "Boot to CDROM" and you should be good to go. If for some reason F12 doesn't work for you, try all of the F-keys.

---

### Post by eyelessfade on 2007-04-19
you may want to check that cd to see if its been burnt correctly. match the md5 sum to the md5sum on the download servers.

---

### Post by cogadh on 2007-04-19
If the F12 option doesn't work, just hit the F2 key while the Dell splash screen is up. That will get you into the BIOS settings. Find the page with the Boot Order settings and put your CD drive at the top of the list. Reboot with the CD in the drive and it should run normally.

---

### Post by nakile on 2007-04-19
It's strange. I've tried F2 and F12 several times. They don't do anything.

---

### Post by SL666 on 2007-04-19
I have the same issue, but when i look at the CD in XP it looks like its still blank? but it burnt successfully..? NFI.

Cheers Steve.

---

### Post by nakile on 2007-04-19
I tried running my old 5.10 CD, which worked correctly back when I used it, but now does the same thing as the Feisty CD.

---

### Post by cogadh on 2007-04-19
> **nakile said:**
> It's strange. I've tried F2 and F12 several times. They don't do anything.

It's a timing thing. You need to hit either key repeatedly while the Dell logo is still on the screen and before Windows begins to load.

> **SL666 said:**
> I have the same issue, but when i look at the CD in XP it looks like its still blank? but it burnt successfully..? NFI.

Cheers Steve.

That CD ain't right, you can actually run it in Windows and install Windows versions of some of the Linux apps.

---

### Post by bwhite82 on 2007-04-19
> **SL666 said:**
> I have the same issue, but when i look at the CD in XP it looks like its still blank? but it burnt successfully..? NFI.

Cheers Steve.

Whatever burn program you're using, you need to use the "Burn ISO image" option (if it's available). Simply burning a "data" disk or any other option will not work.

---

### Post by SL666 on 2007-04-19
I burnt the ISO correctly, but for some reason nothing seems to recognise the disk - i assume I've just burnt a coaster, but it seems that a few people are having the same problem?

Any ideas if it should be an 80minute CD or something like that?

---

### Post by cogadh on 2007-04-20
If it can't be read, then it wasn't burnt correctly, it is a coaster. You just need a standard 700 MB CD to burn to (The final burn is 697 MB). Once burned Windows and Linux will both recognize the CD as "Ubuntu 7.04 i386".

---

### Post by SL666 on 2007-04-20
bizzarely (have burnt many a CD and many an ISO) i seem to have had issues today.. probably just related to how  S-M-R-T i am.. 

burnt the image using a different program, on a different brand of CD's and it was fine - in fact im using it now.

---

### Post by nakile on 2007-05-05
Tried again today. I was able to change the boot order, but still nothing.

---

