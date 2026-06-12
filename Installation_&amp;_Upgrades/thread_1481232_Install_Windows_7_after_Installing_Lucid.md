---
title: "Install Windows 7 after Installing Lucid"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by stevebond001 on 2010-05-12
Hi
I need some help.  I have just installed Lucid and configured it just right (it's running as sweet as a nut):)

However, due to a limitation with a printer / scanner driver (for my Canon MFD) I wish to install Windows 7 alongside my Lucid installation and have the ability to dual boot.  As I have spent a lot of time fine tuning my Lucid installation I don't wish to reinstall this and start again (Installing Windows 7 first then Lucid would be the easiest way as it would sort out my dual boot config for me).

I have 1TB HDD so disk space is not an issue

Does anyone have any instructions on how to adjust my partitions, etc to allow for a Windows 7 installation post Lucid install, or do I have to start from scratch?? (something which I really really do't want to do :( )

Many thanks in advance

---

### Post by stevebond001 on 2010-05-14
Right
I've partitioned my HDD and installed Windows 7, which worked OK.  I have then booted into a live CD and repaired grub so I can boot from Lucid again.  This worked OK.

My problem now is that I can't update grub to show a choice of booting between Lucid and Windows 7.
When I run update-grub it looks through all partitions and updates - however, when it gets to the Windows 7 partition (labelled WIN7) it shows the following error:

"cannot access /media/sda5/WIN7" or something like that (I'm not at my PC at the moment).  It looks like grub can't access the partition for some reason but I'm not sure why as I can browse through the partition and see all the Windows files, etc.

Does anybody have an idea on how to fix this as I'm really stuck and don't want to reinstall Lucid

Thanks

---

### Post by wilee-nilee on 2010-05-14
Post this boot script so we can see the details. Paste into the reply highlight the text and hit the # in the panel to put it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you reinstalled the grub boot loader, to the mbr only; it sounds like something isn't correct the script will tell us what that is.

---

### Post by Doug11 on 2010-05-14
There is also a boot manager called EasyBCD which is installed in your windows which after setup, gives you your choices to boot from. I use it on my Laptop which dual boots windows7 and OSX. Just because I find chameleon a little hard to work with at times. But it would still be good to find out why your grub is messed up.

---

### Post by TimHeckman on 2010-05-14
Yeah.  You may have to use the LiveCD environment to rebuild grub.

Anytime you reload Windows, tho, you'll have to do this.

EasyBCD is the best option for you it seems.

When you install Windows is overwrites MBR and usually kills grub.  That's the simple answer.

---

### Post by wilee-nilee on 2010-05-14
I wouldn't be so sure about easybcd the beta 2 supposedly can read grub2 and ezt4, but that is about the hardest way to go about this, when grub or the MS bootloader can both be restored in about 3 minutes including booting up.

Lets have a look at the script before we start advising on a system we have no idea as to whats going on. We want to help the person not destroy or make this into a much harder fix.
> 
EasyBCD is the best option for you it seems.

This is not true.

---

### Post by stevebond001 on 2010-05-14
> **wilee-nilee said:**
> Post this boot script so we can see the details. Paste into the reply highlight the text and hit the # in the panel to put it in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you reinstalled the grub boot loader, to the mbr only; it sounds like something isn't correct the script will tell us what that is.

Thanks for the replies so far.

Output from the script is as follows:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    97,659,134    97,659,072  83 Linux
/dev/sda2          97,787,655 1,847,940,884 1,750,153,230  83 Linux
/dev/sda3    *  1,847,940,885 1,953,134,504   105,193,620   7 HPFS/NTFS
/dev/sda4       1,953,134,505 1,953,520,064       385,560  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        276105dc-6561-4731-a0ca-784565f27365   ext4                                     
/dev/sda2        fba7af55-015a-4601-87e3-ce733fd96f9c   ext3                                     
/dev/sda3        789384A43AFA9078                       ntfs       Win7                          
/dev/sda4        c23ea31a-b797-4bc3-bc6b-d9bf080d3fb6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext3       (rw)
/dev/sda3        /media/Win7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
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
search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
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
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=276105dc-6561-4731-a0ca-784565f27365 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=276105dc-6561-4731-a0ca-784565f27365 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=276105dc-6561-4731-a0ca-784565f27365 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=276105dc-6561-4731-a0ca-784565f27365 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows_7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 276105dc-6561-4731-a0ca-784565f27365
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=276105dc-6561-4731-a0ca-784565f27365 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fba7af55-015a-4601-87e3-ce733fd96f9c /home           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=c23ea31a-b797-4bc3-bc6b-d9bf080d3fb6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   8.9GB: boot/grub/grub.cfg
  30.2GB: boot/initrd.img-2.6.32-21-generic
  30.3GB: boot/initrd.img-2.6.32-22-generic
  30.2GB: boot/vmlinuz-2.6.32-21-generic
   1.7GB: boot/vmlinuz-2.6.32-22-generic
  30.3GB: initrd.img
  30.2GB: initrd.img.old
   1.7GB: vmlinuz
  30.2GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=============================== StdErr Messages: ===============================

hexdump: /home/lost+found: Input/output error
hexdump: /home/lost+found: Input/output error
hexdump: /home/lost+found: Input/output error
```

sda1 = Lucid root mount partition
sda2 = Lucid home mount partition
sda3 = Windows 7 Installation partition
sda4 = Lucid Swap partition

As I'm back at my PC now I can give you the correct output from update-grub:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Win7/boot
Boot: No such file or directory
done

```

For info the Windows 7 partition can be mounted in Lucid and I can access files in the partition (so not sure why the above message appears stating that it can't access it).
 
Hopefully this provides enough info

Thanks for the assistance

---

### Post by darkod on 2010-05-14
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]

One of the grub2 boot files somehow ended up on your win7 partition. Not sure if you can just move it back to /dev/sda1 but you can try. Just simply move the file (actually it will be boot folder).

ls: cannot access /media/Win7/boot

Why would it be looking here at all? Maybe the boot folder existing on your win7 partition is confusing it. Otherwise, /media/win7 is named when you mount it in ubuntu. Did you try to do anything special about that? Issuing any commands?

If planning to simply dual boot no need to mount your win7 partition in ubuntu, and definitely not automatically on start. You can always mount it from time to time to access files.

---

### Post by wilee-nilee on 2010-05-14
> **darkod said:**
> sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]

One of the grub2 boot files somehow ended up on your win7 partition. Not sure if you can just move it back to /dev/sda1 but you can try. Just simply move the file (actually it will be boot folder).

ls: cannot access /media/Win7/boot

Why would it be looking here at all? Maybe the boot folder existing on your win7 partition is confusing it. Otherwise, /media/win7 is named when you mount it in ubuntu. Did you try to do anything special about that? Issuing any commands?

If planning to simply dual boot no need to mount your win7 partition in ubuntu, and definitely not automatically on start. You can always mount it from time to time to access files.

You got it, I wonder if moving the boot doesn't fix this if testdisk will?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Your more experienced at this so it is all yours.

---

### Post by stevebond001 on 2010-05-14
> **wilee-nilee said:**
> You got it, I wonder if moving the boot doesn't fix this if testdisk will?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Your more experienced at this so it is all yours.

Thanks for the quick replies.

To be honest I'm not too sure how I would move the grub boot files over to the correct partition.

I think that I have just solved the problem anyway using this method:
[http://ubuntuforums.org/showpost.php?p=9118724&postcount=5](http://ubuntuforums.org/showpost.php?p=9118724&postcount=5) 

I have followed this instruction to manually add the right information into the boot configuration files.  Now when I boot up the grub menu appears and I have the option to boot into Windows 7, which boots up OK.

However I'm still not sure that come the next Ubuntu upgrade if this misplaced grub file will come back to haunt me.....

Thanks very much for the help - much appreciated.

---

### Post by darkod on 2010-05-14
What I am worried about is this:
If the OP can boot ubuntu correctly as it is, it seems somehow it's locating core.img where it is right now.
Moving it to /dev/sda1 where it should be might actually make ubuntu unbootable too.

But in the worst case you can reinstall grub2 not just be reinstalling it to the MBR but also to recreate its config files, if it comes to that.

I would still try moving /boot/grub/core.img to /dev/sda1 and see what happens. If ubuntu boots fine, just run again update-grub.

If it doesn't, boot into the cd live mode and reinstall grub2 to the MBR but this time core.img will be where it should be:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If that still doesn't work, we will discuss chroot and running grub-mkconfig.

---

### Post by darkod on 2010-05-14
> **stevebond001 said:**
> 
To be honest I'm not too sure how I would move the grub boot files over to the correct partition.


If it works as it is, leave it, at least for now. As you said, if you have a problem later, we'll sort it out then.

But to answer the above question, once you are in ubuntu you should see your win7 partition in Places too. If it has a label, you will see the label there, if not it could say only for example 100GB filesystem.

Anyway, when you click on it it will mount it. It might or might not ask you for your ubuntu password to mount it. Once mounted you can open it, and then open the folders -boot-grub and copy the file core.img to your 'boot/grub' folder in ubuntu. Which you can find in Computer or Filesystem.

Once the file is copied, you can delete the 'boot' folder from the win7 partition. NOT from the ubuntu root, be careful.

---

### Post by stevebond001 on 2010-05-14
> **darkod said:**
> If it works as it is, leave it, at least for now. As you said, if you have a problem later, we'll sort it out then.

But to answer the above question, once you are in ubuntu you should see your win7 partition in Places too. If it has a label, you will see the label there, if not it could say only for example 100GB filesystem.

Anyway, when you click on it it will mount it. It might or might not ask you for your ubuntu password to mount it. Once mounted you can open it, and then open the folders -boot-grub and copy the file core.img to your 'boot/grub' folder in ubuntu. Which you can find in Computer or Filesystem.

Once the file is copied, you can delete the 'boot' folder from the win7 partition. NOT from the ubuntu root, be careful.


Well, I did as you suggested (moving the core.img file to the grub folder) and it still works! 

I still get the error message about not being able to access the Win7 partition when I run update-grub, but as long as everything is where it's supposed to be then I'm happy :P 

Many thanks again for your help

---

