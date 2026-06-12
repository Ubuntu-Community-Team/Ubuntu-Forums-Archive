---
title: "What would be the best Linux distribution for Asus EEE pc 901?"
date: 2015-10-11
forum: Installation &amp; Upgrades
---

### Post by somebody3 on 2015-10-11
Hardware:

CPU: Intel atom 1.6 ghz

RAM: 1024 gb

SDD: 4 gb and 8 gb

I don't really need a fancy desktop, a simple one would be good enough, but I'd like to have as much functionality of original Ubuntu as possible.

My initial thoughts were to use Lubuntu, but I suppose I'd need to use something even lighter.

My main concern is SSD space. It seems that it can boot only from the 4 gb drive. Initially I've installed OS on a 8 gb drive but it fails to boot. Then I looked at BIOS settings and it says that 4 gb drive is master and 8 gb drive is slave. In boot priority there is only one drive that is shown, I can't tell which one but I suppose its 4 gb one. I've also read that 4 gb one is faster than the other. 

So, I suppose I'm limited to just 4 gb for OS.

Also, after I choose the distribution I need, would that be possible to specify a location for installing new software to 8 gb drive?

---

### Post by sudodus on 2015-10-12
Some time ago I installed ***Lubuntu 14.04.1 LTS*** into an eeePC 900 owned by a friend of mine, so my guess is that Lubuntu is good also for your netbook. The newest point version of the long time support version is Lubuntu 14.04.3 LTS, but the support is longer for the first point version, 14.04.**1** LTS.

***Edit***: If you have problems to install due to the 4GB size, you should be able to install Lubuntu via the Ubuntu mini.iso or with the One Button Installer.

But it is also a good idea to try ***Wary Puppy*** and ***TahrPup*** (Puppy Linux flavours). They are lighter and you may like them.

You can also try ***ToriOS***, which is not released yet, but it might also work well for you, it is very light and can be installed into 4 GB.

---

### Post by coldraven on 2015-10-12
I installed Xubuntu 12.04 on an eeePC 900 and it worked very well. The problem is that the 4GB drive fills up and after a while there is no space in /tmp to uncompress updates. You might be better off installing the minimal iso, adding Xfce and then the applications that you need.
I tried to get around this my creating two 1GB partitions for /tmp and /etc (AFAIR) on the 16GB drive in addition to  /home. This worked but I could not figure out how to hide them from appearing on the desktop. I chose 1GB but it might work with  smaller partitions. My reasoning was that I could store all my files on a SD card that would be permanently in the slot. Sorry if this is not very clear I have not yet had coffee :)

Edit: For more info and for updating the BIOS see my post here:  [http://ubuntuforums.org/showthread.php?t=2144698&p=12645842#post12645842](http://ubuntuforums.org/showthread.php?t=2144698&p=12645842#post12645842)

---

