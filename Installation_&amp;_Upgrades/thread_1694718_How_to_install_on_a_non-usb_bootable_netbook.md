---
title: "How to install on a non-usb bootable netbook"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by JBudOne on 2011-02-24
Hey Ubuntu-ers! 

I'm looking to upgrade my netbook from the default Windows 7 Starter pack, over to the ever amazing Debian Ubuntu package. The problem is that, just as the title suggests, my netbook is unable to boot from a USB device, nor does it have a slot to place CDs/DVDs in. I'm not really in the position to purchase an external CD/DVD drive, however I'm not sure that would work anyways since it would connect via USB.. What can I do? Am I stuck with Windows 7 forever on this netbook? Is there any other way around this? Please let me know. Also, I would like to apologize if this thread belongs under the Laptops/Hardware section instead - and feel free to move it if it does.. Thank you for any help that any of you may provide =]

---

### Post by violinuxer on 2011-02-24
Hello there!

Google "Wubi"- an ubuntu installation that works pretty much like a dual-boot, except for the fact that it's installed inside Windows. You can uninstall like any other windows program. Otherwise works like a normal Ubuntu installation.

Limitations- 

Slightly slower due to the use of windows NTFS filesystem

Not sure about UNR on wubi. If Worst comes to worst you can install Unity desktop from synaptic package manager.

No Hibernation

Look here for installation instructions:

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

All the best!

violinuxer

---

### Post by Coley Gross on 2011-02-24
Your quote is below for Im not used to posting. I am VERY new to Linux Ive only dabbled in it once in a blue moon over the last 8 years.

You didnt state the make and model of your netbook but I got a weird feeling yours would simply auto boot from any bootable device you placed in any of your usb drives. At least there should be a key or combo to press to select what boots first.

OK lets assume you truly don't have it. I have not done this so I cant guarantee it but I see no reason why you couldn't go to [http://unetbootin.net](http://unetbootin.net) or similar linux live creator. with unetbootin you have a dozen or more linux live operating systems  Im not sure you can use WUBI (the windows based linux live installer) with "any" live version so before you go and download a giant 700 meg file ( I like Windows ultimate gamers edition, I think its like a couple gigs). You can go to distrowatch.com and type the live version into their search window and it will show you what files (in other words if wubi is in the mix) then you can use, I think winrar (free windows pgm like winzip but I think it does .ISO's or if it doesnt (they are small windows programs go to snapfiles.com or sourceforge and get a windows iso extractor and extract the yourLinuxChoice.ISO to c:\temp\linux run the WUBI.EXE file and it will install but as the prior poster said a bit slower due to NTFS.

I sincerely recommend that you allow the program UNETBOOTIN make a bootable USB drive for you. Download a small live program for the test like dam small linux (I am pretty sure it is one of the choices on UNETBOOTIN. Maybe 50 megs is all. Turn you computer off as normal and turn it back on with the newly created SAM SMALL LINUX USB drive in place. Maybe if there is a bootable usb drive in your slot an option to choose will appear. Just a plain usb stick wouldnt trip any option to boot from usb. 

The builder knows you will occasionally sooner or later need to reinstall windows. That just seems to be the way windows is. Then again if you just so happened to have a restore cd you can bet you have the option to boot via usb however to save money a lot of mfg are making a well hidden drive that has all the origional restore software and drivers on it. For some reason I had a toshiba and a everex and I deleted the extra origonal install partition for more room but what I didnt know is that the idiots that either include a restore cd or tell you how to make your own restore cd for some reason create said restore cd to look for certain info located on the hidden partition or the darned compuiter refuses to restore. I suppose they are trying to keep you from using win7 on more than one computer.  The most idiotic programming I have ever ran into. Don't ask me why I got lucky n one and copied the partition just in case. It was a pain (since I have little experiance) getting the partition tables back to factory but it wouldnt restore without the restore partition. It is as if you make a cd with 600 megs of data but when you restore it seems to use about 50 megs then pull the rest of the restore off the hidden restore partition. It makes no sense to tell you that you can make a set of restore cd's if in fact they want work if the factory hard drive partition is missing. For example if I wanted to increase the size of the drive it wouldnt allow windows back on. The  reason Im telling this to you is so you dont kill your restore partition. You never know if and when you will need it. I did a lot of learning on a seldome spoke of linux live called YLMF It is suppose to be made to look and feel just like you have got on a windows XP machine for the most part it is kool. For some reason I couldnt get the software installer to work unless I opened it via terminal then the GUI version loads. Figure that one out.

Good luck. I have a feeling your going to be smiling when you see your system boot via USB.

Coley

> **JBudOne said:**
> Hey Ubuntu-ers! 

I'm looking to upgrade my netbook from the default Windows 7 Starter pack, over to the ever amazing Debian Ubuntu package. The problem is that, just as the title suggests, my netbook is unable to boot from a USB device, nor does it have a slot to place CDs/DVDs in. I'm not really in the position to purchase an external CD/DVD drive, however I'm not sure that would work anyways since it would connect via USB.. What can I do? Am I stuck with Windows 7 forever on this netbook? Is there any other way around this? Please let me know. Also, I would like to apologize if this thread belongs under the Laptops/Hardware section instead - and feel free to move it if it does.. Thank you for any help that any of you may provide =]

---

### Post by JBudOne on 2011-02-25
Wow, thanks for the tips guys! I haven't ever even heard of Wubuntu, but I downloaded/installed it and it works like a charm! 

@Coley  I believe its an HP Mini 210 Series.. I forget the exact make though. I've tried using Bootable USB's though with no luck on the thing, after so many tests/fails I ended up calling up the tech support group, and they informed me that my netbook doesn't have the ability to boot from a USB =[  I honestly don't see why they would put that limitation on this, is it really that tough/expensive of a feature to add in ?  


Anyways, thanks for the help guys =]

---

### Post by violinuxer on 2011-02-25
Two things- make sure you defrag often as Wubi relies on the windows partition and Fragmentation can slow it down. Also make sure your files are backed up- you dont want to lose all your files when windows bites the dust (as it too often does! :P)

Good to here that it's working!:D

violinuxer

P.S. I think we can mark this as solved.

---

