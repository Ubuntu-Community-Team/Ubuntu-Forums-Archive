---
title: "Activating a partition to install a new Windows OS?"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by XxFunkMachinexX on 2011-04-01
Can't believe it took me this long to find a "New Thread" button. :P

I recently installed Ubuntu 10.10 and love it. BUT, I miss running applications that are only supported by Windows. Wine is fine and all but it doesn't seem compatible with certain programs..

I received a Windows 7 ISO and placed in on a 4gb flash drive and changed the boot order to boot from the USB first.

The first time I tried to boot from it, I got a black screen with sentence telling me there's nothing bootable on the USB. I researched it and found UNetBootin and thought I had this problem solved. BUT, The next time I tried to boot from it, I just got a single message that says "Boot Error".. :( I tried the same thing with a Windows XP and had the same terrible result.

I've used VirtualBox OSE and have ran both of them with no problem.

So what I really need someone to tell me is, Why does it keep giving me a "Boot Error"?!? And how do I fix it?

I have a Acer Aspire 5315 that originally had Windows Vista Basic.

I'm not SUPER smart when it comes to Ubuntu, but I know how to do things if I get the right directions! :D


Thanks for your time and I'd LOVE to get this issue fixed. :)

-Tevin

[Edit] I forgot the reason for the title. I tried to research the "Boot Error" problem and came across a page that talked about activating a partition but it was executed from a Window DOS thing.. Does the same thing apply here?
That website was: [http://www.askvg.com/how-to-create-bootable-usb-drive-to-install-windows-vista/](http://www.askvg.com/how-to-create-bootable-usb-drive-to-install-windows-vista/)

Another site that I tried was [http://blog.programmerslog.com/?p=383](http://blog.programmerslog.com/?p=383) but none of the codes worked for me because the result always said "-4 /dev/sdb1 0 255 63/usr/bin/mkdiskimage: /dev/sdb1: don't know how to determine the size of this device"

---

### Post by Hedgehog1 on 2011-04-01
What is happening to you is this:  Copying the .iso to a USB will not give you a bootable USB.

Instead, you need to install the .iso on the USB.

Here is a link with the tools:

[usb-linux-tutorials]("http://www.pendrivelinux.com/category/new-usb-linux-tutorials/")

You may need to search some more on what specifics win7 needs.

***The Hedge***

:KS

---

### Post by XxFunkMachinexX on 2011-04-01
I looked at the website you suggested and they all seem to be Linux related.. Was there a specific one that I just passed over?

I thought that my computer might not have had the right specs but I looked it up and it meets (at least from what I could tell) all the system requirements. I also tried to install a Windows XP OS  through the flash drive and I'm SURE my computer at least met THOSE specs.

---

### Post by oldfred on 2011-04-01
I have never used any of these. Most assume you have a version of Windows running. Then you have to borrow someone's computer that has windows.

Create Windows 7 USB 
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)
[http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944)

Create Windows 7 USB
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by XxFunkMachinexX on 2011-04-01
AND WE HAVE PROGRESS!!!!


I used the tutorial from the page [[COLOR=#444444]http://www.webupd8.org/2010/10/creat...usb-drive.html[/COLOR]]("http://www.webupd8.org/2010/10/creat...usb-drive.html"). Thanks oldfred!

I formatted the USB using that Gparted thing and formatted it to NTFS.

I had little faith it was going to work but BAM! Windows started loading files! :DD


But, when it came time for it to ask me where I want it to install Windows, it brought up two options.

Disk 0 Partition 1 which is 146.1GB with 0.0 MB Free Space and a System Type.


Disk 0 Partition 2 which is 2.9GB with 0.0 MB Free Space and a Logical Type.


Even lower down is a exclamation mark saying "Windows cannot be installed to Disk 0 Partition 1. (Show Details). When I click on it, it says "Windows cannot be installed to this hard disk space. Windows must be installed to a partition formatted as NTFS.

Windows cannot be installed to this hard disk space. The partition is of an unrecognized type."

When I highlight the Disk 0 Partition 1, there are some clickable icons at the bottom that are Refresh, Delete, Format, New, Load Driver, and Extend. I would have clicked Format, but it is shaded and unclickable.. :(

I'm leaving the computer as is until I can get some help so hurry! :D

Thanks for your help. :))

---

### Post by oldfred on 2011-04-01
Windows will want an entirely empty disk or a Primary partition formated to NTFS with the boot flag set on (active partition in windows speak).

Win7 will install to two partitions if it is a empty disk. A hidden boot/recovery partition of 100MB. That is so you can encrypt the main install. If you do not want to encrypt the main install you can install to one NTFS partition. 

You cannot install to a logical partition unless you install the boot files to a primary partition.

---

### Post by XxFunkMachinexX on 2011-04-01
Woah.. That was alot. I understood everything up to your second sentence. :P

So, am I out of luck or is there a way for me to format my main hard drive? I don't need to hold onto anything...

---

### Post by Hedgehog1 on 2011-04-01
If you would boot off your Ubuntu LiveCD/LiveUSB, select 'TRY'.

Menu to: System >> Administration >> Gparted Partition Editor.

The select the menu command:

[IMG]http://img834.imageshack.us/img834/8480/gpartedpartitiontable.png[/IMG]

gparted will clear the hard drive and make an 'MBR' partition table just like Windows wants to see.

Then you can install Windows. Later you can add a dual boot of Ubuntu.

***The Hedge***

:KS

---

### Post by oldfred on 2011-04-01
The Hedge's post has the two partition set up.

You just have to have one partition. But it must be a primary NTFS partition sda1 thru sda4 and use gparted to set the boot flag on. Right click manage flags.

---

### Post by XxFunkMachinexX on 2011-04-02
:D Thanks for all the help suggestions but after staring at the computer screen with a empty minded head, I decided to just click on the delete button on both of the hard drive things with NO assurance that this computer would ever work again. :P   It turned them both into Allocated space and I was able to format the hard drive, and click on new. It made my hard drive compatible and made another partition for a system restore. And BAM, it was in motion. :)))


I'm replying to this from my newly installed Windows 7 OS  right now. ;P Thank you so much everyone for all your help! :D :D :D

---

### Post by Hedgehog1 on 2011-04-02
> **XxFunkMachinexX said:**
> :D Thanks for all the help suggestions but after staring at the computer screen with a empty minded head, I decided to just click on the delete button on both of **the hard drive things** with NO assurance that this computer would ever work again. :P  

Those 'hard drive things' are ***partitions***. :D  But what matters is you are operational!

By hook or by crook - you got where you needed to be...


***The Hedge***

:KS

---

