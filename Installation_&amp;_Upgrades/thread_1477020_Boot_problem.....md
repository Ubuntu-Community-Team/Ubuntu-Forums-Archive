---
title: "Boot problem...."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Siddiki on 2010-05-08
Apologies if this it the wrong place, but I am trying all options (even another forum under WinXP/MBR).  My first try at Linux.  I had a working laptop, IBMT-40 and tried to install Ubuntu from the CD (not via WUBI).  Nothing will boot now, and I suspect the MBR was trashed as all partitions (1 NTFS and an extended with 2 Ubuntu and 1 swap) appear to be intact using Gpart and Ultimate Boot App..  I cannot seem to recover XP with any utilities I have tried so far.  Ubuntu runs fine from the CD.  If I were to complete another new installation of Ubuntu (which does not recognize that I have (had?) another OS), might I be able to fix my XP problem from Ubuntu 'terminal', or must I start over from 'format C:'?  I will try to provide any detailed information needed if there are any ideas.  Thanks for the time.  S.

---

### Post by frantid on 2010-05-08
Please run the bootinfoscript from the livecd:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

post results here by pasting the text in between code tags -- i.e. click on the # sign in the reply box and paste in between the brakets ] [

---

### Post by cain071546 on 2010-05-08
Ubuntu should see xp and ask if you wish to install side by side
by doing so it will automatically add xp to Grub and allow you to bootb both

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> Please run the bootinfoscript from the livecd:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

post results here by pasting the text in between code tags -- i.e. click on the # sign in the reply box and paste in between the brakets ] [

     Thanks for the reply.  I *think* that this is what you wanted.  I am working in a language I don't know/understand (UNIX), with apps I didn't have, across platforms between machines. If anything else is needed, i will try to get it.  Thanks also for the details on how to try to get it here, as I am very new to this.     S

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,222,234    29,222,172   7 HPFS/NTFS
/dev/sda2          40,997,880    78,140,159    37,142,280   5 Extended
/dev/sda5          40,997,943    51,391,934    10,393,992   7 HPFS/NTFS
/dev/sda6          51,391,998    62,476,784    11,084,787  83 Linux
/dev/sda7          62,476,848    77,369,039    14,892,192  83 Linux
/dev/sda8          77,369,103    78,140,159       771,057  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B66C58A36C586063                       ntfs                                     
/dev/sda5        3A1DB15D26A575B0                       ntfs       NTFS                          
/dev/sda6        0cf5a1f2-6705-464d-8dfc-0a11e861f9ca   ext3       UBUNTU_ex3                    
/dev/sda7        496ca826-1cdc-4ed9-ab6e-1dba6074112e   ext4                                     
/dev/sda8        107dd150-c14a-4340-ad33-9986d7e11dcc   swap                                     
/dev/sdb1        8811-5589                              vfat       UBUNTU_2                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/UBUNTU_2          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b66c58a36c586063
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

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=107dd150-c14a-4340-ad33-9986d7e11dcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  32.8GB: boot/initrd.img-2.6.31-14-generic
  34.5GB: boot/vmlinuz-2.6.31-14-generic
  32.8GB: initrd.img
  34.5GB: vmlinuz

---

### Post by frantid on 2010-05-08
we'll need to mount the drive.  

     
     ```
sudo mount /dev/sda7 /mnt 
```then recopy grub from the cd.
     
     ```
sudo grub-install --root-directory=/mnt/ /dev/sda 
```we are working through the repair steps here, for more info:
[https://help.ubuntu.com/community/Gr...0from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

then reboot, hopefully you will see grub.

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> we'll need to mount the drive.  

     
     ```
sudo mount /dev/sda7 /mnt 
```then recopy grub from the cd.
     
     ```
sudo grub-install --root-directory=/mnt/ /dev/sda 
```we are working through the repair steps here, for more info:
[https://help.ubuntu.com/community/Gr...0from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

then reboot, hopefully you will see grub.

WOW, thanks!  I now get the GRUB menu.  However, XP says "(ON sda1)" and fails to start, and when I select the "Ubuntu. Linux 2.6.31-14-generic" (first line of menu) I get "error no such device" and a long string of info.  Below is the Terminal screen of my input to the machine and the result.  I appreciate all your help.  S.

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
```


```(hd0)    /dev/sda

---

### Post by frantid on 2010-05-08
ok let's try something.

boot into grub, when the menu  comes up don't let grub try to boot anything.  just push the up arrow.

then highlight the xp menu and press e

it should show you the config for xp.  Use the arrow keys and backspace -- make it look like this:


```

insmod ntfs
set root=(hd0,1)
chainloader +1
```then push Ctrl-x to see what it does.  do you have a second computer to post back or do you just have the one we're working on?

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> ok let's try something.

boot into grub, when the menu  comes up don't let grub try to boot anything.  just push the up arrow.

then highlight the xp menu and press e

it should show you the config for xp.  Use the arrow keys and backspace -- make it look like this:


```

insmod ntfs
set root=(hd0,1)
chainloader +1
```then push Ctrl-x to see what it does.  do you have a second computer to post back or do you just have the one we're working on?

I followed the procedure and edited out two lines ("search --no floppy --fs uuid --set [string of characters]"  & "drivemao -s (hd0)  ${root}" then the unchanged 'chainloader' line, but ended up with the same results.  I do have another Windows computer as the laptop is still non-functional.  The major delay is when I have to boot the CD to run Ubuntu.  From the CD, loading takes a while.  Appreciate the help.  S.

---

### Post by frantid on 2010-05-08
No problem.

Let's try booting the ubuntu entry, same deal as the xp one:


    ```

insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set  496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro
    initrd    /boot/initrd.img-2.6.31-14-generic
```

Edit the blank space before the start of the lines doesn't matter.

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> No problem.

Let's try booting the ubuntu entry, same deal as the xp one:


    ```

insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set  496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro
    initrd    /boot/initrd.img-2.6.31-14-generic
```Edit the blank space before the start of the lines doesn't matter.


Done, frantid.  Gives me a message "error: no such device: 496ca826-1cdc-4ed9-ab6e-1dba6074112e ro"    S.

---

### Post by frantid on 2010-05-08
doesn't it just return to grub when it errors?

if not, boot back into grub -- when you see the menu, press c

try a grub command ```
ls(hd1,7)/
```if that shows a list of files, then do```
 ls (hd1,7)/boot/
```

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> doesn't it just return to grub when it errors?

if not, boot back into grub -- when you see the menu, press c

try a grub command ```
ls(hd1,7)/
```if that shows a list of files, then do```
 ls (hd1,7)/boot/
```


Done.  When I input the first line, I get "unknown command ls(hd1,7)/"    not a list
A straight "ls" gets me "(hd0)  (hd0.7)  (hd0,6)  (hd0,5) (hd0,1)  (fd0)  
error: no such disk"


S.

---

### Post by Siddiki on 2010-05-08
> **frantid said:**
> doesn't it just return to grub when it errors?

if not, boot back into grub -- when you see the menu, press c

try a grub command ```
ls(hd1,7)/
```if that shows a list of files, then do```
 ls (hd1,7)/boot/
```


Sorry, I should have added that it does just return to GRUB on XP choice and to an error message which returns to GRUB on any keystroke.

---

### Post by frantid on 2010-05-09
sorry for the late response, my adsl went down.

It's my fault the error, I mis-typed in the commands.

```
ls (hd0,7)/


then

ls (hd0,7)/boot/
```

---

### Post by frantid on 2010-05-09
With Mother's Day I don't know if I or you will be around.  Here are some directions to fix xp.

I think that perhaps some of the tools you tried, maybe super boot disk,  put syslinux into the MBR of sda.  This probably altered the xp partition.  

To repair xp you will need to boot off an xp cd, then repair the boot sector.

simply boot the xp cd.   pick recovery console.  You want to run 

```
chkdsk /f c:
fixboot c:
```I would then try to reboot and see if grub can boot xp.  If it does not work, you need to boot the xp cd again -- run 

```
fixmbr c:
fixboot c:
```That will over write grub again and you will need to reinstall it.  Like we did before, you may want to read that [link I pasted]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") last time.  It gives 3 ways to try to fix grub.

We were working on the first way.   You may need to do the chroot example, method number 3 -- so you can perform a "update-grub".  The release notes for Karmic suggest adding:
```
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
```
after step number 8, in method chroot.

good luck, I'll be on the forum in a day or so.

---

### Post by Siddiki on 2010-05-09
> **frantid said:**
> sorry for the late response, my adsl went down.

It's my fault the error, I mis-typed in the commands.

```
ls (hd0,7)/


then

ls (hd0,7)/boot/
```

 Good Day, frantid.  Yes, I'm here today (MD), and know how it is when your link goes down. I am following up on your posts in order.  I am totally lost in the language for now.  I tried the 'updated' command  ls (hd0,7)/, got the listing then (hd0,7)/boot/, which I assume listed the info in boot.  Does 'ls'install or change anything? After I ran the sequence, I still get 'no such device' under the Ubuntu choice and revert to the GRUB menu with the XP choice. I again tried to 'repair' with the XP CD, and still get the "path or file specified is not valid" response, so I can't access an MBR repair.  I know this is not an XP thread but do you think if GRUB will boot to Ubuntu, maybe I can use Terminal to work on the XP MBR.  I sure don't know.  In any event, thanks for your assistance; hopefully, see you in a couple of days.       S.

---

### Post by frantid on 2010-05-09
Hi, I've got a few moments:  Can you type out the the results of ls (hd0,7)/boot/  ?  Grub needs to be able to find the files in the menu.  try picking ubuntu, and then editing the menu to look like this:  you don't have to type it all out.  you just go to the end of the line and backspace over what you want to remove.

```
insmod ext2
    set root=(hd0,7)
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e 
    initrd    /boot/initrd.img-2.6.31-14-generic
```make sure those 2 files are there when you do the ls (hd0,7)/boot/  

vmzlinuz-2.6.31.14-generic
initrd.img-2.6.31-14-generic

---

### Post by Siddiki on 2010-05-09
> **frantid said:**
> Hi, I've got a few moments:  Can you type out the the results of ls (hd0,7)/boot/  ?  Grub needs to be able to find the files in the menu.  try picking ubuntu, and then editing the menu to look like this:  you don't have to type it all out.  you just go to the end of the line and backspace over what you want to remove.

```
insmod ext2
    set root=(hd0,7)
    linux    /boot/vmlinuz-2.6.31-14-generic  root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e 
    initrd    /boot/initrd.img-2.6.31-14-generic
```make sure those 2 files are there when you do the ls (hd0,7)/boot/  
 G'Day, ls (hd0,7)/boot/  >  "grub/  System.map-2.6.31-14-generic-config-2.6.31-14-generic memtest86+.bin vmcoreinfo-2.6.31-14-generic vmlinuz-2.6.31-14-genric in itrd.img-2.6.31-14-generic"  or close to this, considering my typing. 
vmzlinuz-2.6.31.14-generic
initrd.img-2.6.31-14-generic

G'Day,
ls (hd0,7)/boot/  >  "grub/  System.map-2.6.31-14-generic-config-2.6.31-14-generic memtest86+.bin vmcoreinfo-2.6.31-14-generic vmlinuz-2.6.31-14-genric in itrd.img-2.6.31-14-generic"  or close to this, considering my typing.

I typed in the second suggestion  "insmod et. al."  and the machine took off, displayed several pages of script and booted into Ubuntu, where it now sits until I know more.   Thanks.    S.

---

### Post by frantid on 2010-05-09
Hey, that's great news.  You did it!


I just have time for this one reply, sorry.  First order of business is to do:

```
sudo update-grub
```That is supposed to correct anything wrong with the config.  When it's done, do NOT reboot.  The more we leave it as is, the better chance we have of getting xp back.  Please run that bootinfoscript again.  This time from inside ubuntu.  That way I can have a look to make sure things are okay and can look at your xp for you.  If you post it I might be able to look at it tonight, but I don't suspect to be back on until tomorrow.

---

### Post by Siddiki on 2010-05-09
> **frantid said:**
> Hey, that's great news.  You did it!


I just have time for this one reply, sorry.  First order of business is to do:

```
sudo update-grub
```That is supposed to correct anything wrong with the config.  When it's done, do NOT reboot.  The more we leave it as is, the better chance we have of getting xp back.  Please run that bootinfoscript again.  This time from inside ubuntu.  That way I can have a look to make sure things are okay and can look at your xp for you.  If you post it I might be able to look at it tonight, but I don't suspect to be back on until tomorrow.


Can you see my smile from there?  Ran the suggested script and here, I think, is the bootinfo after the run   -  machine still not rebooted:
```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,222,234    29,222,172   7 HPFS/NTFS
/dev/sda2          40,997,880    78,140,159    37,142,280   5 Extended
/dev/sda5          40,997,943    51,391,934    10,393,992   7 HPFS/NTFS
/dev/sda6          51,391,998    62,476,784    11,084,787  83 Linux
/dev/sda7          62,476,848    77,369,039    14,892,192  83 Linux
/dev/sda8          77,369,103    78,140,159       771,057  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B66C58A36C586063                       ntfs                                     
/dev/sda5        3A1DB15D26A575B0                       ntfs       NTFS                          
/dev/sda6        0cf5a1f2-6705-464d-8dfc-0a11e861f9ca   ext3       UBUNTU_ex3                    
/dev/sda7        496ca826-1cdc-4ed9-ab6e-1dba6074112e   ext4                                     
/dev/sda8        107dd150-c14a-4340-ad33-9986d7e11dcc   swap                                     
/dev/sdb1        8811-5589                              vfat       UBUNTU_2                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/UBUNTU_2          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b66c58a36c586063
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

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=107dd150-c14a-4340-ad33-9986d7e11dcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  32.7GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
  32.8GB: boot/initrd.img-2.6.31-14-generic
  34.5GB: boot/vmlinuz-2.6.31-14-generic
  32.8GB: initrd.img
  34.5GB: vmlinuz
```

```

---

### Post by frantid on 2010-05-10
Hi Siddiki,

The new grub.cfg file looks ok and yes you did get the right one.  It is the same as the first which concerns me.  We have not done anything to yet fix why the search lines had to be removed to get ubuntu to boot.  I think either the grub has missing pieces or there might be issues with your disks.

First a few questions.  Can you tell me about your second disk, it is a fat32 disk.  What is on that disk?  What tools did you use to try to get xp back?

Grub first, in a terminal:

```
sudo grub-install --recheck /dev/sda
```
please post any errors.


then, we need to check your disks.  We need a program call gparted, I don't remember if it is in the base install.  Check under system/administration in the menu for "GParted" If it's not there we need to add it.  We'll do it via the menu, so you know how to add apps.  Go to applications, down at the bottom open "Ubuntu Software Center".  In the search box type "gparted", it will list it.  Click on it's description, you should see an install button.  Once it's installed, find it in system/administration.
[URL="http://www.dedoimedo.com/computers/gparted.html"]
here is a great gparted tutorial.[/URL]

You need to check all your partitions for errors, including your second disk.  How to check:
[http://www.dedoimedo.com/computers/gparted.html#mozTocId748422](http://www.dedoimedo.com/computers/gparted.html#mozTocId748422)

let me know if it says can't read ntfs.

---

### Post by Siddiki on 2010-05-10
[QUOTE=frantid;9273286]Hi Siddiki,

The new grub.cfg file looks ok and yes you did get the right one.  It is the same as the first which concerns me.  We have not done anything to yet fix why the search lines had to be removed to get ubuntu to boot.  I think either the grub has missing pieces or there might be issues with your disks.

First a few questions.  Can you tell me about your second disk, it is a fat32 disk.  What is on that disk?  What tools did you use to try to get xp back?

Grub first, in a terminal:

```
sudo grub-install --recheck /dev/sda
```please post any errors.


then, we need to check your disks.  We need a program call gparted, I don't remember if it is in the base install.  Check under system/administration in the menu for "GParted" If it's not there we need to add it.  We'll do it via the menu, so you know how to add apps.  Go to applications, down at the bottom open "Ubuntu Software Center".  In the search box type "gparted", it will list it.  Click on it's description, you should see an install button.  Once it's installed, find it in system/administration.
[URL="http://www.dedoimedo.com/computers/gparted.html"]
[/URL]G'day frantid,
First, here is a copy of the recheck.
rag@rag-laptop:~$ sudo grub-install --recheck /dev/sda
[sudo] password for rag: 
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

rag@rag-laptop:~$ 
I have Gparted on CD here and it should run from there OK.  I have tried to restore XP with the XP-CD and under the repair choice, it  says 'path or file specified not valid'.  I looked at the drive with Dr' Dos 2.0 and it looked to be intact but the attempts at fxmbr and the like did not work, seems that it can't find the file or disk.  As for partitioning, it was some time ago, but I *think* I may have used Gparted before I tried to reinstall Ubuntu for the n'th time.  If you mean sda5, I read both OS's could read from a FAT32, maybe I had that in mind when I did it.  Unsure why it is is formatted Vista/7 as I don't run them.  I installed Gparted just now.  Here I hope is a screenshot attached.  Thanks.   S.

---

### Post by frantid on 2010-05-10
thanks for the good info.  I meant the second 4 Gig device.  it's /dev/sdb, says it's fat in your bootscriptinfo.  Or is this a flash card, USB disk or something?

we need to edit your device.map to  include this second device if it's a drive..

---

### Post by frantid on 2010-05-10
we also need to add some ntfs tools.

Well try synaptic this time, so you'll see one more avenue to install software.  It's in System/Admin Synaptic Package Manager -- goto search and type in "ntfs"  Check ntfs-3g and ntfsprogs.  It will prompt you about having to mark dependent packages.  You should look over the list, just make sure you don't have 20 or more only that are checked.

Once your satisfied click apply.

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> thanks for the good info.  I meant the second 4 Gig device.  it's /dev/sdb, says it's fat in your bootscriptinfo.  Or is this a flash card, USB disk or something?

we need to edit your device.map to  include this second device if it's a drive..


Sorry, I believe that was a flash drive that I was using to move stuff around between machines in my futile attempts to find out what was wrong.  The screen-shot no longer shows it.  In Gparted, when I select either sda1 or sda5 'information' it says it 'unable to read contents of file......' and there is no '>check' option to repair anything that I can see.  The version of Gparted is 0.4.5.  Earlier on, I verified that the lines in GRUB did in fact need to be removed each time to get Ubuntu to boot.  The present startup is still running well.   Thanks     S.

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> we also need to add some ntfs tools.

Well try synaptic this time, so you'll see one more avenue to install software.  It's in System/Admin Synaptic Package Manager -- goto search and type in "ntfs"  Check ntfs-3g and ntfsprogs.  It will prompt you about having to mark dependent packages.  You should look over the list, just make sure you don't have 20 or more only that are checked.

Once your satisfied click apply.

It appears that the 'ntfs-3g' was already installed as the only options under package manager were 'mark for reinstallatiion,,, removal,,,,complete removal'   I appreciate your time.      S.

---

### Post by Siddiki on 2010-05-10
> **Siddiki said:**
> It appears that the 'ntfs-3g' was already installed as the only options under package manager were 'mark for reinstallatiion,,, removal,,,,complete removal'   I appreciate your time.      S.

Addendum:  Change 'it' to 'they'.  Both programs are present.    S.

---

### Post by frantid on 2010-05-10
there's a triangle warning on the ntfs drives, what does the warning say?  right click the partition and check info  it might help you see the warning.  You don't have them mounted do you?

If the flash is removed, does it still need to remove the search lines to boot?

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> there's a triangle warning on the ntfs drives, what does the warning say?  right click the partition and check info  it might help you see the warning.  You don't have them mounted do you?

If the flash is removed, does it still need to remove the search lines to boot?

REALLY strange.  I have done almost nothing with the Ubuntu machine but just ran the Gparted again and the triangles are gone, and under 'information', all looks good and they are not mounted, save for sda6, sda7.  I just did a cold boot and still have to remove those lines to make it work.    S.

---

### Post by frantid on 2010-05-10
okay, gparted just needed to be restarted to get the ntfs tools to work.  You should be able to now select the partition and perform a check on them.

---

### Post by frantid on 2010-05-10
I forgot, did you reboot into xp after resizing it to put ubuntu on it?  If you resized it, without running chkdsk from  within xp after that could be why xp won't boot.

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> okay, gparted just needed to be restarted to get the ntfs tools to work.  You should be able to now select the partition and perform a check on them.

Check complete on sda1, sda5.  No significant notices or warnings that I saw.   S.

---

### Post by frantid on 2010-05-10
Does this machine have a floppy on it?

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> Does this machine have a floppy on it?

No, just a CD drive and USB ports.

---

### Post by frantid on 2010-05-10
ok, we need to edit 2 files.


you're probably more comfortable with a gui editor?  so

first

```
sudo cp /etc/fstab /etc/fstab.old
sudo cp /boot/grub/device.map /boot/grub/devicemapold

```


```
gksudo gedit /etc/fstab
```

remove the line
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
```

save exit gedit.

then 
```
gksudo gedit /boot/grub/device.map
```

remove the line with fd0, save exit

```
sudo update-grub
```

---

### Post by Siddiki on 2010-05-10
[QUOTE=frantid;9274730]ok, we need to edit 2 files.


you're probably more comfortable with a gui editor?  so

first

Done.  Reboot still requires the removal of the lines.  I will try to verify that the lines removed just now are in fact, gone.    S.

---

### Post by frantid on 2010-05-10
> **Siddiki said:**
> [QUOTE=frantid;9274730]ok, we need to edit 2 files.


you're probably more comfortable with a gui editor?  so



;)

be right back

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> [QUOTE=Siddiki;9274828]

;)

be right back

Just for more (unneeded?) information, here is a new run of boot_info reflecting the changes made.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,222,234    29,222,172   7 HPFS/NTFS
/dev/sda2          40,997,880    78,140,159    37,142,280   5 Extended
/dev/sda5          40,997,943    51,391,934    10,393,992   7 HPFS/NTFS
/dev/sda6          51,391,998    62,476,784    11,084,787  83 Linux
/dev/sda7          62,476,848    77,369,039    14,892,192  83 Linux
/dev/sda8          77,369,103    78,140,159       771,057  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B66C58A36C586063                       ntfs                                     
/dev/sda5        3A1DB15D26A575B0                       ntfs       NTFS                          
/dev/sda6        0cf5a1f2-6705-464d-8dfc-0a11e861f9ca   ext3       UBUNTU_ex3                    
/dev/sda7        496ca826-1cdc-4ed9-ab6e-1dba6074112e   ext4                                     
/dev/sda8        107dd150-c14a-4340-ad33-9986d7e11dcc   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b66c58a36c586063
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

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=107dd150-c14a-4340-ad33-9986d7e11dcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


=================== sda7: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
  34.6GB: boot/initrd.img-2.6.31-14-generic
  34.5GB: boot/vmlinuz-2.6.31-14-generic
  34.6GB: initrd.img
  34.5GB: vmlinuz


Thanks,   S.

---

### Post by frantid on 2010-05-10
How was the drive before you resized it for ubuntu?  Was it one big xp partition?  How much space did the xp take?  Did you resize it with the ubuntu installer on automatic or by manual or another tool?

I think we should try to run testdisk against the drive.  But you need to have some idea how it was before just to see how much sense the results make.

you can get it via the Ubuntu software center.

after install you run it in a terminal, 

sudo testdisk

Follow through with the steps here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

When you get to the stage that looks similar to this below, copy the text using the mouse and paste it.[IMG]http://www.cgsecurity.org/mw/images/First_results.gif[/IMG]

---

### Post by Siddiki on 2010-05-10
When you get to the stage that looks similar to this below, copy the text using the mouse and paste it.   Will do.  I have to run out until the evening.  I will get the results ASAP.  The HD(40G)was all used for XP.   TTYL     S.

---

### Post by frantid on 2010-05-10
I think we should try

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```that might help fix the search piece.

I'm out til tomorrow..

cheers

---

### Post by Siddiki on 2010-05-10
> **frantid said:**
> I think we should try

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```that might help fix the search piece.

I'm out til tomorrow..

cheers

I tried the above script and still the same, requires the deletes to boot from GRUB.  I then ran Testdisk and hope I have the info you wanted here:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172
 2 E extended              2552   0  1  4863 254 63   37142280
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 255 (HD)
 5 L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
   X extended              3199   0  1  3888 254 63   11084850
 6 L Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
   X extended              3889   0  1  4815 254 63   14892255
 7 L Linux                 3889   1  1  4815 254 63   14892192
   X extended              4816   0  1  4863 254 63     771120
 8 L Linux Swap            4816   1  1  4863 254 63     771057


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

Again, thanks and good night.     S.

---

### Post by frantid on 2010-05-11
before we go any further, can you see the data in your xp partition?  You go to Places on the menu, then Computer.  You should see the partitions on the left column, click to mount.  I would copy any data off to that flash drive you have.  You have to quit testdisk to mount it.  From the screen you were on hit, enter, q, q, q  -- it shows which keys to hit on the bottom of the screen.

---

### Post by Siddiki on 2010-05-11
[QUOTE=frantid;9279144]before we go any further, can you see the data in your xp partition?    

Good Morning, frantid, Yes, all the data appears to be there on the 15G partition and I got all that I needed; it is done.  I appreciate your help and this 'problem' has provided me with quite the learning experience once I find time to analyze just what you have done.    S.

---

### Post by frantid on 2010-05-11
I think we can probably recover the xp partition, but it's good you got your data off.   I just didn't want to attempt the partition repair before you did that.

It's fairly straight forward using testdisk, there's no guarantee's but it won't get any worse.  Testdisk is a nice tool, it doesn't make any changes until you tell it to write and it won't alter the data.  I also think the partition corrections might help fix the search function in grub.

The testdisk log will keep a record of the partition table plus, we can do a back up of the MBR & primary partition table with:  (I assume "rag" is the username?)

```

sudo dd if=/dev/sda of=/home/rag/MBR.img bs=512 count=1
```The error you got in testdisk means it's reading partition data that it doesn't agree with.  Start testdisk, create log, proceed when it selects the drive, then choose type - probably intel, 

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ MBR Code ]  Write TestDisk MBR code to first sector
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection

Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.

```Select geometry, move over to heads on the next screen.  hit enter, it will recommend a setting, in your case should be 255, hit enter.  then Ok.

It will return to the screen above, choose Analyse, then "quick search", then "no" for Vista.

You should get another listing of the partition table.  Press enter to get to the next screen.  Then choose "deeper search"  When you get those results paste them in.

---

### Post by frantid on 2010-05-11
I forgot, if you just want to go scorched earth and re-install -- that's cool.  But if you want to try and salvage it let me know.

---

### Post by Siddiki on 2010-05-11
> **frantid said:**
> I forgot, if you just want to go scorched earth and re-install -- that's cool.  But if you want to try and salvage it let me know.


Here is the info, I think.  If it is not even more trouble and time and you don't mind, we can see what 'just one more step' will do.  If not, we can just reinstall.  again thanks    S.

results of sudo dd.......

rag@rag-laptop:~$ sudo dd if=/dev/sda of=/home/rag/MBR.img bs=512 count=1
[sudo] password for rag: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 6.1461e-05 s, 8.3 MB/s
rag@rag-laptop:~$ 




Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  1818 254 63   29222172
D HPFS - NTFS              0   1  9  2551 254 63   40997809
L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
D Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
D Linux                 3465   1  1  3902 254 63    7036407
D Linux                 3889   1  1  4815 254 63   14892192
D Linux                 3931   1  1  4816 254 63   14233527
D Linux Swap            4816   1  1  4863 254 63     771057
D Linux Swap            4817   1  1  4863 254 63     754992



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
rag@rag-laptop:~$ ^C
rag@rag-laptop:~$

---

### Post by frantid on 2010-05-11
ok, let's try

let's do this so we can compare:

```
sudo parted /dev/sda unit chs print
```

---

### Post by Siddiki on 2010-05-11
> **frantid said:**
> ok, let's try

let's do this so we can compare:

```
sudo parted /dev/sda unit chs print
```

```

```

rag@rag-laptop:~$ sudo parted /dev/sda unit chs print
[sudo] password for rag: 
Model: ATA IC25N040ATCS05-0 (scsi)
Disk /dev/sda: 4863,254,62
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 4864,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start     End          Type      File system     Flags
 1      0,1,0     1818,254,62  primary   ntfs            boot
 2      2552,0,0  4863,254,62  extended
 5      2552,1,0  3198,254,62  logical   ntfs
 6      3199,1,0  3888,254,62  logical   ext3
 7      3889,1,0  4815,254,62  logical   ext4
 8      4816,1,0  4863,254,62  logical   linux-swap(v1)

rag@rag-laptop:~$ 

```

```

---

### Post by frantid on 2010-05-11
thanks, now you have to get back into testdisk, do all the steps over -- don't forget about setting the heads.

---

### Post by Siddiki on 2010-05-11
> **frantid said:**
> thanks, now you have to get back into testdisk, do all the steps over -- don't forget about setting the heads.


I still have the other terminal live with the last screen I sent.  Can I go from there?   S.

---

### Post by frantid on 2010-05-11
This is how I think it should look.  If you're wondering about the number differences between testdisk and parted, it's because one counts from zero at times.


```

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
Partition Start End Size in sectors
***** HPFS - NTFS 0 1 1 1818 254 63 29222172
D HPFS - NTFS 0 1 9 2551 254 63 40997809
L HPFS - NTFS 2552 1 1 3198 254 63 10393992 [NTFS]
**L** Linux 3199 1 1 3888 254 63 11084787 [UBUNTU_ex3]
D Linux 3465 1 1 3902 254 63 7036407
**L** Linux 3889 1 1 4815 254 63 14892192
D Linux 3931 1 1 4816 254 63 14233527
**L **Linux Swap 4816 1 1 4863 254 63 771057
D Linux Swap 4817 1 1 4863 254 63 754992
```To get it to look like that, (You're changing the "D" to either * for boot (XP), L for extended) use the arrow keys - left & right.  As you do it the lines will turn green, if I suggested something wrong it will turn red.  You can browse a list of files in the partition by typing "p".  That always amazes me because you can go into the wrong listings that are old remants and find files you thought you formated away.  Moral of that story, rewrite all hard drives you ever throw away with some type of secure wipe software.

---

### Post by frantid on 2010-05-11
yes, I just thought I saw a ctrl-c in your paste and you ended it.


edit:  duh on my part.  that was the copy command

---

### Post by frantid on 2010-05-11
Here's what it should look like, not the numbers but the colors.

[IMG]http://www.cgsecurity.org/mw/images/Set_partition_to_recover.gif[/IMG]

---

### Post by Siddiki on 2010-05-11
> **frantid said:**
> yes, I just thought I saw a ctrl-c in your paste and you ended it.

You may have.  Something has come up here and I have to take off.  I don't think I will be back until this evening.  I will follow instructions I have now and post the results.  Thank you.   S.

---

### Post by frantid on 2010-05-11
No worries, I think we're on diff. time zones, so I may not be awake when you're back.  The rest is pretty easy, just take it slow and sure.


once your satisfied with the table -- i.e. the green lines give you the right table.  Hit enter.  You will get the following type screen

[IMG]http://www.cgsecurity.org/mw/images/Menu_write.gif[/IMG]


select write and push enter.

Now you will have to reboot.  I'm not sure if the grub menu will work yet, might have to do: -- after the reboot not before.

```
sudo update-grub
```We still might have to repair the boot sector for xp.  Not too much more to go.  Let me know how it goes, or post any errors.

cheers.

---

### Post by Siddiki on 2010-05-12
[QUOTE=frantid;9282599]No worries, I think we're on diff. time zones, so I may not be awake when you're back.  The rest is pretty easy, just take it slow and sure.


once your satisfied with the table -- i.e. the green lines give you the right table.  Hit enter.  You will get the following type screen
select write and push enter.

Back again.  The machine is still here<G>.  Below is a 'Chronicle of the Ships', as it occurred.  This procedure is 'so far above my pay grade' I may never understand it, but thank you.   You were right about the ctrl-c, I automatically used the old DOS copy command rather than SHIFT-ctrl-c for Terminal so I had to start over.

After latest run of Testdisk    5/11  @2200 PDST:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63

The harddisk (40 GB / 37 GiB) seems too small! (< 41 GB / 39 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 4170   2  1  5097   0 63   14892192

[ Continue ]
EXT4 Large file Sparse superblock Recover, 7624 MB / 7271 MiB



After changes:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1818 254 63   29222172
D HPFS - NTFS              0   1  9  2551 254 63   40997809
L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
L Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
D Linux                 3465   1  1  3902 254 63    7036407
L Linux                 3889   1  1  4815 254 63   14892192
D Linux                 3931   1  1  4816 254 63   14233527
L Linux Swap            4816   1  1  4863 254 63     771057
D Linux Swap            4817   1  1  4863 254 63     754992




And 'the following screen':

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172
 2 E extended LBA          2552   0  1  4863 254 63   37142280
 5 L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
 6 L Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
 7 L Linux                 3889   1  1  4815 254 63   14892192
 8 L Linux Swap            4816   1  1  4863 254 63     771057



After sudo update-grub:     (boot to Ubuntu still requires the line deletions and XP won't (yet) boot)

rag@rag-laptop:~$ sudo update-grub
[sudo] password for rag: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
rag@rag-laptop:~$

---

### Post by frantid on 2010-05-12
Let's try to update your grub package, I know there were a few updates to grub in karmic.  I didn't want to do them until you got your data off.  But we can do them now.

```
sudo apt-get update
```then

```
sudo apt-get install grub-pc
```post any errors or held back packages.  It will say it needs to install dependent packages, grub-common perhaps some others; that's ok.

edit:  don't reboot after just yet after the update, run the bootinfoscript again and post results.

---

### Post by Siddiki on 2010-05-12
[/QUOTE]
edit:  don't reboot after just yet after the update, run the bootinfoscript again and post results.[/QUOTE]


My Bad!  I did *almost* what you wanted, but did not get the 'edit' until too late, where you said not to reboot so I did.  Results the same, deletes needed for Ubuntu & no XP.  Here are the results, however:   S.

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

rag@rag-laptop:~$ 


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,222,234    29,222,172   7 HPFS/NTFS
/dev/sda2          40,997,880    78,140,159    37,142,280   f W95 Ext d (LBA)
/dev/sda5          40,997,943    51,391,934    10,393,992   7 HPFS/NTFS
/dev/sda6          51,391,998    62,476,784    11,084,787  83 Linux
/dev/sda7          62,476,848    77,369,039    14,892,192  83 Linux
/dev/sda8          77,369,103    78,140,159       771,057  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B66C58A36C586063                       ntfs                                     
/dev/sda5        3A1DB15D26A575B0                       ntfs       NTFS                          
/dev/sda6        0cf5a1f2-6705-464d-8dfc-0a11e861f9ca   ext3       UBUNTU_ex3                    
/dev/sda7        496ca826-1cdc-4ed9-ab6e-1dba6074112e   ext4                                     
/dev/sda8        107dd150-c14a-4340-ad33-9986d7e11dcc   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 496ca826-1cdc-4ed9-ab6e-1dba6074112e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b66c58a36c586063
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

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=496ca826-1cdc-4ed9-ab6e-1dba6074112e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=107dd150-c14a-4340-ad33-9986d7e11dcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


=================== sda7: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  34.6GB: boot/initrd.img-2.6.31-14-generic
  34.5GB: boot/vmlinuz-2.6.31-14-generic
  34.6GB: initrd.img
  34.5GB: vmlinuz

---

### Post by frantid on 2010-05-12
No problem.  The name of the tool you tried was ultimate boot disk?  I think I need to research what they actually do when they try to rescue an XP partition.  We know they put syslinux in the mbr, but I wonder what they do to the partition.

give me a sec.

in the mean time, you can test if it really is the search function error.

try typing this in a grub command line.

```
search -u 496ca826-1cdc-4ed9-ab6e-1dba6074112e
```

you just get there by doing your normal edit on the menu, once in the edit, you can press Ctrl-c   or you can press "c" in the main menu.  that number has to match exactly.  Let's see if it can really find the right partition.

---

### Post by Siddiki on 2010-05-12
give me a sec.

in the mean time, you can test if it really is the search function error.

try typing this in a grub command line.........

Tried it from GRUB, and get the same error message  'no such device:  496c............'.
The Ultimate Boot CD for Windows fixed nothing, it could not find file or directory when it suggested to use fmbr and the like.  I wonder where GRUB found that 'set 496c.....' value  in the first place?     S.

---

### Post by frantid on 2010-05-12
That number is the id number of your disk partition.  It's the number you see when you type "sudo blkid".  Grub2 uses it to find your partitions in a multiple disk scenario.  It's a better way than saying /dev/sda, because sometimes that changes if you put a different drive in the system.

---

### Post by frantid on 2010-05-12
some thing put syslinux in the MBR.  But I wonder what else it did.

Can you go in the bios of the laptop and see if it sees the hd ok?  Have you ever done it before?

---

### Post by Siddiki on 2010-05-12
> **frantid said:**
> some thing put syslinux in the MBR.  But I wonder what else it did.

Can you go in the bios of the laptop and see if it sees the hd ok?  Have you ever done it before?

Yes.  Had to go in thru 'IBM Access' key  and the HD shows up in the 'boot order' section (IDE HDD0 IC........' so it must see it.    S.

---

### Post by frantid on 2010-05-12
ok we don't have to worry about search command anymore -- seems like a lot of [t40's can't do search]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408") with grub, a bios limitation.

so, we just have to edit them all out of your config or it will error.

```
gksudo gedit /boot/grub/grub.cfg
```

put a "#" sign in front of the "search --no-floppy --fs-uuid" lines every where in grub.cfg.  save and exit.  Do NOT do an update-grub.  If an update like a kernel update does an update-grub, you will have to do it again.

---

### Post by Siddiki on 2010-05-12
put a "#" sign in front of the "search --no-floppy --fs-uuid" lines every where in grub.cfg.  save and exit.  Do NOT do an update-grub.  If an update like a kernel update does an update-grub, you will have to do it again.

Tried, but when saving, it says it's on a 'read only disk'.  How do you remove the 'read only' flag?  S.

---

### Post by frantid on 2010-05-12
sudo chmod 777 /boot/grub/grub.cfg

---

### Post by Siddiki on 2010-05-12
> **frantid said:**
> sudo chmod 777 /boot/grub/grub.cfg


Way cool<G>.  Another command to try and remember.  I have all the past actions in file which I will try to analyze when all this is finished, one way or another.  It now boots with the Ubuntu menu entry without the 'deletes'  Thanks.    S.

---

### Post by frantid on 2010-05-12
Cool.

Now we can use testdisk again and hope that it can find the ntfs backup boot sector.  I'm not sure it can since the resize might have not brought it.

the directions are here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by frantid on 2010-05-12
If it can't restore the backup, we can try to "rebuild BS" and "check MFT", there's not much risk here because we already know the xp cd would not rebuild it.

We might be able to trick the cd, but hopefully testdisk will work.

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1 16391 253 54  263337345 [backup]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                              Rebuild boot sector
```

---

### Post by Siddiki on 2010-05-12
If it can't restore the backup, we can try to "rebuild BS" and "check MFT", there's not much risk here because we already know the xp cd would not rebuild it.

We might be able to trick the cd, but hopefully testdisk will work.

It doesn't seem find the boot sector.  I ran the rebuild just to see what it did.  I wonder if just reinstalling from the beginning would be better.  I am semi-learning from this, but I don't like to take up so much of your time.  I would format C, install XP, try Ubuntu live then install with WUBI, or is that a valid approach.  Below are more 'results' after some of my attempts at doing what I though you said<G>.  Should I have run the full testdisk and made more changes as before?  Thanks.  S.

```

```TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]
                List directories and files, copy data from NTFS




TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172
Directory /

dr-xr-xr-x     0     0         0  1-Apr-2010 13:49 .
dr-xr-xr-x     0     0         0  1-Apr-2010 13:49 ..
dr-xr-xr-x     0     0         0 29-Mar-2010 13:40 00887d7997cecb3c09
dr-xr-xr-x     0     0         0 30-Mar-2010 19:31 ARCHIVES
-r--r--r--     0     0         0 28-Mar-2010 19:06 AUTOEXEC.BAT
-r--r--r--     0     0       211 27-Mar-2010 19:53 boot.ini
dr-xr-xr-x     0     0         0  1-Apr-2010 15:13 Config.Msi
-r--r--r--     0     0         0 28-Mar-2010 19:06 CONFIG.SYS
dr-xr-xr-x     0     0         0 28-Mar-2010 19:11 Documents and Settings
dr-xr-xr-x     0     0         0 28-Mar-2010 19:36 DRIVERS
-r--r--r--     0     0         0 28-Mar-2010 19:06 IO.SYS
dr-xr-xr-x     0     0         0 29-Mar-2010 23:21 minint
-r--r--r--     0     0         0 28-Mar-2010 19:06 MSDOS.SYS
-r--r--r--     0     0     47564 29-Mar-2010 23:22 ntdetect.com
-r--r--r--     0     0    250032 27-Mar-2010 19:53 ntldr
                                                   Next
Use Right arrow to change directory, c to copy,
    q to quit



After 'rebuild boot sector:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172

filesystem size           29222172 29222161
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               1825546 1825546
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.

 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172

```

```

---

### Post by frantid on 2010-05-12
you have to do the geometry steps first, specifying heads.  Then do the rebuild.  I'm ok with continuing if you are.


if you want to re-install you would just have to reinstall xp, not karmic.  After xp, you would need to put grub back in the mbr.  Your choice really.

---

### Post by Siddiki on 2010-05-12
> **frantid said:**
> you have to do the geometry steps first, specifying heads.  Then do the rebuild.  I'm ok with continuing if you are.


if you want to re-install you would just have to reinstall xp, not karmic.  After xp, you would need to put grub back in the mbr.  Your choice really.

 Good by me, frantid.  I will go through all the steps after a re-read and let you know the outcome.  Things moved a bit fast there at the end.  I will reserve the re-build for later on if/when.  Thanks.     S.

---

### Post by frantid on 2010-05-12
no problem, just post back if you need something.

you can enjoy the ubuntu side, it should be fine.  Just remember if you do updates and it doesn't boot it's probably the grub search function.  you're good at getting by that one.


cheers.

---

### Post by Siddiki on 2010-05-13
> **frantid said:**
> no problem, just post back if you need something.

you can enjoy the ubuntu side, it should be fine.  Just remember if you do updates and it doesn't boot it's probably the grub search function.  you're good at getting by that one.


cheers.

 G'day, I'm back at it; just needed some time to fall back and regroup---I was getting even more lost than usual. I needed to find out where I was (or wasn't).  I did get to play around with Ubuntu in the process too.  I stepped through again and changed the geometry, saved and rebooted, but it doesn't seem to stick.  Should it?  I still have the 'incorrect number of heads...' message here in Testdisk.   More fun, my phone line is in and out, but the DSL seems unaffected, so replies may be delayed. Thanks for your patience.   S.

```

```

5/13  1000

Testdisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1818 254 63   29222172
L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
L Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
L Linux                 3889   1  1  4815 254 63   14892192
L Linux Swap            4816   1  1  4863 254 63     771057



TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  1818 254 63   29222172
 2 E extended LBA          2552   0  1  4863 254 63   37142280
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 255 (HD)
 5 L HPFS - NTFS           2552   1  1  3198 254 63   10393992 [NTFS]
   X extended              3199   0  1  3888 254 63   11084850
 6 L Linux                 3199   1  1  3888 254 63   11084787 [UBUNTU_ex3]
   X extended              3889   0  1  4815 254 63   14892255
 7 L Linux                 3889   1  1  4815 254 63   14892192
   X extended              4816   0  1  4863 254 63     771120
 8 L Linux Swap            4816   1  1  4863 254 63     771057


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition




```

```

---

### Post by frantid on 2010-05-14
Hi Siddiki,

I've been doing some research on the t40.  The search function not working was bothering me.  Also when you posted testdisks, printout of your files in your xp partition.  I saw the listing of "c:\minit"  That directory is part of a windows pre-install environment (WinPE).  It is almost never in a regular XP install.

To make a long story short, IBM in it's wisdom put a protected area inside the normal xp partition plus a hidden protected partition for your recovery software.  The default bios setup does not allow, direct listing of all the partitions which is why the search function fails.  Also the partition boot sector of the xp partition is nonstandard.  Instead of the normal single sector, the t40 has 4 sectors.  Therefore the normal xp cd fixboot and fixmbr will not work.  This is also why testdisk is seeing those errors.  IBM also uses a modified boot loader in the MBR this is why the bootinfoscript was reporting syslinux in the boot sectors.  see here:

[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)

So you have a decision to make. Two options I think:

1. If you want to use the default software that came with your t40 -- ibm backups, rescue cd, pre-installed software, the special boot options allowing restores etc; you will have to recover the laptop with the rescue cd's.  This will restore the boot sector and xp partition to its original form.  Then I would do as you mentioned, install ubuntu inside of windows with wubi.

2. If you don't care about the IBM special features, you have to go into the bios and disable predesktop area, from the link above:

```
The BIOS has three settings for the "IBM Predesktop Area" (in the  Security category): 
 
[LIST]
[*]Secure: No user or SW-initiated changes; Contents hidden from OS
[*]Normal: Change allowed; Contents hidden from OS
[*]Disabled: Not Usable; Visible and Reclaimable
[/LIST]

```If you do this, make sure you still have a workable copy of the restore cd's.  

That website above has a lot of resources for people that want to use linux on their thinkpads.  I suggest reading up on your options before you decide.  I think testdisk and xp will not succeed in fixing the partition boot record, until the bios setting is disabled.

-- my hope is that all it would take to fix xp, is disabling the bios setting - then using the xp cd to run fixboot c:   However, I do not know what will happen when grub and xp all of the sudden see an extra partition.  It could be as easy as changing /dev/sda1 to /dev/sda2 in linux and the respective grub settings.  Or it might alter the disk structure in such a way that the partition table has to be rebuilt for linux and xp to work correctly.  Unfortunately, I can't predict it either way.

let me know, I'll try to help.

---

### Post by Siddiki on 2010-05-14
> **frantid said:**
> Hi Siddiki,

I've been doing some research on the t40.  The search function not working was bothering me.  Also when you posted testdisks, printout of your files in your xp partition.  I saw the listing of "c:\minit"  That directory is part of a windows pre-install environment (WinPE).  It is almost never in a regular XP install.



G'morning,  My thanks frantid, for all the help and info.  Good old  IBM.  Looks like it's time for another laptop<G>!   I did have  some driver issues getting the wireless to work much earlier on.   Unfortunately, I don't have a set of restore CDs so that option is out.   If I lock out all the IBM bells and whistles, I guess I could just  format and start over clean with an XP install then WUBI/Ubuntu, giving  me an at least semi-known quantity.  Really, with the laptop. other than  the usual word processing/spread sheet and music/DVD functions which  Ubuntu seems to have apps for, that's all I should need (not necessarily  want <G>).  I have to investigate first whether Zipper's  SmartlinkIV program is supported under Ubuntu as that is the only  nonstandard app I absolutely _need_ on the laptop.  I guess I could try it for a while  from the present configuration before I commit.  From what little I've  read, Ubuntu is stable with normal apps and shouldn't be an issue.  Maybe I  should bite the bullet and just commit to learning Linux for the  laptop.  Decisions, decisions.  Your opinion (as mine got me into this  situation!)?    S.

---

### Post by frantid on 2010-05-14
Well, supposedly the recovery partition is not tampered with if the bios setting is set at default.  So don't change that bios setting yet.

Personally, I would first try to see if you can get access to the Host Protected Area (HPA)

You should be able to hit "access ibm" or similar to get the utility to start.  I think the button you hit to get to the bios.  Does it present you with a menu?  It would be under utilities or repair -- not sure I've never seen it.

From what I read, you should be able create recovery disks - 1 cd & 1dvd using the utility.  Try to access it, just don't make any changes.  tell me what you see there.

---

### Post by frantid on 2010-05-14
Actually, further reading...

states running the recovery from the hpa only over writes the first partition - your xp.  It should give you an option to create a recovery disk (just a bootable cd with access to the hpa) after first boot into xp.

So this might be your fix, recover from the hpa.  This will fix xp, you boot into it, set it up run all million xp updates.  Then once that is good, restore grub to the MBR and you've got both.  Let's see how good these IBM engineers were at the time.

---

### Post by Siddiki on 2010-05-14
> **frantid said:**
> Actually, further reading...

states running the recovery from the hpa only over writes the first partition - your xp.  It should give you an option to create a recovery disk (just a bootable cd with access to the hpa) after first boot into xp.

So this might be your fix, recover from the hpa.  This will fix xp, you boot into it, set it up run all million xp updates.  Then once that is good, restore grub to the MBR and you've got both.  Let's see how good these IBM engineers were at the time.

Looked in the Access IBM again.  Under Create Diag. Disks, they require a floppy drive.  They do not load a CD driver and I don't see the USB/flash so likely no driver there either.  The 'Recover to factory contents' may just wipe the XP partition and fix the MBR to boot there.  Actually I could not do much (more) damage if it just cleans out that first partition.  I would just have to reinstall XP (and the n-million updates).  (This is shades of Compaq, with its hidden proprietary partitions and programs.)   That would leave me safe with an XP OS too, so no worry about Linux support for any apps.  Sounds better and better from here.  Thanks for your research.   S.

---

### Post by Siddiki on 2010-05-14
I wonder if it will return to one large original partition?  Guess I can adjust that as needed.  S.

---

### Post by frantid on 2010-05-14
No problem.  Let me know how it turns out.  I don't know if it will just automatically pick the first partition or if it will prompt you.  

After all the reading, I can say one thing for certain.  The only way you are going to get xp back is wiping it out of that partition first when doing the factory restore.  Seems the xp install is tied to the bios as a feature.

Unless you have a separate xp license from a different xp cd, but then you'd have to find all the drivers and you'd still have to wipe that partition.

And to think my company was looking at a thinkpads, dodged that bullet.

---

### Post by frantid on 2010-05-14
From what I read, as long as there is room, it will just leave the partition as is.

---

### Post by Siddiki on 2010-05-14
> **frantid said:**
> No problem.  Let me know how it turns out.  I don't know if it will just automatically pick the first partition or if it will prompt you.  

After all the reading, I can say one thing for certain.  The only way you are going to get xp back is wiping it out of that partition first when doing the factory restore.  Seems the xp install is tied to the bios as a feature.

And to think my company was looking at a thinkpads, dodged that bullet.

I will do it today ("Films at 11:00")  Thanks for your help and patience.  I will PM the info to you as this thread is about dead (and ending up more XP/T-40 than an Ubuntu forum needs) Take care, and again, tnx.   S.

---

### Post by Siddiki on 2010-05-14
The Recovery program does reformat the HD and reinstall, or so it says.  S.

---

### Post by frantid on 2010-05-14
this is where I got info about using the restore from the hard drive rather than the cd's.

[http://forum.thinkpads.com/viewtopic.php?p=452705#p452705](http://forum.thinkpads.com/viewtopic.php?p=452705#p452705)

> , restoring Factory Contents from the hard drive only overwrites the C:  partition and data.

so I believe karmic will be safe.

---

### Post by Siddiki on 2010-05-14
> **frantid said:**
>  so I believe karmic will be safe.
  Karmic is, I believe, no more, thanks to me with the help of IBM!  I ran the 'Reinstall' function from Access and it 'Fixed several partition problems' then it fails.  I looked at it with Parted and it now has one 37G empty partition!  I tried to run the XP install CD and it told it couldn't find the disk (35128 MB, disk 0, id 0, bus 0)! Looks like it will be an external format, which will mean trying to find all the T-40 drivers, as, if they are not hidden in some hidden partition, they are gone. Such is life. I may try another install of Ubuntu just to see what happens, but looks terminal (no pun intended)  S.

---

### Post by frantid on 2010-05-15
I read a few failed restore stories before, some had success after making sure the hard drive is listed as the first boot device - i.e. not cd or usb first.   

you could call ibm support, they can give access to download or send the factory restore cd's if the hpa is broken.  I just wouldn't mention ubuntu in the call.  good luck

edit:  actually, since it redid all the partitions and MBR -- it would have needed to reboot after, the start the restore again.

---

