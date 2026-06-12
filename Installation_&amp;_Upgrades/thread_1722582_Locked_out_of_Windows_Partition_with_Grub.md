---
title: "Locked out of Windows Partition with Grub"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Enlightened Shadow on 2011-04-05
Hi. I hope this is the right place to ask this.

I have two partitions on my HDD. A Windows XP (hd0,2) and an Ubuntu 9.10 (hd0,1).

I have been using the Windows mainly and ran a program that changes the HDD's serial number. Now when I boot up and Grub loads, I try to access the Windows partition and get the following error:

Error: No Such Device: 2e3857fb3857c08f

I am still able to boot the Ubuntu partition but can not seem to get grub to point to the Windows partition any more. This is very frustrating as I really need to get back into that partition soon.

If anyone could please help with this It would be amazing. Thanks.

---

### Post by Canime on 2011-04-05
Yeah, this happened to me several times, the process requires you get the windows CD out and run the system restore using the windows CD, however later on I ran some updates and I was locked out of windows again. Try,

```
sudo os-prober
```

then 

```
sudo update-grub
```

Maybe it will find it.

---

### Post by Enlightened Shadow on 2011-04-05
Thanks for the reply Canime. I tried it. The code sudo os-prober returned ```
sudo os-prober
[sudo] password for mike: 
/dev/sda2:Windows XP Ultimate:Windows:chain

```
I then ran the update grub command. I restarted and tried to access the Windows partition and got the error again. :(

So I'm back in Ubuntu trying to find another work around. Unfortunately the Opitcal Disk Drive on this machine is shot. I'm restricted to the use of a USB drive. If you know how I could get a Windows Recovery disk loaded onto a thumb drive, that would be great.

However if you knew how to remove Grub and reinstall it from scratch without a recovery CD, that would be even better.

Thanks for trying to help :).

---

### Post by wilee-nilee on 2011-04-06
Lets have a closer look at the whole thing, click on the bootscript in my signature, follow the instructions to generate a text file. Come back open a reply; click on the **(#)** in the reply panel and paste all the text between the code tags.

I have loaded windows recovery W7 that is by formatting the thumb in ntfs putting a boot flag on the partition then using the file roller/archive manager to extract to the thumb, forget if I extracted the ISO or DVD I have both, ISO I think.

---

### Post by Enlightened Shadow on 2011-04-06
Hi again. Sorry for the really late reply. I wanted to say that I was able to get back in. What I did was when it would give me the option to boot into an OS, I would press E for edit and then remove the whole search ---fs--- UUID line. It would then boot from that. It's not perfect and needs to be done each time the PC is started but it works. Thanks.

---

### Post by coffeecat on 2011-04-06
> **Enlightened Shadow said:**
> It's not perfect and needs to be done each time the PC is started but it works. Thanks.

What seems to have happened is that you've changed the UUID of the Windows C: partition from the original 2e3857fb3857c08f. Running 'sudo update-grub' *should* have fixed that by rewriting the Windows entry in your grub.cfg with the new UUID. For some reason that doesn't seem to have happened, but there must be a permanent and relatively easy fix for this. If you run the boot script that wilee-nilee suggested, it should be possible to see what needs to be done.

---

### Post by Enlightened Shadow on 2011-04-06
OK I'll run it when I get home from work. I hope we can figure it out lol. For now I just removed the line in the 40_custom file and updated Grub. That at least lets me boot back into Windows.

---

### Post by coffeecat on 2011-04-06
> **Enlightened Shadow said:**
> 40_custom file

Ah. That's something you didn't mention before. :wink: Simple substituting the new UUID should have done the trick. When you post the boot script output, post the contents of your 40_custom file as well if you still have the relevant stanza.

---

### Post by Enlightened Shadow on 2011-04-08
Hey guys I'm sorry for the really late reply lol. I just now got a chance to run that script. Here is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   195,896,609   195,896,547  83 Linux
/dev/sda2    *    195,896,610   300,383,369   104,486,760   7 HPFS/NTFS
/dev/sda3         300,383,370   312,496,379    12,113,010  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        11c34fd9-bf30-4cef-9cba-ce84536de229   ext4                                     
/dev/sda2        2E3857FB8CC54BFB                       ntfs                                     
/dev/sda3        48c5b437-6284-4c40-8158-719c9820467e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 11c34fd9-bf30-4cef-9cba-ce84536de229
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 11c34fd9-bf30-4cef-9cba-ce84536de229
insmod tga
if background_image /usr/share/images/grub/Dark_Ubuntu.tga ; then
  set color_normal=white/black
  set color_highlight=light-green/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP Ultimate" {
	insmod ntfs
	set root=(hd0,2)
	drivemap -s (hd0) ${root}
	chainloader +1
}

menuentry "Ubuntu" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 11c34fd9-bf30-4cef-9cba-ce84536de229
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=11c34fd9-bf30-4cef-9cba-ce84536de229 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
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
UUID=11c34fd9-bf30-4cef-9cba-ce84536de229 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda6 during installation
UUID=D1B4-28B3  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=48c5b437-6284-4c40-8158-719c9820467e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.5GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.4GB: boot/initrd.img-2.6.31-15-generic
  17.1GB: boot/initrd.img-2.6.31-16-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-15-generic
   3.8GB: boot/vmlinuz-2.6.31-16-generic
  17.1GB: initrd.img
   1.4GB: initrd.img.old
   3.8GB: vmlinuz
    .5GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Ultimate" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Windows Recovery Console" /cmdcons

```

That's a really nifty little script there. Thanks so much for showing it to me lol. Now maybe you guys can show me how to get my UUID back in order :).

---

### Post by Enlightened Shadow on 2011-04-08
> **coffeecat said:**
> Ah. That's something you didn't mention before. :wink: Simple substituting the new UUID should have done the trick. When you post the boot script output, post the contents of your 40_custom file as well if you still have the relevant stanza.

Haha yes I should have mentioned that I'm running Grub 2. If you still need the contents of the 40_custom file after you look at the contents of the results file from the script, I will post it here.

---

### Post by coffeecat on 2011-04-08
> **Enlightened Shadow said:**
> Haha yes I should have mentioned that I'm running Grub 2.

It was always clear that you were running grub2. The fact that you had set up entries in 40_custom and had disabled 30_os-prober was relevant to the advice given, and would have helped if you had mentioned it. Disabling os-prober means that update-grub no longer autoupdates grub menu entries for other OSs. Using 30_os-prober is easier because it will detect the new UUID and sort everything out for you. Using 40_custom, you have to change the UUID yourself. There's no need to post your 40_custom - grub.cfg in your boot script output makes clear what is in it.

Instead of this stanza:

```

menuentry "Windows XP Ultimate" {
	insmod ntfs
	set root=(hd0,2)
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

This should do the trick:

```
menuentry "Windows XP Ultimate" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2e3857fb8cc54bfb
	chainloader +1
}
```

One other thing to note. You have this is your /etc/fstab:

```
# /windows was on /dev/sda6 during installation
UUID=D1B4-28B3  /windows        vfat    utf8,umask=007,gid=46 0       1
```

You do not have a /dev/sda6, nor a partition with the UUID D1B4-28B3. I guess you will be getting a "cannot mount" error on bootup.

---

### Post by Enlightened Shadow on 2011-04-08
Wow thanks for the quick reply. I'll go and switch back over to Ubuntu and update Grub. As for the not having a sda6 (which makes sense lol), should I remove that line from fstab? Or is that possible lol. Sorry for sounding like a newb, I just have basic knowledge of Grub. I am still in the learning process.

---

### Post by Enlightened Shadow on 2011-04-08
Thank you very much. I replaced the line and it worked perfectly. As for the cannot mount error on bootup you mentioned I may be getting, I haven't encountered to date. If I do I will see if I can't fix it.

Thanks for that Bootscript btw. it's very useful.

---

