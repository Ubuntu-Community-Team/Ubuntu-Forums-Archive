---
title: "Installation keeps failing"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Colorado Jack on 2008-07-10
I made a CD and have tried several times unsuccessfully, to install Hardy Heron.  I'm trying to install it on an older Dell Laptop with xp.  It originally came with Millenium.  I keep getting a message that I have 255mb of memory and ubuntu requires 256 and that the installation may fail.  Well, it does. If I have enough memory for xp, why isn't it enough for ubuntu?  I thought that Linux was perfect for older machines.  I don't want to give up, but I'm frustrated. Can you help?

---

### Post by SkonesMickLoud on 2008-07-10
Sounds like you'd be better off with Xubuntu, which is a smaller, lighter Ubuntu, that runs well on older systems.  You can get it by going here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by Colorado Jack on 2008-07-10
> **SkonesMickLoud said:**
> Sounds like you'd be better off with Xubuntu, which is a smaller, lighter Ubuntu, that runs well on older systems.  You can get it by going here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
I tried Xubuntu.  I got the same message before installation,not enough memory, and it failed again.  There was an error message which didn't stay on the screen long enough to read.  Is it time to give up and scrap the old laptop?

---

### Post by SkonesMickLoud on 2008-07-10
You might wannt to consider running Memtest+86.  I'm no computer expert, but I've never heard of a computer having 255 Mb of RAM.  It's usually 256.  You can do this by booting your computer with the CD in the drive and select the Memtest +86 option.  This will take a while however.

It sounds like you may have a bad stick of RAM.

---

### Post by snowpine on 2008-07-10
Hi Colorado Jack, to install Ubuntu (or Xubuntu) using the Live CD (the regular method) you will need more RAM than you have on your computer (384mb minimum, 512 recommended).

However, it is possible to install it with 256mb using the Alternate Install CD, which you should be able to download from the same place you downloaded the Live CD. It has a text-based installer.

Ubuntu is not that speedy on 256mb ram (I've tried it) so I would recommend a ram upgrade or trying Xubuntu instead.

To answer your question, Windows XP is a 7-year-old discontinued operating system, whereas Ubuntu Hardy Heron is a modern, 2008 operating system that's designed to be attractive and easy to use. It is not reasonable to expect the two operating systems to have the same system requirements. A better comparision is between Hardy Heron and Vista. There are other "flavors" of Linux that are better for old hardware (Xubuntu for example).

---

### Post by sande87 on 2008-07-10
I think you might be able to install if you use go directly to the installer, its one of the options you get when you boot the Ubuntu LiveCD. And the reason it says that you have 255mb RAM is because grub has used some to start.

---

### Post by Colorado Jack on 2008-07-11
Many thanks to all who replied to my post.  After many failed attempts, I was finally able to install Xubuntu.  I was having graphics problems, but I was able to finally install the live CD without graphics.  Once there, I was able to fully install Xubuntu.  
One question.  Why are there only 2 screen resolutions?  I would prefer seeing more on my Firefox page.

---

### Post by sande87 on 2008-07-12
maybe because the standard graphics driver in xubuntu doesnt run well with your graphics card. installing a proprietary driver might do the trick. have you checked the "Restriced Drivers" app, maybe your cards driver is there but not activated. You can also try to use synaptic to download and install the ATI or nVidia drivers for you. It has worked for me, but I experienced video playback problems, so I stopped using them.

---

