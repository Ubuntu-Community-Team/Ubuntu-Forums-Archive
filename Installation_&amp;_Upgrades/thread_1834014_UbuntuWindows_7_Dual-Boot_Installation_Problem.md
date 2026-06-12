---
title: "Ubuntu/Windows 7 Dual-Boot Installation Problem"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by rebelagentm on 2011-08-26
I have two hard drives on my computer, one for my OS and apps (C:), and one for my data (D:). I recently reformatted my C: drive, re-installing Windows 7. I want to set up a dual-boot system with Ubuntu 10.04.
 
The problem I am having is that the Ubuntu installer recognizes my D: drive but not the C:. The C: drive is currently partitioned as follows:
 
100 MB NTFS Primary System Reserved
449.59 GB NTFS Primary
146.48 GB Unallocated
 
I have searched all over the net for answers, but none of the solutions I have found work.
 
Any thoughts?

---

### Post by Rubi1200 on 2011-08-27
Hi and welcome to the forums :-)

Are the disks labeled as Dynamic in Windows Disk Management?

Do you have a RAID array?

---

### Post by rebelagentm on 2011-08-27
I created an install disc for Ubuntu  11.04 and it was able to recognize both drives where the 10.04 disc  couldn't.

So, I now have both operating systems installed, but I am still having  an issue.  I want to use the Windows bootloader instead of GRUB, so I installed GRUB to my /boot partition for Ubuntu and used Windows' built-in BCDEdit to add an entry for Ubuntu  to my bootloader.  When I start the computer up, I get the boot menu  with both options, but when I choose Ubuntu, the screen just sits there  with a blinking cursor and never loads the OS.

Any thoughts?

---

### Post by rebelagentm on 2011-08-27
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Are the disks labeled as Dynamic in Windows Disk Management?

Do you have a RAID array?

Thanks for the welcome, Rubi!

The disks are not labeled as dynamic and I do not have a RAID array.

One thing that is interesting to me though is that in Windows Disk Management, all of the partitions show as primary.  How can that be?  I thought there could be only three primary partitions.

When I was installing Ubuntu, I created the partitions during the install and selected Logical for all of them.  I created /, /boot, /home, and swap space.

I followed the instructions located at [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/) to modify the bootloader.

---

### Post by Mark Phelps on 2011-08-27
The maximum number of primary partitions allowed is four, not three.  Sometimes, folks have three primary partitions and an extended partition -- but that is still the maximum of four.

Also, while Win7 is still working, do yourself a favor and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you ever need to repair the Win7 boot loader, or restore the original Win7 MBR.

---

### Post by rebelagentm on 2011-08-27
> **Mark Phelps said:**
> The maximum number of primary partitions allowed is four, not three.  Sometimes, folks have three primary partitions and an extended partition -- but that is still the maximum of four.

Also, while Win7 is still working, do yourself a favor and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you ever need to repair the Win7 boot loader, or restore the original Win7 MBR.

Thanks for the advice, Mark!

Windows Disk Management shows six primary partitions.  Two for Windows and four for the Ubuntu partitions I created.

Any thoughts as to why Ubuntu will not load on my system?  How often do dual-boot systems run into problems?

---

### Post by oldfred on 2011-08-27
+! on Mark Phelps suggestion for Windows repairCD. You should have a repair CD or current version liveCD for every system you have installed. I usually have another repairCD or two just in case. Of course BackUPS are required for any data you think is important.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


I prefer grub2's boot tloader but some Winodws 7 users like neosmarts's boot loader.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

With grub2 installed to the partition boot sector you may have troubles on updates and have to reinstall. It is considered less reliable in the partition boot sector.

But your issues may not even be with grub but with video. Do you get a grub menu or if not hold shift key down from the time you select Ubuntu. Not sure it that works when booting with window or not.

What video card so you have?

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by rebelagentm on 2011-08-27
> **oldfred said:**
> +! on Mark Phelps suggestion for Windows repairCD. You should have a repair CD or current version liveCD for every system you have installed. I usually have another repairCD or two just in case. Of course BackUPS are required for any data you think is important.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


I prefer grub2's boot tloader but some Winodws 7 users like neosmarts's boot loader.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

With grub2 installed to the partition boot sector you may have troubles on updates and have to reinstall. It is considered less reliable in the partition boot sector.

But your issues may not even be with grub but with video. Do you get a grub menu or if not hold shift key down from the time you select Ubuntu. Not sure it that works when booting with window or not.

What video card so you have?

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks!

I once had a dual-boot Windows XP and Ubuntu 9.04 setup, and GRUB got corrupted when I updated Windows, hence the reason I installed GRUB to /boot.  I assume that the trouble with updates you are talking about would be on the Ubuntu side?  Obviously, I don't want to have issues with that either.

Is there a way to have Windows 7 and Ubuntu 11.04 in a dual-boot configuration that won't cause one OS or the other to end up not working?

I have an NVIDIA GeForce GTS250 graphics card.  I do not see the GRUB menu at all, just a blinking cursor on an otherwise black screen.  I will try holding the Shift key and report back.

---

### Post by rebelagentm on 2011-08-27
> **oldfred said:**
> But your issues may not even be with grub but with video. Do you get a grub menu or if not hold shift key down from the time you select Ubuntu. Not sure it that works when booting with window or not.[]("http://ubuntuforums.org/showthread.php?t=1613132")

Holding the Shift key did not do anything.

---

### Post by oldfred on 2011-08-27
I have an older nVidia card 9600GT and have to use nomodeset on the linux line to get it to boot first time after install. Then I install the nVidia driver and have no issues.

You can try hitting down arrow once which in grub menu is recovery mode. Hit down arrow immediately after selecting Ubuntu. I have had grub remember keys even when menu not shown and hit it 5 times to boot my windows once.

---

### Post by rebelagentm on 2011-08-27
> **oldfred said:**
> I have an older nVidia card 9600GT and have to use nomodeset on the linux line to get it to boot first time after install. Then I install the nVidia driver and have no issues.

You can try hitting down arrow once which in grub menu is recovery mode. Hit down arrow immediately after selecting Ubuntu. I have had grub remember keys even when menu not shown and hit it 5 times to boot my windows once.

Unfortunately, no luck there either.  Any other ideas?

Having a dual-boot system would be nice, but I certainly don't want my operating systems getting hosed.  I could install Ubuntu in VirtualBox instead, but I have read that VirtualBox can slow your network connection.  Thoughts?

---

### Post by oldfred on 2011-08-27
It may be best just to install grub2's boot loader to the MBR. Then you can tell if it is grub issue or video issue and fix issue(s).  Then you can go back and reinstall your boot loader.

I have not tried any VMs, I prefer dual boot so I have full speed in both systems. But booting can be a hassle.

---

### Post by Mark Phelps on 2011-08-27
> **rebelagentm said:**
> Windows Disk Management shows six primary partitions.  Two for Windows and four for the Ubuntu partitions I created.

Any thoughts as to why Ubuntu will not load on my system?  How often do dual-boot systems run into problems?

So, HOW did you create the other partitions? (Sorry if I missed that in an earlier post).

And, Win7 still works OK?

What you SHOULD have done (and still can if you haven't actually installed Ubuntu), is have ONE Extended partition, with a bunch of partitions inside that, for Ubuntu.  That allows you to stay within the four-primaries maximum and doesn't run the risk of Win7 forcing the conversion of your partitions into Dynamic Disks -- which caused a new set of problems.

---

### Post by rebelagentm on 2011-08-28
> **oldfred said:**
> It may be best just to install grub2's boot loader to the MBR. Then you can tell if it is grub issue or video issue and fix issue(s).  Then you can go back and reinstall your boot loader.

I have not tried any VMs, I prefer dual boot so I have full speed in both systems. But booting can be a hassle.

Thanks!  I'll keep that in mind to help troubleshoot this.

---

### Post by rebelagentm on 2011-08-28
> **Mark Phelps said:**
> So, HOW did you create the other partitions? (Sorry if I missed that in an earlier post).

And, Win7 still works OK?

What you SHOULD have done (and still can if you haven't actually installed Ubuntu), is have ONE Extended partition, with a bunch of partitions inside that, for Ubuntu.  That allows you to stay within the four-primaries maximum and doesn't run the risk of Win7 forcing the conversion of your partitions into Dynamic Disks -- which caused a new set of problems.

I created a new volume in Windows 7 and then created the partitions for Ubuntu during the install of 11.04.

Win7 still works fine.

As for your suggestion, I have a couple of questions:

1)  Do I leave the space where I want to install Ubuntu as "Unallocated" or do I need to create a new volume in Win7 first?

2)  Earlier on, I tried using a GParted Live CD to create partitions first, but it had the same problem of not recognizing my hard drive in the first place.  Can I use the Ubuntu Live CD in "Try Ubuntu" mode to create the extended partition and then partitions inside it using GParted?

Also, I agree having a rescue disk is always good practice.  Regardless of that though, how often do dual-boot configurations get messed up?

Thanks!

---

### Post by oldfred on 2011-08-28
If you used windows to create partitions, did it say it was converting from basic to dynamic. Nothing works with dynamic paritions. It is a one way conversion and even windows does not repair dynamic partitions in some cases.

Post this from liveCD.
```

sudo fdisk -lu
```

---

### Post by Ubaru on 2011-09-01
Hey, I am dual booting Win7 and Ubuntu 10.10 on same puter.  I have found through some forums that the windows bootloader doesn't like any competition so when you install windows after installing Ubuntu, it'll wipe it out.  I installed Win7 first on a primary partition, then left the other half of the drive for Ubuntu.  (a 1TB WD)  I have been using Grub2, which Ubuntu automatically sets up to load into Ubuntu(fine by me b/c just getting fed up with windows).  When installing Ubuntu I just created a second primary partition to install it on and also swap space of ~2gb? With this, I haven't had any issues updating Win7 or Ubuntu 10.10.  When i originally installed the OS's I had an nvidia 7600gs video card.  supposedly nvidia has a little trouble with Ubuntu, but i didn't have a problem, although I am now using the on-board ATI Radeon HD4250 graphics due to the 7600 dying on me.  The switch was effortless too.  The little cursor blinks for ~1min on my other 2 ghz 400mb ram pc that's running Ubuntu 10.10 before it flashes to Ubuntu splash screen.

---

