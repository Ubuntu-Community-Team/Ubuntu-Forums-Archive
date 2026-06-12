---
title: "Dual Boot install, incompatable GPU, deleted partition."
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by ScousaJAY on 2015-11-08
Hi all,

I was trying out linux on a laptop, first i tried 14.04.3 LTS which seemed to have a problem with the SiS graphics card.  I tried looking for solutions, but nothing worked. 

Some forum articles pointed towards 12.04 (i think) possibly working, so i thought i would give that a try.

So i booted back into windows, deleted the 2 partitions that were created automatically during the installation of Ubuntu 14.04.3, and before restarting, i expanded and then shrunk the C: drive so i could create a separate partition.

The reason i created a partition through windows is because i still have a old version of Wubi, which also had the option of 12.04.

So i ran Wubi, installed 12.04, and restarted.

I am now shown a Grub screen saying something like " No Partition found" or something similar, and i am unable to load windows or ubuntu 12.04.

Reading some of the forum comments on this issue, more say that i should reinstall ubuntu, or insert a windows disc, but the problem is, i dont have a windows disc, and also the Microsoft Serial Key has rubbed off the underneath of the laptop so i cant just use a windows 7 ISO to run a fresh install. 

all i have at this point is a Usb with 14.04.3 ISO, and the screen resolution is unworkable.

any help would be much appreciated ! 

Thanks :)

---

### Post by yancek on 2015-11-08
> The reason i created a partition through windows is because i still have  a old version of Wubi, which also had the option of 12.04.


WUBI is Windows UBuntu Installer which installs Ubuntu within the windows partition as a program.  Wubi is not supported anymore, 12.04 is the last version.  It might have worked on your system though.  So if you ran wubi and installed it, it is on the windows partition.

> So i booted back into windows, deleted the 2 partitions that were  created automatically during the installation of Ubuntu 14.04.3

When you originally installed 14.04, the default was to install it's bootloader to the MBR so unless you manually changed that, that is what happened and you would then use the Grub bootloader to boot Ubuntu and chainload windows.  (You neglected to mention which version of windows you are using??)  Grub puts a tiny amount of code in the MBR but almost all the files needed for Grub to boot are on the partition, the one you deleted from windows!  That' why you get the no partition found message.

You might try installing Ubuntu again and if you still have the problem with your graphics card, you should still have the windows system available and it should be detected and you should be able to use it until you can get more info on your graphics card and find a Linux system which works with it.  I'm not really clear on the statement about the screen resolution.  Was that on the installed Ubuntu or is that a problem with the DVD/flash drive you used to install.

---

### Post by ScousaJAY on 2015-11-08
Hi Yancek, Thanks for your response.

Its windows 7 that was on the laptop, and as for the screen resolution, i was refering to the 14.04.3 install that i tried first..  there has been a long running issue with linux and SiS graphics cards, and it seems that the laptop i have is one that is still affected. the only resolution i can have is 630x400 or something like that, and all windows within ubuntu are half cut off and so it is just unworkable.

As for the installation of 14.04.3 from the USB, i installed this to the windows partition, and because of the issues mentioned above, i booted back into windows, and manually deleted the two (unnamed) partitions, one was 1-2 gigs, and the other 10-15.

After manually deleting those two partitions, i then manually created a new partition, and selected this new partition in the Wubi GUI.
 
After the Wubi installation was complete, i then rebooted the computer and it is then that i got the no such partition message. 


looking at your comment, you mentioned that if i reinstall ubuntu again, i should still have windows 7.  do you mean that if i was to resinstall 14.04.3, it will replace the MBR with the ubuntu install, and from that point, i should be able to boot back into windows?

also, is there a way to revert back to the windows bootloader, rather than grub? 

thanks again :)

---

### Post by oldfred on 2015-11-09
Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

I do not know wubi. 
But you normally do not install it to another partition. If adding partitions, just might as well use a full partitioned install. 
Wubi also only boots from the Windows boot loader. So if you have installed grub do you have a full partitioned install?

Older systems do not run full Ubuntu as it requires a somewhat newer system and good grahpics card or chip. Often better then to use Lubuntu or Xubuntu.

You can use your Windows repair CD or flash drive to restore your Windows boot loader. You need to have that as most Windows repairs cannot be done from Linux.
You also can use Boot-Repair from a live installer to restore a Windows boot loader.

      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

     How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

