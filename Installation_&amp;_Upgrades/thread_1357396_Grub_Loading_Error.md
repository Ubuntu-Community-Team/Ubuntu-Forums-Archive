---
title: "Grub Loading Error"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by AJH101 on 2009-12-17
Hi I am trying to install 9.10 but get the following error. Has anyone got any ideas how I can get this running?
 
Grub loading
error: unknown file system
grub rescue:
 
Thanks!

---

### Post by AJH101 on 2009-12-17
By the way this was when trying to boot from CD!

---

### Post by presence1960 on 2009-12-17
> **AJH101 said:**
> By the way this was when trying to boot from CD!

Your CD may be corrupted. 

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded prior to burning it to CD?

Did you burn the iso as an image to CD at 4x-8x speed? If not then do so. Higher speeds are OK for data, music & video files but not as good for an iso image. One file missed or burbt incorrectly will render the image on the CD no good.

I would also check your documentation for your machine or go to the manufacturer's web site to get your manual. There has to be a way to change or adjust the boot order in BIOS.

**_Please do not start duplicate threads, I saw this same problem on another thread you created . One problem = one thread!_** [http://ubuntuforums.org/showthread.php?t=1356038](http://ubuntuforums.org/showthread.php?t=1356038)

---

