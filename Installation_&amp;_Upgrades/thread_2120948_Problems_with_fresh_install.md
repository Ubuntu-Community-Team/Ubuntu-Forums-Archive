---
title: "Problems with fresh install"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by graham88 on 2013-02-28
I made a bootable USB drive with the Ubuntu .iso using [_these_]("https://help.ubuntu.com/community/Installation/FromUSBStick") instructions. I try booting from the USB (both running Ubuntu from the USB and trying to install Ubuntu from the USB onto my hard drive) and I get the following...

error: invalid magic number.
error: you need to load the kernel first.

Any suggestions?

I am coming from Windows 7. This is my first shot at using Ubuntu.

---

### Post by mörgæs on 2013-02-28
Hi, welcome to the fora.

Which version of Buntu are you trying to boot? 
Does the USB stick work when booting other computers? 
Do you want to install Buntu in stead of Windows or in a double boot?

---

### Post by graham88 on 2013-02-28
I am trying to boot 12.10, 64 bit.
I'm not sure if I understand your second question, but I have not tried booting anything from this flash drive before on any computer.
I want to dual boot Windows and Ubuntu.

---

### Post by presence1960 on 2013-02-28
Can you get to the menu when you boot the USB? If so select check disk for errors and see what that reports back.

---

### Post by graham88 on 2013-02-28
The options that show up when I try to boot the USB are

Try Ubuntu without installing
Install Ubuntu
OWM install (for manufacturers)
Check disc for defects

All options result in the error display from OP.

---

### Post by presence1960 on 2013-02-28
Did you MD5SUM the downloaded iso to ensure it is not corrupted?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I always use unetbootin to create a bootable USB. There is both a linux and a windows version. Unetbootin has never failed me.

---

### Post by graham88 on 2013-02-28
MD5Sum was good. I'll try unetbootin and get back to you.

---

### Post by graham88 on 2013-02-28
Still didn't work... I did notice that for a split second before the menu shows up it says "secure boot not enabled." Could that be the issue, and if so how do I fix it?

---

### Post by graham88 on 2013-02-28
So I decided to try a different flash drive and it worked. I thought you could boot from any flash drive, but I guess not :-\ 

At least I got it figured out :-) 

Thanks for yalls help.

---

