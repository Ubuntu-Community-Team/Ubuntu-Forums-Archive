---
title: "Can't boot from ISO"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Sammm2514 on 2010-06-29
Ok, so I'm a newbie so just hang in there whilst I try to explain my problem.

I have an Acer desktop:
Aspire T671-TB7Z, Intel Pentium D 915, 160GB SATA, 1GB DDRII running on Vista Home Premium.

I have been trying for the past couple of hours to install Ubuntu onto it and have had absolutely no luck. I know that I made the disk containing the ISO correctly as it installed fine on to my laptop, I have also tried (using the guide on the website) to copy the ISO to USB. I boot from the cd drive and it just comes up with a black command screen and a cursor flashes a few times and then goes to a menu with options on how to start windows (Safe mode, etc). :confused::confused:

Any help would be much appreciated! Thanks in advance.

---

### Post by C.S.Cameron on 2010-06-29
If you already have the iso on your Vista PC you might try a MD5SUM check of the ISO file and if that is ok download UNetbootin and use that to make a Live USB.
If the ISO checks you could also make a Live USB booting from the Live CD and using Startup Disk Creator on your laptop.

---

### Post by Sammm2514 on 2010-06-29
Thanks for the advice I'll give that a try in the morning when I can get my head around it!

---

### Post by sgosnell on 2010-06-29
If you did an install from the CD to a laptop, it should work on a desktop.  It sounds like the computer isn't actually trying to boot from the CD drive.  Are you certain it's set as the first boot device in the BIOS?

---

### Post by wilee-nilee on 2010-06-29
> **c.s.cameron said:**
> if you already have the iso on your vista pc you might try a md5sum check of the iso file and if that is ok download unetbootin and use that to make a live usb.
If the iso checks you could also make a live usb booting from the live cd and using startup disk creator on your laptop.

+1

---

### Post by Sammm2514 on 2010-06-30
It's definately set to boot from the CD/DVD - I set that as first priority. I have it on a usb and that is set as second. It doesn't recognise any of those and just goes straight ahead and runs windows, even when I press F12 and manually choose to boot from CD/DVD. It's getting really very frustrating!

---

### Post by sgosnell on 2010-06-30
It has to be either a bad CD or a problem with your BIOS.  Impossible to tell from here.

---

### Post by wilee-nilee on 2010-06-30
> **Sammm2514 said:**
> It's definately set to boot from the CD/DVD - I set that as first priority. I have it on a usb and that is set as second. It doesn't recognise any of those and just goes straight ahead and runs windows, even when I press F12 and manually choose to boot from CD/DVD. It's getting really very frustrating!

So as C.S.Cameron suggested a md5sum check can be run on the ISO and the cd, also you want to burn the cd at a slowest speed possible, and I realize the thumb isn't working, I assume you have tried that from the f12 option.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I'm not sure what you have used to load the thumb but unetbootin has worked fine for me.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

