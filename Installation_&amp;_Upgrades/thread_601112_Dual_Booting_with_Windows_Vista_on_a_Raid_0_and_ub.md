---
title: "Dual Booting with Windows Vista on a Raid 0 and ubuntu on a separate drive"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by sciguy14 on 2007-11-02
hello all,

Here is my setup and what I am trying to accomplish:
-I have 2 500GB Sata drives running in hardware RAID 0 with Windows Vista Installed and working
-I have a separate 320GB Sata drive that I want to install ubuntu on to for use in a dual boot
-I want to use the Windows Boot Manager, not GRUB (explained below)

When I tried this the first time, grub overwrote my windows boot manager, and I couldn't boot into either...after about 4 hours of troubleshooting, I finally restored it the Vista disk :?.

Now, I've installed Ubuntu again, but here's what I did differently, I first unplugged my other raid drives so that ubuntu would be forced to write the MBR to its own drive. After the installation completed, I plugged mine back in and booted to Vista without problem.  Then I configured Easy BCD to make Linux a second boot option, but when I select it on boot, it says "MBR is missing" or something along those lines...

anybody know how I can remedy this?

---

### Post by Tlingit on 2007-11-03
Hey man i am on sorta on the same page as you.
 i'm working it so if i find anything ill let you know. There was this guide i found on here, but it wanted me to take vista off and put it back on on a second partition. i was reading this one post and that caused some problems for that guy. so if you find any leads you should point me there thanks .

---

### Post by Tlingit on 2007-11-03
Oh here is the tutorial's i found don't know if this will help

[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

---

### Post by tubasoldier on 2007-11-03
Grub has to be installed, or a boot loader that supports Linux. 

However, It does not have to be installed into your MBR. The reason you got the no MBR error is that ubuntu still thinks it is physically on the first hard drive.

so, dont unplug anything. During the install there is a window near the end which has an advanced tab that will allow you to choose where grub gets installed. This particular window of the installation looks like this: [http://www.flickr.com/photo_zoom.gne?id=1616105806&size=l](http://www.flickr.com/photo_zoom.gne?id=1616105806&size=l)

Click the advanced button.

Read up on Grub naming conventions:  [http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention)
once you figure out what number the disk is that you want to use then type that into the little box under the afformentioned advanced tab.
Now when you boot up and choose to boot that disk from your bios you will be sent to grub.

Alternatively, it is possible to install grub in windows and manage it from there
OR use a different boot manager that supports linux

---

### Post by sciguy14 on 2007-11-03
my hard drive names seem to start with sdd instead of hd.  does that make a difference?

---

### Post by sciguy14 on 2007-11-03
I tried it two more ways, both with no success:

1. In that advanced menu i set it too (sdd2) - as that was what it showed in the partition setup.  The install would not complete that way.

2. In the advanced menu I set it to (hd3) because there are four hard drives total, and the forth on is the one I am trying to install to.  The installation completed successfully, but when I try to boot to it, it still says, "BootMGR is missing"

---

### Post by sciguy14 on 2007-11-03
any more ideas?

---

### Post by sciguy14 on 2007-11-03
I got it working!

Using easyBCD you can setup NeoGrub which allows you to add linux as an entry without it's grub even installed!

dual boot works great! thanks!

---

