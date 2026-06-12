---
title: "GRUB on it's own partition"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by AeroSigma on 2007-12-12
I have been searching the forums and google, but I haven't been able to find any documentation about this.

I will be playing around with a few different distros on my comptuer, and want to be able to install and format as much as I like without reinstalling/configuring a bootloader each time.  I will be simultaneously booting Windows* as well, and it will need to continuously be bootable.  I am planning on having two versions of linux at a time, but since I will be changing them, I would like to have a seperate partition just for the installation of grub.  Thus when I delete one linux distro, I don't get rid of the /boot/grub with it. 

I'll be starting out with Ubuntu and probably Gentoo, right now I've got just windows. My bios decided that my storage drive is the first and my OS drive is the second sd;  I have no qualms with this.

It would look like this:
____________________
sda:
sda1 - NTFS storage
sda2 - EXT3 storage
____________________
sdb:
   sda1 - Windows
-------
|e   sdb2 - ext3  <-GRUB would go here
|x   sdb3 - swap 
|t    sdb4 - ext3  /home  <-for all distros, so I can keep my files
|e   sdb5 - ext3	<- First Linux (let's say Ubuntu)
|n   sdb6 - ext3  <- Second Linux (how about Gentoo)
|d
|e
|d
-------
____________________

If I have such a partitioning setup would I simply be able to copy the /boot/grub from Ubuntu to /dev/sdb2/boot/grub*** and 
|#sudo grub 
|>root (hd1,1) 
|>setup
then edit the menu.lst** to have proper entries?

Do I have to install GRUB seperatly some how instead?  (I haven't been able to figure out how)

Also, can I create a symlink /boot/vmlinuz that points to /boot/vmlinuz-x.xx.x-whatever and tell the menu.lst
kernel	/boot/vmlinuz
or does the menu.lst need a full
kernel /boot/vmlinuz.x.xx.x-whatever
this would be nice because then whenever I replace a partition with a new distro I could just add the symlink at /boot/vmlinuz instead of having to edit the menu.lst because it uses a different kernel name.  Is this okay with GRUB?

I really don't want to just mount /dev/sdb2 as /boot during an installation because I don't nessecarily want the kernels to be loaded there, I want only grub on that partition.

Thanks,
AeroSigma
_____________________________________
*Windows isn't that bad, and I'm going to keep it, so skip the unproductive comments about that, thanks.
**In case you don't know menu.lst is typically located at /boot/grub/menu.lst and contains the settings that grub loads upon boot, most importantly the list of operating systems, and how to boot them, so you can choose what to boot.
PS-I think it's important to explain where files are located because alot of people reading the forums don't nessecarilly know the location of (or have ever heard of) menu.lst, or config.log or whatever, and this is a great way to learn.
***Dudes, I would mount this first, dont' worry.

---

### Post by mikewhatever on 2007-12-12
I am no expert in GRUB, so look here -->[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by AeroSigma on 2007-12-12
Great!, that confirms my suspicions, thanks for the link!

---

### Post by logos34 on 2007-12-12
Don't forget step 6 in that link mikewhatever gave you--i.e. use 'configfile' format for entries.

I have a separate grub partition (on hda7) and here's how my menu.lst looks in case you're interested:

> 
...

## ## End Default Options ##

title        Ubuntu Studio 7.10 (64-bit) 2.6.22-14-rt (/dev/hda8) 
configfile   (hd0,7)/boot/grub/menu.lst

title        Ubuntu 7.10 Gutsy Gibbon (32-bit) 2.6.22-14-generic (/dev/hda3) 
configfile   (hd0,2)/boot/grub/menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

	
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Boot from CD (SBM)
root		(hd0,6)
kernel		/boot/memdisk
initrd		/boot/sbm.img

title Parted Magic 1.8
root (hd0,6)
kernel /isolinux/bzImage root=/dev/ram0 initrd=initrd init=/linuxrc ramdisk_size=100000
initrd /isolinux/initrd.gz

title Gparted 0.3.3-0
root (hd0,6)
kernel /isolinux2/linux root=/dev/ram0 initrd=initrd.gz init=/linuxrc ramdisk_size=65000
initrd /isolinux2/initrd.gz

Mine's about ~100MB, which is rather large but I wanted to be able to boot from some live utility cd .isos without having to use the actual disc.  As you can can see I have Parted Magic and Gparted, and even SBM so I can boot from any cd without having to change the Bios.  That's what's nice about a dedicated grub.  (I need to move it to a primary partition though, so I can have the option of resizing the extended partition--that's the one thing I can't do now because it's inside on a logical)

---

