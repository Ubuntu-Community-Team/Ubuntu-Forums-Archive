---
title: "making a boot DVD"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by cncybengals on 2007-11-14
I'm trying to take the Ubuntu 7.10 CD and make it into a bootable DVD.  I have an old laptop I want to put Ubuntu on and the DVD-ROM for some reason won't read CD-ROMs anymore but has no problem with DVDs.  I tried making a bootable DVD in Nero 6 but it only boots to DOS and that's not much help.  Any idea how I can convert the Ubuntu .iso to a DVD .iso or just pull the files off the install CD and make it bootable so I can install Ubuntu? or any other ideas? 

Thanks.

---

### Post by logos34 on 2007-11-15
You don't need to convert the iso--you can make a bootable cd or dvd with it.

You burned the .iso as an image with Nero Burning ROM?  

If no luck, get InfraRecorder.

---

### Post by cncybengals on 2007-11-15
I wasn't able to get the iso burnt using Nero but InfraRecord worked fine.  However, I still get the outcome that the disk isn't bootable.  I'm completely at a loss.  I've tried several different boot CD images (ultimate boot cd, win98 boot CD - external floppy worked fine, and three other Linux OS boot/install CDs) and none of them work.  The only thing that the laptop was able to boot with was the OpenSuse install CD.  Of course, my laptop is an old one and doesn't meet the system requirements to run OpenSuse.  What's different about it's boot loader over everything else?  Any other ideas I can try to get Ubuntu installed?

Thanks again.

---

### Post by Can+~ on 2007-11-15
You could install try via Wubi...
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by cncybengals on 2007-11-15
After reading some of the wubi documentation I don't know that it will work.  I currently have no OS installed on the laptop.  I wiped it to start over.  I'm starting to regret that.

---

### Post by logos34 on 2007-11-15
> **cncybengals said:**
> After reading some of the wubi documentation I don't know that it will work.  I currently have no OS installed on the laptop.  I wiped it to start over.  I'm starting to regret that.

yeah, you kinda screwed yourself with that move...if you had still had windows you'd at least have the option of wubi/LVPM or network installation (start from hard disk).  

Not sure what to suggest at this point. If you're burning the .isos as IMAGES (not the same as making a bootable cd/dvd), and the md5sums check out, then it could be the dvd-rom (which for some reason can handle the Suse disc).  If you're burning these discs on another lappy, you could try swapping the dvd drives.  

Other methods:
[https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by cncybengals on 2007-11-16
yikes, looks like a lot of work doing something I've never done.  I can't wait to get home from work and try it, I love this stuff!!!

---

### Post by cncybengals on 2007-11-18
I tried the net install and it worked great!!  I'm now up and running!  Thanks everyone!!

---

