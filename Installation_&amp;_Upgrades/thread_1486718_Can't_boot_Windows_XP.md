---
title: "Can't boot Windows XP"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2010-05-18
I upgraded an Acer computer to 10.04.  There are still problems with the upgrade as I'm having to do partial upgrades and am getting error messages.  10.04 is very usable but is missing things it thinks it needs....and I don't want any hassles from a computer.

The biggest problem is the computer won't boot to XP anymore. 

Does anyone know how to solve this problem....or begin solving it?

---

### Post by Grenage on 2010-05-18
Does it appear if you run this command:

```
sudo update-grub
```

---

### Post by PDA1 on 2010-05-18
I'll try it in a while.

What do you mean by "does it appear"?

XP or the error messages?

---

### Post by Grenage on 2010-05-18
Does XP appear in the Grub list at boot.

---

### Post by PDA1 on 2010-05-18
Yes, it does.

---

### Post by Grenage on 2010-05-18
What happens when you select it?

---

### Post by PDA1 on 2010-05-18
The screen goes black and the cursor flashes in the upper left.  That's the way it stays.

---

### Post by Grenage on 2010-05-18
If you're sure that XP is still there, I'd recommend reinstalling Grub2:

```
sudo grub-install /dev/***sdX***
```

Where sdX is your primary drive.

---

### Post by PDA1 on 2010-05-18
How can I be sure XP is still there?  I do see it in the Grub boot list but no idea whether it hasn't been wiped off the disk (knowing my luck).

How can I identify which disk I should install Grub to, per your instructions?

---

### Post by dvlchd3 on 2010-05-18
> **Grenage said:**
> If you're sure that XP is still there, I'd recommend reinstalling Grub2:

```
sudo grub-install /dev/***sdX***
```

Where sdX is your primary drive.

To find your primary drive run:
```

sudo fdisk -l

```
You should see a large EXT4 partition, thats it! (Assuming you didn't do manual partitioning when you installed Ubuntu)

---

### Post by PDA1 on 2010-05-18
The results below ARE NOT from the problem computer.  I'm just gettin g prepared to work on that one.  The results below are from my notebook just so I can get an understanding of your suggestions.

Do I assume correctly in the example below the primary drive is sda1?

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         894       11675    86606415    7  HPFS/NTFS
/dev/sda2               1         893     7172991    b  W95 FAT32
/dev/sda3           11676       19457    62508915    5  Extended
/dev/sda5           11676       19134    59914386   83  Linux
/dev/sda6           19135       19457     2594466   82  Linux swap / Solaris

---

### Post by Grenage on 2010-05-18
You are correct.  That ***** under *boot* shows that it's the partition the computer boots from.

---

### Post by wilee-nilee on 2010-05-18
post this script in code tags=highlight text in reply and click on # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by PDA1 on 2010-05-18
I'd love to but have no idea what you're talking about or how to execute it.

---

### Post by PDA1 on 2010-05-18
I got the results.txt file.  Do you want to see all of the results posted here (it's a pretty big file)?

---

### Post by PDA1 on 2010-05-18
```

```     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 133075361 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 133067553 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 133075721 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 133073953 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   132,793,289   132,793,227   7 HPFS/NTFS
/dev/sda2         132,793,290   234,436,544   101,643,255   5 Extended
/dev/sda5         132,793,353   230,195,384    97,402,032  83 Linux
/dev/sda6         230,195,448   234,436,544     4,241,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sdb2    *     10,233,405   199,961,054   189,727,650   c W95 FAT32 (LBA)
/dev/sdb3         199,961,055   390,716,864   190,755,810   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        987C02F57C02CDC6                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39289585-c2ea-4b91-b764-a62c613795db   ext4                                     
/dev/sda6        5e572db2-a682-4afa-a2b7-8a27cce38cd7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E4E-05CE                              vfat       PQSERVICE                     
/dev/sdb2        320D-180E                              vfat       ACER                          
/dev/sdb3        8E77-ACA7                              vfat       ACERDATA                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 987c02f57c02cdc6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0e4e-05ce
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod fat
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 320d-180e
    drivemap -s (hd0) ${root}
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
# / was on /dev/sdb5 during installation
UUID=39289585-c2ea-4b91-b764-a62c613795db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5e572db2-a682-4afa-a2b7-8a27cce38cd7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.1GB: boot/grub/core.img
  68.3GB: boot/grub/grub.cfg
  76.4GB: boot/initrd.img-2.6.31-21-generic
  75.5GB: boot/initrd.img-2.6.32-21-generic
  71.6GB: boot/vmlinuz-2.6.31-21-generic
  76.6GB: boot/vmlinuz-2.6.32-21-generic
  75.5GB: initrd.img
  76.4GB: initrd.img.old
  76.6GB: vmlinuz
  71.6GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by PDA1 on 2010-05-18
> **dvlchd3 said:**
> To find your primary drive run:
```

sudo fdisk -l

```You should see a large EXT4 partition, thats it! (Assuming you didn't do manual partitioning when you installed Ubuntu)


Terminal replies that the following isn't a good idea to do....
sudo grub-install /dev/***sdX***

---

### Post by PDA1 on 2010-05-18
***Whoops....double post*******

---

### Post by Grenage on 2010-05-18
> **PDA1 said:**
> Terminal replies that the following isn't a good idea to do....
sudo grub-install /dev/***sdX***

**sdX** isn't a real partition, you'd replace that with your actual partition.

---

### Post by PDA1 on 2010-05-18
Understood.  I only put the command back in for reference sake.

Terminal still says, basically, "you're crazy if you want to do this".

My boot drive is **sda1** which is what I put in for the command.

---

### Post by PDA1 on 2010-05-18
This is the result I get.....(I bolded the scary warning)


kids@kids-desktop:~$ sudo grub-install /dev/sda1
[sudo] password for kids: 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  **This is a BAD idea..**
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by Grenage on 2010-05-18
Oh God, I'm so sorry.  You want to refer to a drive, not a partition:

sudo grub-install /dev/sda

---

### Post by PDA1 on 2010-05-18
Is this the exact syntax I want to use or must I add something else to the end of the "sda" thing?
sudo grub-install /dev/sda

---

### Post by Grenage on 2010-05-18
That is the syntax you'll want to use.

By referring to */sda* and not including a partition number, you're pointing it to the drive itself.

---

### Post by PDA1 on 2010-05-18
Tried the command.

It responded that something (I don't remember what it was) "was installed successfully"....or something like that.


Tried a reboot into Windows- nothing.  Same result of the blinking cursor in the upper left screen.

Any other ideas?

---

### Post by Grenage on 2010-05-18
Does the XP partition show up from within Ubuntu?  Are you able to check that the files are still there, etc?

---

### Post by PDA1 on 2010-05-18
Yes, the Windows files are still there.

---

### Post by Grenage on 2010-05-18
Ok, do you have an XP disk and an Ubuntu disk?

If you boot from the XP disk ad enter a recovery console, you can restore the XP bootloader using *fixboot*.  That will remove your grub2 bootloader, so you'd need the Ubuntu disk to reinstall grub2.

---

### Post by PDA1 on 2010-05-18
***Ok, do you have an XP disk and an Ubuntu disk?***

No XP disk.  Ubuntu disk- yes (assuming that means the 10.04 disk...the one that started the problem in the first place!)


***If you boot from the XP disk ad enter a recovery console, you can  restore the XP bootloader using fixboot.  That will remove your  grub2 bootloader, so you'd need the Ubuntu disk to reinstall grub2.***


There's gotta be an easier way.

---

### Post by oldfred on 2010-05-18
You have installed grub to the partition sda1 when grub should only be in sda:
sda1: 
File system: ntfs
[COLOR=Red]Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and
looks at sector 133075361 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.[/COLOR]
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by PDA1 on 2010-05-18
The fix mentioned in sourceforge for boot sector doesn't address 10.04 and I can't find my boot sector with Windows on it using testdisk.

This is a mess.

---

### Post by Tkdboy on 2010-05-18
Go at Places and open the hard disk that you have WinXp.
If you can work on it try to rein-install grub2

---

### Post by PDA1 on 2010-05-18
Go to Places I understand but reinstalling Grub is beyond me.

How do I do it?

---

### Post by oldfred on 2010-05-18
The problem is a windows problem, you are missing the windows boot sector.

the fix on sourceforge is a fix for windows regardless of Ubuntu version and works for all windows as it recovers the backup that windows has saved.

 If you do not want to run testdisk for some reason then you have to use the windows repair CD and run fixboot - how to use command varies by windows version.

---

### Post by wilee-nilee on 2010-05-18
> **oldfred said:**
> The problem is a windows problem, you are missing the windows boot sector.

the fix on sourceforge is a fix for windows regardless of Ubuntu version and works for all windows as it recovers the backup that windows has saved.

 If you do not want to run testdisk for some reason then you have to use the windows repair CD and run fixboot - how to use command varies by windows version.

oldfred is correct here, with grub being put in the boot loader for XP, this makes it a little more complicated, but fixable.

OP do you have a xp disk? In case the link for the test disk is not usable for you. The testdisk answer is the best to use, it is the link in oldfred's post.

---

### Post by PDA1 on 2010-05-18
No, I don't have an XP disk.

I just re-installed 10.04 after messing everything up....including the fact that I got stuck in Grub rescue....which I had no idea how to use it.

XP is still on my drive.....but not usable.

---

### Post by wilee-nilee on 2010-05-18
> **PDA1 said:**
> No, I don't have an XP disk.

I just re-installed 10.04 after messing everything up....including the fact that I got stuck in Grub rescue....which I had no idea how to use it.

XP is still on my drive.....but not usable.

Here is a link to a XP home oem download for future use in repairs.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
You don't want to install with this but it can be used for repairs, oldfred would be the best to confirm this.
It is a straight sp3 slipstreamed XP home that will not read a sata drive without the drivers.

---

### Post by PDA1 on 2010-05-18
Well, I just re-installed 10.04 with no problems so I'm back to where I was AFTER I upgraded the first time.

Now, if I use the XP oem you mention what exactly is it I want to do with it and how do I do it?  

I don't want to further mess up Windows.

Any simple to understand help is very much appreciated.

---

### Post by wilee-nilee on 2010-05-18
Since you have reinstalled you need to run the boot script again, and when you post it highlight the text and click on the # in the reply panel this will make it easier to read.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
We have to know how it looks again. Download the XP ISO and burn it to a CD and I will post a link that gives you instructions on what to do. The test disk route **was** really the best way to go, but lets see where you are again and go from there. 

You have to be careful not to apply fixes, and trying what you think will work without asking if they will. Try to follow directions that are given, and ask questions if it is confusing. oldfred would have helped you through the testdisk situation if you could just hang and not mess around in the mean time. This not just waiting and confirming is making helping you about 100% more difficult, at the least. If you had asked about reinstalling you would have been told that it would not fix the situation.

If you keep trying fixes that are not confirmed you are at a much greater risk of losing what your trying to save.

---

### Post by PDA1 on 2010-05-18
Thank you for the help.  I'll give it a try and will post the results.

I'm not trying stuff and taking risks.  There's an amount of calculated risk I'm venturing on.  The effected computer is simple one I use for the web and have no bells or whistles or fancy programs on it so a complete re-installation of 10.04 was no loss or trouble.  That I don't have XP on the machine isn't the end of the world....but I would like to have it back.  They promised "dual-boot"....so....that's what I want.

I've found that most of the posts I've read about this issue and the ones I've started are so poorly written that no one of my skill can understand them.  The simple fixes are never that- they usually leave too much out, make too many assumptions and aren't clear.

On the other hand....if the upgrade had indeed been stable and tested severely none of us would be having these problems.  There are just too many threads about the boot problem with many people losing XP capability.

---

### Post by PDA1 on 2010-05-18
> **wilee-nilee said:**
> Since you have reinstalled you need to run the boot script again, and when you post it highlight the text and click on the # in the reply panel this will make it easier to read.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
We have to know how it looks again. Download the XP ISO and burn it to a CD and I will post a link that gives you instructions on what to do. The test disk route **was** really the best way to go, but lets see where you are again and go from there. 


If you keep trying fixes that are not confirmed you are at a much greater risk of losing what your trying to save.


Question for you- my machine is an Acer Aspire T160.  Do I download the same XP iso mentioned in your link?

Thanks.

---

### Post by wilee-nilee on 2010-05-18
So is this a acer computer and did it have XP installed on it when you bought it and did you register with them? If all of this is yes then you may want to get the 3 cd xp oem install disc set. I just had to purchase this myself to reload XP to send mine in for repair, the disc set was 20$ US.

The ISO will not read a sata hard drive if you try to use it for repair, if what you have is a sata hard drive

A reinstall; if the testdisk option can't be done, and the ISO doesn't work may be the answer. Although there may be another way to fix this, but this is a Linux forum, with lots of people who are astute at this sort of thing, but it is hit and miss with free support.

If you do a reinstall you can pull out what is in the XP you have now and put it in a new install. This will get XP back the way it's supposed to be. Then you can get the correct instructions on how to install Ubuntu again if you want.

If it is a acer what model is it?

---

### Post by wilee-nilee on 2010-05-18
> **PDA1 said:**
> Thank you for the help.  I'll give it a try and will post the results.

I'm not trying stuff and taking risks.  There's an amount of calculated risk I'm venturing on.  The effected computer is simple one I use for the web and have no bells or whistles or fancy programs on it so a complete re-installation of 10.04 was no loss or trouble.  That I don't have XP on the machine isn't the end of the world....but I would like to have it back.  They promised "dual-boot"....so....that's what I want.

I've found that most of the posts I've read about this issue and the ones I've started are so poorly written that no one of my skill can understand them.  The simple fixes are never that- they usually leave too much out, make too many assumptions and aren't clear.

On the other hand....if the upgrade had indeed been stable and tested severely none of us would be having these problems.  There are just too many threads about the boot problem with many people losing XP capability.

Your linking problems seen with booting as a cause and effect=Ubuntu when every one I have seen is **user error** in that when asked where to install grub many choose to put it in a partition when it goes in the master boot record only, which would have been sda on your computer. Grub only gets installed where a person tells it to. I don't think the ISO will work due to a sata hard drive,and this doesn't necessarily fix the problem. 

The wording of the grub install and upgrades is wrong when it says to put it in every partition, that is a bug, but a user should know what there doing as well.

I would agree that a lot of the instructions on the site can be more complicated then they need to be, when a quick web search will get better instructions from a wiki or a MS site foe Windows.

Here is the acer support # 1-800-816-2237, you might just talk with them, as well.

---

### Post by PDA1 on 2010-05-18
Here's the Boot info script report......


SEE THE POST BELOW

---

### Post by wilee-nilee on 2010-05-18
So I reposted this in code tags, you can remove the one above as it takes up to much space and id difficult to read. Hold on now.

```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #5 for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #5 for /boot/grub.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb1 and
looks at sector 133067553 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /ntldr /NTDETECT.COM

sdb2: __________________________________________________ _______________________

File system: vfat
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sdb2 and
looks at sector 133075721 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sdb3: __________________________________________________ _______________________

File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdb4: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sdb5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 63 132,793,289 132,793,227 7 HPFS/NTFS
/dev/sda2 132,793,351 234,436,544 101,643,194 5 Extended
/dev/sda5 132,793,353 230,195,384 97,402,032 83 Linux
/dev/sda6 230,195,448 234,436,544 4,241,097 82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 63 10,233,404 10,233,342 12 Compaq diagnostics
/dev/sdb2 * 10,233,405 199,961,054 189,727,650 c W95 FAT32 (LBA)
/dev/sdb3 199,961,055 296,836,054 96,875,000 c W95 FAT32 (LBA)
/dev/sdb4 296,837,118 390,721,535 93,884,418 5 Extended
/dev/sdb5 296,837,120 386,785,279 89,948,160 83 Linux
/dev/sdb6 386,787,328 390,721,535 3,934,208 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/sda1 987C02F57C02CDC6 ntfs
/dev/sda2: PTTYPE="dos"
/dev/sda5 39289585-c2ea-4b91-b764-a62c613795db ext4
/dev/sda6 5e572db2-a682-4afa-a2b7-8a27cce38cd7 swap
/dev/sda: PTTYPE="dos"
/dev/sdb1 0E4E-05CE vfat PQSERVICE
/dev/sdb2 320D-180E vfat ACER
/dev/sdb3 8E77-ACA7 vfat ACERDATA
/dev/sdb4: PTTYPE="dos"
/dev/sdb5 f74c0a33-689f-4a61-8cbe-4d07b1542a38 ext4
/dev/sdb6 210d588a-4cea-4195-99be-37d79833eeba swap
/dev/sdb: PTTYPE="dos"
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sdb5 / ext4 (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
echo 'Loading Linux 2.6.31-21-generic ...'
linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 987c02f57c02cdc6
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
insmod fat
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 0e4e-05ce
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
insmod fat
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 320d-180e
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sdb5 during installation
UUID=39289585-c2ea-4b91-b764-a62c613795db / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb6 during installation
UUID=5e572db2-a682-4afa-a2b7-8a27cce38cd7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


68.1GB: boot/grub/core.img
68.3GB: boot/grub/grub.cfg
76.4GB: boot/initrd.img-2.6.31-21-generic
75.5GB: boot/initrd.img-2.6.32-21-generic
71.6GB: boot/vmlinuz-2.6.31-21-generic
76.6GB: boot/vmlinuz-2.6.32-21-generic
75.5GB: initrd.img
76.4GB: initrd.img.old
76.6GB: vmlinuz
71.6GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro quiet splash
initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
echo 'Loading Linux 2.6.32-22-generic ...'
linux /boot/vmlinuz-2.6.32-22-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 987c02f57c02cdc6
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda5)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
insmod fat
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 0e4e-05ce
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
insmod fat
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 320d-180e
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdb5 during installation
UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb6 during installation
UUID=210d588a-4cea-4195-99be-37d79833eeba none swap sw 0 0

=================== sdb5: Location of files loaded by Grub: ===================


156.4GB: boot/grub/core.img
186.5GB: boot/grub/grub.cfg
156.4GB: boot/initrd.img-2.6.32-21-generic
156.5GB: boot/initrd.img-2.6.32-22-generic
156.4GB: boot/vmlinuz-2.6.32-21-generic
156.4GB: boot/vmlinuz-2.6.32-22-generic
156.5GB: initrd.img
156.4GB: initrd.img.old
156.4GB: vmlinuz
156.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda2

00000000 4f 9d 3e f9 12 05 7a d9 52 53 69 4e 0a 51 bd 1b |O.>...z.RSiN.Q..|
00000010 17 43 26 66 46 44 c2 5f 55 c6 ce 15 23 59 41 48 |.C&fFD._U...#YAH|
00000020 a1 32 00 1f f5 44 bf a4 10 5b ab 73 ba ee f0 b9 |.2...D...[.s....|
00000030 65 79 20 43 7a de 43 63 46 22 80 35 c2 a9 a3 4d |ey Cz.CcF".5...M|
00000040 1e 72 66 6a 8a e5 0f f0 25 24 1b f6 63 97 4e d7 |.rfj....%$..c.N.|
00000050 01 f3 eb 83 ed 5a 38 c3 47 fd 30 a6 04 8c 9a 33 |.....Z8.G.0....3|
00000060 f1 a4 c7 95 bf 56 20 3a 9e c8 ff de 7d 4b 27 47 |.....V :....}K'G|
00000070 ea 23 53 b7 a4 17 8d d5 5c 78 1d 4c 1e 37 9a 53 |.#S.....\x.L.7.S|
00000080 cd a9 2d f4 63 2c 0a a6 52 92 a9 7a 3c b0 a2 d8 |..-.c,..R..z<...|
00000090 b8 60 8e 06 87 3c a8 14 6e 7e b0 c9 ea 24 a8 e1 |.`...<..n~...$..|
000000a0 5d 7e d5 82 10 66 e0 12 60 3a 60 09 8c b2 a2 ff |]~...f..`:`.....|
000000b0 33 0c 33 e8 a6 3f 3a 1d 5f ba 73 aa d9 f3 e2 83 |3.3..?:._.s.....|
000000c0 24 3f 6d 5c 0a cd 8c ee 15 5e 8e 88 36 af 1a 8e |$?m\.....^..6...|
000000d0 23 74 29 ef 64 3f a8 3d 90 2e 56 c6 1f ce bf 70 |#t).d?.=..V....p|
000000e0 79 7d f4 64 e7 9e 46 29 9a e8 51 46 fe 19 16 d0 |y}.d..F)..QF....|
000000f0 86 7d 71 ae b2 57 bb 31 5f 87 1a 20 82 59 4e d7 |.}q..W.1_.. .YN.|
00000100 1d bf 8e 7e 8d 36 d5 ac 75 9b 39 b1 86 30 26 07 |...~.6..u.9..0&.|
00000110 cc 0e 10 e1 d1 2a c0 e4 1a eb 9d 1e e8 d2 56 66 |.....*........Vf|
00000120 43 44 92 2f da 0d 5d a6 0b dd ac 6c ec c3 0f 6c |CD./..]....l...l|
00000130 03 26 d4 a2 06 b6 27 11 c6 04 9b 55 cd 48 24 97 |.&....'....U.H$.|
00000140 be c3 d1 7a a7 66 8b 8c 42 0e 02 70 fb 33 f1 62 |...z.f..B..p.3.b|
00000150 64 ab 18 7d a6 22 e9 6a 09 5e 77 cf 13 a7 c7 09 |d..}.".j.^w.....|
00000160 5a 72 e1 ef 19 8b 66 28 44 a6 27 20 e8 a9 b9 53 |Zr....f(D.' ...S|
00000170 da fc 1f 37 6e 75 5a 08 9f 1a 57 47 eb c9 bf 40 |...7nuZ...WG...@|
00000180 c0 cc 89 fb aa f1 f8 0d 47 b7 67 fe 57 fa 4c 77 |........G.g.W.Lw|
00000190 4f 2c 14 83 bc a9 5f 87 a4 72 15 2e 46 75 57 c2 |O,...._..r..FuW.|
000001a0 6d 0f f1 5c b2 62 03 6f e2 2b 84 27 de 00 82 8c |m..\.b.o.+.'....|
000001b0 f8 b4 a0 45 bb be dc 34 66 c4 c6 d1 a5 66 00 fe |...E...4f....f..|
000001c0 ff ff 83 fe ff ff 02 00 00 00 b0 3c ce 05 00 fe |...........<....|
000001d0 ff ff 05 fe ff ff b2 3c ce 05 08 b7 40 00 00 00 |.......<....@...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Dn4mycrownj on 2010-05-18
i had about the same problem as the OP yesterday. I got it solved from here the OP might want to read this and see if it will work for them. It worked great for me. I used the first command to get back into windows and then downloaded a separate program to make windows recognize grub 2. 

Here is the link   [http://ubuntuforums.org/showthread.php?t=1485547&highlight=lost+mbr](http://ubuntuforums.org/showthread.php?t=1485547&highlight=lost+mbr)

The person helping the OP might want to check it out before the OP does it. This is just a suggestion that helped me get it done.

I was installing 9.1 because i did not want any of the bugs to deal with yet.

---

### Post by wilee-nilee on 2010-05-18
A couple of questions is sdb a external Hard drive and is sda set as the first to boot in bios. I notice that now there is no grub indicator in the sda1 boot now. Also I am not an expert at these things I generally just try to get people to post the boot script in code tags so the people who do know can step in a easily get things going.

If sdb is a usb hard drive, then unplug it and run sudo update-grub in the regular installed Ubuntu in sda. Then reboot and see if this has any positive effect, oldfred did mention a missing boot section in XP so this wont hurt anything but may be a good place to start.

---

### Post by PDA1 on 2010-05-18
> **wilee-nilee said:**
> A couple of questions is sdb a external Hard drive

No.


 and is sda set as the first to boot in bios.

No idea


 I notice that now there is no grub indicator in the sda1 boot now. Also I am not an expert at these things I generally just try to get people to post the boot script in code tags so the people who do know can step in a easily get things going.

If sdb is a usb hard drive, then unplug it and run sudo update-grub in the regular installed Ubuntu in sda. Then reboot and see if this has any positive effect, oldfred did mention a missing boot section in XP so this wont hurt anything but may be a good place to start.


Thanks for the help.  I give up....I quit for now.

---

### Post by PDA1 on 2010-05-19
I found a copy of XP.  I'll give the recommended previous post a try.

---

### Post by PDA1 on 2010-05-19
I re-installed XP and it works fine.  Happily, I just "winged it" and now I have both XP and Ubuntu.  The problem is- I have to select a different drive (or something) by clicking the F12 key to choose other boot locations.  That is- from "such and such" location/drive I can boot directly into XP BUT I must click F12 when the computer first starts so I can select 2 different drives- the 2nd one has Ubuntu on it.

How can I fix this so that the Grub menu (or whatever it's called) allows me to select XP or Ubuntu?  Here's my boot_info_script055.sh output

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 133067553 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 133075721 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   132,793,289   132,793,227   7 HPFS/NTFS
/dev/sda2         132,793,351   234,436,544   101,643,194   5 Extended
/dev/sda5         132,793,353   230,195,384    97,402,032  83 Linux
/dev/sda6         230,195,448   234,436,544     4,241,097  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sdb2    *     10,233,405   199,961,054   189,727,650   c W95 FAT32 (LBA)
/dev/sdb3         199,961,055   296,836,054    96,875,000   c W95 FAT32 (LBA)
/dev/sdb4         296,837,118   390,721,535    93,884,418   5 Extended
/dev/sdb5         296,837,120   386,785,279    89,948,160  83 Linux
/dev/sdb6         386,787,328   390,721,535     3,934,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        987C02F57C02CDC6                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39289585-c2ea-4b91-b764-a62c613795db   ext4                                     
/dev/sda6        5e572db2-a682-4afa-a2b7-8a27cce38cd7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E4E-05CE                              vfat       PQSERVICE                     
/dev/sdb2        320D-180E                              vfat       ACER                          
/dev/sdb3        8E77-ACA7                              vfat       ACERDATA                      
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        f74c0a33-689f-4a61-8cbe-4d07b1542a38   ext4                                     
/dev/sdb6        210d588a-4cea-4195-99be-37d79833eeba   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 987c02f57c02cdc6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0e4e-05ce
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod fat
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 320d-180e
    drivemap -s (hd0) ${root}
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
# / was on /dev/sdb5 during installation
UUID=39289585-c2ea-4b91-b764-a62c613795db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5e572db2-a682-4afa-a2b7-8a27cce38cd7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.1GB: boot/grub/core.img
  68.3GB: boot/grub/grub.cfg
  76.4GB: boot/initrd.img-2.6.31-21-generic
  75.5GB: boot/initrd.img-2.6.32-21-generic
  71.6GB: boot/vmlinuz-2.6.31-21-generic
  76.6GB: boot/vmlinuz-2.6.32-21-generic
  75.5GB: initrd.img
  76.4GB: initrd.img.old
  76.6GB: vmlinuz
  71.6GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set f74c0a33-689f-4a61-8cbe-4d07b1542a38
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 987c02f57c02cdc6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 39289585-c2ea-4b91-b764-a62c613795db
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=39289585-c2ea-4b91-b764-a62c613795db ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 0e4e-05ce
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod fat
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 320d-180e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=f74c0a33-689f-4a61-8cbe-4d07b1542a38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=210d588a-4cea-4195-99be-37d79833eeba none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 156.4GB: boot/grub/core.img
 186.5GB: boot/grub/grub.cfg
 156.4GB: boot/initrd.img-2.6.32-21-generic
 156.5GB: boot/initrd.img-2.6.32-22-generic
 156.4GB: boot/vmlinuz-2.6.32-21-generic
 156.4GB: boot/vmlinuz-2.6.32-22-generic
 156.5GB: initrd.img
 156.4GB: initrd.img.old
 156.4GB: vmlinuz
 156.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4f 9d 3e f9 12 05 7a d9  52 53 69 4e 0a 51 bd 1b  |O.>...z.RSiN.Q..|
00000010  17 43 26 66 46 44 c2 5f  55 c6 ce 15 23 59 41 48  |.C&fFD._U...#YAH|
00000020  a1 32 00 1f f5 44 bf a4  10 5b ab 73 ba ee f0 b9  |.2...D...[.s....|
00000030  65 79 20 43 7a de 43 63  46 22 80 35 c2 a9 a3 4d  |ey Cz.CcF".5...M|
00000040  1e 72 66 6a 8a e5 0f f0  25 24 1b f6 63 97 4e d7  |.rfj....%$..c.N.|
00000050  01 f3 eb 83 ed 5a 38 c3  47 fd 30 a6 04 8c 9a 33  |.....Z8.G.0....3|
00000060  f1 a4 c7 95 bf 56 20 3a  9e c8 ff de 7d 4b 27 47  |.....V :....}K'G|
00000070  ea 23 53 b7 a4 17 8d d5  5c 78 1d 4c 1e 37 9a 53  |.#S.....\x.L.7.S|
00000080  cd a9 2d f4 63 2c 0a a6  52 92 a9 7a 3c b0 a2 d8  |..-.c,..R..z<...|
00000090  b8 60 8e 06 87 3c a8 14  6e 7e b0 c9 ea 24 a8 e1  |.`...<..n~...$..|
000000a0  5d 7e d5 82 10 66 e0 12  60 3a 60 09 8c b2 a2 ff  |]~...f..`:`.....|
000000b0  33 0c 33 e8 a6 3f 3a 1d  5f ba 73 aa d9 f3 e2 83  |3.3..?:._.s.....|
000000c0  24 3f 6d 5c 0a cd 8c ee  15 5e 8e 88 36 af 1a 8e  |$?m\.....^..6...|
000000d0  23 74 29 ef 64 3f a8 3d  90 2e 56 c6 1f ce bf 70  |#t).d?.=..V....p|
000000e0  79 7d f4 64 e7 9e 46 29  9a e8 51 46 fe 19 16 d0  |y}.d..F)..QF....|
000000f0  86 7d 71 ae b2 57 bb 31  5f 87 1a 20 82 59 4e d7  |.}q..W.1_.. .YN.|
00000100  1d bf 8e 7e 8d 36 d5 ac  75 9b 39 b1 86 30 26 07  |...~.6..u.9..0&.|
00000110  cc 0e 10 e1 d1 2a c0 e4  1a eb 9d 1e e8 d2 56 66  |.....*........Vf|
00000120  43 44 92 2f da 0d 5d a6  0b dd ac 6c ec c3 0f 6c  |CD./..]....l...l|
00000130  03 26 d4 a2 06 b6 27 11  c6 04 9b 55 cd 48 24 97  |.&....'....U.H$.|
00000140  be c3 d1 7a a7 66 8b 8c  42 0e 02 70 fb 33 f1 62  |...z.f..B..p.3.b|
00000150  64 ab 18 7d a6 22 e9 6a  09 5e 77 cf 13 a7 c7 09  |d..}.".j.^w.....|
00000160  5a 72 e1 ef 19 8b 66 28  44 a6 27 20 e8 a9 b9 53  |Zr....f(D.' ...S|
00000170  da fc 1f 37 6e 75 5a 08  9f 1a 57 47 eb c9 bf 40  |...7nuZ...WG...@|
00000180  c0 cc 89 fb aa f1 f8 0d  47 b7 67 fe 57 fa 4c 77  |........G.g.W.Lw|
00000190  4f 2c 14 83 bc a9 5f 87  a4 72 15 2e 46 75 57 c2  |O,...._..r..FuW.|
000001a0  6d 0f f1 5c b2 62 03 6f  e2 2b 84 27 de 00 82 8c  |m..\.b.o.+.'....|
000001b0  f8 b4 a0 45 bb be dc 34  66 c4 c6 d1 a5 66 00 fe  |...E...4f....f..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 b0 3c ce 05 00 fe  |...........<....|
000001d0  ff ff 05 fe ff ff b2 3c  ce 05 08 b7 40 00 00 00  |.......<....@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Grenage on 2010-05-19
That's likely because you have a different bootloader on each of the drives, rather than one which points to both.

You'd need to reinstall grub on one drive, then boot from that one drive.

---

### Post by PDA1 on 2010-05-19
How do I do that?  And if I do as you mentioned above will that allow me to select XP or Ubuntu with ease?

---

### Post by Grenage on 2010-05-19
You'd basically just need to reinstall grub as mentioned earlier in the thread.

---

### Post by PDA1 on 2010-05-19
In light of the stuff in post #50 (the bootloader results)

Does this look right-

  	 	 	 	 	 	  sudo grub-install /dev/*sda*

---

### Post by Grenage on 2010-05-19
That looks fine to me, but you could install it to the Ubuntu drive.  Whatever drive is selected as the first boot, you'll want it there.

---

### Post by PDA1 on 2010-05-19
I'll give it a try....and let you know the results.

---

### Post by PDA1 on 2010-05-19
Success!  

Thank you so much.

Summary-

Re-install XP
Install Grub to the drive where you want XP and Ubuntu to load from


Simple....isn't it?  (yeah, like radar)

---

### Post by Grenage on 2010-05-19
Hooray!  I'm glad it worked.

---

### Post by Imatech64 on 2010-05-22
Hello everyone,
After reading as carefully as possible the numerous posts in this thread, having the same problem but with a totally different desktop configuration, I admit just one thing :
I should have never have updated from 9.10-XP dual boot which worked just exceptionally fine to 10.04/XP. 

If I understood right, one should first reinstall/repair XP first and then change something in the grub of the 10.04....is it so?

---

### Post by bcbc on 2010-05-22
> **Imatech64 said:**
> Hello everyone,
After reading as carefully as possible the numerous posts in this thread, having the same problem but with a totally different desktop configuration, I admit just one thing :
I should have never have updated from 9.10-XP dual boot which worked just exceptionally fine to 10.04/XP. 

If I understood right, one should first reinstall/repair XP first and then change something in the grub of the 10.04....is it so?

Link to Imatech64's thread: [http://ubuntuforums.org/showthread.php?t=1490399](http://ubuntuforums.org/showthread.php?t=1490399)

---

