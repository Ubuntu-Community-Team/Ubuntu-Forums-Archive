---
title: "RAID1 Driver"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by walkingstickman on 2012-01-07
After numerous problems running Windows 7 Ultimate and Ubuntu 11.04 on my dual-booting workstation, I decided to abandon Microsoft altogether since I had retired a while back and had no further need for the heavy-duty engineering software that I had been running for years.  In addition to that, my wife had been running Ubuntu since version 6.04 and was very happy with it.  Since I would now be using my rig mostly for serious writing and related illustrating, I waved bye-bye to Uncle Billy and signed on with Ubuntu.

My workstation has a pair of 1TB WD drives in a RAID1 mirror with a Promise Technology FastTrak TX2300 PCI controller. It gave no problems after I wiped Windows 7 from the drives and expanded the partitioning to the entire 900-plus capacity, minus 12GB for the swapfile.  The upgrade to 11.10 went through without problems, but a recent update of something like 119 files caused boot problems. Attempts to correct booting using the Boot Repair Disk killed it altogether, and I wiped the array so I could do a clean install and get back in business.

The problem now is that I can't rebuild the RAID1 mirror.  The disks were wiped clean, and when I try to partition the array, Gparted keeps telling me that it can't format the drives one of them is in use.  Trying to do them one at a time yields that result no matter which one I try.  I guess that because the system has to work through the Promise controller to access the drives it can't process them either together or separately.  The only driver I have is for Windows, and the drives apparently don't play nice with Ubuntu without a driver.

I was able to download a Linux driver from Promise for the TX2300 RAID controller, but it is source code written for Red Hat and Suse, and the instructions for compiling it don't work in Ubuntu. I'm a mechanical engineer who worked in electronics, and I build my own computers, but I have little experience with programming or software.  Can one or more of you folks explain how to adapt the Promise driver for Suse to Ubuntu?

The URL for the Promise download is:  [http://firstweb.promise.com/support/download/download2_eng.asp?productID=136&category=all&os=100](http://firstweb.promise.com/support/download/download2_eng.asp?productID=136&category=all&os=100) and the link to the file is:  &#65279;FastTrak TX2300/4300 Linux Partial Source Code.  I can upload the driver package if it will help.  Thank you for your time and attention to my query.

---

### Post by darkod on 2012-01-07
I have no idea about the controller, but one option is using ubuntu software raid since you will use only ubuntu on the system. I'm not sure if you will have to take a performance hit with this option compared to the Promise. Software raid is usually better than bios raid, but not sure compared to a dedicated controller.

However the benefit in my opinion is that tomorrow you can plug any of the disks in any computer and you will be able to get your data, even with only one disk from your raid1. This is because the OS does the raid.

One idea if you want to give the Promise another go is:
Get both the ubuntu desktop cd (live CD) and the alternate install cd (you use this for raid installs and it might offer support for more controllers than the desktop cd).
First boot with the standard cd into live mode, and in terminal try to get rid of the raid meta data on the disks:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

NOTE: That will DESTROY any data on the array/disks.

After that they should be clean so you might give the controller bios/menu another go at creating a new raid1 array.

If that works, to actually do the ubuntu install use the alternate cd because it has raid support, as opposed to the standard cd which can be used but also often fails to install the bootloader on a raid array.

If you decide to go with the softraid option, again the alternate cd can install it. Again you need to destroy the raid meta data from the disks first and disable the controller, in fact plug the disks directly on the motherboard. The OS will create the raid1 array and the package used is called mdadm.

---

### Post by walkingstickman on 2012-01-10
Hello Darko

I decided to try the software RAID1, setting it up while installing 11.10 from a live alternate disk.  The two drives in the array are the 1TB WDs which I wiped with gparted before I started the install.  I also removed the control card and connected the two SATA drives directly to the motherboard.   As far as I can tell, the array is healthy and functional, but now the harddrives themselves seem to run constantly, or at least the drive indicator is on all the time, with an occasional blink.

It doesn't appear to be slowing down the use of the system, but when I was still using the Promise Tech controller, the the drive indicator only flashed when the array was actually being accessed.  My backup system still has a RAID1 array using an earlier IDE Promise Tech controller, and its drive indicator only blinks when the array is being accessed.  Is there something I can do to reduce the drive activity, if indeed that is why the drive indicator is on most of the time?  I shall be grateful for any suggestions you offer.  Thanks once again for your time and attention to this query.

Walkingstickman.

---

