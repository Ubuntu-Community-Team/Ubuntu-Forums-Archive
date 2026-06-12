---
title: "Unintended Dual-Boot, How to Fix"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by Gary_DeLoach on 2014-03-27
I have an Intel based desktop PC that I built with 2 mobile hard drive bays that gives me the flexability to swap hard drives in and out for a variety of reasons. I decided I wanted to make an Ubuntu boot drive, so I downloaded 13.10 64-bit, booted to the DVD and installed it onto its own physical hard drive. Unfortunately, I forgot to remove my windows 7 drive from its bay beforehand. Evidently, Ubuntu messed with the boot sectors of my Win7 drive without informing me it was about to do so, and now I cannot boot my Win7 OS unless the Ubuntu drive is present in the other bay. Furthermore, the system now boots to a choice I must make between booting Ubuntu or Windows 7 and if I am not sitting right in front of the PC when it is booting, Ubuntu will boot as the deafult OS. Sheesh! I never intended to install a dual-boot system. I did not want a dual-boot system, which is why I installed Ubuntu on a separate physical drive. I do feel Ubuntu should have warned me about this, but that is a topic for another day. Right now, I just need to know how to fix this fiasco. Could someone please give me some walk-through instructions how I can change this so I can only boot Ubuntu when its physical drive is in its bay and my Windows 7 drive will boot normally whether or not the Ubuntu drive is in that drive bay? I would sure appreciate it. This is not just frustrating - I feel wounded by Ubuntu. This shouldn't have happened without prior notice.
Thanks so much,
Gary

---

### Post by oldfred on 2014-03-27
You just need to install grub2's boot loader to the Ubuntu drive and Windows boot loader to Windows drive.

Boot-Repair can do it, just use advanced options. It installs a generic Windows boot loader - syslinux. Or you can use your Windows repair CD or flash drive to run fixMBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Use advanced options and choose operating system and then choose drive for boot loader location.


 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you can boot into Ubuntu it is real easy to install grub to a different MBR. 
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

     

But grub also remembers which drive it installed into and may reinstall to same location on major updates.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Gary_DeLoach on 2014-03-27
oldfred:
THANK YOU immensly for your detailed and thorough answer to my question. WOW! I am very new to Ubuntu and I just wanted to install it in isolation so I could play around with it and become more familiar with it, little by little. As Micro$oft continues to develop into uncharted and unwanted directions (unwanted at least by its loyal installed base), I feel Ubuntu and OS's like it are going to become more and more important for those of us that have real work to do and wish to continue the Desktop UI pretty much as it is.
Thank you again, Sir!
Gary

---

