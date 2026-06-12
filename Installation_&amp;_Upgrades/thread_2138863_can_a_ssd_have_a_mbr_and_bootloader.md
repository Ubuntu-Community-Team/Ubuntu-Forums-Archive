---
title: "can a ssd have a mbr and bootloader?"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by zhangdejia on 2013-04-25
[COLOR=#000000][FONT=Arial]I install both linux and windows on my newly bought ssd(sda)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and when i installed linux, i chose to install the bootloader on ssd(sda).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]After i finished, i got only a black screen when i chose to boot from ssd,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]but the most strange thing is that i got a grub menu when i chose to boot from hdd(sdb),[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and i'm sure i chose the ssd as the bootloader installation location.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So why did the bootloader transfer from ssd to hdd?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Does it mean that a ssd can't hold a mbr or bootloader at the very beginning of it?[/FONT][/COLOR]

---

### Post by oldfred on 2013-04-25
I boot from my SSD without issue. 

Are you sure you installed to the SSD? Grub likes to default to sda and drive order is not always fixed.

You can reinstall grub from inside your install, just confirm which is sda and sdb. Example uses sdb, change to sda if needed.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

You maybe should do this anyway. As grub on a major update may reinstall to wrong drive and I am not sure above install method resets that.
      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You could check before & after first set of commands above to see if this does reset the reinstall drive.

 #To see what drive grub2 uses to reinstall see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by sudodus on 2013-04-25
Welcome to the Ubuntu Forums :-)

The ssd is treated like the hdd, and acts like an hdd. So there should be no difference.

So you need to edit the boot priority list in your bios system (which drive to try booting from first, second, third ...). Also the order between the drives in the early stage (at grub) may be different from the order later on.

But your problem should not be because of the SSD drive. You can even install Ubuntu to USB pendrive, and it will be treated like a HDD.

---

### Post by darkod on 2013-04-25
As mentioned, there is no problem using ssd with msdos table and bootloader installed on it.

However, if it has gpt table there needs to be a small bios_grub partition so that grub2 can install correctly. This applies to both hdds and ssds. Just for info...

---

### Post by Slim Odds on 2013-04-25
> **darkod said:**
> As mentioned, there is no problem using ssd with msdos table and bootloader installed on it.

However, if it has gpt table there needs to be a small bios_grub partition so that grub2 can install correctly. This applies to both hdds and ssds. Just for info...
This is not true. I have 12.10 installed on an SSD using GPT partitions with no small bios_grub partition and it boots just fine.

About 8 seconds from GRUB to login prompt.

---

### Post by darkod on 2013-04-25
And the bootloader is on the ssd?

By default grub2 wouldn't install. If you forced it against recommendations, that's another thing. Same like you can install it onto a partition boot sector.

---

### Post by Slim Odds on 2013-04-25
> **darkod said:**
> And the bootloader is on the ssd?

By default grub2 wouldn't install. If you forced it against recommendations, that's another thing. Same like you can install it onto a partition boot sector.
Please point us to some information about this problem. I've never heard of it and received no warning during installation.

---

### Post by oldfred on 2013-04-25
@Slim Odds
If you forced it in the MBR of a gpt drive, then it used blocklists. Always better to create the small 1MB unformatted bios_grub partition.

 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

   Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

---

### Post by Slim Odds on 2013-04-25
> **oldfred said:**
> @Slim Odds
If you forced it in the MBR of a gpt drive, then it used blocklists. Always better to create the small 1MB unformatted bios_grub partition.

 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

   Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)
I didn't "force" anything and received no warning of any kind. Just curious why that would be.

---

### Post by darkod on 2013-04-25
Do you have only one disk? I assume the bootloader might be on another disk without you knowing that. The bios_grub is needed only if installing grub2 on that disk. Grub2 can install just fine on other disks if you have a gpt disk without the bios_grub partition.

I can't search much right now, but here is a quick google hit where you can see the whole message:
[http://forums.gentoo.org/viewtopic-t-952634-start-0.html](http://forums.gentoo.org/viewtopic-t-952634-start-0.html)

---

### Post by Slim Odds on 2013-04-25
> **darkod said:**
> Do you have only one disk? I assume the bootloader might be on another disk without you knowing that. The bios_grub is needed only if installing grub2 on that disk. Grub2 can install just fine on other disks if you have a gpt disk without the bios_grub partition.

I can't search much right now, but here is a quick google hit where you can see the whole message:
[http://forums.gentoo.org/viewtopic-t-952634-start-0.html](http://forums.gentoo.org/viewtopic-t-952634-start-0.html)
I have 5 disks, but GRUB is definitely installed on the SSD which is where / and /home are located.
All partitions on all drives are GPT and I do NOT have a UEFI motherboard.

---

### Post by darkod on 2013-04-26
And you have grub2 or grub legacy? The problem doesn't exist on grub legacy I think because it's smaller and can fit on the smaller MBR that gpt disks have.

Apart from that, I have no idea what happened but in the link I posted you have the warning message that usually shows when trying to install grub2 on the MBR of gpt disk that doesn't have the bios_grub partition.

---

### Post by Slim Odds on 2013-04-26
> **darkod said:**
> And you have grub2 or grub legacy? The problem doesn't exist on grub legacy I think because it's smaller and can fit on the smaller MBR that gpt disks have.

Apart from that, I have no idea what happened but in the link I posted you have the warning message that usually shows when trying to install grub2 on the MBR of gpt disk that doesn't have the bios_grub partition.


> ============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 
    34804624 of the same hard drive for core.img. core.img is at this location 
    and looks in partition 72 for .
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.


Maybe that was something unusual, but I don't have any problems.

GRUB2, all GPT partitions, Ubunut 12.10, no warning, no problem.

---

### Post by darkod on 2013-04-26
Weird, and also it says core.img looks in partition number 72 which is of course not true. That might have something to do with it.

But anyway, since the machine works good, keep going... :)

---

