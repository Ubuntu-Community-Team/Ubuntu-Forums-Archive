---
title: "GRUB error"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by niteshreddy on 2010-12-04
Hello,


I have a problem with GRUB. I was having ubuntu 9.10 on my desktop installed as "WUBI"(installed inside windows). Very recently(yesterday) i had some package upgrades showing up.

I installed the upgrades, among them one was called [COLOR="Red"]"GRUB PC"[/COLOR]. I though it was a normal gurb update.
But what i see is the my windows boot loader also has been corrupted and GRUB cant access my UBUNTU also..!

The error which i get is this

"error: No such device:<big number here...>"

I hope this information is enough. IF you need more information please do tell me..1

Please help me..! I have data on that computer which i cant loose.

thank you...!!
:D

---

### Post by Rubi1200 on 2010-12-04
Hi,
there is a GRUB update which is causing Wubi installs to fail.

Right now we need to know some things:

1. can you still boot Windows normally?

2. do you have either a Windows installation/recovery CD or an Ubuntu LiveCD?

Thanks.

---

### Post by niteshreddy on 2010-12-04
1) No, i am not able to boot into windows. It seems that, that update has over-written my windows boot loader.

2)Yes i do have ubuntu 10.10 live cd. and also a windows 7 installation cd(with which i was dual booting using WUBI).

I can give you the "boot info" using the "boot info script".

give me some time to get the data.

thank you.

---

### Post by nadeemshariff on 2010-12-04
[B][I]Hi All,

I too have same problem, as 'm unable to boot my pc.
I have dual OS with WUBI, (Ubuntu version  10.04) t asked to download grub, after restart it didn't boot at all.
I have the RESULTS.txt file output as follows :[/I][/B]
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2          30,716,280   312,576,704   281,860,425   f W95 Ext d (LBA)
/dev/sda5          30,716,343   112,631,714    81,915,372   7 HPFS/NTFS
/dev/sda6         112,631,778   194,547,149    81,915,372   7 HPFS/NTFS
/dev/sda7         194,547,213   312,576,704   118,029,492   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2ad1a4c1-3805-4401-b9f1-e46dff0aaa93   ext4                                     
/dev/sda1        22F8D7FBF8D7CAE5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3E0C485B0C480FF7                       ntfs                                     
/dev/sda6        A2201EEB201EC667                       ntfs                                     
/dev/sda7        50E81224E81208BC                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/sda7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda7/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 50e81224e81208bc
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 50e81224e81208bc
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 50e81224e81208bc
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 50e81224e81208bc
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 50e81224e81208bc
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 50e81224e81208bc
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 22f8d7fbf8d7cae5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda7/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda7/Wubi: Location of files loaded by Grub: =================


   2.6GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.32-21-generic
   4.7GB: boot/initrd.img-2.6.32-26-generic
   3.9GB: boot/vmlinuz-2.6.32-21-generic
   4.1GB: boot/vmlinuz-2.6.32-26-generic
   4.7GB: initrd.img
   3.0GB: initrd.img.old
   4.1GB: vmlinuz
   3.9GB: vmlinuz.old

```
[B]
[I]I will be grateful if anyone can solve this problem.

Regards,
Nadeem[/I][/B]

---

### Post by Rubi1200 on 2010-12-04
> **niteshreddy said:**
> 1) No, i am not able to boot into windows. It seems that, that update has over-written my windows boot loader.

2)Yes i do have ubuntu 10.10 live cd. and also a windows 7 installation cd(with which i was dual booting using WUBI).

I can give you the "boot info" using the "boot info script".

give me some time to get the data.

thank you.
Thanks for the information. Right now, I do not think you need to get the results of the boot info script.

The problem you are describing is a known bug in Wubi installs. The fix right now is to restore the Windows bootloader.

> **[COLOR=DarkRed][SIZE=3]Grub Update results in "No Such Disk":[/SIZE][/COLOR]**
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[[COLOR=DarkGreen]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you have any questions, let me know please.

---

### Post by Rubi1200 on 2010-12-04
nadeemshariff, your problem appears to be similar.

If you are unable to boot either Windows or Ubuntu, then use the fix I posted to restore the Windows bootloader.

If you do not have a Windows recovery CD, get hold of an Ubuntu CD as there is another way to restore the bootloader from there.

Just so you know, a Wubi install cannot have GRUB in the MBR, which is why you are experiencing this problem.

Let me know if you need anything else or if anything is unclear.

---

### Post by nadeemshariff on 2010-12-04
Thanks Rubi1200 for your quick reply :), 'll try to restore windows boot loader and check if it works.
Will get back to you.

Regards,
Nadeem

---

### Post by nadeemshariff on 2010-12-04
Hi Rubi 

The windows Repair/recover mode is asking for Administrator password.
I have no idea what my Administrator password is ....:(

Regards,
Nadeem

---

### Post by Rubi1200 on 2010-12-04
You are using the Windows XP CD right?

And you pressed "r"?

Then it asked for the password; did you set a password when you installed XP?

If no, or you can't remember if you did, just try to continue without entering anything; just press Enter and see what happens. If it works, run the commands you are supposed to use.

Let me know what happens.

---

### Post by nadeemshariff on 2010-12-04
Thanks for the quick response Rubi.
Yes 'm using Windows XP CD.
I haven't set any password during installation of windows.
'll try and get back to you.

Regards,
Nadeem

---

### Post by niteshreddy on 2010-12-04
> **Rubi1200 said:**
> Thanks for the information. Right now, I do not think you need to get the results of the boot info script.

The problem you are describing is a known bug in Wubi installs. The fix right now is to restore the Windows bootloader.


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you have any questions, let me know please.


Thanks Rubi1200.

It solved the problem of windows boot loader. I have solved the problem using the windows 7 cd and restored the windows boot loader.

But there is problem with the Ubuntu wubi install. 

 When i choose to boot ubuntu in windows boot loader, it searches for something, and then automatically the system reboots. 
I think it is the same wubi/grub problem.

will go through this link 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

you have given me and will tell you about the progress i made.


Do u know why this is happening?

thanks..!!:D

---

### Post by drs305 on 2010-12-04
> **niteshreddy said:**
> 
will go through this link 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

you have given me and will tell you about the progress i made.


Do u know why this is happening?

thanks..!!:D

The very first paragraph of that link provides two possible solutions. The first copies the *wubildr* file from an ubuntu folder to the c:\ in windows. The second fix mounts your wubi install and has you remove large sections of text from grub.cfg

One or the other will probably solve your problem.

The reason for the second problem is that Grub is failing to make the distinction between a normal installation and a wubi installation. The result is that a lot of files are being copied into Wubi's /boot/grub folder that wouldn't normally be there. It causes the boot failures.

The devs are aware of the problem and have released a patch. Apparently it hasn't reached the Ubuntu version quite yet.

---

### Post by nadeemshariff on 2010-12-04
Rubi the issue is resolved and 'm grateful for your help :-). My Windows is booting as effectively as it was before, i didn't check whether the Ubuntu is booting or not, but i boot screen shows two os to choose from to boot windows and ubuntu.  Should i try running Ubuntu ??  Regards, Nadeem

---

### Post by Rubi1200 on 2010-12-04
> **niteshreddy said:**
> Thanks Rubi1200.

It solved the problem of windows boot loader. I have solved the problem using the windows 7 cd and restored the windows boot loader.

But there is problem with the Ubuntu wubi install. 

 When i choose to boot ubuntu in windows boot loader, it searches for something, and then automatically the system reboots. 
I think it is the same wubi/grub problem.

will go through this link 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

you have given me and will tell you about the progress i made.


Do u know why this is happening?

thanks..!!:D
You are more than welcome niteshreddy :)

As regards the other issues, drs305 has already pointed you in the right direction.

EDIT: I forgot to mention this; please mark this thread Solved using the Thread Tools near the top of the page so that other users can also find a working solution for the same/similar issues.

---

### Post by Rubi1200 on 2010-12-04
> **nadeemshariff said:**
> Rubi the issue is resolved and 'm grateful for your help :-). My Windows is booting as effectively as it was before, i didn't check whether the Ubuntu is booting or not, but i boot screen shows two os to choose from to boot windows and ubuntu.  Should i try running Ubuntu ??  Regards, Nadeem
Excellent! I am really pleased you got it sorted out :)

You can try to boot Ubuntu. If you run into problems, see here:

> There has been a grub update that is wreaking havoc with wubi installs.

If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg.

If it's a 10.04 to 10.10 upgrade, copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file.


To edit grub.cfg:
Boot a live CD, identify your windows partition that contains the root.disk (this example assumes /dev/sd**a1**), and then edit grub.cfg as follows:
 	Code:
 	sudo mkdir /media/win 
sudo mount /dev/sd**a1** /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg 
Delete all lines up to (not including) the first line that starts with "menuentry"
Save, reboot.
courtesy of forum member bcbc.

For a more permanent fix:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)
Note that these fixes apply to Wubi installs from version 10.04 onwards.

---

### Post by nadeemshariff on 2010-12-04
Rubi I 'm able to run Ubuntu too :) 
Thank you sooooooooooo muchhhhh !!!  

Regards, 
Nadeem

---

### Post by Rubi1200 on 2010-12-05
> **nadeemshariff said:**
> Rubi I 'm able to run Ubuntu too :) 
Thank you sooooooooooo muchhhhh !!!  

Regards, 
Nadeem

No problem nadeem, you are more than welcome :D

---

