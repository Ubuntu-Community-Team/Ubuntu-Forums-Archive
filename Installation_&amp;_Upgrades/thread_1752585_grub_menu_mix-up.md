---
title: "grub menu mix-up"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2011-05-08
I am running ubuntu 10.4, windows 7, and I had ubuntu 10.10 on a single hard drive.  I upgrade the 10.10 system to 11.4 and now my grub menu which is on the 10.4 system shows two windows and two 11.4 installations.  

How can I clean this up? Also I have tried to start with the grub 1.99 on the 11.4 system and all I get is a black screen at startup. I am happy with grub on 10.4 except for the extra lines.

Thanks for your help.  Here is my info

```
Here fdisk -l

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25926   208250563+  83  Linux
/dev/sda2   *       25927       39045   105378367+   7  HPFS/NTFS
/dev/sda3           39046       45539    52163055   83  Linux
/dev/sda4           45540       60801   122592015    f  W95 Ext'd (LBA)
/dev/sda5           45540       56185    85513963+   b  W95 FAT32
/dev/sda6           60071       60801     5871726   82  Linux swap / Solaris
/dev/sda7           56186       60070    31206231   83  Linux

Partition table entries are not in disk order


Here is my update-grub info and this is how my grub startup looks.

Generating grub.cfg ...
Found background image: w.tga
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 11.04 (11.04) on /dev/sda7
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 11.04 (11.04) on /dev/sda7
done


Here is my boot script.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 731584098.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 42623879 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   416,501,189   416,501,127  83 Linux
/dev/sda2    *    416,501,190   627,257,924   210,756,735   7 HPFS/NTFS
/dev/sda3         627,257,925   731,584,034   104,326,110  83 Linux
/dev/sda4         731,584,035   976,768,064   245,184,030   f W95 Ext d (LBA)
/dev/sda5         731,584,098   902,612,024   171,027,927   b W95 FAT32
/dev/sda6         965,024,613   976,768,064    11,743,452  82 Linux swap / Solaris
/dev/sda7         902,612,088   965,024,549    62,412,462  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,858,623     3,858,561   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        e7015e6d-30a0-4e41-8fac-dfb8b3deac9f   ext4       10.4                          
/dev/sda2        122BCB654E19FB51                       ntfs       sda2Windows7                  
/dev/sda3        a00809a3-b45c-433c-823f-85350210f4a9   ext3       sda3Ubuntu Home               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5259-8D1D                              vfat       SDA5SHARE                     
/dev/sda6                                               swap                                     
/dev/sda7        2b4a661c-18fb-43da-ab96-70c67094da0b   ext4       11.4 root                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        00EB-1F58                              vfat       STEVE                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/STEVE             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7        /media/11.4 root         ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
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
search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
insmod tga
if background_image /usr/share/images/desktop-base/w.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e7015e6d-30a0-4e41-8fac-dfb8b3deac9f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e7015e6d-30a0-4e41-8fac-dfb8b3deac9f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-31-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e7015e6d-30a0-4e41-8fac-dfb8b3deac9f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=e7015e6d-30a0-4e41-8fac-dfb8b3deac9f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e7015e6d-30a0-4e41-8fac-dfb8b3deac9f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 122bcb654e19fb51
	chainloader +1
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 2b4a661c-18fb-43da-ab96-70c67094da0b
	linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda7
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu 11.04 (11.04) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 2b4a661c-18fb-43da-ab96-70c67094da0b
	linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 122bcb654e19fb51
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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
UUID=e7015e6d-30a0-4e41-8fac-dfb8b3deac9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d077e0a-cd5f-41ad-9e34-e8e6a9d66095 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
   5.5GB: boot/grub/grub.cfg
 104.1GB: boot/initrd.img-2.6.32-31-generic
 156.2GB: boot/vmlinuz-2.6.32-31-generic
 104.1GB: initrd.img
 156.2GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=2b4a661c-18fb-43da-ab96-70c67094da0b /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 477.9GB: boot/initrd.img-2.6.38-8-generic
 489.4GB: boot/vmlinuz-2.6.38-8-generic
 477.9GB: initrd.img
 489.4GB: vmlinuz

```

---

### Post by Quackers on 2011-05-08
According to the grub.cfg part of the boot script os-prober is running twice. I have not seen that before and I don't know why it is doing that. It is undoubtedly the reason for the double entries in grub.
Hopefully somebody else will have seen this before and offer some advice.

---

### Post by lindsay7 on 2011-05-08
Yes I saw that, but I too have no idea how to fix it.

---

### Post by Rubi1200 on 2011-05-08
EDIT: had one of my "moments" again. You already posted the script.

Which Ubuntu currently controls the boot process?

---

### Post by LostFarmer on 2011-05-08
from grub.cfg
> ### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###  What is 30_os-prober_proxy ?

Do you have a file /etc/drub.d/30_os_prober_proxy ?

---

### Post by Quackers on 2011-05-08
> **LostFarmer said:**
> from grub.cfg
  What is 30_os-prober_proxy ?

Do you have a file /etc/drub.d/30_os_prober_proxy ?

That's a very good point LostFarmer! I didn't notice that :shock:

---

### Post by Rubi1200 on 2011-05-08
I have a possible idea as to what happened, but we need to know which partition currently controls the boot process.

And, yes, that was well spotted; nice one :-)

---

### Post by Rubi1200 on 2011-05-08
I have a possible idea as to what happened, but we need to know which partition currently controls the boot process.

And, yes, that was well spotted; nice one :-)

---

### Post by Quackers on 2011-05-08
Looking at the boot script it seems that 11.04 isn't fully installed (boot files missing).
Also the only grub.cfg shown is for sda1 and the boot script appears to be parsing grub well (and it doesn't do that with 11.04's version of grub). That would seem to indicate that 10.04's version of grub is in control - I think  :-)
What do you think Rubi1200?

---

### Post by lindsay7 on 2011-05-08
Grub is booting off of sda1 which is Ubuntu 10.4.  I had 10.10 on sda7 which I upgraded to 11.4 with an online update (not by cd-new install). I can boot into the 11.4 and it runs fine.

Here is a screen shot of grub.d

[ATTACH]191576[/ATTACH]

---

### Post by Quackers on 2011-05-08
Hmm, you have a 10_linux_proxy and a 30_os-prober_proxy.
I don't know where they've come from. Hopefully someone will know something about them :-)
You should be able to disable them without too much problem, but it would be nice to find out why they're there.

---

### Post by Rubi1200 on 2011-05-08
What are those proxified scripts? Something you wrote or added from somewhere?

I suspect there might be a mismatch between the grub versions; 10.04 uses 1.98 whereas 11.04 uses 1.99.

I wonder if reinstalling grub would fix this?

Let's wait and see what Quackers thinks about this.

EDIT: the other thing I noticed was that the 11.04 partition only has fstab on it and sdb has grub in the boot sector. Did you accidentally install grub there during the upgrade?

---

### Post by Quackers on 2011-05-08
I've sent for reinforcements :-) I'm hoping the grub guru can explain it to us mere mortals :wink:

---

### Post by lindsay7 on 2011-05-08
This just showed up after the upgrade. I have reinstalled grub and also have run update-grub. It does not change anything.

I just found this,

```
   1.
      Today 09:15 AM #1
      Setia Budi Halim
      Guest
      [Bug 758887] Re: Following kernel upgrade to 2.6.38-8.42,grub2 generates duplicate entries in the menu

          Having same problem. Seems that "proxy scripts", something new in natty release that might have caused it.
          Here's entries in my /etc/grub.d

          00_header
          05_debian_theme
          05_debian_theme.dpkg-old
          10_linux
          10_linux_proxy
          20_linux_xen
          20_memtest86+
          30_os-prober
          30_os-prober_proxy
          40_custom
          41_custom
          bin
          proxifiedScripts
          README

          If I disabled the *proxy* files and execute update-grub, no duplicate entries generated
          Those scripts were created during natty upgrade process, think the upgrade process should have disabled/removed 30_os-prober before adding new 30_os-prober_proxy

          __
          You received this bug notification because you are a member of Ubuntu
          Bugs, which is subscribed to Ubuntu.
          https://bugs.launchpad.net/bugs/758887

          Title:
          Following kernel upgrade to 2.6.38-8.42, grub2 generates duplicate
          entries in the menu

          __
          ubuntu-bugs mailing list
          ubuntu-bugs (AT) lists (DOT) ubuntu.com
          https://lists.ubuntu.com/mailman/listinfo/ubuntu-bugs 

      Reply With Quote Reply With Quote


```

Do you have any idea on how I would disable the "proxy" files?

---

### Post by Rubi1200 on 2011-05-08
According to that bug report, the user had installed Grub Customizer prior to upgrading:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/758887)

Is that also the case in your situation?

---

### Post by Quackers on 2011-05-08
I suspect that ```
sudo chmod -x /etc/grub.d/10_linux_proxy /etc/grub.d/30_os-prober_proxy
``` would disable the two files, but I urge you to wait for further confirmation of that before you run it.
Hopefully help is on the way :-)

---

### Post by lindsay7 on 2011-05-08
To Rubi1200,

I did and still have the grub customizer installed. 

And Grub was on a flash drive on sdb but I cleaned it up today and it is gone.

---

### Post by oldfred on 2011-05-08
I am one to try things and agree with Quackers on turning off the proxies. You do not need much for the auto update to occur and you can manually create grub.cfg.

I might back up the current grub.cfg so you could revert to the old one if necessary.
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

My only question is also where did the proxy scripts come from. Are they old versions about to be deleted and update did not complete, or new versions that update had not renamed yet, or something else.

From Ranch hand (assumes you have manually created exactly the boot stanzas you want in 06_custom and turn off any other searching.)
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

---

### Post by lindsay7 on 2011-05-08
As I said this all just showed up after the upgrade. I try the suggestions you all have given me a later today.. I am going to be out for a few hours. Thanks for the help, I will get back soon.

---

### Post by Quackers on 2011-05-08
Probably better to wait until later to try everything. There may be a brainstorm in between :-)  Or some advice!

---

### Post by lindsay7 on 2011-05-08
Thanks for the tips and great ideas. I was able to fix this by deleting the bin folder, ProxifiedScpips folder and the 10_linuxProxy and 30_os-Prober-proxy files from my /ect/grub.d 

Then I did update-grub.

This took out the extra lines in the grub menu,


Thanks to all.

---

### Post by drs305 on 2011-05-08
EDIT:  D'OH! Guess I took too long to write this up!!

Most likely your issues have to do with Grub Customizer. 

In /etc/grub.d, it created the *_proxy files, and the *bin* & *proxifiedScripts* folders.

When GC makes a change that requires a script modification, it moves the original script to /etc/grub.d/proxifiedScripts (and removes the leading ##_ from the name). It then creates a replacement script called *_proxy.

[LIST]
[*]To restore the normal Grub 2 files, first inspect 'proxifiedScripts' to ensure the originals are there. 
[*]Then remove any '*_proxy' scripts from /etc/grub.d and the /etc/grub.d/bin folders.
[*]If necessary, move the files in 'proxifiedScripts' back to /etc/grub.d. 'If necessary' means if the originals don't already exist (e.g. 10_linux, 30_os-prober)
[*]Remove the /etc/grub.d/bin and /etc/grub.d/proxifiedScripts folders. In my commands, I will rename them because I don't post "sudo rm" commands. Do as you wish, but be careful.
[*]Rename the modified files, such as linux to 10_linux and os-prober to 30_os-prober.
[*]Update grub.
[/LIST]
Here is the command way, but opening Nautilus as root and accomplishing the same steps would be just as easy and safer.

```
sudo -i  # Change to root. Be careful with the commands!
cd /etc/grub.d
ls proxifiedScripts
mv proxifiedScripts/* /etc/grub.d/ # If necessary.
mv bin bin.old && mv proxifiedScripts proxifiedScripts.old
mv *_proxy proxifiedScripts.old
mv linux 10_linux && mv os-prober 30_os-prober # If necessary.
update-grub
exit

```

---

### Post by lindsay7 on 2011-05-08
Thank you for your efforts and solution.  It should be helpful to others who see the same situation. What you posted would have worked I am sure.

I would think the because Grub Customizer  works at little troublesome with an upgrade that it would be wise to disable it until the upgrade is running without problems.

Thanks again for your help.

---

### Post by drs305 on 2011-05-08
I wrote a guide on Grub Customizer. I didn't include anything on uninstalling, but I can use this experience to go back and do so as there is obviously a need.

I don't think GC has a 'reset' button.  I wrote out all the commands in this post in case someone wanted to make a script to 'erase' the GC changes. It sounds a lot more complicated than it really is. What you wrote really is sufficient as long as you have replacements or renamed the files originally moved into the *proxifiedScripts* folder.

Happy Ubuntu-ing !

---

### Post by Quackers on 2011-05-08
Thanks for the explanation of the proxys, drs305. Something to watch out for in future :-)

---

### Post by Rubi1200 on 2011-05-09
> **lindsay7 said:**
> Thanks for the tips and great ideas. I was able to fix this by deleting the bin folder, ProxifiedScpips folder and the 10_linuxProxy and 30_os-Prober-proxy files from my /ect/grub.d 

Then I did update-grub.

This took out the extra lines in the grub menu,


Thanks to all.
Excellent! I am really glad you got this sorted out. Interesting experience too for all of us if we ever see something with proxy or proxified again.

Enjoy :)

---

