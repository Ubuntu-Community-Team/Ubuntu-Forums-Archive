---
title: "Ubuntu installed first, WinXP second; restoring GRUB2?"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Incarnation on 2010-06-14
Hi everyone.

As you can tell from the title, I am going to attempt to install Windows XP on a separate partition on the same physical hard drive after having installed Ubuntu (9.10) which, by default, installed Grub2.

I was told that it was possible, if I could make a back-up and subsequently restore the Master Boot Record - and then configure Grub2 to add an option to load Windows XP.

Can anyone please provide guidance so that I can complete this task successfully?

Thank you in advance.

---

### Post by garvinrick4 on 2010-06-14
> **Incarnation said:**
> Hi everyone.

As you can tell from the title, I am going to attempt to install Windows XP on a separate partition on the same physical hard drive after having installed Ubuntu (9.10) which, by default, installed Grub2.

I was told that it was possible, if I could make a back-up and subsequently restore the Master Boot Record - and then configure Grub2 to add an option to load Windows XP.

Can anyone please provide guidance so that I can complete this task successfully?

Thank you in advance. Have you already install Ubuntu? If so please give me the results of these two pieces of code and copy and paste to this thread.
```
sudo fdisk -l
```  (small L)
```
sudo blkid 
```  (second letter small L)

If you have not installed anything on the machine tell me that also and how much Ram do you have? It can be done.

---

### Post by wilee-nilee on 2010-06-14
On IIRC we haven't confirmed the grub type so post the script in my sig with code tags as well

---

### Post by Incarnation on 2010-06-14
Hello Garvin

There are 2 gigabytes of RAM installed on this machine.

fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08480847

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6709    53890011   83  Linux
/dev/sda2            6710       19457   102398310    5  Extended
/dev/sda5           18934       19457     4208998+  82  Linux swap / Solaris
/dev/sda6            6710       18933    98189217   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a100a0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS
```blkid:
```
/dev/sda5: TYPE="swap" 
/dev/sda6: TYPE="ext4" 
/dev/sdb1: TYPE="ntfs"
```

That's okay, right?

---

### Post by Incarnation on 2010-06-14
Hello wilee-nilee

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```Do you require the rest of the file as well? It's kind of long..

---

### Post by wilee-nilee on 2010-06-14
Yeah post the whole thing, thanks garvinrick4 knows this stuff to.

You can edit the original post of the script by going to advanced if needed to just paste the whole thing in and then hitting the # in the panel if the code tags get removed

---

### Post by Incarnation on 2010-06-14
Okay, here's the rest of it:

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08480847

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   107,780,084   107,780,022  83 Linux
/dev/sda2         107,780,085   312,576,704   204,796,620   5 Extended
/dev/sda5         304,158,708   312,576,704     8,417,997  82 Linux swap / Solaris
/dev/sda6         107,780,211   304,158,644   196,378,434  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a100a0f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        045c80a2-73a9-4713-90fc-380d990cac98   swap                                     
/dev/sda6        b8e2eece-d728-44c3-84d8-cd2183770f4d   ext4                                     
/dev/sdb1        A0147BB4147B8BD2                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set b8e2eece-d728-44c3-84d8-cd2183770f4d
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b8e2eece-d728-44c3-84d8-cd2183770f4d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=b8e2eece-d728-44c3-84d8-cd2183770f4d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b8e2eece-d728-44c3-84d8-cd2183770f4d
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=b8e2eece-d728-44c3-84d8-cd2183770f4d ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b8e2eece-d728-44c3-84d8-cd2183770f4d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b8e2eece-d728-44c3-84d8-cd2183770f4d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b8e2eece-d728-44c3-84d8-cd2183770f4d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b8e2eece-d728-44c3-84d8-cd2183770f4d ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b8e2eece-d728-44c3-84d8-cd2183770f4d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=045c80a2-73a9-4713-90fc-380d990cac98 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  55.3GB: boot/grub/core.img
  58.3GB: boot/grub/grub.cfg
  55.7GB: boot/initrd.img-2.6.31-14-generic
  56.0GB: boot/initrd.img-2.6.31-22-generic
  55.7GB: boot/vmlinuz-2.6.31-14-generic
  55.8GB: boot/vmlinuz-2.6.31-22-generic
  56.0GB: initrd.img
  55.7GB: initrd.img.old
  55.8GB: vmlinuz
  55.7GB: vmlinuz.old

```

---

### Post by wilee-nilee on 2010-06-14
So we should probably look in the bios to make sure we know if the HD is set to sata or ide. If it is sata you will need a sata driver to install XP. XP will install into ide without drivers though, but if you have Ubuntu installed with it being sata I don't think it will boot when changed to ide. Others can confirm this.

---

### Post by garvinrick4 on 2010-06-14
You have to make room for the XP partition on your drive and make it a primary partition 
formatted in NTFS,

So we will Go into System/ADmin to gparted to your sda drive and right click on the partition you want to shrink and resize it. If you had room all the better, if not resize it.
do not forget to click on green Arrow after you resize to apply it. Nothing is official in gparted until it is applied.  You do not really need the swap so you can delete that one.
Shrink the Extended partition because Windows needs a Primary partition and inside of extended are logical partitions where linux can exsist in logical or primary for that matter.
 Once you have your space for xp in a primary partition formatted in ntfs by right clicking on left over space and choosing New, then format in ntfs. Now go over and right click on sda6 your 9.10 install and label it karmic Go to your XP install disk and put it in where ever it was given sda1 sda3 or sda4. The grub always go's in sda not sda1 or sda2 just sda. So install xp when done take out disk and put in Ubuntu disk. and choose try ubuntu. 
Now open up a terminal and put in this code. We are going to overwrite the XP grub we just installed.

```
sudo mkdir /media/karmic
``````
sudo mount /dev/sda6 /media/karmic
```                          ```
sudo grub-install --recheck --root-directory=/media/karmic [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/karmic
```   ( Not a typo)

remove disk and boot and will have a boot menu with grub2 installed in sda
Boot into your Ubuntu install and give these 2 commands it a terminal one at a time.

sudo update-grub

sudo grub-mkconfig

---

### Post by wilee-nilee on 2010-06-14
Thats all correct garvinrick4, but if the HD is set to sata XP wont install without drivers.

---

### Post by Incarnation on 2010-06-14
> **wilee-nilee said:**
> So we should probably look in the bios to make sure we know if the HD is set to sata or ide. If it is sata you will need a sata driver to install XP. XP will install into ide without drivers though, but if you have Ubuntu installed with it being sata I don't think it will boot when changed to ide. Others can confirm this.

Both drives are physically hooked up via SATA cables; BIOS reports them as being SATA as well.

---

### Post by wilee-nilee on 2010-06-14
> **Incarnation said:**
> Both drives are physically hooked up via SATA cables; BIOS reports them as being SATA as well.

It's good that we checked, XP wont install to sata without the sata drivers being on the CD or on a floppy or thumb for the f6 prompt at booting in the installation.

I have never had to install with adding sata drivers, and this should be confirmed by others, in whether I am correct and instructions on how to do so if needed. You can install XP to the Sun virtual though quite easily as your system is. XP runs quite well in a virtual, it just wont have the same 3d for gaming and other programs that would use this I believe.

Here is a link for the sun site if you want to at least get up and running while the sata issue is looked over.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Incarnation on 2010-06-15
Actually, I managed to install WinXP; I think it must be the install version I'm using; it comes with service pack 3 integrated into the installation, maybe that's why?

Anyhow, I'm typing all this using the Ubuntu 9.10 LiveUSB.

I just completed garvin's instructions, but for some reason when I installed windows, my 500gb hard drive was assigned drive letter C: while the 160gb which houses the partition on which WinXP exists was assigned drive letter G:

The reason I mention that is that it might have something to do with the fact that what was before sda6 is not sda5. Obviously I modified the commands.

```
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/media/karmic /dev/sda
Installation finished. No error reported.
This is the contents of the device map /media/karmic/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
```Unmounting didn't seem to work - no such command exists? Is it a function of a newer version of Ubuntu?

```
ubuntu@ubuntu:~$ sudo unmount /media/karmic
sudo: unmount: command not found
ubuntu@ubuntu:~$ man unmount
No manual entry for unmount
```The rest of the process was a success; I had a more detailed reply written and I was going to post it but it seems like it didn't save correctly, and I've forgotten what else I was going to post... sorry! I installed VirtualBox as well, it's very interesting but not quite as magical as I thought it would be.

Anyway thank you for both of your help, it was really great. I thought I would have to do electronic heart-bypass just to get this thing working - things have changed for the better.

---

### Post by garvinrick4 on 2010-06-15
The command is

```
sudo umount /media/karmic 
``` That is not a typo


In windows with 2 installs I do not believe you are allowed 2 named C: drive when both
installs are recognized. Do not know for sure but seems like a lot of software in Windows would
look for C: to install its wares by default, as I say not sure but seems logical. Post here if any problems
with XP on sda and sdb if you would please. Seems like a problem many would have incountered before now.

---

### Post by Incarnation on 2010-06-15
Oh... crud. I misread it is unmount by accident; I was wondering why you said "that's not a typo" the first time around? :/

I can't be sure why windows picked the G: drive, I'm literally just thanking my lucky stars it worked at all.

If I run into any problems I'll make a post, yes? But from the looks of things, things will be just fine - save for the usual XP horrors... getting the machine compromised by hackers and having spyware hosted on it and who knows what else.

---

