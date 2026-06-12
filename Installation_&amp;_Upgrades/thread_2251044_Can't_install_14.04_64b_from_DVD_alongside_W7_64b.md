---
title: "Can't install 14.04 64b from DVD alongside W7 64b"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by Gergo_Santha on 2014-11-01
Hi!

I'm trying to install Ubuntu 14.04 from DVD which I've prepared by burning it as an image file. I'm not a new Ubuntu user and usually the installation process works like charm, but not now. I've got an installed W7 64 bit system on my 500GB HD and with diskmgmt.msc I've separated a 150GB chunk for the Ubuntu OS. Here is the result:

[IMG]http://i.imgur.com/IZvTxar.png[/IMG]

 After that I rebooted the computer and changed CD/DVD as first boot option. Fast boot and secure boot was disabled and I was using Legacy mode. The Ubuntu installer started with its purple screen with symbols but soon changed to a black screen and after some disk reading it was apparently stucked with a blinking cursor. After 10-15 minutes of this I had to shut down the computer. I tried it a couple of times with no avail.
Then I changed to UEFI mode where the installation has started as expected however the installer could not detect the existing W7 OS so I had to quit the installation. I've already read several forum posts and honestly I've got no idea what to do next ... maybe return to the 13.xx versions? Any help would be great and welcome.

---

### Post by ubfan1 on 2014-11-01
With Windows installed in legacy mode (no EFI partition, so can't be UEFI mode), you should install Ubuntu in legacy mode also.  At the purple grub screen, try the function keys to select options, like "nomodeset".  Your black screen might be a video problem.

---

### Post by Gergo_Santha on 2014-11-01
The problem is I don't even get to the grub screen in legacy mode. Just the purple screen and two symbols at the bottom of the display (a keyboard and and the ubuntu logo as far as I remember).

---

### Post by ubfan1 on 2014-11-01
The two symbols are a keyboard and a "man", indicating type any key for "manual" entry.  Type return, select a language on next screen, and a few other things, and you should get to the grub screen, avoiding some video issues the automatic route has.

---

### Post by Gergo_Santha on 2014-11-02
ubfan1 thanks for the help. 'nomodeset' option - what you already suggested in your first post but I strangely I did not give much attention - has solved the problem. Now I'm struggling with slow graphics but that'll be the next story.

---

