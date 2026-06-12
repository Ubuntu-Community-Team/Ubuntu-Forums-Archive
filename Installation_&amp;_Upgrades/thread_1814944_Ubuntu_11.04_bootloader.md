---
title: "Ubuntu 11.04 bootloader"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by linuxisgreat on 2011-07-30
Hi I just have a few questions about the ubuntu 11.04 bootloader.
 
I have an acer aspire 5742 laptop with windows 7 on it's internal disk and it is still under warrenty. I don't want ubuntu's MBR bootloader to be installed on the main internal drive which is inside the ACER because there are special tools designed for recovery in the MBR program and if the MBR was deleted by ubuntu I don't know if I could fix it by using the recovery DVDs I burned and if that were the case I don't know if MBR deletion will void the warrenty.
 
The ubuntu 11.04 installer interface has changed quite allot and I need to know how to set the installer to only install the ubuntu bootloader to the MBR of my portable hard drive I intend to install ubuntu 11.04 to and not to my main hard drive with windows on it.
 
Also thsi laptop has a different way of setting boot order than most computers. Instead of changing the default boot order there is an F12 boot menu which is required to select boot device temporarily. If I use this to boot ubuntu from the portable drive will it know that the portable drive it has booted from is hd0 the one with it's MBR on or will it consider my main internal drive hd0 because it is the default in the BIOS? I ask this because I notice update manager in ubuntu quite often asks me to update the grub-mbr package and I do not want any MBR updates overwriting my main drive either.
 
This ACER laptop is quite fast and there are quite allot of open source drivers for most of the components in the laptop but when it comes to ACER's support and warrenty they are not very clear. Has anyone had any experience with acer's support and their recovery disc tools? Do the discs restore the MBR to it's factory state?
 
Please help. This is quite important and I really need to upgrade my distro on my portable drive but I don't want to mess up my computer's main windows 7 drive.

---

### Post by oldfred on 2011-07-30
If installing to an external you definitely want to install grub2's boot loader to the MBR of the external.

The Ubuntu installer defaults to sda with all the automatic install choices, so you have to use manual install or Something Else in Natty. Then you have to create partitions, what format for each except swap and choose / (root) & swap. Also /home is suggested but not required. On that screen is a combo box that will also default to sda drive, just choose to install to the drive that is the external drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by linuxisgreat on 2011-07-30
Thanks for that.
 
Ubuntu on this new machine sees my external drive as sdc so I need to change the bootloader option on the partitioning screen to install on that drive and I need to tell it to put the root file system on the one of the partitions of the disk and set up another partition as swap space.
 
I think I know what I am doing with this new installer.

---

### Post by haresear on 2011-07-30
I would offer a word of caution based on my own experiences with 11.04 and grub2. Pay close attention when you do subsequent updates on 11.04 after the initial install. I had at least one update to grub2 in the 11.04 updates in which the updater asked where it should reinstall grub2, so apparently it doesn't always remember where grub2 was initially installed. I had one other 11.04 update on a different machine that I left running unattended, and it reinstalled grub2 to the wrong MBR (there were two internal drives). It is possible that it asked where to reinstall grub2, and when I didn't answer, it made the wrong choice. In any case if I were in your situation I would keep a close eye on the list of updated components to see if grub2 is going to be updated.

---

### Post by oldfred on 2011-07-31
Grub saves a location that it is install to and reinstalls to that location. So if you change drives, you also need to update the saved location.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by haresear on 2011-07-31
> **oldfred said:**
> Grub saves a location that it is install to and reinstalls to that location. So if you change drives, you also need to update the saved location.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I didn't change any drive configurations, so not sure why it needed to ask where to reinstall grub.

In any case, thanks for the info -- these look like handy commands for keeping control of grub2.

---

