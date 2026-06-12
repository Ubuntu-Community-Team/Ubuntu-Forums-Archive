---
title: "Install multiple versions of Ubuntu from 1 USB flash drive"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by rishav2 on 2016-04-11
Hey there,

I got a new 32G USB flash drive recently &, naturally, I converted it to a Ubuntu 14.04 LTS bootable flash drive while storing some other version ISOs, including: 10.04, 12.04, 14.04 & 15.10, in a separate folder (required for testing occasional backwards compatibility where I have enough spare old machines to use them instead of running VMs on my slow machine). This allows me the flexibility of installing 14.04 on a device or copy over the ISOs on to the host device then select one of them to use as my chosen bootable flash drive OS. Understandably, this is a rather tedious process & one I'd like to make more efficient.

Some programmes I've come across that could help me are [MultiBootUSB]("http://multibootusb.org/features/") & [Easy2Boot]("http://www.easy2boot.com/"). Note, I've purposely left out [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") due to the disclaimer stating "*[COLOR=#333333][FONT=Lucida Grande]Installing Linux from the YUMI created USB Drive to a Hard Drive is not officially supported[/FONT][/COLOR]*" & [SARDU]("http://www.sarducd.it/") due to lack of any updates during the last few years. So, coming back to the former 2 options, which would be the best choice for the functionality needs I have explained above? Is there a better alternative you know of? In case it's relevant, ideally, I'd like the program to run on Linux but I do have a Windows 10 device, if required. This is the primary question for the thread while I have a few more below for anyone feeling like providing some additional guidance. Thanks for your time!


Secondary questions:
[LIST]
[*]Some advice/guides/tips on how to go about getting the best out of the chosen program?
[*]What is the range of Ubuntu versions it supports?
[*]Can I edit them at a later stage (eg. remove or add 1) without having to start from scratch?
[*]Can I store other files to make use of the remaining space so that I'm not left with 5GB of actually useful data while the rest is wasted space?
[/LIST]

Tertiary questions (for anyone feeling extra generous!):
[LIST]
[*]What is the range of Linux distros it's compatible with?
[*]Can I also use Windows 10 boot ISO with the program in addition to the Ubuntu ones, provided my device is UEFI/BIOS-compliant & all?
[/LIST]

---

### Post by yancek on 2016-04-11
Does your flash drive have an actual install of Ubuntu or is it just a Live CD on a flash drive.  If it is an install and you have Grub2 installed to the MBR of the flash drive, you could find the /boot/grub/grub.cfg file and put menuentries there and boot the iso files directly from a partition on the flash drive.  You can then use them as Live Cd's and also as installers.  The link below explains the basic process.  I would start by reading through it.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I've been making multiboot flash drives for years.  I don't know anything about the software you mention, never used any of them.  I think all the versions of Ubuntu you mention can be booted directly from an iso, if that's what you want.

As far as editing, if you mean replacing an iso on the flash drive with another or just adding one, yes you can do that and simply modify the grub.cfg file appropriately.  You can store files either by creating a persistent partition and you could probably create an additional data partition.  With a 32GB drive, it might be easier to install Ubuntu and then put the iso files of other releases in a directory or separate partition on the flash drive and boot from the install Ubuntu Grub.

> What is the range of Linux distros it's compatible with?

If you mean the software you mention above to create multi-boot, their sites are the best source of info for that.  If you mean booting an iso file directly, most of the major Ubuntu derivatives will work as will a number of others.

You can boot a windows 10 iso from Grub2 but only after it has been extracted and copied to an ntfs partition on the flash drive and the partition is marked as active/bootable.  I just did this today and it was a real pain to get working, for me at least.  I don't know anything about EFI.

If you have any specifics questions, post back.

---

### Post by sudodus on 2016-04-12
Do you want a tool that does the work for you, or do you want to understand how it works, and do it yourself?

If you want a tool, test ***MultiBootUSB***, ***Easy2Boot*** and ***YUMI***. There is also ***Multisystem***.

Try them all and settle with the tool that you like best :-)

Otherwise it is a good idea to start with *yancek*'s link, and links from that link and learn how to do it yourself.

-o-

For me USB pendrives are ***temporary devices*** for booting or for storing and moving data. I store iso files in my main computer, and flash one of them to a USB pendrive, whenever I want to install it into some other computer. I find that more convenient than to keep a multiboot pendrive up to date with a lot of iso files.

---

### Post by C.S.Cameron on 2016-04-12
I have had good luck with MultiBootUSB.
It is a grub2 iso booter. 
Besides for every version of 'buntu you can install gparted, clonezilla and hundreds of other Linux based O/S's.
Ubdating to a new version of 'buntu is a simple matter of copying the new iso to the disk, and copying an existing menuentry and editing to suit the new iso.
I don't think it works with Windows 10, as that requires a NTFS format and iso booting uses FAT32.

---

### Post by rishav2 on 2016-04-12
> **yancek said:**
> Does your flash drive have an actual install of Ubuntu or is it just a Live CD on a flash drive. If it is an install and you have Grub2 installed to the MBR of the flash drive, you could find the /boot/grub/grub.cfg file and put menuentries there and boot the iso files directly from a partition on the flash drive. You can then use them as Live Cd's and also as installers. The link below explains the basic process. I would start by reading through it.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I've been making multiboot flash drives for years. I don't know anything about the software you mention, never used any of them. I think all the versions of Ubuntu you mention can be booted directly from an iso, if that's what you want.

As far as editing, if you mean replacing an iso on the flash drive with another or just adding one, yes you can do that and simply modify the grub.cfg file appropriately. You can store files either by creating a persistent partition and you could probably create an additional data partition. With a 32GB drive, it might be easier to install Ubuntu and then put the iso files of other releases in a directory or separate partition on the flash drive and boot from the install Ubuntu Grub.

If you mean the software you mention above to create multi-boot, their sites are the best source of info for that. If you mean booting an iso file directly, most of the major Ubuntu derivatives will work as will a number of others.

You can boot a windows 10 iso from Grub2 but only after it has been extracted and copied to an ntfs partition on the flash drive and the partition is marked as active/bootable. I just did this today and it was a real pain to get working, for me at least. I don't know anything about EFI.

If you have any specifics questions, post back.

Thanks for your reply, yancek! The flash drive just has an Ubuntu Live CD on it as well as the ISO files of a few other Ubuntu versions. This prevents me from editing the grub configuration file's menu entries at the moment.
 
Although, I really appreciate the link as I found an alternate solution but this could still come in handy to understand the process & improve it further. Also, good to hear of the wide support of Ubuntu/Linux distros ISOs & *relative* ease of the update procedure. I could tell that Windows won’t play nice in such a scenario hence its low level priority. Still, it’s something I can work towards over time.
 
Will come back to this shortly to talk more about the .cfg file.
 
[HR][/HR]> **sudodus said:**
> Do you want a tool that does the work for you, or do you want to understand how it works, and do it yourself?

If you want a tool, test ***MultiBootUSB***, ***Easy2Boot*** and ***YUMI***. There is also ***Multisystem***.

Try them all and settle with the tool that you like best [IMG]file:///C:/Users/Rishav/AppData/Local/Temp/msohtmlclip1/01/clip_image001.gif[/IMG]

Otherwise it is a good idea to start with *yancek*'s link, and links from that link and learn how to do it yourself.

-o-

For me USB pendrives are ***temporary devices*** for booting or for storing and moving data. I store iso files in my main computer, and flash one of them to a USB pendrive, whenever I want to install it into some other computer. I find that more convenient than to keep a multiboot pendrive up to date with a lot of iso files.
 
Thanks for your reply, sudodus! Ideally, I’d like to learn what goes on in the background & do it myself but who can pass up on a tool to automate it. My original question already lists 3 of the mentioned tools while Multisystem is the Linux variant of YUMI. I was torn between MultiBootUSB & Easy2Boot as both of them seemed quite recently updated & reliable.
 
While I also agree that USBs are temporary devices used to transfer files intermittently, I have little else use of it. Whereas, most of its contents are Ubuntu ISOs so it would appear to make more sense to use it purely as a bootable USB to install various versions of Ubuntu on to host devices as required. As far as updating is concerned, LTS versions are few & far between while non-LTS versions are not of significant priority to have so I can manage the occasional hassle. :)
 
[HR][/HR]> **C.S.Cameron said:**
> I have had good luck with MultiBootUSB.
It is a grub2 iso booter. 
Besides for every version of 'buntu you can install gparted, clonezilla and hundreds of other Linux based O/S's.
Ubdating to a new version of 'buntu is a simple matter of copying the new iso to the disk, and copying an existing menuentry and editing to suit the new iso.
I don't think it works with Windows 10, as that requires a NTFS format and iso booting uses FAT32.
 
Thanks for your reply, C.S.Cameron. You tipped the scales in favour of MultiBootUSB so that’s what I went with. GParted is another valuable addition which I often overlook simply because it comes pre-packaged with all Ubuntu releases even though it’s well-worth having just by itself. As before, I’ll leave Windows out of this for now sheerly due to the NTFS/FAT32 formatting predicament.
 
[HR][/HR]
Thanks to everyone’s help here, the current visual of the MultiBootUSB GRUB menu without any sort of manual modifications done to it is attached below. It’s completely functional & surprisingly easy to accomplish within minutes. It also allows of uninstallations of selected distros as well as QEMU to observe the bootable USB in action before even rebooting the machine.
 
Furthermore, I came across syslinux.cfg which I believe is yancek’s equivalent of the grub.cfg file. I’ll be playing around with this a bit more to improve readability of which distro I’m looking as well as their ordering. In the meantime, I’m more than happy to mark this thread as resolved. Thanks once again to all involved & I intend to post another update at a later stage with better text formatting of the GRUB menu!

[ATTACH=CONFIG]268353[/ATTACH]

---

### Post by yancek on 2016-04-12
Creating a multi-boot flash drive with only iso files on to boot and use isn't all that difficult.  The one thing you need to do manually is install Grub2  to the flash drive and create the grub.cfg file.  If you do that, you can easily modify the menuentries when you remove or add an iso.  The output below is what shows on a partition of a flash drive with multiple iso files which all boot and you can see that all you need is the boot directory containing the grub directory and it's files an the iso files .

> bodhi-2.4.0-32.iso
boot/
clonezilla-live-2.3.1-18-i686-pae.iso
efi/
elementaryos-stable-i386.20130810.iso
kubuntu-14.04-desktop-i386.iso
linuxmint-17-cinnamon-dvd-32bit-rc.iso
linuxmint-17-mate-32bit-v2.iso
lubuntu-14.04-desktop-i386.iso
Peppermint-4-20130611-i386.iso
ubuntu-14.04-desktop-i386.iso
xubuntu-14.04-desktop-i386.iso
zorin.iso

---

