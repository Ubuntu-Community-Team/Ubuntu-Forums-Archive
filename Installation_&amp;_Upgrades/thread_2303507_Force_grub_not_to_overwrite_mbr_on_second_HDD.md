---
title: "Force grub not to overwrite mbr on second HDD"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2015-11-19
I don't want grub or anything else to overwrite a windows mbr, what are my options. I was thinking that if I change the flags on the HDD to hidden using the partition manager in kubuntu would grub ignore those partitions completely. [br]1[/br]The longer story is that I have a HDD from a laptop that came preinstalled with windoze7(three partitions mbr, recovery and win7), I've already swapped the HDD with a SSD and installed Kubuntu, bought a caddy-drive-bay and plan on using the HDD as a second drive for storage. I'm keeping windows in case I want to sell the laptop otherwise I don't have any need for it. I would make a backup image but the HDD is 320gb and windows is only using 50gb.[br]1[/br]Thanks

---

### Post by Bucky Ball on 2015-11-19
Choose 'Something Else' at the partitioning section of the install and choose not to install grub anywhere. You get the choice there or just after it from memory.

---

### Post by J_Me on 2015-11-19
My post was bunching up and I didn't explain myself properly either, hopfully I fixed that.[br]1[/br]I've already got kubuntu up and running on a SSD and would like to use a second HDD in the laptop.[br]1[/br] My head is a bit fuzzy today.

---

### Post by yancek on 2015-11-19
I'm not sure what the problem is.  You say you don't want Grub on Kubuntu to overwrite the MBR  but you also say you already have Kubuntu installed.  So how are you booting Kubuntu?  A default install of windows won't do that.  If you are going to install Kubuntu, you can select which drives MBR to install to or to install it to a partition using the Something Else option suggested above.

---

### Post by oldfred on 2015-11-19
Check default drive that grub installs into. And change if necessary.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

And reinstalling a boot loader to a MBR should be one of the easiest repair tasks. But you always need a Windows repair flash drive or a Ubuntu live installer for the current versions of every install you have. And installing a Windows boot loader to MBR is one of the few Windows repairs you can do from Linux with either Boot-Repair or command line.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
If UEFI both systems have boot folders in the ESP - efi system partition so not an issue anyway.

---

### Post by ajgreeny on 2015-11-19
Let's get this cleared up!

Firstly, the MBR is not on a partition; it is on the root of the drive, ie /dev/sda, not /dev/sda1.

You have a computer with two hard disks, a new internal SSD and the old HDD attached in a USB caddy; correct?

You have already installed Kubuntu on the new SSD and have the old HDD with Win7 using the USB caddy; correct?

When you installed Kubuntu it could (theoretically) have put grub on either disk, depending on how you installed Kubuntu, but if the old HDD was not attached at the time grub will obviously not be on that, but will be on the new SSD.

With the old drive now USB attached it will certainly not get grub installed in normal updating etc etc, so I do not think you need to worry about that.

---

### Post by ubfan1 on 2015-11-19
Additional caution is necessary if your "caddy-drive-bay" is an optical drive replacement (SATA).  That might be unexpectedly enumerated first in the disk order instead of second.  I found grub just died when trying to access such a caddy, and it was enumerated before the internal hard disk, so that forced the use of a USB boot device so grub could start without accessing it.  The caddy worked fine as a second disk after boot.

---

### Post by J_Me on 2015-11-19
@ajgreeny Yes that sums it up about right.[br]1[/br] And by reading over my previous post, this 'caddy-drive-bay' is causing confusion so here it is [http://www.amazon.co.uk/Drive-Caddy-Lenovo-Thinkpad-Ultrabay/dp/B005XCX5DY/ref=sr_1_1?ie=UTF8&qid=1447949715&sr=8-1&keywords=t420+caddy-drive-bay](http://www.amazon.co.uk/Drive-Caddy-Lenovo-Thinkpad-Ultrabay/dp/B005XCX5DY/ref=sr_1_1?ie=UTF8&qid=1447949715&sr=8-1&keywords=t420+caddy-drive-bay)  >  With the old drive now USB attached it will certainly not get grub installed in normal updating etc etc, so I do not think you need to worry about that. Great that is what I needed to hear, but the reason why I brought this up in the first place is that I had a situation a while back where grub overwrote the grub boot loader on another drive, somewhat simialr to this setup.[br]1[/br] @ubfan1 Thanks for that, I'll make sure to remove it before booting the laptop.[br]1[/br] As always everyones help is very much appreciated.

---

