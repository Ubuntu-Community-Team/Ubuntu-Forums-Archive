---
title: "Installation Advice, Please"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by budzooka on 2006-12-24
Hello and Happy Holidays!

Small problem in need of some advice:

An instructor of mine at school gave me a few machines to tinker around with and the one with the most juice etc has Fedora Core installed. I figured that I would install Ubuntu on this box and let the kids take it to their moms, since they are getting better and better using it and teaching their friends as well

Anyways - I checked the BIOS and have it set correctly to boot from the CD first and attempted installation this way to no avail. No matter what I attempt, I keep ending up at the Fedora Core log-in screen. Since this machine was orphaned, I have no way of getting a UID/password and  was wondering if anyone has any suggestions on overwriting this machines OS?

Any help is appreciated

budzooka

---

### Post by meng on 2006-12-24
If it is set to boot from the CD first, then the CD is defective - either a bad burn on a bad download. Bad burn - reburn at lower speed. Bad iso download - confirm by checking md5sum.
3rd possibility: CD-ROM drive broken.

---

### Post by wpshooter on 2006-12-24
> **budzooka said:**
> Hello and Happy Holidays!

Small problem in need of some advice:

An instructor of mine at school gave me a few machines to tinker around with and the one with the most juice etc has Fedora Core installed. I figured that I would install Ubuntu on this box and let the kids take it to their moms, since they are getting better and better using it and teaching their friends as well

Anyways - I checked the BIOS and have it set correctly to boot from the CD first and attempted installation this way to no avail. No matter what I attempt, I keep ending up at the Fedora Core log-in screen. Since this machine was orphaned, I have no way of getting a UID/password and  was wondering if anyone has any suggestions on overwriting this machines OS?

Any help is appreciated

budzooka

Yes, get the **KILLDISK** program and **WIPE** that bad Fedora O/S completely off of there and I bet the Ubuntu can then boot.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by petok on 2006-12-24
Can't you boot from a floppy and then access the cdrom somehow? I dont think removing Fedora would solve the problem

---

### Post by meng on 2006-12-24
Try using the CD to boot another computer. If it works, then it's less likely it's a CD problem, but could still be a drive problem.

---

### Post by wpshooter on 2006-12-24
Budzooka:

Are you positive that you **BURNED** the Ubuntu ISO image to a CD as opposed to **copying** the image to the CD ?

It has to be **BURNED**, in order to be bootable.

---

### Post by budzooka on 2006-12-24
Guys - thanks for the responses

The CD boots just fine on 2 other machnes and my laptop, I used the same CD to install 2 machines at work as well..... 

I'm going to try that Killdisk you are talking about and I'll post the results.....

Thanks again

budzooka

---

### Post by meng on 2006-12-24
Check whether the CD drive itself may be faulty.

---

### Post by budzooka on 2006-12-25
> **meng said:**
> Check whether the CD drive itself may be faulty.

I am going to check that as well...... thanks

budzooka

---

