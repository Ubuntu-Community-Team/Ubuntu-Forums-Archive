---
title: "how  install with dual boot system"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Jacob-Gates on 2012-05-24
I had a guy install Ubuntu on my computer and he made it a dual boot system so I can keep Windows (at my request because i have programs that have to run in Windows). Well, I immediately noticed he installed the 32 bit system which I was fine with at first (my windows is 64). So it's been a few months and I have studied some and learn my way around the more technical side of linux and now I would like to get the 64 bit Ubuntu OS. But I was afraid to tackle this with out check if I need to know anything about the dual boot. It would be really bad if my Windows got deleted because I didn't do my research. 

Now I'm sure this has a lot to explain so if any of you have any links or documents I can download I am willing to read and study on my own... just not sure where to look. Thank you in advance.

Jacob

---

### Post by eleftg on 2012-05-24
You don't need to study for a dual boot installation of Ubuntu + Windows...

Just make sure you don't remove/format the Windows partition during ubuntu installation. Then ubuntu installer will take care of the rest

---

### Post by fantab on 2012-05-24
> **Jacob-Gates said:**
> 
Now I'm sure this has a lot to explain so if any of you have any links or documents I can download I am willing to read and study on my own... just not sure where to look. Thank you in advance.

Well its fairly Simple. (Asssuming you have only one hard disk. )

1. [**Download Ubuntu**]("http://www.ubuntu.com/download/desktop") 12.04 64bit .iso
2. Burn the downloaded .iso to a CD or USB (Use [**UNETBOOTIN**]("http://unetbootin.sourceforge.net/") to create a USB).
3. Boot with Ubuntu LiveCD or USB
4. At appropriate Screen Choose to "**Try Ubuntu**"... wait till you have a working desktop and try around to see if all the software and hardware is working.
5. There will be an option or icon on the Desktop launcher to** install** Ubuntu to hard disk: double click it.
6. The installation will start... the process is interactive so read all the screens you are presented with and make your choice accordingly.
7. When you reach the screen which says "**Allocate drive space**" choose "**Something Else**". And Manually select the Partition you want the Ubuntu to install to. At the bottom of the same screen you will have to choose the location to install **GRUB-Boot Loader**- make sure you install it correctly to the Hard Disk (/dev/sda)  and not to a partition (/dev/sda1 or /dev/sda2).

Thats it. 

Follow the instructions [**HERE**]("http://members.iinet.net.au/%7Eherman546/p22.html")

for more read [**here**]("https://help.ubuntu.com/community/Installation") and keep [**this page**]("https://help.ubuntu.com/community") bookmarked.

There is lot more information on the world wide web if you search.

Good Luck.

---

### Post by Jacob-Gates on 2012-05-25
Thank you so much. Makes me feel so much better knowing it's that easy. I always have this fear I'm going to screw something up in my computer by getting into these things.

---

