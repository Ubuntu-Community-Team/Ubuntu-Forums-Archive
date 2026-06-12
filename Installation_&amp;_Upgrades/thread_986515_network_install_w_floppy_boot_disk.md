---
title: "network install w/ floppy boot disk"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by korokinopio on 2008-11-18
Hi

I have 2 computers, a Desktop (this one) and a laptop that does not have a CD drive.

on my desktop I am running Ubuntu 8.10 Desktop edition. I currently do not have an operatng system on my laptop.

My laptop cannot natively boot from the network, nor can it boot from a usb flash stick, but it can boot from an external floppy drive, which i have.

therefore, what I am hoping to accomplish is booting from the floppy disk, with the network active, and installing ubuntu 8.10 onto my laptop.

the only tutorial i have been able to find is [this one]("http://mywheel.net/blog/index.php/ubuntu-network-install/").

now, let me say that I am not a total noob when it comes to ubuntu, or linux for that matter, but i am not a pro either, and i find that tutorial to be hard to follow.

does anyone know how i would go about doing this? please be as specific as possible, thanks

---

### Post by korokinopio on 2008-11-19
Been almost a day, thought I would bump and update saying I haven't gotten any closer.

---

### Post by frankos44 on 2009-09-08
> **korokinopio said:**
> Been almost a day, thought I would bump and update saying I haven't gotten any closer.

You could try PXE but you will need to configure your other computer to be a PXE server for that.

I would love to find a Ubuntu boot floppy that configures your network card and allows you to install via the internet, i know its is possible.. I will keep looking

---

### Post by Fafler on 2009-09-08
Some of the older versions of Ubuntu should include floppy images. Find and install something like 6.04 and upgrade?

---

### Post by frankos44 on 2009-09-08
> **Fafler said:**
> Some of the older versions of Ubuntu should include floppy images. Find and install something like 6.04 and upgrade?

Come to think of it, I actually made some once. I cant remember if it supported network install though. I cant install through usb or cdrom on this particular device.

---

### Post by frankos44 on 2009-09-08
Smart boot manager look cool.. [http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

---

### Post by Fafler on 2009-09-08
Is network install really necessary? If you have a boot disk with the kernel and a root disk with a preliminary root file system, it should get you long enough to use a USB cdrom drive.

---

### Post by frankos44 on 2009-09-08
I agree... if there is usb available.

---

