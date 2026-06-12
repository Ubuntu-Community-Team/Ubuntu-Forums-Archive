---
title: "Grub 2 fails at booting ubuntu 9.10, help needed!"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by joggleh on 2010-05-16
So, here's my situation:

I have a dual boot system with two seperate hard drives (or at least i try:P). On my master WD 160GB hard disk i have ubuntu installed, on the Maxtor 80GB slave disk i have my windows XP. 

Ubuntu install went just fine, made my grub2 boot from my master drive in the advanced settings at the last install screen (maybe this is the mistake?).

Rebooted my pc, Grub2 loads fine. I am able to boot my windows xp partition, but unable to boot into my 9.10. When i try, all i get is a black screen, no command line or anything. However, i can boot ubuntu using the live disk or boot in recovery mode.

Is there anything wrong with my graphics card? Is my dual boot with two drives the problem? I am desperate, i've been trying reinstalling for a few days now (just like all the other noobs).

Help would be appreciated:).

---

### Post by mistichu on 2010-05-16
boot in to recovery and do this
 
cd /boot/grub/
(hopefully you have a terminal text editor like nano or vi)
nano menu.lst
 
then read through it and make sure whatever the recovery option is the hdx where x is the number is the same for the main ubuntu option if not then arrow key to navigate to it then change it then hit ctrl o to write the file then reboot
 
so you should have something that looks like this (not exactly mind you but the variables should match)
 
Ubuntu
hd0,0(which is equivalent to master hard drive, partition one)
Ubuntu recovery
hd0,1 (which is equivalent to master hard drive, part 2)
Windows
hd1,0 (same as second hard drive, partition one)
 
hope that helps
 
EDIT: i thought i should clarify that only the hdx should match on the ubuntu side not the number after the comma (where x is the number) since they should both be on the same hard drive unless something freaking happened

---

### Post by kansasnoob on 2010-05-16
Post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we can see what's where, etc :)

---

### Post by kansasnoob on 2010-05-16
> **mistichu said:**
> boot in to recovery and do this
 
cd /boot/grub/
(hopefully you have a terminal text editor like nano or vi)
nano menu.lst
 
then read through it and make sure whatever the recovery option is the hdx where x is the number is the same for the main ubuntu option if not then arrow key to navigate to it then change it then hit ctrl o to write the file then reboot
 
so you should have something that looks like this (not exactly mind you but the variables should match)
 
Ubuntu
hd0,0(which is equivalent to master hard drive, partition one)
Ubuntu recovery
hd0,1 (which is equivalent to master hard drive, part 2)
Windows
hd1,0 (same as second hard drive, partition one)
 
hope that helps

You're suggesting editing menu.lst without even knowing if the OP has legacy grub or grub2. Are you psychic?

Testing is always better than guessing :)

---

### Post by oldfred on 2010-05-16
It is a real mess now, even if the OP had told us what version of Ubuntu he was using we do not know if it is an upgrade which may be grub legacy or grub2 or a new install which is grub2.

But it sounds like he is able to get a grub menu and may be beyond grub problems and into Ubuntu boot issues.

---

### Post by mistichu on 2010-05-16
> **kansasnoob said:**
> You're suggesting editing menu.lst without even knowing if the OP has legacy grub or grub2. Are you psychic?
 
Testing is always better than guessing :)
assuming he installed fresh when he installed he should have grub 2 as it is default with 9.10 if he upgraded he might have legacy but then again you get asked if you want to replace grub when you upgrade so there is a 85% chance that he has grub 2
 
op is only having trouble booting into ubuntu main
recovery is fine
ubuntu will never modify the recovery option(unless user intervention) it will only modify the main option (where grub may have mistaken the place of ubuntu main) that has happend to me countless times trying to dual boot using two hard drives.
 
oh and kansas he said his grub2 boot lol :)

---

### Post by mistichu on 2010-05-16
> **oldfred said:**
> It is a real mess now, even if the OP had told us what version of Ubuntu he was using we do not know if it is an upgrade which may be grub legacy or grub2 or a new install which is grub2.
 
But it sounds like he is able to get a grub menu and may be beyond grub problems and into Ubuntu boot issues.
unless grub mistook where ubuntu was located then its still a grub issue.

---

### Post by kansasnoob on 2010-05-16
> **mistichu said:**
> assuming he installed fresh when he installed he should have grub 2 as it is default with 9.10 if he upgraded he might have legacy but then again you get asked if you want to replace grub when you upgrade so there is a 85% chance that he has grub 2

But, quoting, you made this assumption:

> cd /boot/grub/
(hopefully you have a terminal text editor like nano or vi)
nano menu.lst

And upgrades from either Karmic or Hardy will not ask you if you want to upgrade from legacy grub to grub2. They will ask if you want to replace the existing menu.lst with the "maintainers version" and if you fail to do so you may find that you can't boot Ubuntu.

OTOH if you say yes the maintainers version will often make you unable to boot Windows or other OS's.

There is only one right way to handle this and that's by troubleshooting first. The Boot Info Script usually provides all of the info needed:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's always a good starting point. I use it for things that are not grub related because it provides info that would otherwise require the output of 3 or more commands.

---

### Post by mistichu on 2010-05-16
> **kansasnoob said:**
> But, quoting, you made this assumption:
 
 
 
And upgrades from either Karmic or Hardy will not ask you if you want to upgrade from legacy grub to grub2. They will ask if you want to replace the existing menu.lst with the "maintainers version" and if you fail to do so you may find that you can't boot Ubuntu.
 
OTOH if you say yes the maintainers version will often make you unable to boot Windows or other OS's.
 
There is only one right way to handle this and that's by troubleshooting first. The Boot Info Script usually provides all of the info needed:
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
It's always a good starting point. I use it for things that are not grub related because it provides info that would otherwise require the output of 3 or more commands.
good point (forgot the maintainers bit) but normally if you update it should replace grub) but still op should do what op feels like
but to clarify he did say grub2
>  
Rebooted my pc, Grub2 loads fine. I am able to boot my windows xp partition, but unable to boot into my 9.10. When i try, all i get is a black screen, no command line or anything. However, i can boot ubuntu using the live disk or boot in recovery mode.
 

which even if op messed up he could still repair grub via ubuntu live disk

---

### Post by kansasnoob on 2010-05-16
> to clarify he did say grub2

Correct! But you said:

> cd /boot/grub/
(hopefully you have a terminal text editor like nano or vi)
nano menu.lst

If the OP has a *buntu OS with grub2 and a menu.lst that's a problem :)

EDIT: we're on the OP's dime here and no longer helping him or her!

---

### Post by mistichu on 2010-05-16
> **kansasnoob said:**
> Correct! But you said:
 
 
 
If the OP has a *buntu OS with grub2 and a menu.lst that's a problem :)
 
EDIT: we're on the OP's dime here and no longer helping him or her!
IGNORE THIS POST
EDIT:
never mind lol lol that was ubi 8 that i was checking damn keyboard the down arrow was jammed lol my bad
 
EDIT:
any way op go check you grub.cfg file instead lol make sure the hdx(x is number still ) is the same as the recovery partition
sorry kansas

---

### Post by kansasnoob on 2010-05-16
> **mistichu said:**
> im not following i have grub2 and menu.lst both of which do not affect performance

Good for you, but you're ignoring my request to stop hijacking the OP's thread :)

This was their request for help, not an opportunity for you and I to debate.

I will not respond to you again!!!!!!!!!!!!

---

### Post by joggleh on 2010-05-16
> **kansasnoob said:**
> Good for you, but you're ignoring my request to stop hijacking the OP's thread :)

This was their request for help, not an opportunity for you and I to debate.

I will not respond to you again!!!!!!!!!!!!

LOL i don't mind your flamewars;). I will do your booting test, will test the results soon (as a tar gz file i assume?) Thanks in advance:)

---

### Post by mistichu on 2010-05-16
To be honest i was just trying to help since THESE FORUMS are so slow to help any one without a very easy topic ie my current broadcom thread  but anyway sorry :(

---

### Post by oldfred on 2010-05-16
joggleh 

Just post the entire results.txt and put it in code tags. As you paste it while it is still highlighted click on the # in the edit panel above. Code tags preserve formating and put it in a scroll box to make it easy to review.

---

### Post by joggleh on 2010-05-17
> **oldfred said:**
> joggleh 

Just post the entire results.txt and put it in code tags. As you paste it while it is still highlighted click on the # in the edit panel above. Code tags preserve formating and put it in a scroll box to make it easy to review.

Here you go:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=32e67e07-4794-4aff-adc4-54d80d21a0c4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c4797

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   309,588,614   309,588,552  83 Linux
/dev/sda2         309,588,615   312,576,704     2,988,090   5 Extended
/dev/sda5         309,588,678   312,576,704     2,988,027  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba26ba26

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        32e67e07-4794-4aff-adc4-54d80d21a0c4   ext4                                     
/dev/sda5        668f41eb-dfaf-4aa0-843c-0a09f777ac84   swap                                     
/dev/sdb1        B820CFDD20CFA0AC                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/32e67e07-4794-4aff-adc4-54d80d21a0c4 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /media/B820CFDD20CFA0AC  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 32e67e07-4794-4aff-adc4-54d80d21a0c4
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
menuentry "Ubuntu, Linux 2.6.31-21-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 32e67e07-4794-4aff-adc4-54d80d21a0c4
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=32e67e07-4794-4aff-adc4-54d80d21a0c4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-21-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 32e67e07-4794-4aff-adc4-54d80d21a0c4
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=32e67e07-4794-4aff-adc4-54d80d21a0c4 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set b820cfdd20cfa0ac
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
# / was on /dev/sdb1 during installation
UUID=32e67e07-4794-4aff-adc4-54d80d21a0c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=668f41eb-dfaf-4aa0-843c-0a09f777ac84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   7.9GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.31-21-generic-pae
    .1GB: boot/vmlinuz-2.6.31-21-generic-pae
    .4GB: initrd.img
    .1GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

```

---

### Post by oldfred on 2010-05-17
I do not see anything in your results.txt. You have both 9.10 and parts of  a wubi install in windows.

I would try this as it worked for my nvidia:

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

For other video cards different setting may be required.

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by joggleh on 2010-05-17
> **oldfred said:**
> I do not see anything in your results.txt. You have both 9.10 and parts of  a wubi install in windows.

I would try this as it worked for my nvidia:

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)


Thank you, it worked flawlessly. Can I somehow save my edited command list? Or do I have to retype it at every boot?

---

### Post by kansasnoob on 2010-05-17
You can edit "/etc/default/grub" as shown here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

It would be interesting to know what graphics card you have. To find out run:

```
lspci | grep VGA
```

---

### Post by joggleh on 2010-05-17
> **kansasnoob said:**
> You can edit "/etc/default/grub" as shown here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)



It would be interesting to know what graphics card you have. To find out run:

```
lspci | grep VGA
```

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
```Is it true that ubuntu is now working in low graphics mode?

I will try to edit my grub boot loader, will see if it works!

EDIT: It turns out to be that I don't have the rights to edit the grub file, how can i change this?

Thanks to all (mistichu, you too;)) for the great help.

---

### Post by kansasnoob on 2010-05-17
> **joggleh said:**
> ```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
```Is it true that ubuntu is now working in low graphics mode?

I will try to edit my grub boot loader, will see if it works!

EDIT: It turns out to be that I don't have the rights to edit the grub file, how can i change this?

Thanks to all (mistichu, you too;)) for the great help.

I'd suggest first creating a simple text backup of the original by running:

```
cat /etc/default/grub
```

Then copy-n-paste that into a word document, email program, etc. just so you have a backup of the original. Simply doing a "cp" to create a backup requires that you make the backup non-executable.

Then to edit:

```
gksudo gedit /etc/default/grub
```

Be sure to click on Save, then to "apply" the changes you must run:

```
sudo update-grub
```

And, yes, that's basically equivalent to running in low graphics mode :(

I'd strongly recommend looking for a "better" fix. I'll see what I can find :)

I've never used ATI so must google.

---

### Post by kansasnoob on 2010-05-17
Not sure how "up-to-date" this is:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by joggleh on 2010-05-17
> **kansasnoob said:**
> Not sure how "up-to-date" this is:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The cards listed:

 
```
**Full 3D support (r100 and r200 series)**

 All these cards and derivatives have full 3D acceleration support 
7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards
```

Is it just me or isn't my graphics card able to handle the 3d effects? My pc is getting pretty much of an oldie...

---

