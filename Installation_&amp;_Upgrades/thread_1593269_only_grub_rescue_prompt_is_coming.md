---
title: "only grub rescue prompt is coming"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Praveen30 on 2010-10-11
hello,

my friend has installed ubuntu 10.04 inside windows.he worked on ubuntu for 2-3 days and then he updated his system.after updation when he restarted the system only this is coming-

error:
no such device:(some numbers here..)
grub rescue>

please help..i do not want him to lose faith on linux....

---

### Post by Rubi1200 on 2010-10-11
Hi Praveen30,
if you mean a Wubi install, we need a bit more information, but don't worry there is a solution :)

Can your friend boot into Windows at all?

Does he remember if it was an update for Wubi or just normal updates?

Does he have a Windows installation/recovery CD and/or an Ubuntu CD?

---

### Post by Praveen30 on 2010-10-11
> **Rubi1200 said:**
> Hi Praveen30,
if you mean a Wubi install, we need a bit more information, but don't worry there is a solution :)

Can your friend boot into Windows at all?

Does he remember if it was an update for Wubi or just normal updates?

Does he have a Windows installation/recovery CD and/or an Ubuntu CD?

no, he is not able to boot into windows at all.

i have a cd and his laptop is with me so i can do whatever you will say...

actually he had updated first time his ubuntu after installation..

i have just inserted the live cd....so what next???

---

### Post by Rubi1200 on 2010-10-11
Hi,
if you have the Windows CD, then follow these instructions to restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

If you have an Ubuntu CD:

Restore basic windows boot loader - universe enabled
 	Code:
```
sudo apt-get install lilo
```
 	Code:
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR.

courtesy of forum member oldfred.

This will install a basic Windows bootloader and allow you to get back into Windows.

Let me know if you have any questions.

---

### Post by Roreek on 2010-10-14
Rubi1200 (& oldfred),

thank you.

I had the same problem as Praveen30 after updating my Wubi install from Lucid to Maverick.

As my netbook doesn't have an optical drive, I booted from USB stick, (created with [unetbootin]("http://unetbootin.sourceforge.net/")) then followed the instructions for lilo.

And it worked -  back to normal in minutes.

---

