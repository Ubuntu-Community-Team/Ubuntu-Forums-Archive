---
title: "How to install ubuntu without putting it into cd or any other media..?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by ranjithnair on 2008-06-19
i want to use the live cd without putting it into cd or any other media....i want to know how to load the image in windows sot that when i restart i may be able to boot into live cd......somebody suggested me to use daemon tools..is it possible to do so....

---

### Post by Dizzle7677 on 2008-06-19
You might want to check out this site about mounting/using it virtually within windoze.
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

---

### Post by BLTicklemonster on 2008-06-19
I'm running basic ubuntu on a 64 bit machine, and want to install ubuntu 64 bit, but dad gummit if I can't get a cd to burn right. Every one I do, upon verification in k3b says that the first part of the burned disk differs from the first part of the image file. The computer won't boot from any of these.

So can I, in ubuntu, mount an iso and install ubuntu to a partition that I want it on?

---

### Post by wpshooter on 2008-06-19
What speed are you burning at ?  Burn at 4X or slower.

---

### Post by avtolle on 2008-06-19
> **BLTicklemonster said:**
> I'm running basic ubuntu on a 64 bit machine, and want to install ubuntu 64 bit, but dad gummit if I can't get a cd to burn right. Every one I do, upon verification in k3b says that the first part of the burned disk differs from the first part of the image file. The computer won't boot from any of these.

So can I, in ubuntu, mount an iso and install ubuntu to a partition that I want it on?
Give a look at this: [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

---

### Post by BLTicklemonster on 2008-06-19
Auto, but I'll try setting it at 4, and I'll look at the link provided, too.

Thanks (I suppose you're both) guys!

---

### Post by VMC on 2008-06-19
> **ranjithnair said:**
> i want to use the live cd without putting it into cd or any other media....i want to know how to load the image in windows sot that when i restart i may be able to boot into live cd......somebody suggested me to use daemon tools..is it possible to do so....

I don't see how this is possible. If you boot up Windows, daemon tools just uses your ISO as a virtual CD. You can use that to look inside but that won't help to boot.

Maybe a virtual machine would work like Virtualbox. With a VM it isn't possible to boot Linux while Windows is running. I haven't used. Wubi makes a file system inside Windows. Maybe this is the solution your after.

---

### Post by Therion on 2008-06-19
I don't see how this is going to be possible...
> **ranjithnair said:**
> i want to use the live cd without putting it into cd or any other media...
Okay, but you HAVE to boot to an Operating System, so if the LiveCD is not in the drive, that means booting into Windows.  You can then run Ubuntu in virtual environment from within Windows if you want, but a LiveCD/DVD is just that... a CD or a DVD.

> **ranjithnair said:**
> ...i want to know how to load the image in windows so that when i restart i may be able to boot into live cd...
That just doesn't make any sense.  

Maybe you want to "dual-boot"?  Meaning when you restart your PC you have the choice of booting into either Windows or Ubuntu without needing the Ubuntu LiveCD?

It boils down to three options, really:

1.  Run Ubuntu from a LiveCD/DVD.
2.  Run Ubuntu in Virtual Box environment.
3.  Run Ubuntu as one-half a dual-boot setup, alongside Windows.

---

### Post by BLTicklemonster on 2008-06-20
Is there not an installer on the cd you can get to via the terminal and see the setup dialog, and just install ubuntu to a drive/partition of your choice while still in ubuntu? Seems like that would be a plus right there. You could even mount an iso file and do it from there without ever having to burn a cd or boot to a live cd. I mean heck, WE ALREADY LIKE UBUNTU, why would we even need the live cd, eh?

---

### Post by VMC on 2008-06-20
> **BLTicklemonster said:**
> Is there not an installer on the cd you can get to via the terminal and see the setup dialog, and just install ubuntu to a drive/partition of your choice while still in ubuntu? Seems like that would be a plus right there. You could even mount an iso file and do it from there without ever having to burn a cd or boot to a live cd. I mean heck, WE ALREADY LIKE UBUNTU, why would we even need the live cd, eh?

Sounds like your talking about loop-back. I will give you two links on the subject:
[http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html](http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html)
This one is for Lunar Linux. Substitute ubuntu:
[http://wiki.lunar-linux.org/index.php/Installation:No_CD](http://wiki.lunar-linux.org/index.php/Installation:No_CD)

---

### Post by BLTicklemonster on 2008-06-20
As for burning at 4x, I tried it in k3b and brazero, and the cds still came out messed up. k3b says that the 1st section on the original differs from the original. Brazero just says something different (late last night when I got done, and I don't remember the brazero message exactly). That's two different iso files that were downloaded at different times. 

I'll try the link posted above perhaps this evening, thank you.

---

### Post by BLTicklemonster on 2008-06-20
Thanks for the links, but I don't trust myself enough to go for it when they are written for a different distribution. I don't think I'll know exactly what to put where.

The first link look like it will be installed from a usb drive, so that won't do me any good, but I like the idea of the second one.

---

