---
title: "Boot ubuntu from pen drive then to sata?"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by jpin321 on 2011-02-28
OK, Forum help me out here.

I have a HP PC that I have installed a PCI SATA controller in.  The PC doesn't support booting from the card.... So here is what I would like to do.  (btw..I'm a seasoned noob on Linux.)

I would like to be able to boot ubuntu 10.10 from a usb pin drive 2Gb to a point where the kernal can recognize the SATA drive then start the OS from the SATA HDD.

I can see and access the drive if I boot to a live CD but when I install it won't boot because the PC's bios does not see the PCI card.

This has to be possible but my Google foo isn't strong enough to find out how.

Would a simple GRUB install on the pen drive work?

---

### Post by metalf8801 on 2011-02-28
I haven't done this before but it sounds like you want to put your /boot partition on your flash drive and all of the other partition on your Sata hard drive. I think you can do this using the advanced partitioning option during the install. 

I hope this helps and please post if this does or doesn't work
Dan


Edit and Important 
Since grub is going to be on this drive you will always need it when you boot this computer even if you are booting into another OS on a different drive unless you disconcert the other drive(s) when you do the install. Then after the install and you reconnected the hard drive(s) you have to press a key at bios screen to select which drive you want to boot to. Often the key is F12

---

### Post by jpin321 on 2011-02-28
> **metalf8801 said:**
> I haven't done this before but it sounds like you want to put your /boot partition on your flash drive and all of the other partition on your Sata hard drive. I think you can do this using the advanced partitioning option during the install. 

I hope this helps and please post if this does or doesn't work
Dan


Edit and Important 
Since grub is going to be on this drive you will always need it when you boot this computer even if you are booting into another OS on a different drive unless you disconcert the other drive(s) when you do the install. Then after the install and you reconnected the hard drive(s) you have to press a key at bios screen to select which drive you want to boot to. Often the key is F12

I tried this but im kind of confused on how to setup the partitions.  Can you provide instructions or screenshots of how to do this?  Like partition names and sizes that sort of thing.  All these partition names so confusing...:confused:

---

### Post by metalf8801 on 2011-02-28
Ok new idea do a regular install on the SATA hard drive then install grub on a flash drive here's a how to I just found 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by jpin321 on 2011-02-28
> **metalf8801 said:**
> Ok new idea do a regular install on the SATA hard drive then install grub on a flash drive here's a how to I just found 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")


Wow that looks complicated.  Ill try that this afternoon and get back with you.  Is it easy to point grub at my hard drive?

---

### Post by jpin321 on 2011-02-28
Ok I finally got this to work.  Here is what I did.

I used the first option.. the second option seemed a little to complicated for my liking. 

I booted the live disk.  Clicked install.

I went through the menus until I made it to the place where you choose where to install the OS.

I chose the HDD on the SATA controller and clicked advanced.  I deleted all the partitions on the USB drive and the HDD.

I then created a primary EXT4 partition, Format and mount point "/" (root) and a Swap partition on the HDD.

On the USB drive I created a EXT4 partition, Format and mount point "/boot".

I also selected the USB drive as the boot device on the bottom.

Let everything install... On boot I had some errors and I thought it had failed but I just let it sit and after about 45 sec it booted and is working great.

Thanks for all your help.  I hope this helps someone else in the position.  :D

---

