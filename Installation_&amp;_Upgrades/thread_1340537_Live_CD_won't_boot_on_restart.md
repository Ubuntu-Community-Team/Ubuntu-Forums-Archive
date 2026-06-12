---
title: "Live CD won't boot on restart"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by alreadytaken4536 on 2009-11-28
Hello, I'm trying to boot the live CD from a TOSHIBA laptop running Windows Vista. I burned the disc with the correct software on a lightscribe HP CD-R. When I go into My Computer, it shows the Ubuntu disc in the CD drive and it appears to have burned correctly, when I run the disc it gives me options on installing or simply booting with the disc in the drive. When I restart the laptop, all it does is take me into Vista. Is there a step I'm missing?

---

### Post by mechro on 2009-11-28
You probably need to change your Boot Device order in the BIOS. When you first power up the computer you might see a message that tells you to press such and such a key to enter the BIOS. On mine I have to press the Delete button.

If you've got a manual it might tell you in there.

Having said that, if you're able to boot other CD/DVD's eg Windows then that would indicate a problem with your Ubuntu disc, possibly a bad burn.

---

### Post by alreadytaken4536 on 2009-11-28
> **mechro said:**
> You probably need to change your Boot Device order in the BIOS. When you first power up the computer you might see a message that tells you to press such and such a key to enter the BIOS. On mine I have to press the Delete button.

If you've got a manual it might tell you in there.

Having said that, if you're able to boot other CD/DVD's eg Windows then that would indicate a problem with your Ubuntu disc, possibly a bad burn.
I haven't done anything like this before and I don't know how to do anything with the BIOS.

---

### Post by mechro on 2009-11-28
Have you ever booted your laptop from a CD/DVD?

---

### Post by alreadytaken4536 on 2009-11-28
> **mechro said:**
> Have you ever booted your laptop from a CD/DVD?
No. I've never installed an operating system period.

---

### Post by lisati on 2009-11-28
I use a Toshiba laptop. When I want to start the computer from CD/DVD I need to push F12 while the Toshiba logo is showing at power up. Hope this helps.

---

### Post by mechro on 2009-11-28
OK. You'll need to change the boot order in the BIOS.

Basically when you turn on your computer it checks a list to see what to boot first. In your case it's probably set to boot the Hard Drive first so you need to alter this list to put your CD/DVD drive first.

Have a read of the following link which gives an explanation...

[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

If you can give me as much information as you can about your laptop I might be able to find a manual and tell you which buttons to press.

---

### Post by mechro on 2009-11-28
+1 for what lisati said. Nice and simple. Hope it works.:D

---

### Post by alreadytaken4536 on 2009-11-28
> **lisati said:**
> I use a Toshiba laptop. When I want to start the computer from CD/DVD I need to push F12 while the Toshiba logo is showing at power up. Hope this helps.
It worked and it's running great. Thanks!

---

