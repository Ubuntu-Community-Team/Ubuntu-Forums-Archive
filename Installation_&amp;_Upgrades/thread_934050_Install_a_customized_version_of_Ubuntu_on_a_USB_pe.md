---
title: "Install a customized version of Ubuntu on a USB pendrive"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by risbac on 2008-09-30
Here is my problem:

-we are a company and we would like to use a USB pendrive as an "emergency tool" for our employees having a broken OS. 

-we want install and configure the necessary software (Citrix, VPN, etc...), and then be able to replicate this usb pendrive easily to have a small batch ready for shipping to our desperate employees :).

-currently we didn't find any good solution. We can easily create an USB pendrive from a LiveCD, but we cannot customize the softwares installed, as only the /home is persistent.

-apparently the idea would be to customize a liveCD, then transfer it on the pendrive, but we have no idea on how to do that :) 

-so any help would be more than welcome! :)

---

### Post by arkticcool on 2008-09-30
This link should help, tells you how to make a distributable LiveCD with remastersys, just put it onto your usb as is stated on the second link.

Tutorial:
Creating custom install .iso
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

Creating the LiveUSB:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by dsm iv tr on 2008-09-30
If ~ is persistent, why not install the software into ~/software/<appname> and create icons on the desktop to the applications? They should be saved in ~/Desktop/.

Easier than going through all your work again.

---

### Post by risbac on 2008-09-30
But how do you install softwares from repo in a local directory? Like for instance a plugin for NetworkManager? :)

---

### Post by timcredible on 2008-09-30
you can do a normal install to an external drive, check out details at ubuntukids.org.  same procedure works for installing to flashdrive.  the only problem i ran into was that gnome tried to automount the flashdrive on login, and it would stop the system.  i never got back to figuring out what file needed to be changed to fix that, but i'm sure it's just a gnome setting - something in .gnome, or .gnome2, or .gconfd

---

### Post by snowpine on 2008-09-30
Definitely look into Remastersys to create a custom Live CD. Then, you can transfer that ISO onto the pen drive using the same technique you already know. (You could also distribute the Live CD for employees with older computers that can't boot from USB.)

The easiest way to get full persistence is to simply install to the USB device as if it were a regular hard drive. The disadvantage is it uses much more space on the drive (4gb instead of  700mb).

---

### Post by snowpine on 2008-09-30
(double post, sorry)

---

### Post by risbac on 2008-09-30
Thanks for all the info guys!

But I still have more questions :)

-If I use a normal installation instead of a LiveCD one (no pb, we buy 4Gb pendrives now), will it work with different laptops? We don't have the same hardwares for everybody, so it needs to be flexible. 

-If I transfer a normal installation, shouldn't I make some adjustments to avoid problems with flash memory? Like avoid writing too much on it, like logs for instance? 

Thanks in advance for your comments!!

---

### Post by snowpine on 2008-09-30
> **risbac said:**
> 
-If I use a normal installation instead of a LiveCD one (no pb, we buy 4Gb pendrives now), will it work with different laptops? We don't have the same hardwares for everybody, so it needs to be flexible. 

-If I transfer a normal installation, shouldn't I make some adjustments to avoid problems with flash memory? Like avoid writing too much on it, like logs for instance? 


1. Ubuntu auto-detects hardware at start up, no problem there. (You can take your Ubuntu hard drive out of your computer and put it in a completely different computer and it should still boot, no different with a USB drive.)

2. My understanding is that flash memory does degrade over time, however, we are talking months/years, not days/weeks. I would not recommend a full USB install for everyday use, however as an occasional-use rescue device I don't think it will be a problem. You are correct that a Live USB install will prolong the life of the device vs. a full install if it's a big concern. I also would not recommend setting up a swap partition on a USB drive. :)

---

### Post by snowpine on 2008-09-30
I just learned of a new utility called usb-creator that is in beta testing:

[http://ubuntuforums.org/showthread.php?t=927878](http://ubuntuforums.org/showthread.php?t=927878)

Perhaps this will be helpful. :)

---

### Post by risbac on 2008-09-30
Thanks! You are right, it should only be a temporary solution, and with the price of a penddrive, I guess it's not even worth improving a problem that may just never occurs!

Ok for the hardware also, I know it can adapt quite easily to new hardwares. My main concern was the graphic card. Maybe it's just better to create the Pendrive without an xorg.conf to let the system rebuild it when booting for the first time on the laptop? I think that if I let an xorg.conf with wrong settings, the failsafe interface will appear maybe? That's better than no X at all, but still not very userfriendly for the user. Without an xorg.conf, it should just recreate it automatically no?

---

### Post by snowpine on 2008-09-30
I currently have two USB thumb drive installs: 

8gb with full (hard-drive style) install of Crunchbang. It has a full suite of office and multimedia applications, so I can do all of my work on the road. The user experience is identical to working on my full hard drive install, except slower.

2gb with Live USB install of SliTaz. This is for quickly getting online to check email (and Ubuntu Forums obviously). SliTaz has a very nice TazUSB utility where your /home directory is persistent but downloaded packages need to be explicitly written to the USB with 'tazpkg writefs'. This is optimized to prolong the life of the drive.

I use these devices rarely, not every day. I am curious to see which one will die first. :) My understanding is that the drive capacity will slowly decrease over time, rather than a sudden catastrophic failure.

---

### Post by C.S.Cameron on 2008-09-30
This might be what you want, works for me:
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)

---

