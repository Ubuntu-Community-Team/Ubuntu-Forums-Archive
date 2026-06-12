---
title: "GRUB and dual boot"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-05-16
I already have Windows 2000, multiiboot, and I wish to add Ubuntu 7.04.

Linux would be installed in an ext3 on a USB drive (last 30GB of a 200GB drive).

It is my understanding that this can be accomplished by:
1. Installing Linux from the LiveCD to  the USB drive, call it /dev/sdb5.
2. Copying the GRUB boot sector to, say, a FAT32 drive, booting to Windows, putting the GRUB boot sector file on the C drive, and modifying boot.ini accordingly

The rub here is that the Ubuntu 7.04 install seems  to not offer an option to NOT place the GRUB boot record in the MBR of sdb5. So I am not sure where the boot record was recorded.

I had already used Partition Magic to create the ext3 and swap partitions, so I likely should not have allowed the install to format the drives.I may need to reformat the partitions with Partition Magic, then redo the install.

Is there a cheat sheet of the exact steps I must follow to achieve a dual boot using the NT Loader and GRUB?

Currently, I get a GRUB GEOM Error when trying to boot to Linux.

---

### Post by Howard Kaikow on 2007-05-16
Being a masochist, I reformatted the ext3 partition and tried another install from the LiveCD.

This time, I understood how to cause the GRUB boot loader to NOT be written to the boot sector.

However, I still get the GRUB GEOM ERROR.

Anyi deas?

---

### Post by Howard Kaikow on 2007-05-17
Unless I can install Linux so that I can multiboot with Linux on a USB drive, I just cannot use Linux, at least on my current system.

I reformatted the USB drive so the ext3 partition is the first partition on the drive to avoid the possible 1024 cylinder issue.

I had GRUB write the loader to the partition, not the MBR.

I then copied the GRUB boot sector to the C drive, adjusted boot.ini accordingly, but still get GRUB GEOM ERROR.

What can cause this problem?

Would the C drive have to be FAT32?


When NT Loader is running are the USB drives available?

---

### Post by confused57 on 2007-05-17
Creating ext3 partitions for Ubuntu using Partition Magic doesn't usually work...if this is what you did, I'd recommend using the desktop live cd installer to format the ext3 partitions & swap that you're installing Ubuntu on.

If you install grub to the root partition, you could use the GAG bootloader(floppy or cd) to boot your external drive:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

You could boot your Ubuntu regardless of where grub is installed, by using the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Howard Kaikow on 2007-05-17
> **confused57 said:**
> Creating ext3 partitions for Ubuntu using Partition Magic doesn't usually work...if this is what you did, I'd recommend using the desktop live cd installer to format the ext3 partitions & swap that you're installing Ubuntu on.

The LiveCD insists on formatting the / partition anyway.
I believe it is also formatting swap.

> **confused57 said:**
> If you install grub to the root partition, you could use the GAG bootloader(floppy or cd) to boot your external drive:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

I'll take a look.
One more thing on which to gag.

> **confused57 said:**
> You could boot your Ubuntu regardless of where grub is installed, by using the Super Grub Disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Ayup, I just download SGD and the info at hermanzone.

> **confused57 said:**
> 
The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

So, I've heard.

Thanx.

---

### Post by bulldog on 2007-05-17
> **Howard Kaikow said:**
> The LiveCD insists on formatting the / partition anyway.
I believe it is also formatting swap.



I'll take a look.
One more thing on which to gag.



Ayup, I just download SGD and the info at hermanzone.



So, I've heard.

Thanx.

Most important to know,**can you boot from an USB device** if not it probably won't work anyway.
If you have such an option when you boot,you have to put ubuntu with GRUB on the external drive.

If I didn't understand it at all,never mind........:)

---

### Post by Herman on 2007-05-17
Hello Howard Kaikow,
I agree with confused 57 and bulldog.

Knoppix is a very nice debian based distribution which runs from a CD or DVD and works very well with a USB disk. Please visit  the [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html") of my website, there you will find an illustrated step by step how-to for setting up Knoppix with a persistent /home in a USB disk, optionally encrypted to AES256. I recommend Knoppix if you want a nice Linux distro that is made for use with USB disks. 
That will be a lot easier for you and better. It will save you a lot of time and frustration. Your (Microsoft) computer will be safe, you can keep booting with NTLDR and do all your partitioning with Partition Magic. :)

The easiest and best way to install Ubuntu is to do your partitioning with one of the the Ubuntu installation CDs. The 'Alternate' CD uses  partman and the 'Desktop' (Live) CD uses a version of GParted.  Install Ubuntu to hard disk, and install Grub boot loader to the MBR of your first hard disk. 

It is possible to install Ubuntu and boot it from a USB disk, but I have never tried it. I believe it is a little advanced. Here is a link to the most famous thread I know of on that subject, [SUCCESS - Breezy loaded on external USB drive !]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+on+usb")
 All you need to know will probably be there,
Regards, Herman :)

---

### Post by Howard Kaikow on 2007-05-17
> **Herman said:**
> Hello Howard Kaikow,
I agree with confused 57 and bulldog.

Knoppix is a very nice debian based distribution which runs from a CD or DVD and works very well with a USB disk. Please visit  the [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html") of my website, there you will find an illustrated step by step how-to for setting up Knoppix with a persistent /home in a USB disk, optionally encrypted to AES256. I recommend Knoppix if you want a nice Linux distro that is made for use with USB disks. 
That will be a lot easier for you and better. It will save you a lot of time and frustration. Your (Microsoft) computer will be safe, you can keep booting with NTLDR and do all your partitioning with Partition Magic. :)

The easiest and best way to install Ubuntu is to do your partitioning with one of the the Ubuntu installation CDs. The 'Alternate' CD uses  partman and the 'Desktop' (Live) CD uses a version of GParted.  Install Ubuntu to hard disk, and install Grub boot loader to the MBR of your first hard disk. 

It is possible to install Ubuntu and boot it from a USB disk, but I have never tried it. I believe it is a little advanced. Here is a link to the most famous thread I know of on that subject, [SUCCESS - Breezy loaded on external USB drive !]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+on+usb")
 All you need to know will probably be there,
Regards, Herman :)

Thanx, I'll take a look later today.

It seems that the ultimate problem is that the GRUB GEOM ERROR likely means that the GRUB loader cannot get to the USB drive.

Would SGD handle this?

Does the SGD have drivers to handle extermal USB drives?
For example, the Acromis True Image rescue CD uses Linux and includes drivers enabling acces to USB drives. It would seen that SGD could do the same.

In my case, the USB drives are not connected to the mobo, rather, they are connected to an Adaptec USB card.

---

### Post by Howard Kaikow on 2007-05-17
Looking in the BIOS menus, I see no option to boot from USB.

I will look at SGD, and other, boot managers.

If they will not do the deed, then I may, Sigh!, remove the tape drive (not used in about 4 years) and add a 4th hard drive to the system.

The difficulties are:

1. All current drives are SCSI, so adding a non-SCSI drive, tho less expensive, might mess up drive lettering.

2. Cabling. The tape drive is just below an ATAPI CD-RW, so it will likely not be difficult to have the CD-RW and 4th drive on the same IDE controller. For SCSI. not sure the current cabling mess can easily, if at all, add a 4th SCSI drive.

3. I would need to add a drive fan ordrive  bay fan.

---

### Post by Howard Kaikow on 2007-05-17
I believe the problem is that my USB drives go thru an Adaptec USB 2 connector, and the mobo BIOS does not appear to support booting from USB.

I tried a  Super Grub CD and, SGD did not make the USB drives available.

Guess, I gotta decide whether to ditch the tape drive and add a 4th hard drive.

---

### Post by Howard Kaikow on 2007-05-17
> **Howard Kaikow said:**
> I believe the problem is that my USB drives go thru an Adaptec USB 2 connector, and the mobo BIOS does not appear to support booting from USB.

I tried a  Super Grub CD and, SGD did not make the USB drives available.

Guess, I gotta decide whether to ditch the tape drive and add a 4th hard drive.

Could I have forced SGD to make available the USB drives?

---

### Post by Herman on 2007-05-17
>  It seems that the ultimate problem is that the GRUB GEOM ERROR likely means that the GRUB loader cannot get to the USB drive. Here is the best link I know of about the Grub GEOM error, [SDB:The Boot Process Hangs with the Message GRUB Geom Error]("http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error")
>  Would SGD handle this? SuperGrubDIsk does have some special modifications in it so you can use a command called 'usbshift', by adrian 15. I think if you had a computer that had the ability to boot from USBdisk it would be a good idea to use SuperGrub instead of regular grub to boot with. Read this thread in Hardware Guys Forum by mikemqa and adrian15, [GRUB on USB Thumb Drive]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=12;t=5353"). This link explains how mikemqa and adrian15 can use the '[COLOR=#000000]setgrubdevice' and[/COLOR] 'usbshift' commands to make the usbdisk's grub get the hard disk numbering right. 
However, you still need a computer that has the ability to boot from USB in the BIOS.
>  Does the SGD have drivers to handle extermal USB drives? SuperGrub DIsk is very super, but not quite that super. :) You could try checking your BIOS version and date and then going to your computer manufacturer's website or a BIOS website and looking for an updated version of your BIOS, maybe if you are very lucky there will be one that can make your motherboard boot from USB disk. You would have to be very lucky, but you can try.  
If you don't know how to check your BIOS version number, here's an example showing how I do mine, [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information").

I think you are wasting your time trying to get Ubuntu to boot in a USBdisk.
You will be better off to use a Knoppix CD or DVD like I said already, it will still work with your USB, because you will be booting Knoppix in the CD or DVD, and just reading and writing the persistent /home in your USB disk. That will work fine. 
Or, the other way, as you said, remove your tape drive that you never use and plug the hard disk in there instead. Ubuntu is made for booting inside your computer. Even though it is possible in some computers to get it installed in a USB, that isn't what Ubuntu is mainly for. 
You can use a screwdriver for a pry bar but it doesn't make the best pry bar. You can use a screwdriver  handle for a hammer but it doesn't make the best hammer. In a workshop, you can get a lot more work done when you use the right tools for the job you are trying to do.
It's the same with Linux distros, you will find things a lot easier if you choose the right distro for what you want to do. :)

Regards, Herman  :)

---

### Post by Howard Kaikow on 2007-05-17
> **Herman said:**
> 
However, you still need a computer that has the ability to boot from USB in the BIOS.
 SuperGrub DIsk is very super, but not quite that super. :) You could try checking your BIOS version and date and then going to your computer manufacturer's website or a BIOS website and looking for an updated version of your BIOS, maybe if you are very lucky there will be one that can make your motherboard boot from USB disk. You would have to be very lucky, but you can try.  
If you don't know how to check your BIOS version number, here's an example showing how I do mine, [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information").

The mobo is 9 years old, and, has the latest BIOS update issued by Micron (the system manufacturer).
Even if Intel had a more recent update, I would not be courageous enough to install on an OEM mobo.

> **Herman said:**
> 
Or, the other way, as you said, remove your tape drive that you never use and plug the hard disk in there instead.

I'm leaning in that direction.

> **Herman said:**
> Ubuntu is made for booting inside your computer. Even though it is possible in some computers to get it installed in a USB, that isn't what Ubuntu is mainly for. 


A hard drive by any other name is a hard drive.
Working around the mobo restrictions is the problem.

---

### Post by Herman on 2007-05-17
> A hard drive by any other name is a hard drive.
Working around the mobo restrictions is the problem. Yeah, you're right. :)

A hard drive is just a hard drive. We only call it a USB drive or an IDE drive depending on how we decide to plug it in to the motherboard. I have several hard drives here in USB caddys myself, they have all been used as internal hard drives at some point in time, and when I feel like it I just remove them again and put them back in their boxes and use them as external USB drives again, and then visa versa.

Some new computer cases today feature very quick and easy removal and switching of hard drives. For most computer cases you have to open the case and fiddle around a little with cable connections and a screwdriver. If you aren't experienced you should read up about that first. Be especially careful about ESD (ElectroStatic discharge). The other thing is to be aware of IDE hard drive cabling and jumper settings. 

Regards, Herman :)

---

### Post by Howard Kaikow on 2007-05-17
> **Herman said:**
> Yeah, you're right. :)

A hard drive is just a hard drive. We only call it a USB drive or an IDE drive depending on how we decide to plug it in to the motherboard. I have several hard drives here in USB caddys myself, they have all been used as internal hard drives at some point in time, and when I feel like it I just remove them again and put them back in their boxes and use them as external USB drives again, and then visa versa.

Some new computer cases today feature very quick and easy removal and switching of hard drives. For most computer cases you have to open the case and fiddle around a little with cable connections and a screwdriver. If you aren't experienced you should read up about that first. Be especially careful about ESD (ElectroStatic discharge). The other thing is to be aware of IDE hard drive cabling and jumper settings. 

Regards, Herman :)


I've done that stuff, including replacing a mobo.

The biggest issue is finding a drive with a capacity that can be supported by the SE440BX mobo.
No emply slots to add a controller card.

---

### Post by Herman on 2007-05-17
Hey! :)

This link looks promising! [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
I was looking for something else for you in the Official Ubuntu Wiki when I found that, check that out! That might be just what you need! :)

I think This is the link I was actually looking for, [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") - Installing Ubuntu or Kubuntu on a USB pendrive with persistent mode.

It would be easier just to use Knoppix instead though. I also looked up [gnoppix]("http://www.linuxshop.de/shop/catalog/index.php?cPath=36&osCsid=1e911cf36ddb8222f35e8faf4bae242c") for you, that would be Knoppix with the Gnome desktop, which would be very similar to Ubuntu. I see it has been discontinued. I imagine it has the option for using the  English language if you don't speak German, (I can't either).

Other than that, as you say, you may need to look for a hard disk drive that isn't to big for your BIOS. Hard disks are relatively cheap nowadays but it's hard to find some very small ones. I think they still make new 20 or 30 GB hard disks. I have picked up old second hand hard disks 20 GB and under  that no-one wants but  are still usable for very low prices from computer shops that do upgrades. 
Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

Regards, Herman :)

---

### Post by Howard Kaikow on 2007-05-17
> **Herman said:**
> Hey! :)

This link looks promising! [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
I was looking for something else for you in the Official Ubuntu Wiki when I found that, check that out! That might be just what you need! :)

Thanx!

Sigh!
I must admit that I found that article a few daze ago.
I guess that I forgot to print it out, or misplaced the printout.

For any OS, there has to be a way to create a CD that boots the OS.

---

### Post by Herman on 2007-05-17
Can't you just move a lot of stored data like music and videos if that's what's taking up the hard drive space in your existing drives and put the data on the USB disk? Then you'd have room to install Ubuntu in one of your existing hard disks. That would be a lot simpler.
Regards, Herman :)

---

### Post by Howard Kaikow on 2007-05-18
> **Herman said:**
> Can't you just move a lot of stored data like music and videos if that's what's taking up the hard drive space in your existing drives and put the data on the USB disk? Then you'd have room to install Ubuntu in one of your existing hard disks. That would be a lot simpler.
Regards, Herman :)

No.

tHe system is multiboot as follows on 3 SCSI hard drives:

Drive 1(9GB): C and D
Drive 2(18GB): F-H
Drive 3(36GB): I-M

OS are on C, F, G, and J.
Lots of stuff is shared amongst the 4 OS on, say, I,  K, L and M.
As of 12 May 2007:

```
Drive	Total Bytes	Free Bytes	Available Bytes	Used Bytes	Used(%)

C	4,318,236,672	884,654,080	884,654,080	3,433,582,592	79.51%
D	4,778,852,352	659,378,176	659,378,176	4,119,474,176	86.20%
F	8,587,157,504	1,362,337,792	1,362,337,792	7,224,819,712	84.14%
G	8,587,157,504	859,811,840	859,811,840	7,727,345,664	89.99%
H	1,176,178,688	333,185,024	333,185,024	842,993,664	71.67%
I	8,587,157,504	5,040,033,792	5,040,033,792	3,547,123,712	41.31%
J	8,587,157,504	1,251,889,152	1,251,889,152	7,335,268,352	85.42%
K	8,587,157,504	5,003,182,080	5,003,182,080	3,583,975,424	41.74%
L	8,587,157,504	3,663,622,144	3,663,622,144	4,923,535,360	57.34%
M	2,413,461,504	1,962,921,984	1,962,921,984	450,539,520	18.67%
Total	64,209,674,240	21,021,016,064	21,021,016,064	43,188,658,176	67.26%
```

I still intend to look into the booting from USB this weekend, but I have decided that rather than spend money on a 4th drive, cooling fan/bay cooler, and the aggrevation of removing tape drive, fiddling with cabling, it may be better to just appy that money to buying/building a low end PC.

---

### Post by Herman on 2007-05-18
Oh, okay, I can see your problem, now I understand a little better. :(

That's a good idea you have to just appy that money to buying/building a low end PC.
I have a 'new' PC here, it is my best computer now, made out of old parts and a few new ones. I was visiting my brother's place and pulled an old broken PC out of the hay in an old shed. They said it was no good and the next stop for it was the rubbish dump. I am an incurable fiddler and immediately started testing to see what was wrong with it and if I could fix it. It needed a new motherboard. I guess I went a little overboard. Originally it had a 700 Mhz celeron processor, 128 mb of RAM and a 20 GB hard disk.
Now it has an ASUS M2V-TVM motherboard, AMD Athlon 64 3500+ AM2 SKT940 processor and 1 GB DDR@533Mhz memory in a new case and power supply. That cost only about $405.00, which is about a third of the cost of an equivalent PC if I bought it new. 
It sure is a lot faster now than before I started! Oh, and to fix the worst problem I deleted Windows out of it and replaced it with free space for data.   :)

Old parts I'm using are a keyboard, monitor, hard disk and CD-ROM drive. Those don't matter too much to the performance. I would like to add a DVD drive some day.
I bought some hard drives, those were about $100 each, for 160 GB ones. I got two IDE hard disks and two SATA hard disks.  I put two IDE hard drives in the old (but now new) computer. It has room for seven drives now if I want.

The biggest saving comes from using Ubuntu. I could have gone and bought a new computer with a certain well known operating system in it which they tell you is "free with your new computer" and anyway you have no choice. (That's changing that goodness!). With Ubuntu in it it does everything already, there is no need to go buy another half a dozen CDs fuil of software to add to the operating system to make it do something. That's what really blows up the cost of a new computer that the salesman might forget to tell you about until he has your money. I do add some software to Ubuntu too, but I download that for free over the internet.

From now on if I ever buy a new computer it will be a Dell, with Ubuntu already in it, or else I'll build my own and install Ubuntu myself. 
Before I had Ubuntu all I did was scan for viruses and malware and watch my firewall. Knowing all the time I was being fooled into a false sense of security. I had some bad malware for six months that could have turned my computer into a zombie, under the total control of a stranger somewhere, and the antivirus and anti malware (well know and trusted brand) assured me the whole time I was safe because I was paying them for their great services.  Eventually an online scan with a different brand discovered the malware after it had been in my computer for six months. I confirmed it with another different brand of on-line scan. And all that time they were still telling me my computer and my data was "safe and protected". (As long as I keep paying). Hmmph! :lolflag:

I would upgrade your old computer and put aside the old discs with that junk software in them and just keep the CD Drive like I did. get a modern mother board, processor and case and take your 200 GB drive in it. Put one of the other old drive in the external USB case. Use it for a data drive, that's all it's good for. Convert to a*** real ***operating system! :)
You''l be glad you did!
Regards, Herman :)

---

### Post by Howard Kaikow on 2007-05-18
> **Herman said:**
> Oh, okay, I can see your problem, now I understand a little better. :(

That's a good idea you have to just appy that money to buying/building a low end PC.
I have a 'new' PC here, it is my best computer now, made out of old parts and a few new ones. I was visiting my brother's place and pulled an old broken PC out of the hay in an old shed. They said it was no good and the next stop for it was the rubbish dump. I am an incurable fiddler and immediately started testing to see what was wrong with it and if I could fix it. It needed a new motherboard. I guess I went a little overboard. Originally it had a 700 Mhz celeron processor, 128 mb of RAM and a 20 GB hard disk.
Now it has an ASUS M2V-TVM motherboard, AMD Athlon 64 3500+ AM2 SKT940 processor and 1 GB DDR@533Mhz memory in a new case and power supply. That cost only about $405.00, which is about a third of the cost of an equivalent PC if I bought it new. 
It sure is a lot faster now than before I started! Oh, and to fix the worst problem I deleted Windows out of it and replaced it with free space for data.   :)

Old parts I'm using are a keyboard, monitor, hard disk and CD-ROM drive. Those don't matter too much to the performance. I would like to add a DVD drive some day.
I bought some hard drives, those were about $100 each, for 160 GB ones. I got two IDE hard disks and two SATA hard disks.  I put two IDE hard drives in the old (but now new) computer. It has room for seven drives now if I want.

The biggest saving comes from using Ubuntu. I could have gone and bought a new computer with a certain well known operating system in it which they tell you is "free with your new computer" and anyway you have no choice. (That's changing that goodness!). With Ubuntu in it it does everything already, there is no need to go buy another half a dozen CDs fuil of software to add to the operating system to make it do something. That's what really blows up the cost of a new computer that the salesman might forget to tell you about until he has your money. I do add some software to Ubuntu too, but I download that for free over the internet.

From now on if I ever buy a new computer it will be a Dell, with Ubuntu already in it, or else I'll build my own and install Ubuntu myself. 
Before I had Ubuntu all I did was scan for viruses and malware and watch my firewall. Knowing all the time I was being fooled into a false sense of security. I had some bad malware for six months that could have turned my computer into a zombie, under the total control of a stranger somewhere, and the antivirus and anti malware (well know and trusted brand) assured me the whole time I was safe because I was paying them for their great services.  Eventually an online scan with a different brand discovered the malware after it had been in my computer for six months. I confirmed it with another different brand of on-line scan. And all that time they were still telling me my computer and my data was "safe and protected". (As long as I keep paying). Hmmph! :lolflag:

I would upgrade your old computer and put aside the old discs with that junk software in them and just keep the CD Drive like I did. get a modern mother board, processor and case and take your 200 GB drive in it. Put one of the other old drive in the external USB case. Use it for a data drive, that's all it's good for. Convert to a*** real ***operating system! :)
You''l be glad you did!
Regards, Herman :)

I cannot junk the old computer.
It has 4 Windows 2000, each with a different version of MSFT Office.
When I can find Clients, I write VBA macros to fill my tummy.
Indeed, I cannoot become a full time Linux user until I learn how to write equivalent programs for OpenOffice. I've heard there is a VBA prohect for OpenOffice, but I'm not ready to investigate.

System has an SE440BX mobo, with a numbe rof ISA slots, all slots filled.
It would be easier to build a new critter.

Not yet read, but [Triple Booting]("http://ubuntuforums.org/showthread.php?t=220452") seems interesting.

---

### Post by Herman on 2007-05-18
[http://en.wikipedia.org/wiki/Visual_Basic_for_Applications](http://en.wikipedia.org/wiki/Visual_Basic_for_Applications)

Hey, you will really LOVE Ubuntu then! If you enjoy doing things like that.

I think the future will be with open source. A lot of users are switching over to it, and more and more who have all kinds of different skills and abilities too. Some day in the not too distant future you will find customers who won't have MSFT Office anymore, they'll have [    Open Office.org]("http://www.openoffice.org/") or [    KOffice]("http://www.koffice.org/"). In the future businesses won't want software they can't legally have someone program to suit their exact business needs, (not to mention the fact that what they use now has so many vulnerabilities).

I still think that at least for now the first thing I suggested will be the best. Try Knoppix. Knoppix is a little slow on less than 512 Mb or RAM, but you'll be able to do all you want to do. It will only take five minutes to create a persistent /home for it in your external USB drive. Stick around Ubuntu Web Forums and when you get around to building your new machine then install Ubuntu and just copy and paste all your Knoppix stuff into your new Ubuntu /home. The applications are the same, Ubuntu will open all the work you do in Knoppix. If it doesn't just install KDE desktop in Ubuntu. Then Ubuntu will be quite similar to hard disk installed Knoppix, but with over 27721 packages you can install if you want! :)
Regards, Herman :)

EDIT: I went to look for some other Grub thread that I might be able to help with and found your other thread: [Booting from USB]("http://ubuntuforums.org/showthread.php?t=447773&highlight=grub"). :)
You already have a stage2 eltorito if you installed Ubuntu in your usbdisk. Look in [FONT=Bitstream Vera Sans Mono]/usr/lib/grub/i386-pc [/FONT]you should find one there. :)

---

### Post by Howard Kaikow on 2007-05-18
> **Herman said:**
> [http://en.wikipedia.org/wiki/Visual_Basic_for_Applications](http://en.wikipedia.org/wiki/Visual_Basic_for_Applications)

Hey, you will really LOVE Ubuntu then! If you enjoy doing things like that.

I think the future will be with open source. A lot of users are switching over to it, and more and more who have all kinds of different skills and abilities too. Some day in the not too distant future you will find customers who won't have MSFT Office anymore, they'll have [    Open Office.org]("http://www.openoffice.org/") or [    KOffice]("http://www.koffice.org/"). In the future businesses won't want software they can't legally have someone program to suit their exact business needs, (not to mention the fact that what they use now has so many vulnerabilities).

OPenOffice, Koffice, etc. will not be a valid replacement for MSFT Office for quite a long time.
In the real world, lots of folkes take advantage of VBA macros, the integration of the Office apps, the Windows API, etc.

Even if the day should come that OpenOffice would have equivalent capabiloity, th cost of conversion will be huge.

And open source sounds nice, but programmers want to have proprietary code. OpenOffice violates the protections given code by MSFT Office.

Any way, I'm not willing to discuss this religious issue.
> **Herman said:**
> 
I still think that at least for now the first thing I suggested will be the best. Try Knoppix. Knoppix is a little slow on less than 512 Mb or RAM, but you'll be able to do all you want to do. It will only take five minutes to create a persistent /home for it in your external USB drive. Stick around Ubuntu Web Forums and when you get around to building your new machine then install Ubuntu and just copy and paste all your Knoppix stuff into your new Ubuntu /home. The applications are the same, Ubuntu will open all the work you do in Knoppix. If it doesn't just install KDE desktop in Ubuntu. Then Ubuntu will be quite similar to hard disk installed Knoppix, but with over 27721 packages you can install if you want! 
I'm not interested in running thru Knoppix.
> **Herman said:**
> 
EDIT: I went to look for some other Grub thread that I might be able to help with and found your other thread: [Booting from USB]("http://ubuntuforums.org/showthread.php?t=447773&highlight=grub"). :)
You already have a stage2 eltorito if you installed Ubuntu in your usbdisk. Look in [FONT=Bitstream Vera Sans Mono]/usr/lib/grub/i386-pc [/FONT]you should find one there. :)

Good, but a few folkes stated that they could not get the Bootfrom USB stuff working.

---

