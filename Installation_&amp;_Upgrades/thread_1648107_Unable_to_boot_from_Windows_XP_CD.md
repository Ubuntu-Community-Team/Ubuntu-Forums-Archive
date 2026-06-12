---
title: "Unable to boot from Windows XP CD"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by DeathFrag on 2010-12-18
Hi guys,

I was using Windows XP before. I installed Ubuntu some weeks back and removed Windows completely.

Now I want to completely remove Ubuntu and install Windows XP back.
But the Windows XP bootable CD won't boot. I DON'T get a screen saying, "Press any key to boot from CD..."
I've changed my boot sequence under BIOS settings to CD first and then HDD. 
Still every time I restart with the CD, it loads Ubuntu.

I'm frustrated. Please guide me. I would be very grateful.

---

### Post by karthick87 on 2010-12-18
Welcome to ubuntuforums :)

Are you sure that you have changed your first boot device to CDROM in your BIOS??And is that bootable XP disc??

---

### Post by DeathFrag on 2010-12-18
> **karthick87 said:**
> Welcome to ubuntuforums :)

Are you sure that you have changed your first boot device to CDROM in your BIOS??And is that bootable XP disc??
Yes..i've changed the boot sequence to CD first. 
The CD is bootable, I've tested the CD on my room-mates laptop. It is a bootable XP CD.
What to do?

---

### Post by oldfred on 2010-12-18
If it is still booting Ubuntu then it is not booting the CD. IF disk is good then you may need to clean CD lens or check the CD drive is working correctly.

Windows will not normally 'see' Linux partitions. It will want either a blank disk or a NTFS primary partition with the boot flag (active partition in windows).

---

### Post by DeathFrag on 2010-12-18
> **oldfred said:**
> If it is still booting Ubuntu then it is not booting the CD. IF disk is good then you may need to clean CD lens or check the CD drive is working correctly.

Windows will not normally 'see' Linux partitions. It will want either a blank disk or a NTFS primary partition with the boot flag (active partition in windows).

You're right, Windows won't detect Linux partition & that's the reason why the CD didn't boot.

That's why I booted with Ubuntu Live CD and deleted my Linux partition completely. I created a partition with NTFS.

Now when i try to boot with the Win XP CD i get the following error:

Unknown partition
grub rescue>

Please guide.

---

### Post by karthick87 on 2010-12-18
LOL who asked you to remove your LINUX partition??

---

### Post by Pillars of Creation on 2010-12-18
“You're right, Windows won't detect Linux partition & that's the reason why the CD didn't boot.”

The CD boot option is at a level below any OS’s on the hard drive or the master boot record. The Windows XP CD should boot, you do have to hang around and hit the space bar. If it is not booting it indicates one of four things:

1. The BIOS is not set the boot the CD.
2. The CD drive is bad.
3. The CD drive is not reading the disk.
4. The CD media is bad.

It sounds like you’ve eliminated option four. If you been able to get the Ubuntu disk to boot then you eliminated the question as to whether the CD drive is bad. If you got the setting and the BIOS set correctly within the conclusion would be that the CD drive was not like that particular disc. What do you happen to have another Windows XP disk lying around? If you happen to have an iMac handy I compose the procedure how to copy the Windows OS install disk.

---

### Post by DeathFrag on 2010-12-18
You're right. It beats me too.

I've tested my CD on my room-mates computer. It works on his machine.(He has Windows 7)
I ran across some thread that the partition should be NTFS or unallocated with 'boot' flag set to it. I did that with my Ubuntu Live CD.

But I still get the following error:

error: unknown filesystem
grub rescue>

Please help

---

### Post by Pillars of Creation on 2010-12-18
Another thing you might try is to make the hard drive manufacturers diagnostic disk and boot it. See if you can do a full or low-level format on the hard drive and then try booting the Windows XP OS install disk.

Acronis True Image WD Edition

[http://support.wdc.com/product/download.asp?groupid=606&sid=30&lang=en](http://support.wdc.com/product/download.asp?groupid=606&sid=30&lang=en)

Seagate SeaTools for DOS 

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatooldreg&vgnextoid=480bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatooldreg&vgnextoid=480bd20cacdec010VgnVCM100000dd04090aRCRD)

Samsung ES Tool (The Drive Diagnostic Utility)
[URL="http://www.samsung.com/global/business/hdd/support/downloads/support_in_es.html"]
http://www.samsung.com/global/business/hdd/support/downloads/support_in_es.html[/URL]

---

### Post by Pillars of Creation on 2010-12-18
If you don’t know the manufacturer your hard drive you can use the audits soccer program listed below for free dirt

Berlarc PC audit system advisor

Belarc Advisor 8.1p

[http://download.cnet.com/Belarc-Advisor/3000-2094_4-10007277.html?tag=mncol;1](http://download.cnet.com/Belarc-Advisor/3000-2094_4-10007277.html?tag=mncol;1)

---

### Post by oldfred on 2010-12-18
You are still booting hard drive. With Ubuntu partition missing the grub install to the MBR has no place to jump to. It would not really matter if you had a windows boot loader in the MBR as it would have no place to jump to.

You still need to resolve why CD is not booting. Does your system boot USB flash drives. You could then use your friends system to create a USB flash version of the XP installer.

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
Windows In Your Pocket USB using BartPE
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)

---

### Post by Pillars of Creation on 2010-12-18
“I ran across some thread that the partition should be NTFS or unallocated with 'boot' flag set to it. I did that with my Ubuntu Live CD.”

If you boot from the Ubuntu disk again try making the drive just empty and unformatted. So just delete all the partitions. The Windows XP install disc can handle making its own partitions just fine.

---

### Post by DeathFrag on 2010-12-18
> **oldfred said:**
> You are still booting hard drive. With Ubuntu partition missing the grub install to the MBR has no place to jump to. It would not really matter if you had a windows boot loader in the MBR as it would have no place to jump to.

You still need to resolve why CD is not booting. Does your system boot USB flash drives. You could then use your friends system to create a USB flash version of the XP installer.

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
Windows In Your Pocket USB using BartPE
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)

I've a Windows XP bootable CD that works on my room-mates laptop.
Means: CD is working.

I've run my Ubuntu Live CD with CD ROM as the first boot device.
Means: Boot sequence is also working fine.

Which means my Windows CD should boot.

I will have to try out the USB thing you shared. But I don't have  USB as of now. Really frustrating.

But tell me one thing. Can i somehow delete the GRUB loader. Why is it still trying to locate my linux partition through GRUB. I've deleted everything on the disc, erased all. Will removing Grub help?

Are there any commands to be punched from **grub rescue>**

---

### Post by DeathFrag on 2010-12-18
I got this from Microsoft Support Forum

To remove Linux from your computer and install Windows XP, follow these steps:
Remove the native, swap, and boot partitions used by Linux:
Start your computer with the Linux Setup floppy disk, type fdisk at the command prompt, and then press ENTER.

NOTE: For help with using the Fdisk tool, type m at the command prompt, and then press ENTER.
Type p at the command prompt, and then press ENTER to display partition information. The first item listed is hard disk 1, partition 1 information, and the second item listed is hard disk 1, partition 2 information.
Type d at the command prompt, and then press ENTER. You are then prompted for the partition number that you want to delete. Type 1, and then press ENTER to delete partition number 1. Repeat this step until all the partitions have been deleted.
Type w, and then press ENTER to write this information to the partition table. Some error messages may be generated (because information is written to the partition table), but they should not be significant at this point because the next step is to restart the computer and then install the new operating system.
Type q at the command prompt, and then press ENTER to quit the Fdisk tool.
Insert either a bootable floppy disk or the bootable Windows XP CD-ROM, and then press CTRL+ALT+DELETE to restart your computer.

How can i achieve the same from Ubuntu console?? Please help.

Someone also suggested that I remove grub.
he said:

# dd if=/dev/null of=/dev/sdX bs=512 count=1

Just remove MBR, without the partition table (see comment below):
# dd if=/dev/null of=/dev/sdX bs=446 count=1

Replace /dev/hdX with your actual device name such as /dev/hda. Use fdisk -l command to find out device name:
# fdisk -l

Shall I try it out??

---

### Post by Pillars of Creation on 2010-12-18
I agree with oldfred that the issue here is that the Windows XP disk should boot.

“But tell me one thing. Can i somehow delete the GRUB loader. Why is it still trying to locate my linux partition through GRUB. I've deleted everything on the disc, erased all. Will removing Grub help?”

Yes you can delete the grub2 loader by fully formatting or low-level formatting the hard drive. The MBR is at the front of the hard drive and is not deleted when you simply add and remove partitions. So you have not erased everything on the disk.

The Boot Process

[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP)


Master Boot Record

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Pillars of Creation on 2010-12-18
“The MBR is not located in a partition, it is located at a main boot record area in front of (with a lower LBA sector number than) the first partition.”

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by DeathFrag on 2010-12-18
> **Pillars of Creation said:**
> “The MBR is not located in a partition, it is located at a main boot record area in front of (with a lower LBA sector number than) the first partition.”

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Thanks for the support guys...I really appreciate it. Although my problem is not yet resolved.

After i ran the GRUB uninstall commands, my system now just keeps on restarting itself. (if the WinXP CD is inserted) And if Linux is inserted, it boots from Linux CD. Strange. 

Let's see. Let me get another Win XP CD from someone & try. I'll get back to you.

---

### Post by Pillars of Creation on 2010-12-18
Another thing you might try is to download the ISO file and make a CD boot disk for Ultimate Boot 5.0.3. It’s a self booting CD that does multiple computer maintenance things including partitioning formatting and checking RAM. It’s free. I haven’t had  the time to explore all that it offers but amongst other things it does have a built-in FDISK which should well be capable of blowing away the MBR.

Go to the link below and next to the down arrow click on “softpedia secure download (US)


[http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html](http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html)

If you don’t have a USB stick you can buy one at OfficeMax or whatever and take it back within 30 days. Just cut the plastic packaging with a razor blade cardboard cutter on two sides very carefully. If your good they will never know you even opened it.

---

### Post by Pillars of Creation on 2010-12-18
[http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)

---

### Post by DeathFrag on 2010-12-19
> **Pillars of Creation said:**
> Another thing you might try is to download the ISO file and make a CD boot disk for Ultimate Boot 5.0.3. It’s a self booting CD that does multiple computer maintenance things including partitioning formatting and checking RAM. It’s free. I haven’t had  the time to explore all that it offers but amongst other things it does have a built-in FDISK which should well be capable of blowing away the MBR.

Go to the link below and next to the down arrow click on “softpedia secure download (US)


[http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html](http://www.softpedia.com/progDownload/Ultimate-Boot-CD-Download-5992.html)

If you don’t have a USB stick you can buy one at OfficeMax or whatever and take it back within 30 days. Just cut the plastic packaging with a razor blade cardboard cutter on two sides very carefully. If your good they will never know you even opened it.

I've downloaded the Ultimate Boot CD shared by you. I burned it in a CD and tried to boot from it. But it doesn't boot.

I've tested the CD on my friend's laptop where it boots perfectly.

I've installed ubuntu on my laptop again.
After installing I used Ubuntu Live CD and used GParted to resize the primary partition and created a new NTFS partition on it.

So I've Linux installed on my laptop. With a 9GB NTFS primary partition 
too. 
The Windows XP CD still won't boot. Even the Universal Boot CD doesn't boot. But the Ubuntu Live CD boots perfectly. What's going on?

I believe there's something fishy with the GRUB loader or the MBR.

Why does my system doesn't boot from any bootable CD except Ubuntu CD??

Please help me. I'm trying since 2 days.

---

### Post by oldfred on 2010-12-19
I have seen CD drives that are borderline. Or they work with one disk but not another. Often they only work on one's they write. May be an alignment issue. This used to be a big problem with floppys but not so much with CDs.

---

### Post by DeathFrag on 2010-12-20
> **oldfred said:**
> I have seen CD drives that are borderline. Or they work with one disk but not another. Often they only work on one's they write. May be an alignment issue. This used to be a big problem with floppys but not so much with CDs.

I don't think that's the problem. 
To my surprise, I tried booting from my Windows 7 Ultimate Edition CD and it worked!! 

Although it's a very bad solution, I did the following:
1. I installed Windows 7 on my laptop(which has just 512 MB RAM).
2. Once installed, I booted from my Windows XP CD.
3. Now it boots perfectly.
4. I deleted my partition and re-formated it again.
5. Installed Windows XP successfully.
6. My weekend is spoiled. Duh!! ;)

Thanks to everyone of you for the great help.

---

### Post by oldfred on 2010-12-20
I know windows will not install unless it sees a empty drive or a NTFS partition with a boot flag. But not booting unless you have a good partition is very strange.

Glad you managed to work it out.

---

