---
title: "limiting ubuntu installation program to one drive (multiple drive system) )"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by rafciu123 on 2010-04-13
Hi,

I have 3 hard drives in my desktop: 1TB sata (I have w7 installation there) 320GB sata (data) and 250GB IDE (data). I want to install ubuntu on my 320GB drive but I want to make sure that it **does not** alter my standard boot manager that loads w7 (I don't want it to touch 1TB drive at all). I want to point ubuntu installation program to a drive and limit its actions only to this particular drive. I want to be able to remove Ubuntu by formatting 320GB drive from Windows. I am willing to change boot sequence from BIOS to be able to load either w7 or ubuntu on as needed basis. 

A link to a relevant post or a short explanation would be highly appreciated.

Regards,

rafciu123

---

### Post by oldfred on 2010-04-14
There is an advanced button on the last partition screen that lets you choose where to install grub. The newest version sometimes has a menu listing every drive and partition and many users check them all and create all sorts of confusion. When I installed the first beta I missed the button even though I was looking for it and it defaulted to sda.

It is not that difficult to reinstall windows or grub boot loaders if you have a liveCD or windows CD available to run the fixes:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

About 1/3 way down is a snapshot of the advanced button. Right above the install button.
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

The new Lucid install I think the advance button was on screen 9 last or next to last screen.

---

### Post by rafciu123 on 2010-04-14
OldFred,

Thanks for the reply, I am going to give it a try.

Regards,

rafciu123

---

### Post by rafciu123 on 2010-04-15
Hi,

I have installed Ubuntu and actually used Advanced option to install Grub on the drive which I wanted. I assumed that I need some kind of boot manager on that drive to be able to boot operating system. Before I posted this question on the forum advice I got from someone was to disconnect cables to other hard drive but I was sure there must be an easier way.

Thanks for help!

---

