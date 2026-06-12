---
title: "Ubuntu 9.10 installation - dual hard disk"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by theotherjustin on 2010-01-08
Hi,

Firstly, thanks for a great OS in Ubuntu! :KS

I've tried searching the forum for an answer to my query but nothing precisely matches (or so it seems). My system is currently a single hard disk Windows XP box. I have a brand new HDD sitting here in a box and an iso image of 9.10 burned onto a CD-ROM. I'm ready to go! I'd like some advice on the best way of installing Ubuntu onto the new HDD (and hence dual booting) and keeping my Windows XP on the 1st HDD.

Any advice or pitfalls to watch out for etc?

Many thanks.

---

### Post by gsmanners on 2010-01-09
For simplicity, you will need a boot loader installed on the Windows drive. Ubuntu uses GRUB by default when it installs, so just go ahead and install the way you see fit, but keep this in mind. The Ubuntu installer will try to install GRUB on the Windows drive, and hopefully that will allow you to boot into either XP or Ubuntu when the computer restarts.

---

### Post by oldfred on 2010-01-09
I prefer to have each operating system on separate drives and on that drive have the boot loader for that system. If one drive fails I can still boot the other. Since grub is good at finding other operating systems I make Ubuntu the boot drive in BIOS and let grub set up windows to boot from the second drive.

I would install your new drive and make it first in BIOS. You will have to boot from the liveCD and then install to the new drive. That should keep your windows boot in the MBR of the windows drive.

There is also and advance button during the install (about when it wants to do the partitioning) that lets you choose which drive to install grub.

If you have lots of space since it is a new drive you may want to manually partition and add either /home partition or my preference a /data partition.

[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by theotherjustin on 2010-01-09
Just thought I'd give an update, as I'm writing this now from my fresh Ubuntu installation! The installation was incredibly straightforward. I installed the brand new disk and enabled it within the BIOS, and then booted into XP and initialised the disk using Disk Management. 

I then inserted the Ubuntu install disk and booted from it and up came the Ubuntu installation dialogs! The only thing I had to do was to choose the new disk (when asked where to install, I just chose "Use Entire Disk" and then the appropriate disk) and the installation was pretty much automatic. It recognised all of my network/sound/graphics cards and router etc. 

However, there are a few teething problems I need to deal with, including very strange, grainy graphics. For example the buttons (Home, New Tab, etc) on Firefox are pretty much unrecognisable - grainy - and whenever I open a menu and roll over the options they immediately become grainy - not quite sure what this is. Maybe a graphics card problem, since a similar thing occurs in XP? 

Hmm.

---

### Post by oldfred on 2010-01-09
On my nvidia system after about a minute or two and after all the updates, it asked if I wanted to install the propriety driver. Do not know about other video, my portable just worked without any special install. You can look under system, admistration, hardware drivers to see if it says anything.

---

### Post by theotherjustin on 2010-01-09
> **oldfred said:**
> On my nvidia system after about a minute or two and after all the updates, it asked if I wanted to install the propriety driver. Do not know about other video, my portable just worked without any special install. You can look under system, admistration, hardware drivers to see if it says anything.

Hi - I tried doing as you suggested and the dialog box that came up appeared completely blank with "No proprietary drivers are in use on this system". I have an ATI Radeon Pro 9800 card so would presume there should be something in there. 

I get the same problem in XP, so am thinking maybe the graphics card is kaputt?

---

