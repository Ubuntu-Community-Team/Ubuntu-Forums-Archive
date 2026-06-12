---
title: "USB drive boot problem"
date: 2016-04-02
forum: Installation &amp; Upgrades
---

### Post by glaman5266 on 2016-04-02
Hello. I'm not sure if this is the place to post this (new here and to Linux), but here goes. I'm attempting to create a bootable/live USB with Ubuntu on it. I'm new to Linux but I have successfully done this with Linux Mint on a 4 gig flash drive. I'm aware of how to change the BIOS settings to boot from the USB first and how to create the live disk with Windows (currently using Windows 7). I'm liking Mint so far, but I want to try Ubuntu. So far I have created a live USB with my 500gb external drive after using a 3rd party formatter to format in FAT32 and then Pendrive to create it.

When I boot the compy with the drive attached it will not boot. I have double-checked in the BIOS settings that it should boot from the USB first and I'm pretty sure the live disk was created properly (I can see all the files and whatnot in Windows). Even trying to manually boot from the USB in the boot options immediately on startup does not yield results. All I get is a blank screen with a blinking underscore in the top-left corner.

What do I need to do to get it to boot into Ubuntu? Is it because I'm using an external hard drive instead of a flash drive? Are there boot settings I need to tweak yet? I read something about video drivers somewhere... I don't know what to do next.
Any help would be appreciated. :)

EDIT: I'm not looking to install it at the moment. I simply want to try it out. The version I'm trying to use is 14.04.4.

---

### Post by Bucky Ball on 2016-04-02
*Thread moved to **Installation and Upgrades**.*

Welcome. If you are trying to boot from the USB then whether you have external drives attached or not makes no difference. They don't come in to it. You are attempting to boot Ubuntu from the live USB and run it from that if I understand you correctly.

Have you [checked the ISO for defects]("https://help.ubuntu.com/community/HowToMD5SUM")? Have you attempted to boot the USB on another machine?

---

### Post by glaman5266 on 2016-04-02
Yes, I'm attempting to run Ubuntu from the live USB (my external hard drive). I tried running it on another machine and got the same result. I followed the instructions in the link you posted, using winMD5Sum, and the hash checks out.

---

### Post by grahammechanical on 2016-04-02
There is the source of my confusion.

When some people say "live USB" they mean a USB memory stick. But you mean a 500 GB USB external drive. Next question, did you install Ubuntu to the 500 GB external USB drive or just "burn" the ISO image to it?

If you installed Ubuntu to the external USB drive then the question becomes, where did the Grub boot loader go? The default location for the Linux boot loader is the first hard drive (sda). It really should go on the external USB drive. Which may be sdb.

If we go into the BIOS/UEFI and select the external USB drive as the drive to boot from and it does not have a boot loader we will get a result similar to the one you are seeing. By the way, are you setting the boot option from the Boot>Hard drives section of the BIOS? And not from the USB section. The BIOS/UEFI will see a USB memory stick & an external USB drive as hard drives if they have an OS on them.

Regards.

---

### Post by Bucky Ball on 2016-04-02
Yes, slightly confused. If you simply dropped the ISO on a partition in the external drive, or USB for that matter, that is not going to work.

You need to create bootable install media, either DVD or USB, and boot from that, THEN install to the external USB drive.

You might find some [clues here]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop").

---

### Post by yancek on 2016-04-02
If you used pendrivelinux to try to create a bootable usb, where were you planning to install Ubuntu?  You can't install it to the external 500GB drive from which you are booting.   Much simpler to use a flash drive as you did before.

> Yes, slightly confused. If you simply dropped the ISO on a partition in  the external drive, or USB for that matter, that is not going to work.

 
In this particular instance it would not work because all the OP has to work with is a windows bootloader.  If Grub2 was installed on a partition on one of the drives it would be a simple matter to create a proper loopback menuentry to boot it.

---

### Post by C.S.Cameron on 2016-04-02
Try using UNetbootin to make the external drive, or do a Full install.
If you unplug your internal drive first, you can install to USB same as to internal drive.

---

### Post by glaman5266 on 2016-04-02
> **Bucky Ball said:**
> Yes, slightly confused. If you simply dropped the ISO on a partition in the external drive, or USB for that matter, that is not going to work.

You need to create bootable install media, either DVD or USB, and boot from that, THEN install to the external USB drive.

You might find some [clues here]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop").
So what you're saying is I should use a flash drive as opposed to using my external hard drive to boot from? The external drive can't be used for bootable install media?
> **yancek said:**
> If you used pendrivelinux to try to create a bootable usb, where were you planning to install Ubuntu?  You can't install it to the external 500GB drive from which you are booting.   Much simpler to use a flash drive as you did before.
 
In this particular instance it would not work because all the OP has to work with is a windows bootloader.  If Grub2 was installed on a partition on one of the drives it would be a simple matter to create a proper loopback menuentry to boot it.
Well, I wasn't planning on installing it (yet). I wanted to try it out first. I was thinking I could use my external drive as a live USB. What you guys are saying makes sense now. Sorry, I'm still new to some of this. :redface: I will acquire another flash drive and give that a try first. I'll install it on the external hard drive later.

Thanks a lot for the replies guys. I really appreciate it. I'll post again if I'm still having issues booting it.

---

### Post by yancek on 2016-04-02
> So what you're saying is I should use a flash drive as opposed to using my external hard drive to boot from?

Yes, either that or a DVD.

> The external drive can't be used for bootable install media?

Yes, it can.  You could just copy the iso to a partition on the external drive or put the iso on a partition of your internal drive where you have Mint or you could put the iso on the windows partition and boot it from Grub2 you have with Mint.  If you still have Mint and use the Grub bootloader from Mint?  If this is the case, it's not all that complicated if you are pretty familiar with Grub.  Getting a blinking cursor is usually a sign that the bootloader wasn't created properly.  I've never used pendrivelinux so don't know what it uses.

---

### Post by Bucky Ball on 2016-04-02
As a new user I'd go the easiest route: DVD or USB. By all means, go the ISO from a hard drive if you're feeling like a learning curve and getting down and dirty with grub. Otherwise, no.

But as yancek mentions, it is do-able, just not often done. You could use Virtualbox if you wanted to try it out as a virtual machine directly from the ISO, but that is another learning curve if you're not familiar. ;)

---

### Post by glaman5266 on 2016-04-02
> **yancek said:**
> Yes, it can.  You could just copy the iso to a partition on the external drive or put the iso on a partition of your internal drive where you have Mint or you could put the iso on the windows partition and boot it from Grub2 you have with Mint.  If you still have Mint and use the Grub bootloader from Mint?  If this is the case, it's not all that complicated if you are pretty familiar with Grub.  Getting a blinking cursor is usually a sign that the bootloader wasn't created properly.  I've never used pendrivelinux so don't know what it uses.
I actually run Mint from a flash drive. I just didn't want to wipe that as that was the only flash drive I had and I want to keep Mint for another compy. I acquired another flash drive today though.
I am not at all familiar with Grub. I've read a little about it, but that's it.
> **Bucky Ball said:**
> As a new user I'd go the easiest route: DVD or USB. By all means, go the ISO from a hard drive if you're feeling like a learning curve and getting down and dirty with grub. Otherwise, no.

But as yancek mentions, it is do-able, just not often done. You could use Virtualbox if you wanted to try it out as a virtual machine directly from the ISO, but that is another learning curve if you're not familiar. ;)
I see. I am not familiar with Virtualbox. I'll use the new flash drive I picked up. I just thought I could do it with an external drive the same way you could with a flash drive.So much to learn! Thanks again. You guys have been helpful.

---

### Post by sudodus on 2016-04-03
It ***is*** possible to treat a USB hard disk drive like it were a USB pendrive. You can even use an internal drive or eSATA drive to boot a live session.

But there might be problems:

Some tools to create USB boot drives will overwrite the contents of the USB drive, so if you have a lot of personal files in the USB hard disk drive, they might be overwritten (and destroyed). If there is nothing, that you must keep in that drive, there is no problem.

Some tools to create USB boot drives will not overwrite the contents of the USB drive, but might not work correctly unless you remove all the files.

And some tools to create USB boot drives might work correctly even if you keep old files.

***Backup:*** If you are not sure about the tool you are using, you should copy all important files from the USB hard disk drive to a safer place before using it this way.

-o-

If you want to use a USB hard disk drive for

- *both* storage and transfer of files between linux and Windows
- *and* booting a live system,

you can create a persistent live drive with [mkusb](https://help.ubuntu.com/community/mkusb/persistent). It will remove the partition table , create a new one, in other words overwrite the contents of the USB drive, but afterwards you can use the drive for storage and transfer of files in the 'usbdata' partition and for persistence of installed programs and tweaks of your linux system (as well as storage of files) in the 'casper-rw' partition.

You can also make a real installed system in the USB hard disk drive. See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by glaman5266 on 2016-04-07
OK, I keep getting this error when I attempt to boot from the live USB flash drive I created (selecting "Try Ubuntu without installing" on startup):
(initramfs) Unable to find a medium containing a live file system

Searching through Google tells me that I could try changing from ACHI to IDE. I do not have an IDE option in BIOS, so I'm unsure on that one. Found that info here: [http://askubuntu.com/questions/15425/error-when-installing-unable-to-find-a-medium-containing-a-live-file-system](http://askubuntu.com/questions/15425/error-when-installing-unable-to-find-a-medium-containing-a-live-file-system)
That page also mentions enabling IOMMU for gigabit boards. I do not see that setting in BIOS either, but I'm actually not sure if I have a gigabit board or not (compy is secondhand). I'll look into that.

Are there any other things I could try?

---

### Post by sudodus on 2016-04-07
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

I think you can run the following command in Linux Mint to find out (at least most of the data)

```
sudo lshw -sanitize | less
```

If not available, you can install it temporarily with

```
sudo apt-get install lshw
```

- What brand name and model is the USB pendrive?

- Which tool did you use to create the USB boot drive?

- Did you create it from Windows or from Linux Mint?

Knowing about these things makes it easier to give the help you need. Otherwise we can only guess.

I think you should keep the settings of the computer, that can boot Linux Mint. I am rather sure that the same settings work also for Ubuntu. Please set the computer, so that it can boot Mint again, and after that try the pendrive with Ubuntu again.

-o-

It Ubuntu still does not work, I suggest that you try another tool to install it into the pendrive.

Boot into Linux Mint and install [mkusb](https://help.ubuntu.com/community/mkusb).

```
sudo add-apt-repository universe  # and press Enter (it may be active already)

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

and then run mkusb from the menu. See the [quick start manual](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-1.pdf) if you need more detailed help.

---

### Post by glaman5266 on 2016-04-07
> **sudodus said:**
> Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- What brand name and model is the USB pendrive?

- Which tool did you use to create the USB boot drive?

- Did you create it from Windows or from Linux Mint?

Knowing about these things makes it easier to give the help you need. Otherwise we can only guess.

I think you should keep the settings of the computer, that can boot Linux Mint. I am rather sure that the same settings work also for Ubuntu. Please set the computer, so that it can boot Mint again, and after that try the pendrive with Ubuntu again.

-o-

It Ubuntu still does not work, I suggest that you try another tool to install it into the pendrive.

Boot into Linux Mint and install [mkusb]("https://help.ubuntu.com/community/mkusb").
Oops. Meant to put that info in my previous post.

Dell Inspiron 1545 laptop running 64-bit Windows 7
2.10Ghz T4300 Pentium Dual Core
3.00GB RAM
Mobile Intel(R) 4 Series Express Chipset
Dell Wireless 1397 WLAN mini-card (currently disabled- I hardwire this compy)

Flash drive: Sandisk Ultra USB 3.0 (2.0 compatible) 32GB
I used Pendrive's universal USB creator in Windows 7 to create it.

Mint has always worked on this computer. I haven't changed any computer settings since I started playing with Mint a few weeks ago. I will remake the live USB in Mint. I feel kind of dumb not thinking about trying that... :redface: If that doesn't work I'll try mkusb.

---

### Post by sudodus on 2016-04-07
I think your computer might work better with an Ubuntu flavour with a lighter desktop environment than standard Ubuntu: Lubuntu with the ultra light LXDE, Xubuntu with the medium light XFCE or Ubuntu MATE with the medium light MATE.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Try with the version 14.04.1 LTS or the newer but short-lived 15.10. At the end of this month, version 16.04 LTS will be released. The versions 14.04.1 LTS and 16.04 LTS have long-time support, 5 years for standard Ubuntu and I think 3 years for the flavours Lubuntu and Xubuntu (from the release dates April 2014 and April 2016).

---

### Post by Bucky Ball on 2016-04-07
I agree with sudodus, but I say be adventurous! Go [Xubuntu-core 16.04 LTS]("https://unit193.net/xubuntu/core/"). Only another two weeks til it's released anyway and all you need to do is keep updating/upgrading it and you'll get there. It is a very stripped back Xubuntu (it says 'just the best bits' on the packet) and you add the rest via a terminal or Synaptic Package Manager. Will fly on that machine. :D

(PS: Xubuntu LTS are supported for three, rather than five, years.)

---

### Post by glaman5266 on 2016-04-13
> **sudodus said:**
> It Ubuntu still does not work, I suggest that you try another tool to install it into the pendrive.

Boot into Linux Mint and install [mkusb]("https://help.ubuntu.com/community/mkusb").

and then run mkusb from the menu. See the [quick start manual]("https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-1.pdf") if you need more detailed help.
OK, I installed and ran mkusb in Mint to put Lubuntu 14.04.4 LTS onto the 32Gb flash drive. I get the same error: (initramfs) Unable to find a medium containing a live file system
I tried both the 32-bit and 64-bit ISO files and double-checked the MD5SUMs (they both checked out). Neither worked.

Just to try it, I attempted to create a live USB with Mint on it (on the same 32Gb flash drive). I used the same computer, program, options, etc. that I used to create the Mint live USB I currently have (which works on every computer in the house). I got the same error when trying to boot from it.

At this point I'm wondering if it is the flash drive itself. Thoughts?

EDIT: Do I need to set up a partition on the flash drive that is less than 4Gb? Also, if it matters, when I ran mkusb I set up the live USB as a live-only USB (no persistence).

---

### Post by sudodus on 2016-04-13
Normally I would not think the pendrive is bad, because the computer *boots* from the pendrive. Otherwise you would not get the output:

'(initramfs) Unable to find a medium containing a live file system'

But you have tested a lot of alternatives. It seems something is wrong with the pendrive, for example that some memory cells are too slow - a long delay during reading maybe makes the system fail to 'find a medium containing a live file system'.

Now that you know mkusb, you could try a method, that sometimes helps remove causes of slow read/write operations in pendrives: *wipe the whole device*.

You find it at the [wipe menu of mkusb](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by Bucky Ball on 2016-04-13
Before I create a USB installer, I boot into gparted, wipe all partitions, create new partition table and then create a FAT32 partition that uses all available space (the whole USB).

I'm guessing you can do something similar in mkusb (never tried) but it is important that the USB is completely wiped before proceeding. If you're creating an installer, it doesn't work, so you're simply creating it again without wiping the USB completely and creating a new FAT32 partition that uses the whole USB, please do so, using whatever method, and see if that makes a difference.

---

### Post by sudodus on 2016-04-13
Bucky Ball,

Your method works with installers that use the existing FAT32 file system. But mkusb (and dd, Disks and the new version 0.3.2 of the Ubuntu Startup Disk Creator) *clone* the iso file. In this case the partition table and file system are overwritten anyway. It makes no difference to treat it with gparted before the cloning.

But still, if there are certain problems, wiping the whole device (overwriting with zeros) will 'refresh' an ageing pendrive :-)

---

### Post by glaman5266 on 2016-04-13
> **sudodus said:**
> Now that you know mkusb, you could try a method, that sometimes helps remove causes of slow read/write operations in pendrives: *wipe the whole device*.

You find it at the [wipe menu of mkusb]("https://help.ubuntu.com/community/mkusb/wipe")

> **Bucky Ball said:**
> Before I create a USB installer, I boot into gparted, wipe all partitions, create new partition table and then create a FAT32 partition that uses all available space (the whole USB).
OK, I wiped the flash drive via mkusb and created a new partition table and FAT32 partition. With the 32-bit ISO I get the same error I've always been getting: (initramfs) Unable to find a medium containing a live file system

I repeated the process and used the 64-bit ISO. The error I get then is simply: (initramfs)
I should note that above the error is a list of read errors ("device descriptor read/64, error -71" and several similar) and an error that states the USB cannot be enumerated. I've seen this every time I've tried to boot ubuntu/lubuntu.

Doing a Google search tells me that I'm not the only one having issues with this particular flash drive (Sandisk Ultra) booting Linux. I noticed the list of flash drives that are good for booting in your thread here:[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
My Mint USB is a PNY Attache and I've had no issues. Perhaps I'll pick another one up.

---

### Post by sudodus on 2016-04-13
Yes, I think we can conclude, that there are problems to boot with this particular Sandisk Ultra pendrive. It might still be good for storing data, if you restore the file system in the mkusb/wipe meny. Select the standard option,

"Standard: create MSDOS partition table with FAT32 partition"

-o-

I have only a small Sandisk Ultra, 8 GB. There are no particular problems with it, but it is rather slow. I have good experiences with Sandisk Extreme 16 GB and 32 GB. They are USB 3, have fast flash memory hardware, and are good booters too. After using them a lot (maybe after a year), they tend to get slow, and I refresh them by wiping the whole device.

---

### Post by glaman5266 on 2016-04-21
I know this thread's a bit old now, but I acquired a better flash drive and am now running Ubuntu 14.04. Thank you guys very much for the assistance. I learned quite a bit from your posts. Thanks again for teaching me. You guys are great. :)

---

### Post by sudodus on 2016-04-21
Congratulations to a working Ubuntu system :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

