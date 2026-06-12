---
title: "How to use grub2 to have live usb that retains changes"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by josephellengar on 2010-05-22
I have used grub2 to be able to boot multiple iso files on a flash drive as per this thread: 
[http://ubuntuforums.org/showthread.php?t=1484582](http://ubuntuforums.org/showthread.php?t=1484582)

Is there any way to add a persistent installation of 10.04 to this flash drive, similar to what the startup disc creator application can do?  I'd like to be able to have the clean installation and the persistent installation plus the other tools that I have on the flash drive.  It's an 8 gb drive so there is ample room.

---

### Post by josephellengar on 2010-05-25
Bump.  Anybody have any ideas?

---

### Post by kansasnoob on 2010-05-25
I've never done exactly what you're doing but I prefer Portable Linux:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Because:

> Save disk space and use your removable drive as usual: The live removable drives created by this program let you use the remaining disk space on your removable drive to store and transport files between Windows, Mac and Linux computers, as usual.  Since it uses a Live CD, you save valuable disk space on your removable drive.

Not sure how that would work with multiple OS's :confused:

---

### Post by josephellengar on 2010-05-25
> **kansasnoob said:**
> I've never done exactly what you're doing but I prefer Portable Linux:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

Because:



Not sure how that would work with multiple OS's :confused:

Neat.  Does that use grub 2 or grub1.x?

---

### Post by oldfred on 2010-05-25
Just do a full install to the Flash using grub2. You then have a full install and if you have room you can add the ISO directory and boot those also.

Herman also has some other alternatives on his site.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by josephellengar on 2010-05-25
> **oldfred said:**
> Just do a full install to the Flash using grub2. You then have a full install and if you have room you can add the ISO directory and boot those also.

Herman also has some other alternatives on his site.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

Can I do this with the usb creator tool that comes in the standard version?  Or does that not use grub 2?  Last time I tried to do an install directly to a flash drive it screwed up the bootloader on the computer that I used.  But once I solve that I just put the iso files in /boot/iso or whatever directory and edit the grub.cfg file or whatever grub2 uses now?

---

### Post by oldfred on 2010-05-25
No the USB creator creates on system using syslinux.

When you do a full install and want grub2 somewhere other than sda you have to use the advanced button on the last partition screen.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by theozzlives on 2010-05-25
With Jaunty, I made sdb1 FAT32, then did a full install on sdb2. Be sure to unplug your hard drive first.

---

### Post by C.S.Cameron on 2010-05-25
To make this type of thumb drive persistent:
First divide the thumb drive into a FAT32 partition and an ext2, 3 or 4) partition. Label the ext partition casper-rw.
Install grub to the FAT32 partition and save your iso files there also.
Then edit the menuentry line in grub.cfg as shown below:

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt -- persistent

If you want a separate persistent Home make another ext partition and label it home-rw.

Some people believe using ext2 for the persistent partitions will make the flash drive last longer, I don't believe it is an issue.

---

### Post by josephellengar on 2010-05-25
> **C.S.Cameron said:**
> To make this type of thumb drive persistent:
First divide the thumb drive into a FAT32 partition and an ext2, 3 or 4) partition. Label the ext partition casper-rw.
Install grub to the FAT32 partition and save your iso files there also.
Then edit the menuentry line in grub.cfg as shown below:

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt -- persistent

If you want a separate persistent Home make another ext partition and label it home-rw.

Some people believe using ext2 for the persistent partitions will make the flash drive last longer, I don't believe it is an issue.

So, just to make sure that I understand this, the --persistent flag will tell grub2 to boot the iso and save all changes to the casper partition, and load all changes from the casper partition?  Is casper some special program for this built into grub?  And then, if I save the iso file on the partition with grub in the directory /boot, could I change the command that you gave to 
```

linux (loop)/casper/vmlinuz boot=casper /boot/*file_location*=$isofile quiet splash noprompt -- persistent

```

And then the rest of the /etc/grub.cfg or whatever would just load up the rest of the iso files that I have on the thumb drive as outlined in the post that I linked to above?

For example, if I want to use spinrite on my flash drive the entry would be something like:

```

 loopback loop /boot/iso/spinrite.iso
 linux (loop)/vmlinuz boot=cd isofrom=/dev/sdcx/boot/iso/spinrite.iso xbmc=nvidia,nodiskmount,tempfs,setvolume loglevel=0 --
 initrd (loop)/initrd0.img

```

I don't really get what all of that means, but it seems to follow the patterns I've seen elsewhere.  If I have a tool that doesn't use a linux base (spinrite is based on freeBSD but I want to have the ghost restore utility on this drive) would I put dos in front of the command or something?

---

### Post by C.S.Cameron on 2010-05-25
As I understand, Ubuntu by default, (well when given the "persistent" prompt), first looks for a partition named casper-rw when booting to load persistent stuff from.
If it can't find a partition by this name it looks for a file by the same name.
This is true even when booting the Live CD, but then you have to press F6 and type <space>persistent.
The first time you boot "persistent" a bunch of stuff gets written to this partition, including a home folder, unless of course you make the home-rw partition.

I think the way you wrote it will also work, from what I have tried you just got to get the word <space>persistent into menu.cfg, grub.cfg or text.cfg somewhere.
You can manually press F6 at the first screen after language, and type it then also, (if you only want persistence on demand).

Please let us know what works for you.
Cork

---

### Post by josephellengar on 2010-05-25
> **C.S.Cameron said:**
> As I understand, Ubuntu by default, (well when given the "persistent" prompt), first looks for a partition named casper-rw when booting to load persistent stuff from.
If it can't find a partition by this name it looks for a file by the same name.
This is true even when booting the Live CD, but then you have to press F6 and type <space>persistent.
The first time you boot "persistent" a bunch of stuff gets written to this partition, including a home folder, unless of course you make the home-rw partition.

I think the way you wrote it will also work, from what I have tried you just got to get the word <space>persistent  into menu.cfg, grub.cfg or text.cfg somewhere.

Please let us know what works for you.
Cork

Will do.  My 8gb flash drive that I've been preparing for should arrive soon.  :D

---

### Post by wilee-nilee on 2010-05-25
I haven't read through the whole thread but you have good advisers that's for sure. Here is a pendrivelinux description of the casper-rw stuff.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)
This is for making a casper-rw file but also how to make it bigger then 4 gigs altogether.

---

### Post by josephellengar on 2010-05-27
This is sort of off topic, but I'm having troubles with my grub2.  My grub.cfg is as follows, and every single option, when chosen, says "must load kernel first."  I have copied identically from the configurations that are suggested online.  I can't figure out what the problem is.  Here is my grub.cfg: (Just trying to get the temporary ones to work before I work on the persistent installation)

```

#Clonezilla v1.2.5-17 ====================================================================================================================

menuentry "Clonezilla 32" 
{
	set isofile="/boot/isos/clonezilla32.iso"
	loopback loop $isofile 
	linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile 
	initrd (loop)/live/initrd.img
}

menuentry "Clonezilla 64" 
{
	set isofile="/boot/isos/clonezilla64.iso"
	loopback loop $isofile 
	linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile 
	initrd (loop)/live/initrd.img
}

#gparted v0.5.2 ==========================================================================================================================

menuentry "Gparted"
{
	set isofile="/boot/isos/gparted.iso"
	loopback loop $isofile
	linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
	initrd (loop)/live/initrd.img
}

#Ubuntu v10.04 downloaded 5/27/10 ========================================================================================================

menuentry "Ubuntu 32" 
{
    set isofile="/boot/isos/ubuntu32.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 64" 
{
    set isofile="/boot/isos/ubuntu32.iso" 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```

And would anyone know how I would set up an option to boot a spinrite cd?  It's based on freedos.  Thanks for any help.

---

### Post by oldfred on 2010-05-27
These are two of my entries that I know work. your file with the ISOs has to be the file they are in and Capitialization is critical. My location is /boot/ISOs but yours is /boot/isos and I have seen just ISO as the subdirectory.

```
menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry " " {
set root= 
}

```

---

### Post by josephellengar on 2010-05-27
What do these lines do in your gparted entry:

```

insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600

```


Do I need them in my other entries, since I am loading the kernel module through the iso in all of my entries?
Thanks.

---

### Post by oldfred on 2010-05-27
I notice those also but did not add them to the other entries and they seem to work.

I think the ismod is just another grub2 mod setting to make it think it is a CD iso9660 is a CD standard.

set gfxpayload=800x600x16, 800x600
This sets grubs screen size, you can use your defaults also and there is a way to tell what grub sees as available, but I forgot since I do not use it.

---

### Post by josephellengar on 2010-05-28
> **oldfred said:**
> These are two of my entries that I know work. your file with the ISOs has to be the file they are in and Capitialization is critical. My location is /boot/ISOs but yours is /boot/isos and I have seen just ISO as the subdirectory.

```
menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry " " {
set root= 
}

```
I can't figure out why, but your gparted entry didn't work for me ("must load kernel first").  Could you possibly post your entire grub.cfg so I can see if I'm going anything else wrong?

---

### Post by C.S.Cameron on 2010-05-28
I had the same problem once and found that the path in menuentry was not 100% correct.

---

### Post by oldfred on 2010-05-28
I think    	C.S.Cameron is correct as the path has to be correct for it to work. In linux ISO is not equal to iso nor Iso. And I used /boot/ISOs as plural.
Check what path you have used to store the iso files. 

I attached my complete grub.cfg and I have tested it for all the Ubuntu entries and the system rescue & gparted. Anything else I have in there may not be finalized yet.

---

### Post by josephellengar on 2010-05-28
> **oldfred said:**
> I think    	C.S.Cameron is correct as the path has to be correct for it to work. In linux ISO is not equal to iso nor Iso. And I used /boot/ISOs as plural.
Check what path you have used to store the iso files. 

I attached my complete grub.cfg and I have tested it for all the Ubuntu entries and the system rescue & gparted. Anything else I have in there may not be finalized yet.

I did modify your entry so that the path was correct on my machine.  For me it was /boot/isos/filename

---

### Post by oldfred on 2010-05-28
I thought I had attached my grub.cfg.

---

### Post by oldfred on 2010-05-28
Attach is not working:

```
menuentry "Ubuntu 10.04 64bit" {
    set isofile="/boot/ISOs/ubuntu-10.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.10 64 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 9.10 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.04 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

menuentry "Parted Magic" {
    set isofile="/boot/ISOs/pmagic-4.8.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry "Ubuntu Mini 9.10 32 bit" {
    set isofile="/boot/ISOs/miniKarmic32.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}


menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-beta.2006042900_i386.iso
 linux (loop)/ISOLINUX/DBAN.BZI nuke="dwipe" silent --
}




```

---

