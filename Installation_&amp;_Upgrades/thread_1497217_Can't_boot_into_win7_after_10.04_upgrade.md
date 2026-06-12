---
title: "Can't boot into win7 after 10.04 upgrade"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by 6SPEED on 2010-05-30
I had Ubuntu 9.04 and Win7 dual booted for a while with really any problems. I upgraded to 10.04 2 days ago and now can't get into Win7. During upgrade when the install asked me what drive to pick to install grub to, no matter what drive or partion I picked it would always say install failed do you want to continue. So I eventually just continued. After Install 10.04 boots fine but when I select Win7 it just reloads grub right away. I restarted with my super grub cd and choose detect other OS and win7 isn't listed, just Ubuntu, memtest, and 3 "other OS". I tried using my Win7 disk to repair but it told me that the version of repair tools wouldn't work with that version of windows even though its the same disc I used to install windows. I installed testdisk but didn't have the "backupBS" option at the end like [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") says.

Here is my boot info script

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 477589134 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 477584526 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,307,214   477,307,152   7 HPFS/NTFS
/dev/sda2         606,421,620   625,137,344    18,715,725   7 HPFS/NTFS
/dev/sda3         477,307,215   606,421,619   129,114,405   5 Extended
/dev/sda5         477,307,278   601,055,909   123,748,632  83 Linux
/dev/sda6         601,055,973   606,421,619     5,365,647  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CAC32366C57A10                       ntfs       Win7Ultimate                  
/dev/sda2        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        115d9967-d8a5-42af-9f33-d60f3d1cda1f   ext4                                     
/dev/sda6        d4fe7f0a-893c-47b4-b5f4-d6cf70105d83   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       M SPEED                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CAFB55C0D30FD0                       ntfs       M SPEED2                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=speed)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="6"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01cac32366c57a10
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d4fe7f0a-893c-47b4-b5f4-d6cf70105d83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 244.5GB: boot/grub/core.img
 262.4GB: boot/grub/grub.cfg
 245.8GB: boot/initrd.img-2.6.31-21-generic
 245.7GB: boot/initrd.img-2.6.32-22-generic
 245.6GB: boot/vmlinuz-2.6.31-21-generic
 260.2GB: boot/vmlinuz-2.6.32-22-generic
 245.7GB: initrd.img
 245.8GB: initrd.img.old
 260.2GB: vmlinuz
 245.6GB: vmlinuz.old
```

---

### Post by darkod on 2010-05-30
Even though you didn't have the BackupBS did it show something like RebuildBS? That fix is the only I know for deleting grub2 from your windows partition(s).

And you should have never told it to install on a partition by the way.

On top of that, even your win7 dvd is saying it can't repair it which is ridiculous (I have also had the message about the version not being the same when using the same dvd). I don't have a clue what is that all about.

---

### Post by 6SPEED on 2010-05-30
I did have the option for rebuildBS, should I try that?

---

### Post by darkod on 2010-05-30
> **6SPEED said:**
> I did have the option for rebuildBS, should I try that?

Personally I never needed to use that fix. But I don't see how it can make things worse.

---

### Post by 6SPEED on 2010-05-30
I tried rebuildbs and then it gave me the option to write so I did that. Restarted and change still just restarts grub right when I click win7.

---

### Post by oldfred on 2010-05-30
I have also seen where the /grldr can cause confusion. It is from grub4dos and it you are not using  that you should delete that. 

If testdisk does not rebuildBS then retry the windows repairs with the grub4dos file deleted.

---

### Post by 6SPEED on 2010-05-30
> **oldfred said:**
> I have also seen where the /grldr can cause confusion. It is from grub4dos and it you are not using  that you should delete that. 

If testdisk does not rebuildBS then retry the windows repairs with the grub4dos file deleted.

not sure what that is, or if I use it or how to delete it. Sorry I'm still new to grub and Ubuntu and dual booting anything.

---

### Post by oldfred on 2010-05-30
From Ubuntu or a liveCD you should be able to browse your windows system. From Ubuntu it may ask for a password. You should then be able to see the /grldr not sure if it is a file or a partition with files in it.

---

### Post by 6SPEED on 2010-05-31
I found the grldr file and deleted it. tried rebuildBS again and also tried my Win7 cd again. no changes. I do have a repair MFT, haven't done it yet, not sure what it does. Do you guys need me to post another boot info script after doing all these different things? Don't know if it would have affect.

---

### Post by darkod on 2010-05-31
I don't think the script will show much difference now (except /grldr being gone).

But you could try downloading a win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Since your win7 dvd says it doesn't even want to try and fix the boot files, I guess trying the generic win7 repair cd can't hurt. Just select the correct image for 32bit or 64bit version.

This is only a repair cd, not a full install dvd and that's why it can be legally distributed like this. See if that helps repairing the boot sector.

---

### Post by 6SPEED on 2010-05-31
> **darkod said:**
> I don't think the script will show much difference now (except /grldr being gone).

But you could try downloading a win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Since your win7 dvd says it doesn't even want to try and fix the boot files, I guess trying the generic win7 repair cd can't hurt. Just select the correct image for 32bit or 64bit version.

This is only a repair cd, not a full install dvd and that's why it can be legally distributed like this. See if that helps repairing the boot sector.
Thanks for the link I was just thinking of looking for something like this. I'll try this when I get home.(on my Iphone right now)

---

### Post by 6SPEED on 2010-05-31
I checked it on my phone and seen it's a torrent file. I've never done torrents on Ubuntu. Is there a Utorrent program for linux? I'm also assuming its a ISO file what program do you recommend to mount and burn it, I use powerISO on Win7, I just don't have a program on Ubuntu.

---

### Post by darkod on 2010-05-31
The default torrent client is Transmission, I think it's in Applications-Internet.

As for burning, there is also software in Applications-Accessories or close by. Have never tried it though.

Usually even right-click on ISO would give you option to burn a disc from it, just make sure it burning the disc from the ISO, not simply the ISO file onto the disc as a file. :)

---

### Post by 6SPEED on 2010-05-31
Oh ok. Thats very nice, I didn't know Ubuntu had these kinds of options built into it.

---

### Post by NWJefferies on 2010-05-31
I'm new to this and I know this is slightly off-topic, but it came up first in my search.  We built a computer in high school class and installed UBUNTU 9.04.  I want to install win7 now, but can't find how to partition the disk.  I tried using the 9.04 disk, but Gnome partition editor does not load.  I made a  bootable thumb drive, but that didn't seem to work either.  Can someone direct me to how to do this?

---

### Post by 6SPEED on 2010-05-31
ok, I downloaded burnt the Win7 repair disc. It atleast worked but it said it could not find and startup errors. Is there anything I can do through the command prompt to rebuild the boot files or whatever to get it to work again?

---

### Post by darkod on 2010-05-31
> **NWJefferies said:**
> I'm new to this and I know this is slightly off-topic, but it came up first in my search.  We built a computer in high school class and installed UBUNTU 9.04.  I want to install win7 now, but can't find how to partition the disk.  I tried using the 9.04 disk, but Gnome partition editor does not load.  I made a  bootable thumb drive, but that didn't seem to work either.  Can someone direct me to how to do this?

That question is for a new thread and it's not related to this. Can you just open a new thread?

Also, give more info like are you trying to add win7 or you want to install win7 on the whole disk? However, Gparted should have no problems loading and working.

---

### Post by darkod on 2010-05-31
> **6SPEED said:**
> ok, I downloaded burnt the Win7 repair disc. It atleast worked but it said it could not find and startup errors. Is there anything I can do through the command prompt to rebuild the boot files or whatever to get it to work again?

Look here at the instructions for vista/7, how to do it from command line, and use only /fixboot command, you shouldn't need the /fixmbr (and that will delete grub2 from the MBR):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Lets see how it goes from command like.

---

### Post by bigseb on 2010-05-31
If I under stand your problem correctly then should be quite easy to remedy. I would first repair the Windows bootloader, this will kill grub so you then need to reinstall grub.

To fix Windows bootloader: Start Command Prompt using your W7 disc and type:

     bootrec /fixmbr  (press enter)

     bootrec/fixboot  (press enter)

(link: [http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html?ltr=D](http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html?ltr=D))

Then you need to reinstall grub. Start Ubuntu from Live CD, open terminal. Then type:

     sudo mount /dev/sdXY /mnt

     sudo grub-install --root-directory=/mnt/ /dev/sdX

Then simply reboot and update your grub menu. Type

     sudo update-grub

[FONT=Verdana](link: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202))

I hope this helps...
[/FONT]

---

### Post by 6SPEED on 2010-05-31
> **darkod said:**
> Look here at the instructions for vista/7, how to do it from command line, and use only /fixboot command, you shouldn't need the /fixmbr (and that will delete grub2 from the MBR):
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Lets see how it goes from command like.

Well now when I try to boot into Win7 it doesn't just go back to grub. I just get a blinking dash in the top right corner that just blinks. I left it go for about 5 mins, but my HDD activity light on my PC isn't even blinking so I don't think it was trying to do anything. I'm going to go cook dinner now but when i'm done I think i'll try bigseb fix. Thanks to everyone that has helped me through this so far, I really appreciate it. I'll let everyone know how it goes.

---

### Post by darkod on 2010-05-31
The blinking cursor is still a sign grbu2 is there on the windows partition. Running the script again will show it again for you.

One additional thing you could try is the testdisk process again. Who knows, after running /fixboot it might actually be able to repair the boot sector now.

Apart from that, I am really running out of ideas. You've got one resilient PC it seems. It took everything we threw at it. :)

---

### Post by 6SPEED on 2010-05-31
I ran testdisk again and the option to backupBS was there, so I did, and it listed Win7 in the list when I updated grub. But now it just does what it did before when I choose Win7, just restarts grub again and again.

---

### Post by EnzoA on 2010-05-31
Dude I had the same problem. 
Luckily I installed Ubuntu 9.04 on a separate hard drive. 
The other hard drive I had partitioned: one for all my files, one for Win XP.
The only mistake I made, was not unplugging the SATA cables to the Xp hard drive when I was upgrading to 10.04. 
same thing: 
grub........
I was like: WTH is grub:confused:!!! (noob). thank god my files on the other partition were untouched[-o<.
so I just cut my losses and installed Xp all over again. lost some good apps. but my files are safe.

---

### Post by oldfred on 2010-05-31
If you rerun the boot script does it still show grub in the PBR (partion boot sector) of the windows.

If it did get grub out then maybe windows will see it and now repair it. 

I know we are grasping at straws. But there are not a lot of choices.

---

### Post by darkod on 2010-05-31
> **EnzoA said:**
> 
The only mistake I made, was not unplugging the SATA cables to the Xp hard drive when I was upgrading to 10.04. 


Just to be correct here, the only mistake you made was selecting all disks and all partitions when asked where to install grub2. Agree, the message might be more user-friendly, and also, the partitions not to be offered as choice, but on the other hand plenty of people would then say: wasn't linux about freedom to do as you wish? Why have they limited my ability to select partitions too? :)

The basic rule that we can't highlight enough: a bootloader goes to the MBR of the disk in 99% of cases!!! Only in special situations do you need it on a partition and if that is the case you would probably know what exactly to do.

So, when asked where to install grub, NEVER EVER EVER EVER select a partition!!!!!!!!!

This is not intended for any of you, but for anyone else reading it. Unfortunately, usually people visit here only after they have the problem. :)

---

### Post by pr0t3g3 on 2010-05-31
**AHA!**  I thought so... I can't even boot back to my old windows installation... I smell ubuntu treachery ... or maybe I'm being paranoid o.o.....On a more serious note, I really can't seem to boot any other os on my laptop since I booted ubuntu 10.04 ... which is a bit suspicious; then again it's probably just an error on my part.

---

### Post by Shenandoah on 2010-06-01
All,

I am having the exact same problem as the orignal poster.  I have a dual boot netbook with Windows 7 and Xubuntu.  When I upgraed from 9.04 to 10.04 through Synaptic, I could no longer boot Windows 7.  

I did check sda1 (windows 7) and sda5 (xubuntu) in the grub partition check box window.  It was unclear as what to do, so I selected the two partitions where my operating systems were.  

I am going to try to run the Windows 7 repair disc and see if that fixes it.  Thanks.

Shenandoah

---

### Post by darkod on 2010-06-01
> **Shenandoah said:**
> All,

I am having the exact same problem as the orignal poster.  I have a dual boot netbook with Windows 7 and Xubuntu.  When I upgraed from 9.04 to 10.04 through Synaptic, I could no longer boot Windows 7.  

I did check sda1 (windows 7) and sda5 (xubuntu) in the grub partition check box window.  It was unclear as what to do, so I selected the two partitions where my operating systems were.  

I am going to try to run the Windows 7 repair disc and see if that fixes it.  Thanks.

Shenandoah

Don't hurry with the win7 repair disc. This OP has a particular problem that the fix for this situation didn't work.

The first thing to try is to use this procedure to fix the boot sector of your partition /dev/sda1:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to apply it to partition #1 on disk /dev/sda. No need to fix /dev/sda5, booting ubuntu is not hit by this problem.

---

### Post by kansasnoob on 2010-06-01
I'm totally aware of the problem and I'm trying like the devil to get this behavior changed. I reported it as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

I was bold enough to subscribe one of the grub 2 devs:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17)

Yesterday I went another step into "no-no" land by saying this at the Ayatana project:

> Subject: [Ayatana] Is this the worst (or most ignored) Ubuntu bug ever?
To: "ayatana" <ayatana@lists.launchpad.net>
Cc: [email]mark.shuttleworth@canonical.com[/email]
Date: Monday, May 31, 2010, 3:19 PM

In order to cut to the chase look here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

There are many internal links there to explore!

The problem is simple! At some point towards the end of the Lucid development cycle we changed from offering just "drive MBR's" for grub install points to "ALL DEVICES", yet we said:

"The grub-pc package is being upgraded. This menu allows you to select which devices .....................................", and  then:

"If  .............. unsure .............. install to all of them". Some fairly good screenshots linked to here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15)

This behavior has been catastrophic for noobs and anyone not paying close attention!

I was bold enough to subscribe Colin Watson here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17)

I would not "step outside of the ilnes" if I didn't feel I'd otherwise exhausted all other options. But, IMHO, this is a distro killer!

If there ever was a bug that deserved a lot of attention this is it!

Only one reply:

> this is the kind of bug i refer to as "dry developer humor":
These bugs seem to be saying:
"i'm already busy writing time consuming reliable code, so if you can't even know how to respond to this dialog screen, you don't deserve to use my application safely"

But I seem to be the only one to take this serious enough to go the extra mile! I feel like a one-legged man in a butt kicking contest!

---

### Post by darkod on 2010-06-01
@kansas

To add more salt to it, not sure if you saw my post on another thread. I have also seen a results.txt file where this grub2 to partitions thing happened with the user using only wubi.

There was no full ubuntu install. The user hit the Upgrade button in wubi, yet, all of the 'real' partitions AND mbr on the disk ended up with grub2.

Imagine using VB and your virtual system changing your real partitions... :(

---

### Post by kansasnoob on 2010-06-01
> **darkod said:**
> @kansas

To add more salt to it, not sure if you saw my post on another thread. I have also seen a results.txt file where this grub2 to partitions thing happened with the user using only wubi.

There was no full ubuntu install. The user hit the Upgrade button in wubi, yet, all of the 'real' partitions AND mbr on the disk ended up with grub2.

Imagine using VB and your virtual system changing your real partitions... :(

ARRRGH!

I hope I can get someone to address this soon but I'm beginning to have serious doubts.

---

### Post by wilee-nilee on 2010-06-01
> **darkod said:**
> @kansas

To add more salt to it, not sure if you saw my post on another thread. I have also seen a results.txt file where this grub2 to partitions thing happened with the user using only wubi.

There was no full ubuntu install. The user hit the Upgrade button in wubi, yet, all of the 'real' partitions AND mbr on the disk ended up with grub2.

Imagine using VB and your virtual system changing your real partitions... :(

I had wondered about this as some have seemed to get the full grub treatment without requesting it in the choose where to install gui. It is very hard to tell at times what has actually happened. As soon as somebody posts, the want to help brings out those that provide this worked for me advice without any knowledge via the script as to what; is where in the OS's

---

### Post by oldfred on 2010-06-01
Has anyone seen a win7 user with the 100MB boot/recovery partition get it working again. I have tried helping many users and the testdisk seems to work for XP & Vista but not the win7 with the separate boot partition.

I did see one thread where the user said he found a second /Boot interfering with /boot partition. I know we see that in the script if it has a grub file in it, but the boot script did not show it in this case.

It seems strange that they would delay the release of 10.04 to make sure users did not have to run sudo-update grub with windows as they did not want to look bad to windows users but they let a major bug in explanation of how to install that really corrupts windows continue.

---

### Post by darkod on 2010-06-01
> **oldfred said:**
> Has anyone seen a win7 user with the 100MB boot/recovery partition get it working again. I have tried helping many users and the testdisk seems to work for XP & Vista but not the win7 with the separate boot partition.


It works. [http://ubuntuforums.org/showthread.php?t=1497280](http://ubuntuforums.org/showthread.php?t=1497280)

But I can't make a rule why sometimes the fix doesn't help. :(

---

### Post by wilee-nilee on 2010-06-01
> **oldfred said:**
> Has anyone seen a win7 user with the 100MB boot/recovery partition get it working again. I have tried helping many users and the testdisk seems to work for XP & Vista but not the win7 with the separate boot partition.

I did see one thread where the user said he found a second /Boot interfering with /boot partition. I know we see that in the script if it has a grub file in it, but the boot script did not show it in this case.

It seems strange that they would delay the release of 10.04 to make sure users did not have to run sudo-update grub with windows as they did not want to look bad to windows users but they let a major bug in explanation of how to install that really corrupts windows continue.

The test disk option I think is kind of confusing for a new user of Ubuntu. When I have given advice it usually is to run the full bcd rebuild commands that you have provided, as reloading grub to the MBR is easy. I suspect that running the full command set will rebuild the 100 mb partition correctly, I am not sure though on this.

---

### Post by kansasnoob on 2010-06-01
> **oldfred said:**
> Has anyone seen a win7 user with the 100MB boot/recovery partition get it working again. I have tried helping many users and the testdisk seems to work for XP & Vista but not the win7 with the separate boot partition.

I did see one thread where the user said he found a second /Boot interfering with /boot partition. I know we see that in the script if it has a grub file in it, but the boot script did not show it in this case.

It seems strange that they would delay the release of 10.04 to make sure users did not have to run sudo-update grub with windows as they did not want to look bad to windows users but they let a major bug in explanation of how to install that really corrupts windows continue.

I've honestly not paid attention that specifically.

Have you tried to PM Meierfra?

Would you prefer I PM him?

I will, I just generally only PM someone as a last resort. And this really is something that needs to be fixed before it happens.

---

### Post by kansasnoob on 2010-06-01
> **wilee-nilee said:**
> The test disk option I think is kind of confusing for a new user of Ubuntu. When I have given advice it usually is to run the full bcd rebuild commands that you have provided, as reloading grub to the MBR is easy. I suspect that running the full command set will rebuild the 100 mb partition correctly, I am not sure though on this.

I would think that testdisk would actually be simpler to follow, but that's just me :)

Something else, for XP:

[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

For Win Vista or 7:

[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

The latter requires tweaking for grub 2 :)

Maybe it is time to bother Meierfra :confused:

---

### Post by wilee-nilee on 2010-06-01
> **kansasnoob said:**
> I would think that testdisk would actually be simpler to follow, but that's just me :)

Something else, for XP:

[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

For Win Vista or 7:

[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

The latter requires tweaking for grub 2 :)

Maybe it is time to bother Meierfra :confused:

I agree in that it is a great tool, and I'm just a onlooker to most of this, but it is a good tool because we understand what the terminal is showing, and know where and what the partition or partitions that need to be fixed are. Sometimes people get freaked out by their OS being messed up, personally I have everything saved off my computer so it is only a reinstall that is needed, which I haven't had to do for a long time. 

So if a person is looking around the forums and finding fixes that work for somebody else, and trying them rather then waiting for help from the trio here that really are who I would follow, a set of miss run commands can make things worse. Now we have the variable of the others that just start throwing the fixes that worked for them at a new user as well. 

So it becomes a convoluted mess of a inexperienced user, bad advice, and trying fixes that don't work. It is hard I think to sit down and take a deep breath and wait for legitimate help. Many users also don't just do a full backup of the important stuff, media....etc off of the computer, just for in the end having that stuff no matter what. This is also compounded by many MS users don't have a full install DVD for W7 or the OEM set, or the install cd for XP. So that in a worse case scenario a reinstall can just be done and the saved media is still okay on a external HD. Or the fix commands can be run from a disc that contains them.

Personally I take the road that a tech friend of mine uses when fixing peoples computers, as he has to charge them for the service, at a very fair rate comparably. If it takes longer to fix it, then pulling out the needed stuff is done a reinstall is then executed.

This doesn't apply to people though that have not had their ducks in a row by having a install discs, a backup of important data, and a basic understanding of the errors if made by the user.

I see a similar problem in the college I attend with professors giving information that they understand, but have forgotten that it took them a period of time to do so, and think that since they understand it why doesn't everybody else instantly.

Like I said though the 3 of you, you know who I'm referring to are the best daily source for learning and help, no doubt in my mind. There are others who stop by periodically, and others that will help if inclined, but may not want to work with a new user in general, as it can be a trying endeavor at best.

---

### Post by oldfred on 2010-06-01
I do not know if he would want to add that or not. If you look at his script he sets up many default paths for files related to booting and that is why the script finds a /boot/grub in a windows that interferes with /Boot. The bigger issue may be how is grub even writing a second /Boot with different capitalization into windows? Should this be another grub bug report? I have seen several cases.

I also have an issue and have seen several other users, but do not know if it is grub or the script. I have Lucid on sdc7 and its grub2 in sda (I boot Karmic thru sdc). I only have 3 partitions in sda and the script v55 reports partition 7 of the same drive. It does boot ok so grub is working but why is the drive not correct?

---

### Post by kansasnoob on 2010-06-01
> So it becomes a convoluted mess of a inexperienced user, bad advice, and trying fixes that don't work.

To some degree that happens no matter what :)

I'm always amazed at having to teach someone how to copy-n-paste :confused:

Seriously! You're trying a new OS and don't know how to copy-n-paste? That one always blows me away.

---

### Post by darkod on 2010-06-01
> **kansasnoob said:**
> 
Seriously! You're trying a new OS and don't know how to copy-n-paste? That one always blows me away.

There are many things someone should know before taking on installing a new OS. :) Lets not even go there...

---

### Post by wilee-nilee on 2010-06-01
> **kansasnoob said:**
> To some degree that happens no matter what :)

I'm always amazed at having to teach someone how to copy-n-paste :confused:

Seriously! You're trying a new OS and don't know how to copy-n-paste? That one always blows me away.

I suspect the people who can't do this either don't know how or have been burned by doing this. A command can look innocent and be chocked full of bad script that will take them down. On this forum though this is watched very carefully by the staff and the experienced users, so very little if ever gets on the forum.

I'm just glad to be able to watch the people who know what their doing and learn from it, and if possible get them set up with a posted script so it is easier to just get to the root of the problems. I'm not sure if, I don't get in the way though even if my intentions are good. :)

---

### Post by Shenandoah on 2010-06-03
Guys,

Just an update on my issues:  I finally got Windows 7 to boot from the grub menu.  I tried several different things suggested in this thread, but here is what finally worked:

From post 37 in this thread I did the manual repair for the bootloader.  When I did the bcdedit commands, I got a message saying element not found for all of them.  I did the next step (bootsect  /nt60  C: ), then launched xubuntu and did the sudo update-grub.  When I rebooted, the Windows 7 menu item launched Windows 7.  

Testdisk did not work for me.  I also tried the Windows 7 repair disk instead of the Windows 7 install disk.  The Windows 7 repair disk did not work.  

Thanks for the help and suggestions in this thread.  

Shenandoah

---

### Post by 6SPEED on 2010-06-04
Sorry i've been away from here, looooong work hours. I tried what Shenandoah tried I think from post 37, but when I try "copy E:\bootmgr C:\" I get "access denied". So I tried bootrec/fixmbr then bootrc/fixboot and then had to reinstall grub2 on my HDD and grub2 works again but it still won't boot Win7. I am willing to have to completely remove Ubuntu and grub to get my win7 back. I was planning on deleting Ubuntu anyways and reinstalling it on another HDD with a SATA switch and use on HDD for win7 only and the other for Ubuntu and another OS which I haven't decided on. There has gotta be a way to get win7 back without having to do a whole new install. Thanks everyone again for helping and giving me your time.

---

### Post by wilee-nilee on 2010-06-04
Post the boot script again since a lot of tweaks have been done and your willing to remove Ubuntu and use it in another way. The main thing now seems to be to get Windows working, and this should be done first, if Ubuntu is still booting. Removing Ubuntu will just leave you with a unbootable computer. Do you have access to a install DVD I think you will need one, although I think you have a recovery partition, but it can be a real trick to get it to overwrite everything, which I don't think you want at this point, but Windows working as it had.

A regular install DVD will reload the whole MS boot setup and is good to have in your toolset.

---

### Post by 6SPEED on 2010-06-04
I do have a install disk but when I tried to use the boot recovery option it said my Win7 disk to repair but it told me that the version of repair tools wouldn't work with that version of windows even though its the same disc I used to install windows. Also my recovery partition is from when I got my PC and it came with Vista, I just never deleted it, so I don't know if it will help since it's vista. I have a supergrub disk, Ubuntu 9.10 disk, Ubuntu 10.04 disk, Win7 install disk and a Win7 repair disk.



```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 477584526 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,307,214   477,307,152   7 HPFS/NTFS
/dev/sda2         606,421,620   625,137,344    18,715,725   7 HPFS/NTFS
/dev/sda3         477,307,215   606,421,619   129,114,405   5 Extended
/dev/sda5         477,307,278   601,055,909   123,748,632  83 Linux
/dev/sda6         601,055,973   606,421,619     5,365,647  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CAC32366C57A10                       ntfs       Win7Ultimate                  
/dev/sda2        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        115d9967-d8a5-42af-9f33-d60f3d1cda1f   ext4                                     
/dev/sda6        d4fe7f0a-893c-47b4-b5f4-d6cf70105d83   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        24483AB0483A809A                       ntfs       M SPEED                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01CAFB55C0D30FD0                       ntfs       M SPEED2                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="6"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 115d9967-d8a5-42af-9f33-d60f3d1cda1f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 01cac32366c57a10
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=115d9967-d8a5-42af-9f33-d60f3d1cda1f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d4fe7f0a-893c-47b4-b5f4-d6cf70105d83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 244.5GB: boot/grub/core.img
 247.6GB: boot/grub/grub.cfg
 245.8GB: boot/initrd.img-2.6.31-21-generic
 245.7GB: boot/initrd.img-2.6.32-22-generic
 245.6GB: boot/vmlinuz-2.6.31-21-generic
 260.2GB: boot/vmlinuz-2.6.32-22-generic
 245.7GB: initrd.img
 245.8GB: initrd.img.old
 260.2GB: vmlinuz
 245.6GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-06-04
I'm certainly not an expert at any of this stuff. But if it was me since you have a install disc I would back up whatever you want to save and wipe the whole HD with a fresh install of W7 so that you have the correct 100mb boot partition and a correct W7 main partition.

Like I said this is what I would do and isn't necessarily, what you might want. personally I just do a fresh install if the repairs take longer then reinstalling. Also if the install dvd could be run from a live W7 environment the fresh install would save the overwritten one in a old windows file. So if you can boot W7 with supergrub, then pop in the install dvd you would just delete the Vista recovery and overwrite the W7 that isn't booting correctly and have the old windows backup file. 

This set up would allow you to install Ubuntu in the same HD or another with ease of travel since you are already aware of where grub should go. There might be other fixes but the more convoluted it gets the harder it becomes to fix when needed.

I only suggest this option as it seems that everything has been thrown at the computer to fix it probably has been done, and I think the vista recovery and it's setup is the problem, as you can't just run the standard commands and reload MS in the MBR.

I would wait for the people who have been helping you as they are way more knowledgeable and really where the best advice is.

---

### Post by oldfred on 2010-06-04
The Vista recover partition in sda2 has not been repaired but if your system was Vista and now you are win7 it may not need repairing.

Did your windows boot when you did the fixmbr? If so I would expect grub to boot it.

Some more advanced windows repairs.
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by darkod on 2010-06-05
The results look fine now as long as win7 boot should be concerned. As oldfred says, grub2 is still on the recovery partition but you don't need it anyway.

So what exactly is happening now when you try to boot win7? Any particular error or message?

Ubuntu doesn't look to have anything to do with this at the moment. Even removing it will not help win7.

---

### Post by 6SPEED on 2010-06-05
When I try to boot win7, both from grub and also when grub was deleted, it just had a blinking dash in the top left corner and didn't do anything. But now I have another problem. Ubuntu won't connect to the Internet. Right when ubuntu loads the led on my router for port 1 which my pc is plugged into, turns off and ubuntu won't connect to the internet. I've never had to do any network stuff with ubuntu so I don't even know where to start. I know hardware is good because I can get on the net through my asus expressgate right when I boot up. I just don't know how upgrading ubuntu could cause so much destrution.

---

### Post by 6SPEED on 2010-06-06
Bump for any other ideas before I do a full format and reinstall.... 
Not really worried about the network thing, just want win7 to boot

---

### Post by Shenandoah on 2010-06-07
6speed,

Just checking back in. One thing I forgot to mention is I could not copy "E:\bootmgr to C:\".  What I did to get around this is boot into xubuntu, mount the partition that has Windows 7, and then copy the bootmgr from the DVD to the Windows 7 partition.  

I then booted the Windows 7 DVD and did the remaining steps.  Hope that helps.  


Eric

---

### Post by 6SPEED on 2010-06-07
Hey, thanks for the tip, I will try it out when I get home.

---

