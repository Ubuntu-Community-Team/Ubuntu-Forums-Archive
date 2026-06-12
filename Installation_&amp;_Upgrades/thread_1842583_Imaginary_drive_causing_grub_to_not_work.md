---
title: "Imaginary drive causing grub to not work"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by hyper2hottie on 2011-09-11
I have already solved this problem but am posting in case someone has a similar problem.  I would also appreciate any explanations about why I had this issue.

My problem started when I broke my ubuntu installation.  After a many attempts to fix it I decided to reinstall.  The install worked except that when I booted grub would say:
```

Error: Device not found: "crazyHexString"

```
My system has windows installed on a 60 GB ssd and ubuntu installed on a 60GB partition on a 1TB drive.  I assumed that grub was broken and reinstalled ubuntu about 10 times.  

After a while I went into the BIOS and looked at my boot order.  Here I found:

```
2.2 TB INFINITY
```

This was odd because I do not have a 2.2 TB drive in my system.  I disabled this drive, removed it from the boot order, and reinstalled ubuntu.  This fixed grub.  It now loads up and windows and ubuntu both work.

So my question is where might this virtual drive have come from?  
I am also curios why disabling it in the BIOS fixed grub.  
Does grub get the bootable drives from the BIOS?

An interesting point is that when I disabled the 2.2 TB INFINITY I was no longer able to pus F12 to select the device to boot from.

---

