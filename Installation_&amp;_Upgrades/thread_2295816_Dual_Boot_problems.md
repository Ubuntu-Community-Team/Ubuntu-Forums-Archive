---
title: "Dual Boot problems"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by mike364 on 2015-09-21
Hello everyone, a very inexperienced Linux user here.

I installed Linux a month ago or so, and did so on an external hard drive. I thought this would be a good idea because I pictured it working like this:
1. I want to boot into Windows, no problem; leave it unplugged.
2. Want to boot into Linux? Just plug it in.

Now, the first time I rebooted my laptop, I got a device not found message, given by grub rescue mode. I restarted the laptop and this time it successfully found it, giving me the option to boot into Ubuntu or Windows 7. Next, I unplugged the EHD, restarted, only to be greeted by the grub rescue mode yet again, but this time, restarting doesn't help.

I think the reason I got the first device not found message is because I started the drive from a cold state, not giving it enough time to power up before grub starts scanning and in turn finds nothing.
But the second incident, I'm thinking is because I may have put ALL my boot settings onto it. What I'm essentially saying is that, without my EHD, my laptop won't be able to boot up properly.

TL;DR Wonkily installed Linux, now my computer's booting is dependant on an EHD.

---

### Post by yancek on 2015-09-21
The description you give of your boot situation would indicate that you incorrectly installed the bootloader, most likely putting some Grub boot code on the master boot record of the windows drive.  You could have avoided this problem if you did not have the drive attached when you installed Ubuntu to the external drive.  During the install of Ubuntu, if you select the manual installation method referred to as "Something Else", you have the option to change the default under "Device for bootlaoder installation".   The link below explains in detail installing Ubuntu singly or as a dual-boot and also has a Step By Step install section and another section specifically on installing the bootloader.  Would have been more useful for you to have read it or something similar before installing but still useful for future installs.  You would need to repair the windows drive by putting windows boot code in the MBR and generally, you will need the windows installation DVD for that.  You might find some other method if you do an online search or some windows user might post with some other way.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2015-09-21
UEFI or BIOS system?
If UEFI, you can boot Windows from UEFI boot tab or one time boot key.

If BIOS you need to install grub to the MBR of the external drive first, then install a Windows boot loader to the MBR of the internal drive.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But grub has a setting on which drive by model it originally installed into. And it will reinstall to that drive on a major update. You need to reset that:

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates for BIOS
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by mike364 on 2015-09-22
So, basically I messed it up bad...?

---

### Post by oldfred on 2015-09-22
No?
But without more info we do not really know.

Did you try any suggested fixes?

---

### Post by mike364 on 2015-09-22
No, not yet anyway. 
I can tell you another thing that probably helps alot; right before I get the grub error message, if i spam F12, or F2, it brings up the UEFI and I have an option to choose what to boot on. I noticed something really messed up when I saw that the Seagate Portable drive wasn't showing up in the list; it was just TOSHIBA "something-something" in first place.

---

