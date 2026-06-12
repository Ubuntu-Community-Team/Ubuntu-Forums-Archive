---
title: "Problem with boot menu not install w10!!!!!!!!!!"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by dimosss on 2015-12-09
&#921; have a huge problem on my ubuntu(15.10) version. My computer now has only ubuntu and i tried to install windows 10 via usb(as a live cd) unsuccessfully. Firstly i saw in the bios menu the message "SYSLINUX 6.03 EDD 20150813 Copyright (C) 1994-2012 H. Peter Anvin et al Boot Error". I fix that by searching on the website. So i formatted the hard disk on ntfs.

Now i have a different problem. When i open my pc i saw that message "error unknown filesystem entering rescue mode grub rescue>_". But if i use an ubuntu live cd the pc lets me to install the os. However when i am trying to install windows 10 i see the same message on a black screen "error unknown filesystem entering rescue mode grub rescue>_"

I tried to use some combinations like

set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
insmod normal
normal

or 

grub rescue> set prefix=(hd1,1)/grub
grub rescue> set root=(hd1,2)
grub rescue> insmod (hd1,1)/grub/linux.mod
grub rescue> normal


but when i wrote insomd normal i saw always this command "no such partition"
the same thing with normal word but i see a different message "unknown command normal"

Any help please?

---

### Post by yancek on 2015-12-09
> windows 10 via usb(as a live cd

There is no such thing as a live cd with windows.  Obviously, you can put windows on a usb and boot it to install.  If that is what you did, how did you do it?  Does your windows installation medium boot on another computer?  The "SYSLINUX" message is generally shown on boot from a CD/DVD or flash drive when installing a Linux system.  Is that what you were doing, booting the Ubuntu installation medium?

It isn't really clear from your post where you are at with the install.  Is the problem that you have installed Ubuntu and cannot now boot it?  Or you can boot Ubuntu but cannot install windows 10?  Or both?  

 >  So i formatted the hard disk on ntfs.

Does that mean you formatted the hard drive on which you had Ubuntu?  If so, there is nothing to boot from the hard drive.  I would think that if you have unallocated space on the drive on which to install windows, the installation should begin.  You could format a partition for windows ntfs from Ubuntu with GParted if you want.  Historically, it has always been much easier to install windows and then install another OS such as a Linux distribution/Ubuntu. 

Probably the best thing to do is to post more details which you can get by downloading the boot repair iso from the site below, burning it to a CD and booting it.  Select the Create BootInfo Summary option and do not try to do any repairs.  Post the link you get so someone here can review and advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dimosss on 2015-12-09
You are right. I meant i put windows 10 on a usb. Sorry but english is not my native language.

About the other you asking, i mean i can boot ubuntu but i am unable to install windows 10. So it is very easy to have every ubuntu version on my computer but now it is impossible to install every windows OS. ABout hard drive you are absolutely right. My hard disk is now ntfs and empty. So i assume that the problem is not on my hard disk but on my computer. If you need to post a screenshot or a video, in order to understand better my problem i will do it.

 I have been also tried boot-repair(as you recommend me to do). Here are the results [http://paste.ubuntu.com/13859180/](http://paste.ubuntu.com/13859180/)

However the problem is still remaining.

---

### Post by oldfred on 2015-12-09
You currently have MBR(msdos) partitioning.
Is hardware newer UEFI that can boot in UEFI or BIOS or older BIOS?
Windows only boots with BIOS from MBR partitioned drives.
Windows only boots with UEFI from gpt partitioned drives.
So how you boot install media UEFI or BIOS is how it installs, but that  must match your partitioning. If you partition in advance. 
Or you change partitioning before booting installer to match the way you want to install UEFI or BIOS.

You show a NTFS primary partition with boot flag, which is what Windows needs for a BIOS install when preformatted. If created with gparted it should be ok, but you may want to recreate with Windows?

---

### Post by dimosss on 2015-12-09
I think my hardware is older bios. My computer is hp pavilion dv6. So what do you suggest me to do? If you wish please explain it to me because i am newbie to linux. thank you

---

### Post by oldfred on 2015-12-09
If you are getting syslinux, I do not think you created Windows installer correctly. That is the Linux boot loader, which may be left over on flash drive. Only if you correctly installed Windows to flash drive would you get the install of the Windows boot loader to MBR, so it boots the Windows installer.

I do not know what system you have but most Windows tools should create a correct installer. But you do not just copy ISO or extract ISO to flash drive, you must install ISO to flash drive. Subtle difference is that installers format, extract & install boot loader to flash drive. 

I know Windows users have posted that Rufus works to create Ubuntu installer. Since it is a Windows application I would expect it to work for Windows also.
       Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

---

### Post by dimosss on 2015-12-09
Of course i know that i must install iso to flash drive. I have been tried to install windows 10 with that way but i had the problem with black screen and this message "error unknown filesystem entering rescue mode grub rescue>_". I will give a shot also with windows 7. About rufus i will find another pc with windows os and i will give a try to install windows 7 on my computer.

About the other you asked, now i do not have any system. Previously i had ubuntu only(i have been installed them on windows 10) and after i formated my hard disk i have not any OS on my pc. I am typing now by using my usb, which has ubuntu live-cd inside(if i say it right)

So until now i do not find another solution, except to install windows 7 via bios

---

### Post by oldfred on 2015-12-09
If you are getting grub rescue then you either do not have flash drive as first in boot order.  It is defaulting to hard drive which would still have grub in MBR, but not the rest of grub as partitions are now gone. 

Better to use one time boot key to chose the drive that is the flash drive.

Or you have not created a valid installer. Not sure how to check if Windows is correctly set up on flash drive as an installer.

---

### Post by yancek on 2015-12-09
If you are getting the Syslinux message you posted earlier then I doubt you have a correct windows installation medium.  Exactly how did you get windows on the flash drive?  It's possible to put windows on a flash drive and boot it from Grub to install.   The link below explains it in detail and you should be  able to do it from the Ubuntu Live CD on the flash drive if you have multiple usb ports.  If you decide to try it, read carefully before beginning.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

