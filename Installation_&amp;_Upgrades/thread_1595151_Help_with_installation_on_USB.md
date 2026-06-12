---
title: "Help with installation on USB"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by konang on 2010-10-12
So Im totally new, so I need pretty simple explanations, so here is my doubt. I have a simple tech external hard drive 300GB, and I want to install ubuntu 10.10 Netbook edition, but I dont want the usb version which will only let me have 4GB of persistent I want the whole external hard drive to be used, as if it would by my laptops hard drive. Can someone explain me step by step what could I do?

---

### Post by oldfred on 2010-10-13
this is for Lucid and the install screens are a little different.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

But your install to an external drive is just like any install to another drive. I think the new Maverick only lets you choose which drive to install grub2 to with the advanced partitioning screen. You do want to install grub to the external.

The external will run a little slower as you are using the USB port which is slower that SATA.

---

### Post by konang on 2010-10-13
> **oldfred said:**
> this is for Lucid and the install screens are a little different.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

But your install to an external drive is just like any install to another drive. I think the new Maverick only lets you choose which drive to install grub2 to with the advanced partitioning screen. You do want to install grub to the external.

The external will run a little slower as you are using the USB port which is slower that SATA.

So I followed the instructions like on the image, and it was almost done copying the files when suddenly the live cd stop spinning and left the instalation in the 85% on the screen where you choose the keyboard language. why does it stops?

---

### Post by oldfred on 2010-10-13
Keyboard is one of the first screens. Did you burn ISO at slowest speed possible? Have you verified that ISO was downloaded correctly with verified ms5sum. Did you try running system as liveCD to see if there were any issues?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by konang on 2010-10-13
> **oldfred said:**
> Keyboard is one of the first screens. Did you burn ISO at slowest speed possible? Have you verified that ISO was downloaded correctly with verified ms5sum. Did you try running system as liveCD to see if there were any issues?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

I did check it was downloaded correctly, but what I did is that I burned the liveCD at the maximum speed, I am right now burning another liveCD with the minimum speed, but still I choose the option of check the disk for any errors at the ubuntu boot up screen and it said that the CD had no mistakes. And one more thing on the image you posted firts he installed Ubuntu inside a partition of the internal drive or sda drive, is ok for me if I install it to the sdb directly or this may the cause of which it wont complete the installation?

---

### Post by konang on 2010-10-13
> **konang said:**
> I did check it was downloaded correctly, but what I did is that I burned the liveCD at the maximum speed, I am right now burning another liveCD with the minimum speed, but still I choose the option of check the disk for any errors at the ubuntu boot up screen and it said that the CD had no mistakes. And one more thing on the image you posted firts he installed Ubuntu inside a partition of the internal drive or sda drive, is ok for me if I install it to the sdb directly or this may the cause of which it wont complete the installation? 
Now I tried to install it, and same as the other time it stopped when it said copying files and then said "Ready when you are", but now I could go all the way up to the "Who you are" window, but same as the other time, it wouldn't let me through the whole process

---

### Post by konang on 2010-10-14
I solved it, the problem was that  the CD wouldnt burn right but now it did, tnx. Just one las thing it wont let me start in the netbook edition itll only let me access the desktop edition, I have an HP Pavilion dv6 series with intel core i7, w7, and 1GB nvidia GeForce dedicated video memory.

---

