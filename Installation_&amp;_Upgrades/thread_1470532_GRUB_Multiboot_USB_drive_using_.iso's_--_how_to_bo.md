---
title: "GRUB: Multiboot USB drive using .iso's -- how to boot into Windows ISO?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by IConrad01 on 2010-05-02
Hello -- and thank you for your attention.

I am attempting to create a multiboot USB drive.  I have two Ubuntu versions (32-bit and 64-bit Lucid/10.04) running just fine.

Where I am stumbling, however, is determining how to get GRUB to boot up the .iso of Windows 7.

The purpose of this drive is to allow me to attempt to do repairs on installs for my friends and family, without having to lug around multiple objects (in lieu of a pen-drive attached to my keychain) -- so simply burning the .ISO onto a CD/DVD is not an option [[The entire point is to do away with physical disks in lieu of a single flash-drive.]]

Am I going to simply have to give up and get a second pen-drive for my Windows install?  :-(

---

### Post by Jeff Anthony on 2010-05-02
Are you asking how to put the iso on the USB and then boot from it, or how to install from iso on to the USB drive?

I appears you're trying to boot from USB so that grub shows all your options to boot to, one being Windows. 

To be honest I'm kinda scared to touch that one as it has to do with non-open-source software and I've been booted from forums before over questions such as this. I will say that if it has any similarities to creating a multiboot physical machine I would start with the Windows one first and then install your Ubuntu using the wubi from Live disc.

---

### Post by IConrad01 on 2010-05-02
The goal here is to place all three separate .ISO images onto my USB drive, and through GRUB load up whichever of the three I prefer at time of boot.

I.e.; instead of having three separate LiveCD's (well, boot-CD), one single multiboot USB drive, which contains the .ISO files for each of the three boot-CDs.

> I will say that if it has any similarities to creating a multiboot physical machine I would start with the Windows one first and then install your Ubuntu using the wubi from Live disc. That's got absolutely nothing to do with my question.  At no time am I creating actual installs of the various OS's.  My major difficulty is in the fact that I cannot determine what the menuentry field for the Windows .iso should look like, as compared to this:

```
menuentry "Ubuntu Live 10.04 32bit" {
 loopback loop /boot/iso/ubuntu-10.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}
```

---

### Post by CPPCrispy on 2010-05-03
I have messed around with this before and the wall I kept coming up to is the Windows boot loader. When you put in a DVD, the BIOS reads the DVD's mbr and then boots the Windows boot loader.

When Grub boots a Linux ISO, Grub opens the ISO and then boots the Kernel directly. With Windows, Grub reads the Windows partition mbr and then passes control to ntldr (XP) or bootmgr (Vista, 7). This is where the problem is. Grub can not read the ISO mbr and thus can not load the Windows boot loader.

There are some ways to get around this by using syslinux (memdisk and isolinux) but then you run into problems with ram constraints and real mode OS and boot loaders. I also messed around with making an image of the mbr and having Grub with syslinux boot that to boot the OS files but that did not work.

One thought that I had, but never did, was to partition the flash drive. Make 4 primary partitions, put Grub and the Linux ISO on one partition and set it to active, and put the Windows installation files on the other partitions. (Make a Windows-Linux dual boot using Grub but with Installation files) This would get around most, if not all, of the problems by making a multi boot flash drive. The only limitation with this would be that you would only be able to boot 3 Windows installation. Which if you were doing XP, VISTA, and 7, would not be a problem. You could also take this a step feather and create a Windows multi boot installation DVD and then putting that on to the partition.

I spent a few months on and off to get this to work but i did not get anywhere. Good luck.

---

### Post by IConrad01 on 2010-05-03
> One thought that I had, but never did, was to partition the flash drive. Make 4 primary partitions, put Grub and the Linux ISO on one partition and set it to active, and put the Windows installation files on the other partitions. (Make a Windows-Linux dual boot using Grub but with Installation files) This would get around most, if not all, of the problems by making a multi boot flash drive. The only limitation with this would be that you would only be able to boot 3 Windows installation. Which if you were doing XP, VISTA, and 7, would not be a problem.  Now *that* is a more progressive idea.  I ran into it elsewhere in my googling but couldn't make heads or tails of what I was reading. (Not exactly what you'd call an "expert" on GRUB2).

So here's the thing; I have no problem repartitioning the flash drive -- done it plenty of times already.  So here's the real question:  how would I go about constructing the GRUB "menuentry" for such a beast?  Just tell it to chainload into the partition?  How would I get it to always designate the right partition?

---

### Post by oldfred on 2010-05-03
I do not ever plan on reinstalling windows, this is mostly XP.

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
non-commercial all versions of windows
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

### Post by CPPCrispy on 2010-05-03
> **IConrad01 said:**
> So here's the thing; I have no problem repartitioning the flash drive -- done it plenty of times already.  So here's the real question:  how would I go about constructing the GRUB "menuentry" for such a beast?  Just tell it to chainload into the partition?  How would I get it to always designate the right partition?

You would chainload to Windows, just like you do on a normal dual boot config. The only difference would be that when you boot, you will be in the Windows installation process, not a usable OS. For the Linux ISO files, you would use the code you posted on a earlier post. 

The partitions are labeled independently of any other devices (other hdd, etc.). The only thing that you would have to worry about is Grub using the flash drive by default but I think that it does this by default when you boot from the device. If Grub was on another device, then you would have to map the drive so that Grub can boot from it.

---

### Post by IConrad01 on 2010-05-03
> **oldfred said:**
> I do not ever plan on reinstalling windows, this is mostly XP.

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
non-commercial all versions of windows
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/) These are only good for single-boot USB flash-drives, however...  they don't allow for creating a multiboot flash-drive.

[quote="CPPCrispy"]You would chainload to Windows, just like you do on a normal dual boot config. The only difference would be that when you boot, you will be in the Windows installation process, not a usable OS. For the Linux ISO files, you would use the code you posted on a earlier post.[/quote] Yes, but **how**?  I have to do this manually and I can't for the life of me figure out what to make the entry look like.  You can't do this with update-grub, because it requires you to be able to chroot and that requires a working install to chroot to.  So I need a manually-configured entry.  The one I gave above works for an Ubuntu 10.04 32-bit .iso.  If I were to extract all the files from a Windows .iso and dump them into a partition, how would I go about chainloading that partition -- and how is it different from merely chainloading from a loopback-mounted *.iso (Which doesn't work)?

EDIT:  An alternative idea springs to mind, which might work with the previous suggestions given... perhaps one could boot up into a *.iso image (well, with the right configuration/scripting) from an already running LiveCD environment?  I.e.; keep the Windows *.iso's on the pen-drive, but boot from the drive into Linux and then from the running environment trigger a boot from the *.iso (which may or may not have been dumped onto the HDD of the host computer?)

All in all I might just be better off just running with Ubuntu and PCRegedit.iso's for my target goal, if this is too difficult.  Still -- a viable solution would be nice...

---

### Post by chinoto on 2010-06-06
I made a thread, then found this one while I was looking for information. Heres my post from that thread. (Need to find a way to remove that thread)
> I want to put ISOs on the second partition of my thumbdrive and be able  to boot them. Is there any way to have the ISO load as if it were  actually in the CD drive, instead of loading the kernel and initrd? I  tried Grub2, but when Ubuntu and TRK booted they complained about not  having their CD. UNetbootin extracts the ISO, so I don't want to do  that. If isolinux would work, could someone direct me to some  instructions on installing it to the usb and configuring it?

Useful Links:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)  (Tried it, complained about not having CD when partially booted)
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)  (Trying to stay away from Windows, but I'm getting a bit too frustrated  to be picky)This is basically a bump to get things going again.[]("http://www.mepis.org/docs/en/index.php/Create_a_multiboot_CD_%28or_USB_flash_drive%29")

---

### Post by oldfred on 2010-06-06
If you have a large 8 or 16GB flash drive you can install the full Ubuntu just like on a hard drive. You can then add the iso to a iso directory and loop mount them.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I use parts of panticz since his is a bash script to automate the entire thing. I did not want his exact setup but ran some of the commands. I also used the ubuntu-ky site.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb](http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb)
See post #11 for my grub.cfg to boot iso files
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

### Post by rmaxwell on 2010-06-08
Try the information at: [http://flyakite.msfn.org/](http://flyakite.msfn.org/)

Basically you'll need to extract the windows setup from the *.iso file.
And you need to change specific things.  (Mostly so windows won't be looking at the usb drive for the setup files.)

In the end, its mostly because it looks like when linux does loopback to load the virtual cd-rom (*.iso image).  Windows doesn't know where the install files are located, as its trying to access the files from the physical drives?  Atleast from my understanding.
I'm probably wrong.  But you should be able to chain load the windows setup.

Specifically, check out the ":: Windows Longhorn 4051 ::" instructions.
It should be basically the same method for Vista & 7.


As for the linux part, I'm a little confused.
Here's my understanding so far.

loopback loop /boot/iso/ubuntu-10.04-desktop-i386.iso
loads iso as "virtual disc"?

linux (loop)/casper/vmlinuz
I think this sets the directory to load the disc to?

boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso
Not certain about this part?

noeject noprompt --
Don't eject/unmount the disc while loaded, and don't prompt for any errors/verifications?

initrd (loop)/casper/initrd.lz
Chain loads the iso boot file?
(Although I'm wanting it to chain isolinux.bin as the bootloader.. for Fedora?)

If you could point me in the correct direction here, I would be very appreciative.
Secondly, as most distros are hardcoded with linuxrc paths (for the setup files), does the loopback method get around this issue?  This is the current problem I am having.
(If I could find the miniroot.gz or linuxrc files I wouldn't have a problem.)

Thanks.

~~rmaxwell

---

### Post by chinoto on 2010-06-09
My understanding of the menu entry (which is likely to be incorrect in some points):
```
#This is from one of IConrad01's posts

menuentry "Ubuntu Live 10.04 32bit" { #Creates an entry in the grub menu that executes the code below
 loopback loop /boot/iso/ubuntu-10.04-desktop-i386.iso #Creates a way to access the ISO's files similar to mount (or is it mounting?)
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- #Tells where the kernel is (in some cases, _which_ kernel to use), what booting method to use, tells the kernel (not grub) where the iso is, and some extra options
 initrd (loop)/casper/initrd.lz #initial ramdisk is to speed up boot by placing a partially booted system into memory (something like that)
}
```

---

### Post by vaikz on 2010-07-06
:DGuys,
 
if you are interested in booting iso from your UFD, I think the best place to go is [http://www.boot-land.net/](http://www.boot-land.net/). The you can learn a lot.
 
For specific iso booting using grub4dos, you can go directly here: [http://www.boot-land.net/forums/?showforum=66](http://www.boot-land.net/forums/?showforum=66) and a number of successfull iso's to be booted is here: [http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944).
 
Hope this can help everybody who are interested in multibooting ISO's in UFD. 
 
:popcorn:

---

### Post by mk67 on 2010-09-02
I've got the same problem you have and turn around it during more than 2 weeks.
But my issues where a bit different than yours, my goals was to boot alternative Win installer like Win Trust (and don't tell me again it's illegal!!! It's not... not really).

Finally boot a proper Win Installer CD is not really excessively hard, for that Grub4dos is your friend and there's many googled topics about it, alternative installer is a different matter. Install CD boot, but win installer seems to by confuse when ther's time to find the hdd and then "patatra",blue screen etc ...

I've finally turn around the problem by virtutalizing the install.

For this I use a 8Go bootable pendrive partitioned in 3 parts (1* 3Go fat, 2* 4Go ext4,3* 1Go ext3) where I've installed Grub4dos. Because I wish to use many repair tools and test many OS I first create fat32 part with Grub4dos and all Iso/img on it. On the ext4, I've installed Ubuntu Netbook because is very useful to managed tools and other (changed menu order,entry,etc ...), and installed VirtualBox. Third and last ext3 part is for img or iso that have some issues to be boot directly with grub (systemrescuecd,for exemple,or moblin).

Next, I've just virtualize the install of Win. 
It work perfectly if you don't omit to copy/past and run MergeID(.bat and .reg) on the newly installed Win
That way can install anything.

grub:
[Main Page - Grub4Dos Wiki]("http://grub4dos.sourceforge.net/wiki/index.php/Main_Page") 

Vbox tuto:
[Howto: Windows XP in both VM and native (View topic) • virtualbox.org]("http://forums.virtualbox.org/viewtopic.php?t=9697") 

initial tuto I've learn before all:
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

and surely:
[http://www.boot-land.net/](http://www.boot-land.net/)

---

