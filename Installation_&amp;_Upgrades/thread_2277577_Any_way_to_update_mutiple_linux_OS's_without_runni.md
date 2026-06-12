---
title: "Any way to update mutiple linux OS's without running OS-proble"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2015-05-09
I have been collecting Linux OS's for some years.  At this point I have 15 of them in addition to multiple Windows OS partitions. I find that the OS probing process adds about 10 minutes to each update for each Linux distro.  Is there a way to do the updates one at a time and turn off the OS prober each time and not corrupt my grub menu.  Here is the list:  Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1            2048  29296969  29294922    14G 83 Linux
/dev/sdc2        29298686 625141759 595843074 284.1G  f W95 Ext'd (LBA)
/dev/sdc5        29298688  39452671  10153984   4.9G 82 Linux swap / Solaris
/dev/sdc6        39454720  82075647  42620928  20.3G 83 Linux
/dev/sdc7        82077696 123844607  41766912  19.9G 83 Linux
/dev/sdc8       123846656 154687487  30840832  14.7G 83 Linux
/dev/sdc9       154689536 185438207  30748672  14.7G 83 Linux
/dev/sdc10      185440256 218402815  32962560  15.7G 83 Linux
/dev/sdc11      218404864 259850239  41445376  19.8G 83 Linux
/dev/sdc12      259852288 294955007  35102720  16.8G 83 Linux
/dev/sdc13      294957056 331900927  36943872  17.6G 83 Linux
/dev/sdc14      331902976 366860287  34957312  16.7G 83 Linux
/dev/sdc15      366862336 402122751  35260416  16.8G 83 Linux
/dev/sdc16      402124800 435568639  33443840    16G 83 Linux
/dev/sdc17      435570408 466913159  31342752    15G 83 Linux
/dev/sdc18      466913280 500070399  33157120  15.8G 83 Linux
/dev/sdc19      533502648 625141759  91639112  43.7G  7 HPFS/NTFS/exFAT
/dev/sdc20      500072448 533501951  33429504    16G 83 Linux

---

### Post by Dennis N on 2015-05-09
There is a two-part answer:

1) Use custom menus that you never have to update.
2) Turn off the os-prober in every OS after creating the custom menus.

For (1) I used this guide to make my custom menu. Study it carefully:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

For (2) you simply run this command in every OS to turn it off.
sudo chmod -x  /etc/grub.d/30_os-prober

The key to avoiding updating is in the section "Maintenance-Free Menu Entries" where you replace the normal linux and initrd lines in each OS menu entry by the type of entry shown there. Notice these have no kernel number. They use symbolic links to point to the most recent kernel instead.
---------------------------------
My /etc/grub.d

```
dmn@Daphne:/etc/grub.d$ ls
00_header         06_k-ubuntu-mate-1404    10_linux          40_custom
05_debian_theme   06_m-ubuntu-mate-1504    20_linux_xen      41_custom
06_d-xubuntu1404  06_n-xubuntu-1504-beta1  20_memtest86+     README
06_f-lubuntu1404  06_p-linux-mint-mate-17  30_os-prober
06_h-lubuntu1504  06_r-Ubuntu-Mate-1404-2  30_uefi-firmware

```
Each file starting with 06 is a custom menu entry for just one OS. (You can start these file names with any of 06, 07, 08, 09 so my use of only 06 is arbitrary).

06_f-lubuntu1404 looks like this, and was copied from grub.cfg, pasted into 40_custom, title then edited to what I want to appear, changing the linux and initrd lines, then finally  saved as 06_f-lubuntu1404 in /etc/grub.d. Very simple.

```
dmn@Daphne:/etc/grub.d$ cat 06_f-lubuntu1404 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'LUBUNTU 14.04  (sda6)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-05b2fc6c-8b44-4745-a8d3-5f8fd8b357f2' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  05b2fc6c-8b44-4745-a8d3-5f8fd8b357f2
	else
	  search --no-floppy --fs-uuid --set=root 05b2fc6c-8b44-4745-a8d3-5f8fd8b357f2
	fi
	linux	/vmlinuz root=UUID=05b2fc6c-8b44-4745-a8d3-5f8fd8b357f2 ro  quiet splash $vt_handoff
	initrd	/initrd.img
}

```

That's my method, with thanks to the author of that guide I linked to.

---

### Post by oldfred on 2015-05-09
This is very similar to Dennis N's link and procedure which looks very good.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

I keep one install in control & let grub update its kernels, but then add other installs to 40_custom. I also add direct loop mount boot of ISO and keep os-prober turned off.

I also hate a new install as yes it takes forever to parse all the other installs & it seems to do it more than once.

---

