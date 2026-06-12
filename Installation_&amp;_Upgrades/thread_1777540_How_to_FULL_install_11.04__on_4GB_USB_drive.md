---
title: "How to FULL install 11.04  on 4GB USB drive?"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by dforionstar on 2011-06-07
I'm trying to perform a FULL install of 11.04 onto a 4GB USB drive, but the Ubuntu installer insists I must have at least 4.4GB free space.

I am able to run the ISO LIVE from a 1GB usb drive created with LiLi USB Creator ;), but the Ubuntu installer demands at least 4.4 GB to install :(.

I can give Ubuntu the entire 4GB drive, but how do I get past the Installer's 4.4 GB requirement? 

I don't need the larger apps like Gimp/Office/Games to free up space. When I completely remove these apps from the persistent live install via Synaptic, I run out of space - Possibly due to cache issues. I'm very new and don't know how to proceed.

I am able to FULL-install and boot Fedora successfully as its installer does not have the 4 GB limitation.

Is is possible to install Ubuntu 11.04 onto the 4GB drive?

Thanks in advance!:)

---

### Post by tommcd on 2011-06-08
You can try installing Ubuntu using the Minimal CD image and then build up your system as needed from there: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
I don't think you will be able to get around the 4.4GB requirement for the full Ubuntu install.

EDIT: Perhaps you can try using manual partitioning during the install and limit the size of the swap space to 256-500MB. Or, if you have a good amount of memory (at least 1GB, preferably more), you could eliminate the swap space altogether.
This may get you under the 4.4GB size limit.

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **dforionstar said:**
> I'm trying to perform a FULL install of 11.04 onto a 4GB USB drive, but the Ubuntu installer insists I must have at least 4.4GB free space.

I am able to run the ISO LIVE from a 1GB usb drive created with LiLi USB Creator ;), but the Ubuntu installer demands at least 4.4 GB to install :(.

I can give Ubuntu the entire 4GB drive, but how do I get past the Installer's 4.4 GB requirement? 

I don't need the larger apps like Gimp/Office/Games to free up space. When I completely remove these apps from the persistent live install via Synaptic, I run out of space - Possibly due to cache issues. I'm very new and don't know how to proceed.

I am able to FULL-install and boot Fedora successfully as its installer does not have the 4 GB limitation.

Is is possible to install Ubuntu 11.04 onto the 4GB drive?

Thanks in advance!:)

What I usually do is create a clone of my system with Remastersys.  And then I use Startup Disc Creator to transfer that *.iso file to my Flash Drive to create a Live Bootable Clone of my entire Ubuntu system (which I can then install to other like architecture systems).  I have made them this way up to the DVD-R limit size. That would be 4.7Gb.   I'm not really sure which method you are using currently though... Maybe you are using Unetbootin or maybe you are doing it from the command line.  Remastersys and Startup Disk Creator work great though, and if you are going to maximum capacity you would need to disable persistence in Startup Disc Creator.  Hopefully that works for you.  You can add at the remastersys repo from their web site. And even though it says it is for Karmic, it installs nicely in 10.10 and 11.04, when I recently re-installed the remastersys repo on another 11.04 system.

---

### Post by dforionstar on 2011-06-08
> **tommcd said:**
> You can try installing Ubuntu using the Minimal CD image and then build up your system as needed from there: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

EDIT: Perhaps you can try using manual partitioning during the install and limit the size of the swap space to 256-500MB. Or, if you have a good amount of memory (at least 1GB, preferably more), you could eliminate the swap space altogether.
This may get you under the 4.4GB size limit.

*Thank you!* This may be the way to go. But as a newbee, I'm not sure what all I should install afterwards. There is also an alternate installer which may not have the 4.4GB limit. The default Ubuntu installer won't even allow me to partition because at 4GB I am below the limit. I was not able to get it to run using a USB build via LiLi USB Creator, or Unetbootin. I may have to just burn it to a CD. I will report back if it works.

---

### Post by dforionstar on 2011-06-08
> **linuxinstalledfromhdd said:**
> What I usually do is create a clone of my system with Remastersys.  And then I use Startup Disc Creator to transfer that *.iso file to my Flash Drive to create a Live Bootable Clone of my entire Ubuntu system (which I can then install to other like architecture systems).  I have made them this way up to the DVD-R limit size. That would be 4.7Gb.   I'm not really sure which method you are using currently though... Maybe you are using Unetbootin or maybe you are doing it from the command line.  Remastersys and Startup Disk Creator work great though, and if you are going to maximum capacity you would need to disable persistence in Startup Disc Creator.  Hopefully that works for you.  You can add at the remastersys repo from their web site. And even though it says it is for Karmic, it installs nicely in 10.10 and 11.04, when I recently re-installed the remastersys repo on another 11.04 system.

*Thank you :D !* I don't already have a running Linux system to work from so this may not be appropriate for my situation at this time, but is an interesting approach nevertheless.

---

### Post by syoung27 on 2011-06-08
out of curiosity what's the purpose on a thumbdrive?
im a linux newb myself.

---

### Post by tommcd on 2011-06-08
> **dforionstar said:**
> I'm not sure what all I should install afterwards.
The minimal install CD tutorial that I linked to tells you what to install to get a graphical desktop. You could try just substituting *gnome* for the *icewm* window manager. Then just build it up from there.
To get the full on Ubuntu desktop you could just run:
```
sudo apt-get install ubuntu-desktop
```
But that may come close to filling up your 4GB flash drive.
> **dforionstar said:**
> 
 There is also an alternate installer which may not have the 4.4GB limit. 
You could try the alternate install CD. The alternate CD also has an option to install a command line only system (without a graphical desktop). You could then build up the system as needed from there.
> **dforionstar said:**
> 
I was not able to get it to run using a USB build via LiLi USB Creator, or Unetbootin. I may have to just burn it to a CD. 
Are you trying to boot the installer from a flash drive, and then trying to install Ubuntu to the same flash drive? If so, then this may be the problem. Perhaps installing from a CD to the flash drive would work.

Another option is to go with the fast and light Lubutnu. My Lubuntu installs on my desktop and laptop are only about 3GB each for the root partitions.

---

### Post by tommcd on 2011-06-08
> **syoung27 said:**
> out of curiosity what's the purpose on a thumbdrive?

A flash drive (or thumb drive) is a portable solid state (flash based) hard drive for storing files. They are great for copying data from one computer to load it onto another. I have the 4GB Sandisk Cruzer: [http://www.sandisk.com/products/usb-flash-drives/sandisk-micro-usb-flash-drive](http://www.sandisk.com/products/usb-flash-drives/sandisk-micro-usb-flash-drive)
Since these function as hard drives, you can also install linux onto them for a portable linux distro.

---

