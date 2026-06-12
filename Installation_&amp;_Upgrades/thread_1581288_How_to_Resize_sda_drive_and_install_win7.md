---
title: "How to Resize sda drive and install win7?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by farmerjohn73 on 2010-09-24
Hi,
 
 I have installed Ubuntu 10.04LTS on my entire hard drive of my laptop.   It's been smooth ride, of course.  Now I want to resize my drive and  install windows 7 on the new partition.
 
 How do I do that?  I have installed Gparted.  I have ubuntu installation  disk.
 
 I want Ubuntu to be the default OS and I want to log on to wndows 7 when  I want to from the boot menu.
 
 How do I do that?
 
 Pls. help.

Thanks in Advance.

---

### Post by pricetech on 2010-09-24
Can't answer your question, but I do have a suggestion;  VirtualBox, either the OSE version from the repositories or the PUEL version from the website.  I've installed it here and while I haven't used it much, installation was a breeze.

---

### Post by Mark Phelps on 2010-09-25
> **farmerjohn73 said:**
> I want Ubuntu to be the default OS and I want to log on to wndows 7 when  I want to from the boot menu.
 
 How do I do that?

Since Windows OSs want to be near the beginning of the Disk, although you MIGHT be able to install Win7 into a second partition, your chances would be a lot better if you did the following:
1) Burn a GParted LiveCD -- which you can get from distrowatch.com
2) Shrink the Ubuntu partition and move it to the right -- to make room for a Win7 partition
3) Create an NTFS partition in the unallocated space at the beginning of your drive (recommend 30 GB as a minimum)

After you install Win7, it will automatically overwrite the MBR -- wiping out GRUB in the process.  But you can then use an Ubuntu LiveCd to restore GRUB.

---

### Post by farmerjohn73 on 2010-09-27
phelps,

thanks a lot for your suggestion.  I wanted to try what you said.  But I wanted to know if there was a short cut way to resize the hard drive.  

I will try that and post the feed back here.

Thank you.

farmerjohn.

---

### Post by mixmastamyk on 2010-09-27
Have you tried gparted from the ubuntu live cd?

It may not be necessary to move the linux partition first, just shrink it.  In fact I would try installing windows into a second or third partition to see if it works before going thru all the trouble of moving linux, as it will take hours.  Also you could lose everything to a bug in the partition tools.  If windows refuses to cooperate then move linux and try again.

As always make a backup first!  ;)

---

### Post by farmerjohn73 on 2010-09-28
thank you mix,

this also sounds good.  I will boot with live cd and try to shrink the HDD into two and install win7.  

I 've been busy so I didnt give it a shot.  May be today I will do that.

I am trying to take back up of my Linux with latest updates and all the softs installed first.

I will be in touch.

thank you all.:)

---

### Post by farmerjohn73 on 2010-10-01
phelps,

I followed you to some extent.  I used gparted live cd and created ntfs partition (but I didn't move it to the beginning of the disk) and installed win7 on it.  As you said, it has overwritten the MBR.  I booted with an ubuntu installation disk [coz I dont have live cd :-( ] and when I cancelled installation, it started the ubuntu but not with my username.  It booted with ubuntu@ubuntu: prompt.

I searched for help on net to restore grub and was successful in restoring grub.  But the boot menu is not loading and windows is not shown.

I am trying to solve this.

Hoping for some advice from some one here.

thank you all, guys  :-)

---

### Post by farmerjohn73 on 2010-10-01
With the help of you guys, I am successfully restored my linux.  Please see my post above.

When I checked with fdisk -l, my screen shows somethig like this.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036c15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5522    44351488   83  Linux
/dev/sda2   *        5522        9359    30818304    7  HPFS/NTFS
/dev/sda3            9359        9730     2978817    5  Extended
/dev/sda5            9359        9730     2978816   82  Linux swap / Solaris

Disk /dev/sdc: 3959 MB, 3959422976 bytes
137 heads, 48 sectors/track, 1175 cylinders
Units = cylinders of 6576 * 512 = 3366912 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1176     3866600    b  W95 FAT32


Now I want to change my default boot to be from the linux partition i.e., sda1 with boot option for linux and windows, linux being default to boot if windows is not chosen.  Please help me to do this.

I tried to add entries to grub menu but I could not do that.  When I probed OS, I get this screen :


Found Windows 7 (loader) on /dev/sda2
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7b5d6eb83c9db573
	chainloader +1


What should I do to repair this??

---

### Post by farmerjohn73 on 2010-10-04
No reply yet !  Mods, you see this at least, please.... :(

---

### Post by Mark Phelps on 2010-10-04
Are you able to boot into both Win7 and Ubuntu but just want to change the default to be Ubuntu?

If so, install startup-manager in Ubuntu.  Then, launch it and use the pull-down to select the default OS entry.

When you reboot, that entry will boot by default.

It's that simple.

---

### Post by farmerjohn73 on 2010-10-05
thanks you phelps for replying me.

No, I am not booting into win7.

The boot loader is showing only ubuntu.  There is no entry for win7.

Please let me make it clear.

I want to boot with my sda1 linux partition with a boot loader which shows me the option to boot from sda1 with Linux and sda2 with win7.

I think right now I am booting with sdc1 which is only 3GB.

[Please see my earlier post]

How do I do that?

---

