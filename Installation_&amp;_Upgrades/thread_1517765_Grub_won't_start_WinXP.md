---
title: "Grub won't start WinXP"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by 50GreenDodge on 2010-06-25
Hi folks:  Been a little while.

Here's today's problem: I upgraded to Ubuntu 10.04 and hope to have it run alongside Win XP PRO, which it had for months.

Only, when I select WinXP in GRUB, nothing happens. Oh the screen goes dark for a few seconds, but then the GRUB screen reappears. Ubuntu 10.04 functions correctly.

here are the contents of what I assume is grub.cfg:

insmod ntfs
set root= '(hd0,2)'
search --no-floppy --fs-uuid --set 5684846e84845303
drive map -s (hd0) ${root}
chainloader +1

BTW, the WINDOWS partition is listed as on /dev/sda2)


What I need to know is how to make GRUB load WinXP.  Thanks guys.

Jack - Phoenix - [email]laeva65@gmail.com[/email]

---

### Post by wilee-nilee on 2010-06-25
Post the bootscript in my signature in code tags.

---

### Post by 50GreenDodge on 2010-06-25
> **wilee-nilee said:**
> Post the bootscript in my signature in code tags.
bootscript  by meierfra
dweezilzappaworld```
insmod ntfs
set root= '(hd0,2)'
search --no-floppy --fs-uuid --set 5684846e84845303
drive map -s (hd0) ${root}
chainloader +1
```

Is this correct or did I do something dumb?

---

### Post by oldfred on 2010-06-25
A little too litteral. It is a link.

Same link:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by wilee-nilee on 2010-06-25
> **oldfred said:**
> A little too litteral. It is a link.

Same link:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

he he been there lol.
oldfred is correct here.

---

### Post by 50GreenDodge on 2010-06-26
1st I dl'ed from the link on the page you sent, and saved 'boot_info_script055.sh' to the 'home/greendodge50' directory.

then I typed 'sudo bash ~home/greendodge50/boot_info_script*.sh' and pressed <Enter.>

I also tried with '055' instead of '*.' All I got was 'no such file or directory.'

Can you tell me what I'm screwing up?  All I want to do is use 'grub' to start WinXP Pro on my Thinkpad alongside Ubuntu 10,04

Thank you very much for all your time.

Jack Lavelle - Phoenix

---

### Post by darkod on 2010-06-26
> **50GreenDodge said:**
> 1st I dl'ed from the link on the page you sent, and saved 'boot_info_script055.sh' to the 'home/greendodge50' directory.

then I typed 'sudo bash ~home/greendodge50/boot_info_script*.sh' and pressed <Enter.>

I also tried with '055' instead of '*.' All I got was 'no such file or directory.'

Can you tell me what I'm screwing up?  All I want to do is use 'grub' to start WinXP Pro on my Thinkpad alongside Ubuntu 10,04

Thank you very much for all your time.

Jack Lavelle - Phoenix

The ~ sign replaces your home folder, in other words /home/username. If you put the script in your home folder (not in any subfolder in it), you execute with just:

sudo bash ~/boot_info_script*.sh

The results file will be in the same folder as the script.

---

### Post by oldfred on 2010-06-26
The instructions are for liveCD which used to at least default to desktop for downloads. I think now both liveCD and your working Ubuntu default to ~/Downloads.

So to run it 
 sudo bash ~/Downloads/boot_info_script*.sh 

Or you can copy it to your Desktop and run from there.

Another way is to change to that directory and run from there.

cd Downloads
sudo bash boot_info_script055.sh

Once you have typed boot_ you can hit tab and it will complete the line.

---

### Post by presence1960 on 2010-06-26
If you can't get the command to work just move the boot info script file to desktop and open terminal and run ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by 50GreenDodge on 2010-06-27
Well, after all the ways I could do it wrong, I guess I did it right. Finally.

Here is my RESULTS.TXT:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 271167 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 271167 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 271167 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 271167 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   269,249,399   269,249,337  83 Linux
/dev/sda2    *    269,256,960   300,494,879    31,237,920   7 HPFS/NTFS
/dev/sda3         300,495,825   312,576,704    12,080,880   5 Extended
/dev/sda5         300,495,888   312,576,704    12,080,817  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 14.4 GB, 14386462720 bytes
255 heads, 32 sectors/track, 3443 cylinders, total 28098560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    28,098,559    28,098,528   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        de03282a-27f6-4f09-8986-f185fe2c6aac   ext4       Ubuntu                        
/dev/sda2        5684846E84845303                       ntfs       (C:)                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        11b26c3c-8447-4a27-94a6-681a0a47c667   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D1C7-4ECB                              vfat       PublicZone                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PublicZone        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="0"
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=de03282a-27f6-4f09-8986-f185fe2c6aac ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=de03282a-27f6-4f09-8986-f185fe2c6aac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=de03282a-27f6-4f09-8986-f185fe2c6aac ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=de03282a-27f6-4f09-8986-f185fe2c6aac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set de03282a-27f6-4f09-8986-f185fe2c6aac
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5684846e84845303
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=de03282a-27f6-4f09-8986-f185fe2c6aac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=11b26c3c-8447-4a27-94a6-681a0a47c667 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   4.0GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.31-21-generic
   1.2GB: boot/initrd.img-2.6.32-22-generic
   1.3GB: boot/vmlinuz-2.6.31-21-generic
   1.2GB: boot/vmlinuz-2.6.32-22-generic
   1.2GB: initrd.img
   1.2GB: initrd.img.old
   1.2GB: vmlinuz
   1.3GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```


Thanks for sticking with me guys.  I may be dumb but not terminally so.

Jack in Phoenix

---

### Post by darkod on 2010-06-27
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda2[/COLOR] and 
                       looks at sector 271167 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

You have installed grub2 on your XP partition, /dev/sda2. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #2 on disk /dev/sda.

---

### Post by presence1960 on 2010-06-27
> **darkod said:**
> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda2[/COLOR] and 
                       looks at sector 271167 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

You have installed grub2 on your XP partition, /dev/sda2. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #2 on disk /dev/sda.

+1 

Darko's suggestion will do the trick!

---

### Post by wilee-nilee on 2010-06-27
> **presence1960 said:**
> +1 

Darko's suggestion will do the trick!

Good to see you back periodically.:p

---

### Post by 50GreenDodge on 2010-06-30
Boy do i feel stupid. I did everything as you suggested and I had testdisk running as I guess it was supposed to.  But stupid Jack here neglected to see he'd left a thumb drive in his USB port.  Not sure what all happened next, but I do know that testdisk only sees my ubuntu partition.

When I use the graphical 'disk utility' app that comes with Lynx, it shows that the windows partition - sda2  - is still there.

Any idea how I get to see sda2 in testdisk?  

Oh, BTW, I tried just on the off chance but nooooooohh, WinXP will not boot through Grub2.  

Sorry guys.

---

### Post by oldfred on 2010-06-30
You have to step thru the instructions on the site for testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

  First   screen:  Select "No Log" and press enter.
  Second  screen:  Select the hard drive containing  the Windows system partition and  choose "proceed".
  Third   screen:  "intel"
  Fourth  screen:  "advanced",
  Fifth   screen:  Select the Windows system partition  and choose "boot"
  Sixth   screen:  "BackupBS"
  Seventh screen:  type "Y" to confirm

---

### Post by wilee-nilee on 2010-06-30
Edit I just noticed oldfred had posted while I was typing, and I'm quite sure it's correct.;)

---

### Post by 50GreenDodge on 2010-06-30
It's all good now.  I have quite a few new friends to thank for their patience and knowledge to help get me through this problem.

Man, that 'testdisk' is a powerful utility.  But not as powerful as a group of Ubuntu hackers willing to help out a fellow.

Thanks again.  I'm pretty sure we can call this case solved.

---

### Post by oldfred on 2010-06-30
Glad you got it working.

---

