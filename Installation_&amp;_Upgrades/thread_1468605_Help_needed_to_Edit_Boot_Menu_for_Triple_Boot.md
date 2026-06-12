---
title: "Help needed to Edit Boot Menu for Triple Boot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2010-05-01
I have had a triple boot system with XP, Kubuntu 8.04 and Ubuntu Studio 8.04 on my desktop with a wireless internet connection.  I have never been able to get the wireless working in Linux, so I haven't used it for about a year.  Today I formated the Kubuntu partition and installed Ubuntu 10.04 in its place.  I installed from the advance option and chose the partition and it told me to choose a (boot area??) I chose "/".  After installing it replaced my old customized boot menu, I used to know how to edit and customize the boot menu, by the following commands:
sudo mount /dev/sda3/mnt && gksudo gedit /mnt/boot/grub/menu.lst

Now when I do this it will give me some silly error about not finding menu.lst, which I hadn't wrote the exact details down.  But it seems that it will not mount the partition.  So I mounted the partition and browsed to that grub folder and do not find any file named menu.lst (there is just a bunch of sound files).   However when browsing to the old ubuntu studio partition, I do see my old menu.lst.

My question is: when I installed the new 10.04 and chose the "/" area, is that where the new menu.lst is located and if so how do I get to that to edit my menu selections.  I am trying to edit my menu to be like this:
1) Windows XP
2) Ubuntu 10.04
3) Ubuntu Studio

Other Options

If anyone can help me make sense of this, I would appreciate it, I am somewhat rusty after taking a year off of ubuntu, so patience might be needed.  Thanks ~Mahogan.

---

### Post by malrost on 2010-05-01
What's going on here is that when you installed 10.04, GRUB was replaced with GRUB 2.  There are a few changes, and among those is that menu.lst no longer guides controls the menu; a file named "grub.cfg" does. 

There are a few other changes as well. (See [this]("http://grub.enbug.org/Manual#head-68cc51835aa5531f789f30d26708b7cdffa05769") for differences between "legacy" GRUB and GRUB 2.) It's the same basic idea however: edit the GRUB menu to the appropriate settings for your partitioning.

If your menu.lst file is still readable it might help, but you'll need to translate a few entries to the new syntax.

Alternatively, you could also install legacy GRUB over GRUB 2. However, if you were able to figure out GRUB last year, I imagine that it would be a lot more time efficient for you to just familiarize yourself with the changes in GRUB 2.

I'm still bringing myself up to speed on GRUB 2, and so I can't help you with the specifics of the grub.cfg file (yet). However, if you need further help, I think it would helpful for others to post your grub.cfg file and your partition table (that is, if you only have one hard disk the output of ```
sudo fdisk -l /dev/sda
```. If you had two it would be ```
sudo fdisk -l /dev/sda /dev/sdb
```, etc.)

---

### Post by oldfred on 2010-05-01
Some info on grub2:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

ranch hand's custom grub2
[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553)

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

---

### Post by Don1500 on 2010-05-01
Just a thought, I've been there and tried to do all the wonderful junk Grub2 does, Had the menu in order, had a great splash screen, etc., but I have found that it all means squat after the first Kernel update (or the first time you "sudo update-grub"). You're right back to the standard Grub menu, built the way Grub wants it. So I just let it do what it wants and wait for others to complain. Grub2 works well and really doesn't interfere with my using the computer, it just does what it wants and to h*ll with what you want.

---

### Post by malrost on 2010-05-01
> **Don1500 said:**
> Just a thought, I've been there and tried to do all the wonderful junk Grub2 does, Had the menu in order, had a great splash screen, etc., but I have found that it all means squat after the first Kernel update (or the first time you "sudo update-grub"). You're right back to the standard Grub menu, built the way Grub wants it. So I just let it do what it wants and wait for others to complain. Grub2 works well and really doesn't interfere with my using the computer, it just does what it wants and to h*ll with what you want.

For some reason OSes seem rather cavalier about overwriting one's bootloader config file. Two things have completely eliminated this problem for me.

First is avoiding unwanted overwrites of my GRUB files by having a separate partition for the menu.lst file I actually use. I let other OSes install /boot in their own partitions, I just don't flag those partitions as bootable. This makes for easy review and merging of changes upon updates or upgrades.

The second thing has been keeping an online backup of my current bootloader configuration file.

---

### Post by Mahogan on 2010-05-01
Thanks fellas for your help with this.  I didn't know that there was Grub2, thanks for pointing out that the menu.lst is replaced with grub.cfg.  While I am somewhat lazy when it comes to learning lots of stuff about the new Grub2, I figured it was similar enough to the old way of editing the menu.lst and I was right, I was able to get my grub menu customized quite quickly and almost the way I wanted it.  

So for those that might have the same issue as I had...
Here is how I did it....


I started by pasting this into the terminal to edit the grub.cfg:

[COLOR="Red"]gksudo gedit /boot/grub/grub.cfg[/COLOR]

then I backed up the existing file by saving as: grub_backup.cfg

Then I very dangerously reopened the original grub.cfg and made my changes and saved over the original grub.cfg.   I know this is not recommended, but I tend to live on the edge!

Now my menu looks like this:

[COLOR="Green"]1) Windows XP
2) Ubuntu Studio
3) Ubuntu LTS
    Ubuntu (recovery)
    Memory test 86+
    Memory test (memtest86+, SC 115200)[/COLOR]

In order to get Window XP first as the default was last on the list, I cut and pasted the entire section that was automatically written when I installed Ubuntu LTS, see below.

Thanks again for your help, The only thing I would do different is to have a sub menu for the recovery and tests.  This is what I had on my old setup, but not sure how to do this, guess I better get reading this [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)



(((((  I did not paste the stuff that is irrelevant that was not changed  )))))

I did not change anything but what is in Red, other than moving the whole block at ### BEGIN /etc/grub.d/30 os-prober ### before the grub.d/10 so that XP was my first menu option, I wrote the 1), 2) etc.  Hope that makes sense.


### BEGIN /etc/grub.d/30_os-prober ###
menuentry [COLOR="Red"]"1) Windows XP"[/COLOR] {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e28b61a28b5e14f
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry [COLOR="Red"]"2) Ubuntu Studio"[/COLOR] {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f2c9a6bb-6047-4bca-952a-cdd40f250711
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711 ro ROOTFLAGS=syncio quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}

### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/10_linux ###
menuentry [COLOR="Red"]'3) Ubuntu LTS'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set bfb59f4a-7adf-4790-8a73-a1dbdb61be3c
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=bfb59f4a-7adf-4790-8a73-a1dbdb61be3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry [COLOR="Red"]'      Ubuntu (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set bfb59f4a-7adf-4790-8a73-a1dbdb61be3c
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=bfb59f4a-7adf-4790-8a73-a1dbdb61be3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry [COLOR="Red"]"      Memory test (memtest86+)"[/COLOR] {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set bfb59f4a-7adf-4790-8a73-a1dbdb61be3c
	linux16	/boot/memtest86+.bin
}
menuentry [COLOR="Red"]"      Memory test (memtest86+, SC 115200)"[/COLOR] {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set bfb59f4a-7adf-4790-8a73-a1dbdb61be3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

---

