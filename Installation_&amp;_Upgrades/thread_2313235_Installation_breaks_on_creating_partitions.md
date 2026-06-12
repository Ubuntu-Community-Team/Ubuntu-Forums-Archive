---
title: "Installation breaks on creating partitions"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by Nardrus on 2016-02-10
Hi all!

I tried Linux other times before but this time I wanted to install ubuntu as my main OS.
I bought all components and mounted a computer by myself. This is what I got:

Motherboard: [FONT=arial]Gigabyte GA-970A-UD3P v2.0
Hard drive: [/FONT][FONT=arial]WD Blue 1TB SATA3
Processor: [/FONT][FONT=arial]AMD FX Series FX-8320 3.5Ghz 8X
Memory: [/FONT][FONT=arial]Kingston HyperX Fury Blue DDR3 1866MHz 16GB 2x8GB CL10
Graphics: [/FONT][FONT=arial]Gigabyte GeForce GT730 2GB GDDR5
Net: [/FONT][COLOR=#000000][FONT=Arial]Edimax EW-7612PIn V2 N300 Wireless PCI Express Adapter
Power: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Tacens Mars Gaming 700W

I first burned the Ubuntu version 15.04 on a DVD but the installation crashes when is trying to create the partitions (see image attached). The same happened on the Ubuntu version 15.10 and on Debian, but the installation of windows vista worked (it is running windows right now).

I would like to completely remove windows and have just Ubuntu but I always get that error. I also tried other hard drives with the same results. I think that my motherboard has something to do with this but I could not know what and the Gigabyte support just say they don't give support to Linux (and that if it works on windows it means that it is fine).

Can I have some help please?

Edit:
[/FONT][/COLOR][COLOR=#006400][FONT=Arial]SOLUTION: Enable [/FONT]IOMMU on bios.[/COLOR]

---

### Post by Bucky Ball on 2016-02-10
*Thread moved to **Installation & Upgrades**.*

Forget 15.04. Not supported. Try 15.10 or 14.04 LTS. They are supported.

(You are not assigning a /swap space or there isn't room for one. Are you hitting 'Something Else' and partitioning manually at the partitioning section of the install? How are you installing? Absolutely nothing to do with motherboards or any other hardware issue. There is a problem with partitioning during install and specifically, partition #5, the /swap.

You might try wiping the drive completely first then doing this. Ubuntu needs free space to install to, not prepared partitions, particularly created by Windows. It can't install to them anyway. Ubuntu uses EXT* partitions, not FAT or NTFS for the OS partition.)

---

### Post by kansasnoob on 2016-02-10
I stumbled across that while testing Wily, seems to be an old ignored (what they call triaged) bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/990744](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/990744)

If memory serves properly I believe I had to create all of my partitions with Gparted before beginning the install and then assign them properly during installation.

---

### Post by Bucky Ball on 2016-02-11
> **kansasnoob said:**
> If memory serves properly I believe I had to create all of my partitions with Gparted before beginning the install and then assign them properly during installation.

Definitely worth a shot. Just make sure you create EXT partitions for them and not anything else (which means you'll need to boot from the install media, 'Try Ubuntu', launch Gparted and use the free space on the disk to create the partitions). When you're finished in Gparted and back at the desktop, click the 'Install' icon and when you get to partitioning, choose 'Something Else'. 

Assign mountpoints to the partitions you've created.

---

### Post by Nardrus on 2016-02-11
I already tried Gparted and failed, but I will try it one more time detailing all my actions and let you know if it works or it doens't work.
While installing I chose several options:
The default one.
Creating the partitions by hand.
Not creating SWAP.

I even tried filling all the disk with 0 with the dd command to erase any possible broken partition.

As said before I will choose "Try Ubuntu", use GParted and let you know.

Many thanks!!

Edit: @kansasnoob, thanks for the link to the bug report, it may be useful.
@Bucky Ball: Thanks for moving the thread to the proper section.

---

### Post by sudodus on 2016-02-11
If you don't want Windows, it should work to

0. Boot into a live session with the Ubuntu 15.10 boot drive, 'Try Ubuntu'

1. Wipe the first megabyte with zeros (like you did before with dd, but it should be enough with one megabyte)

2. Create a partition table (a default MSDOS partition table)

3. Start the installer. Select *'Erase disk and install Ubuntu'* at the partitioning page. This is the easy alternative, that you can use when there is no other operating system.

-o-

There may be problems with the nvidia card in the installed system. In that case you can try with the boot option nomodeset, and after that install a proprietary driver. See this link

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by Nardrus on 2016-02-11
Hi all!

I'm here again to report what I did.

First of all I selected "Try Ubuntu" and run the GParted. And ... I could not make any partitions with it :'(

I'm not very used to use GParted, but it doesn't seem very difficult and seems that something is not going fine (see attached GParted_1.jpg).
1.- I tried to create a partition, but a message popped up saying I need a partition table (see attached GParted_2.jpg)
2.- I created an msdos partition table (see attached GParted_3.jpg) but nothing changes, and I'm still not able to create a new partition.
3.- I attach one more screenshot of GParted (see attached GParted_4.jpg) with the information of this hard drive. I may look broken but, as said on my first post, I tried this on another hard drive with the same results and I have been able to install windows vista on both hard drives.
4.- After that I tried what sudodus said (thank you!) and wipped the first megabyte with zeros with the dd command (see attached wipping_zeros.jpg)
But GParted still does nothing when creating the partition table and obviously the installation breaks again on creating the partitions (I also tried to different configurations but none work).

Do you have any more ideas? I will keep trying different options and reading similar cases on google. Installing Ubuntu is not that difficult, there must be something I'm missing.

PS: I really appreciate your help and would like to keep receiving ideas for what is going on here.
PS2: @sudodus, thanks for the nvidia card tip, if I can manage to make this work I would try it.

---

### Post by buzzingrobot on 2016-02-11
> **Nardrus said:**
> [COLOR=#000000][FONT=Arial]I think that my motherboard has something to do...

[/FONT][/COLOR]


It's possible.  Check the BIOS settings. Try setting secure boot off, no quick boot, use legacy settings instead of settings intended for Win8/Win10. Make sure the disk is set as SATA.

Also, open a terminal in "Try" mode and see what fdisk says: > sudo fdisk /dev/sda  Use fdisk to change something (like delete any existing partition(s) and make a new one.)  Be sure to write any partition changes out ("w") and reboot so the kernel picks up the changes.  Then run fdisk again and see if you see the changes.

---

### Post by oldfred on 2016-02-11
Those Gigabyte boards need IOMMU settings changed in UEFI and a boot parameter.
  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

And nVidia usually needs nomodeset, so you need to add several boot parameters to have it work.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If only running Ubuntu or if system is UEFI, better to use gpt partitioning. You can boot from gpt with 
BIOS if you have a tiny 1 or 2MB bios_grub unformatted partition or boot with UEFI if one of the first partitions is the ESP - efi system partition formatted FAT32 with boot flag. I typically add both in case I later want to change how it boot. 

 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]15-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by Nardrus on 2016-02-12
Many thanks buzzingrobot and oldfred.

I will take a look at this and let you know if I can solve my issues.

Many thanks for all this detailed information (I will need some time understand it xD).

Best regards

---

### Post by Nardrus on 2016-02-13
Hi all!

@buzzingrobot: I remember I tried fdisk time ago without results.
@oldfred: It worked, many many thanks!!

Well, after 5 months having this computer and not being able to properly work on it I could finally install Ubuntu and keep it working after reboot.

What I did was to enable IOMMU on the bios (pressing del at startup) and then proceeding to install Ubuntu normally.
The first thing I noticed was a black screen completely full of lines saying:

[COLOR=#696969][     4.6007655] AMD-Vi: Event logged [IO_PAGE_FAUlT device=02:00.0 domain=0x0011 address=0x00000000ceb5d6c0 flags=0x0010][/COLOR]

But then I could select the "Install Ubuntu" option.
Then I noticed that USB 2.0 was working fine but not USB 3.0 (it was the other way around before, 2.0 didn't work and 3.0 did). Just like it happened when I installed Windows vista (I didn't try to fix USB 3.0 because it was just a temporal OS).

Then I noticed that the Wifi card I bought just to make it work on linux was working out of the box (an Edimax EW-7612PIn V2 N300 Wireless PCI Express Adapter that didn't work before setting IOMMU on Linux but did work on Windows).
Finally I experienced some freezes just before setting the partitions, but it was a freeze, not the same issue as before. I "solved" it not selecting "Download updates while installing" before doing partitions (I would install them once all OS was working).

There is more work to do, but the thing that was blocking me for 5 months is solved!
Also I have all the links you guys have provided me to fix this things.

Many many thanks!

This thread can be considered closed.

---

