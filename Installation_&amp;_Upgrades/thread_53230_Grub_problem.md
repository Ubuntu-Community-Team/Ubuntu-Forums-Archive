---
title: "Grub problem"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by WaferMouse on 2005-07-30
Hi! I'm new to Ubuntu, trying it out because I've heard a lot of ex-Debian users are into it and also for the 64-bit support (which I've heard is better than Debian's).

Unfortunately I've had some problems. Whilst I can get the new 64-bit release of Debian to install fine from the CD, Ubuntu crashes.

So I've decided to try [these instructions](https://wiki.ubuntu.com/Installation/FromWindows), with the only changes being using the AMD64 linux and initrd files, and also using the latest grub for dos package from [here](http://sarovar.org/projects/grub4dos/). However, grub seems unable to find the menu.lst file.

I'm wondering whether it's because I have Windows installed somewhere other than the first partition. parted lists it as minor 4, in Linux it is /dev/hda4 and in boot.ini it is partition 3.

I'm also guessing I need to change the menu.lst to reflect this, but I'm more concerned with getting grub to even find menu.lst first.

Could anyone help?

---

### Post by amohanty on 2005-07-30
> Ubuntu crashes. 

How?? 
What happens after you install the amd64 version from CD and boot into it?

AM

---

### Post by WaferMouse on 2005-07-31
It doesn't finish installing. It hangs at a random point during the installation of the base packages.

---

### Post by amohanty on 2005-07-31
Wow that is strange. Did you verify the CD which you burned from the ISO image.

ALso menu.lst is in /boot/grub/menu.lst

If during partitioning you created a /boot it _must_ be on the primary master drive (doesnt matter if you only have one drive). If you didnt create one then the same applies to  /

AM

---

### Post by WaferMouse on 2005-07-31
I verified the CD from inside the installer and it checked out. I'm downloading it again right now, see if I have better luck with another copy.

Ahh, yeah, that would explain why grub4dos isn't working. I suppose I could do some partition jiggery pokery to fix that.

---

