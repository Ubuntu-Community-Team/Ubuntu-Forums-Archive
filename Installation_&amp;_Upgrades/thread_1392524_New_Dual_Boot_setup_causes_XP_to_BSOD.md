---
title: "New Dual Boot setup causes XP to BSOD"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Giltrap on 2010-01-28
I have recently installed Ubuntu 9.10 into some free space I made with GParted, and now every time I try to boot into my Windows XP it gives me a lovely BSOD.

The error code I get on the BSOD is 0x24 which I've found means it's something to do with the NTFS filesystem or something like that, although it doesn't appear to be completely broken as I can still access my files from Ubuntu.

I know this isn't an XP board, but meierfra. said they'd take a look if I posted the RESULT.txt of the Boot Info Script in a new thread, so here it is.

> ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc88bc88b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   120,583,889   120,583,827   7 HPFS/NTFS
/dev/sda3         120,583,890   488,392,064   367,808,175   f W95 Ext d (LBA)
/dev/sda5         173,759,103   435,955,904   262,196,802   7 HPFS/NTFS
/dev/sda6         435,955,968   488,392,064    52,436,097   7 HPFS/NTFS
/dev/sda7         120,584,016   171,461,744    50,877,729  83 Linux
/dev/sda8         171,461,808   173,759,039     2,297,232  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00094214

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    52,436,159    52,436,097   7 HPFS/NTFS
/dev/sdb2         314,761,545   976,768,064   662,006,520   7 HPFS/NTFS
/dev/sdb3          52,436,160   314,761,544   262,325,385   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AAE4BF8DE4BF5A71                       ntfs       Int OS                        
/dev/sda5        C0C4CF46C4CF3D82                       ntfs       Int My Docs                   
/dev/sda6        383C87B43C876BA6                       ntfs       Int Ableton Library           
/dev/sda7        a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07   ext4                                     
/dev/sda8        3b417f89-890f-43e5-b9a9-60f6519dd4c0   swap                                     
/dev/sdb1        6BC2F903460522CF                       ntfs       Ext AbLibBac                  
/dev/sdb2        6D434E0978841AFB                       ntfs       Ext Dumpzone                  
/dev/sdb3        402493FA2493F0E0                       ntfs       Ext MyDocBac                  

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

/dev/sda7        /                ext4       (rw,errors=remount-ro)
/dev/sda5        /media/Int       Docs       type
/home/giltrap/.Private /home/giltrap    ecryptfs   (ecryptfs_sig=812e31a376a5cb9f,ecryptfs_fnek_sig=71593dc5c9ee86aa,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
/dev/sdb3        /media/Ext       type       fuseblk
/dev/sdb1        /media/Ext       type       fuseblk
/dev/sdb2        /media/Ext       type       fuseblk


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="General Use - XP MCE" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft WinXP (on Volume 1)" /noexecute=optin /fastdetect

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aae4bf8de4bf5a71
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

proc /proc proc defaults 0 0
UUID=a1f7c72f-4fd5-4fb1-85bf-5569bf9a2f07 / ext4 errors=remount-ro 0 1
UUID=3b417f89-890f-43e5-b9a9-60f6519dd4c0 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/Int\040My\040Docs ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


  61.7GB: boot/grub/core.img
  61.7GB: boot/grub/grub.cfg
  61.7GB: boot/initrd.img-2.6.31-14-generic
  61.7GB: boot/initrd.img-2.6.31-17-generic
  61.7GB: boot/vmlinuz-2.6.31-14-generic
  61.7GB: boot/vmlinuz-2.6.31-17-generic
  61.7GB: initrd.img
  61.7GB: initrd.img.old
  61.7GB: vmlinuz
  61.7GB: vmlinuz.old

---

### Post by dstew on 2010-01-28
If by BSOD you refer to the blue screen with hexadecimal codes on it, that happened to me recently after an installation. The fix was to go into BIOS and change the RAID setting. I don't recall exactly what I changed it to, but that was the problem. When I get home I can look at my BIOS and tell you what I did. Apparently, the dmraid program (or something) on the Ubuntu installation did something to the BIOS RAID settings. I don't have the RAID implemented, but the BIOS of my computer has some RAID extensions.

---

### Post by Jonasan Cope on 2010-01-28
I think i'm having almost exactly the same problem right now as well. have just posted a thread describing my problem (next one after yours). how did you get the RESULT.txt of the Boot Info Script? - looks like it might be useful to get and compare.
 cheers

---

### Post by darkod on 2010-01-28
> **Jonasan Cope said:**
> I think i'm having almost exactly the same problem right now as well. have just posted a thread describing my problem (next one after yours). how did you get the RESULT.txt of the Boot Info Script? - looks like it might be useful to get and compare.
 cheers

Look here in post #2 for instructions:
[http://ubuntuforums.org/showthread.php?t=1392226](http://ubuntuforums.org/showthread.php?t=1392226)

The script is also in my signature.

---

### Post by darkod on 2010-01-28
> **dstew said:**
> If by BSOD you refer to the blue screen with hexadecimal codes on it, that happened to me recently after an installation. The fix was to go into BIOS and change the RAID setting. I don't recall exactly what I changed it to, but that was the problem. When I get home I can look at my BIOS and tell you what I did. Apparently, the dmraid program (or something) on the Ubuntu installation did something to the BIOS RAID settings. I don't have the RAID implemented, but the BIOS of my computer has some RAID extensions.

If I'm not wrong, you need to set the SATA type to IDE, or Native IDE. I think other options are RAID (if using it, this setting if enabled can create lots of issues with Karmic even if you only have single hdd), or AHCI.
Ubuntu can handle AHCI but I'm not so sure about XP.

In any case, this is very strange. Did you reboot XP few times after resizing with Gparted? You always need to boot windows few times after resizing (even if it's done with windows disk management in vista and 7) to make sure it's happy after the resize. And that is especially true for XP.

Not sure if the XP bootloader repair process would help you from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And that will destroy grub2 on the MBR so you have to reinstall grub2 to the MBR also after that, the instructions are on the same link. Just make sure for grub2 you are using instructions for 9.10 and 9.10 cd.

---

### Post by meierfra. on 2010-01-28
It could be the "RAID" setting in BIOS, so go ahead and  try the suggestion from dstew. If you make any changes in the  bios, make sure to write down the original setting, so that you can undo your changes if necessary.

Sometimes if you resize a Windows XP partition, your run in problem with the "Mounted_Devices" Registry in XP. Since this registry will regenerate it self, I suggest to delete it:

Boot from your Windox XP CD. Press "R".  
At the next screen,  press the number for your operating System, (should be "1")
Unless you set a administrative password, just press "enter" then asked for a password. Type

```
 regedit 
```
to open the Registry Editor.

Select "HKey_Local_Maschine" in the left panel.
Select  "Load Hive" in the "File" menu.
In the Pop Up Box, Select "My Computer". Take note of the drive letter of your  XP partition. Should be "C:".
Navigate to   \Windows\System32\config folder in your XP  Partition.
Select the file "system" and click open. 
In the new box type "MyHive" and hit enter.
Click on the "+"  sign next to "HKey_Local_Maschine"". 
You should now have an entry  named "MyHive in the left panel.
Click on the "+" sign next to "MyHive".
You should now have an entry  named "Mounted_Devices in the left panel.
RightClick "Mounted_Devices" and choose "Delete"
Select "MyHive" and choose "Unload Hive" in the "File" menu. 
Click on "yes" in the PopUP menu.
Choose "exit" in the "File" menu.

As long as you are booted into the Windows CD, I suggest to also run a file system check and run fixboot:

```
chkdsk /f C:
fixboot C:
```
but replace "C:" by the actual drive letter of your Windows XP partition.

I would not run "fixmbr". There is nothing wrong with  your MBR and you will have to reinstall grub, which will undo all the changes made by "fixmbr"

---

### Post by dstew on 2010-01-28
Reading the post from darkod, I remember that it was the BIOS AHCI setting.

---

### Post by Jonasan Cope on 2010-01-28
hey giltrap,
 
dont know if this will help in this case but if your using a laptop with a recovery parition preinstalled, try disabling the Hidden Protected Area in the BIOS (in my case the IBM PreDesktop Area). Just did this on mine and solved a very similar problem.
 
[http://ubuntuforums.org/showthread.php?t=1392564](http://ubuntuforums.org/showthread.php?t=1392564)
 
best of luck

---

### Post by oldfred on 2010-01-28
I do not know if meierfra. (or someone else) recently created another page on sourceforge or I just ran across it. This includes instructions as well as the same link to the previously posted  boot_info_script:

Follow these instruction to run the boot info script and post the RESULTS.txt.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by meierfra. on 2010-01-28
> I do not know if meierfra. (or someone else) recently created another page on sourceforge or I just ran across it.Couple of weeks ago I edited  the Web page associated to the Boot Info Script. It used to be  the default sourceforge page, but now it actually contains some useful information.
 > This includes instructions as well as the same link to the previously posted boot_info_script:

Follow these instruction to run the boot info script and post the RESULTS.txt.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

???? Both Giltrap and Jonasan Cope already posted the RESULTS.txt (Jonasan Cope in his new thread, which is already solved)

---

### Post by Giltrap on 2010-01-29
Hey again, thanks for all the quick replies. I've had a lot to do. :D

-----

> **dstew said:**
> If by BSOD you refer to the blue screen with hexadecimal codes on it, that happened to me recently after an installation. The fix was to go into BIOS and change the RAID setting.
and
> **darkod said:**
> If I'm not wrong, you need to set the SATA type to IDE, or Native IDE. I think other options are RAID (if using it, this setting if enabled can create lots of issues with Karmic even if you only have single hdd), or AHCI.
Ubuntu can handle AHCI but I'm not so sure about XP.

I had a look in the BIOS and I couldn't find a RAID type setting like the ones you've described. I pretty much looked at everything. The only one I found was one to turn RAID on or off in an "Advanced > IDE", which I ultimately left off. I switched it on in the menu to see if anything else came up, but it didn't so I didn't save any changes to the BIOS.

-----

> **darkod said:**
> Did you reboot XP few times after resizing with Gparted?

Not sure if the XP bootloader repair process would help you from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I don't think I did, I think I was so set on getting Ubuntu in and working that I just went straight to installing that. Must have assumed it'd be happy with it because every time I've added in a documents partition it's ran it's checks and was fine with it. I guess that wasn't such a bright move on my part.

Also, I had a look at the restoring of the XP bootloader, and it depended on the "Press R" aspect on the repair or recover section, which doesn't work. (more details below)

-----

> **meierfra. said:**
> Sometimes if you resize a Windows XP partition, your run in problem with the "Mounted_Devices" Registry in XP. Since this registry will regenerate it self, I suggest to delete it:

Boot from your Windox XP CD. Press "R". 

I've been through XP repair instructions involving the CD and I appear to not have any option saying "R" is ever an option.

The first screen I get says this (paraphrased because the laptop I'm using to write the information on has a horrible keyboard):

> 
Windows XP professional setup
-----------------------------

Following list shows existing partitions and unpartitioned space

Use up and down to navigate

*To set up XP on the selected item, press ENTER
* To create a partition on the unpartitioned space, press C
* To delete the selected partition, press D

----
**(First disk listed is my external HDD. The names of the partitions are all showing)**

238473 MB Disk 0 at Id 0 on bus 0 on atapi (MBR)

C: Partition 1 (Unknown) 58879 MB <58878 MB free>
**(I installed XP on the C partition, but it's doesn't seem to be recognised here. It also looks about the same size if I remember correctly.)**
K: Partition 4 (Unknown) 24843 MB <24842 MB free>
L: Partition 5 (Unknown) 1122 MB <1121 MB free>
**(E and F, partitions 2 and 3, are named and NTFS)**

This makes me think that something is up with the filesystem. I can access my install partition in Ubuntu, but Windows doesn't want to know.

I suspect some form of repair needs to be done. Currently I have GParted (sort of old), Parted Magic (new, and has GParted anyway) and Ultimate Boot CD (new, but I haven't a clue how to use it)

-----

Thanks again for the speedy responses. :D

---

### Post by darkod on 2010-01-29
If it's only the partition table not being correct, maybe TestDisk can help but I have no clue how to use it for that. You'll have to wait for meierfra for those instructions.
But I've seen it mentioned that testdisk can repair wrong partition table.

---

### Post by meierfra. on 2010-01-29
> C: Partition 1 (Unknown) 58879 MB <58878 MB free>
I don't think deleting  the "Mounted Devices" registry will fix this. So running the "chkdsk" will be  your best option.  You might be able to trigger a file system check from Ubuntu:

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```

ntfsfix is able to repair some minor errors and  it will  flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk". (Although I'm not sure that you get far enough into the XP boot process for this do happen)

You can also run "chkdsk" from the UBCD, but I have never done that and don't have time right now to figure out exactly how to do that. But I'll look into into tonight.

You should also  look at Jonasan Cope's last post. Any chance you have a area on your hard drive hidden by the bios?

---

### Post by Giltrap on 2010-01-29
I did the NTFS fix thing but it didn't get into "chkdsk". From what I remember from when I've repartitioned before "chkdsk" doesn't happen until after the the black loading screen with the windows XP logo goes.

The UBCD I have ([http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)) doesn't have "chkdsk" so I guess you were referring to UBCD4Win which does. Unfortunately I haven't got a CD with that on, so I'm going to make one later. It looks like the UBCD4Win builder only works on Windows PC's, so I'm waiting for my dad to bring his laptop up in a few hours.

Finally, I checked out the Jonasan Cope's last post. It is unlikely that I would have a hidden area on my hard drive as I built this computer myself and don't remember ever doing such a thing. Besides every GB seems accounted for from the partition sizes I've seen while using Ubuntu/GParted etc.

---

### Post by meierfra. on 2010-01-29
I suggest to download a Vista Repair CD from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). It has "chkdsk"  and "regedit" and I know how to use it:


Boot from Vista CD.

At the first screen select your favorite language.
Since you don't have Vista installed, the CD might not  let you go the command line directly. So we'll take to back road:
At the second screen choose "Install Now".
At the  license agreement  screen press "SHIFT+F10". 
This should open the command line.
Type 

```
diskpart
list volume
``` 
and take note of the drive letters for your XP partition.   In the following I  assume that the XP partition is on "C:"  But you have to replace "C:" by the actual drive letter.

Type 

```
exit
chkdsk /r C:
```

If "chdskk" fixed some errors, run it again  until its does not find any errors anymore.

If "chkdsk" did not solve your problem,  type "regedit" in the Vista CD command line and follow my earlier instruction to delete the "Mounted_Device" registry. 

But **DO NOT** run fixboot from the Vista CD.  That will install a Vista type boot sector which is incompatible with XP.

---

### Post by Giltrap on 2010-01-29
Hey,

I made the disk, and ran chkdsk twice.
XP has worked and started up, Ubuntu started up, and XP has started successfully again. I didn't have to use regedit at all.

Thanks! Now I can get back to using Ableton Live and making tunes. Awesome!

---

### Post by meierfra. on 2010-01-29
> I didn't have to use regedit at all.
The "regedit" procedure usually is only necessay when one move the start point of a Windows XP partition. So "chkdsk" should have been my first suggestion. 


> XP has started successfully again
Great. Getting XP  to boot after resizing can be tricky. So I'm glad that "chkdsk" solved your problem.

---

### Post by beyercj on 2010-07-16
I had an almost identical problem trying to dual boot Windows XP Home edition and Ubuntu Lucid Linux. I checked my hard drives in Ubuntu and they are ok. Windows XP does not recognise my hard disk anymore. When I tried to list volumes with diskpart, I only saw my empty USB drives and the Vista repair disk but not the hard drive, neither with the Windows XP installation disk nor with the Vista Repair Disk as described in this threat. I also deleted mounted devices in regedit but no luck.

Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

Any more ideas?

---

