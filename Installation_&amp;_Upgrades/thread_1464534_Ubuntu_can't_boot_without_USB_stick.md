---
title: "Ubuntu can't boot without USB stick"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by jadmaestro on 2010-04-28
Hello all...
I'm running Ubuntu 9.10 on my notebook by booting from USB hard drive and running XP on my internal hard disk. Everything works well. One of my friend interested in using Ubuntu by booting from his USB hard drive. So I did the same step that I previously installed on my USB hard drive.


Here is the step how I successfully installed Karmic on my USB drive :

[I]1. Install Ubuntu to my USB stick using unetbooting unetbootin-windows-429.exe.

2. Boot from USB stick. Run installation and choose specify partition manually. I create a partition of swap and ext4. Installed Ubuntu on ext4. Works fine

3. Change my boot sequence to USB hard drive. Remove the USB stick. Ubuntu 9.10 was installed without any problems.
[/I]


So, I used the same method and installed Ubuntu into my friend USB hard drive. Everything works, grub2 is fine, update is working. So, I removed the USB stick as it is no longer needed. 

What happened is that the USB hard disk is not recognize in the boot sequence when the USB stick is removed. The USB hard disk is only recognized when I plugged in the USB stick and there I can select the USB hard disk as the primary boot. I really have no idea what to do because everything works well on my machine. My friend is really frustrated and already given up. 

I need help so that I can run Ubuntu on my friend's USB hard disk without plugging in the USB stick together. 

Here is the information of my friend's notebook :

[I]Model : HP Pavilion DV1000
Internal Operating System : Windows XP
USB hard drive : Western Digital 250GB[/I]

Please help me with tutorial how to overcome this problem...

Thanks

---

### Post by mikewhatever on 2010-04-28
From your Ubuntu installation, please post the outputs of the following commands:

cat /boot/grub/device.map

sudo fdisk -l

---

### Post by jadmaestro on 2010-04-28
Thanks for the feedback. Here is another problem. I am now using my friend USB hard drive as portable ubuntu on my notebook and ubuntu is running perfectly without the USB stick. This is weird. I think the problem lies on my friend notebook, not the USB hard disk or the USB stick.

And I tried to run ubuntu once again in my friend notebook (together with the USB stick) but the system crashed. Immediately after start up, the computer shut down. I can't run the following command on his notebook.

> 
cat /boot/grub/device.map

sudo fdisk -lThings are getting complicated...any suggestions?

---

### Post by Vined Adobo on 2010-04-28
[QUOTE=[I]

3. Change my boot sequence to USB hard drive. Remove the USB stick. Ubuntu 9.10 was installed without any problems.
[/I]


So, I used the same method and installed Ubuntu into my friend USB hard drive. Everything works, grub2 is fine, update is working. So, I removed the USB stick as it is no longer needed. 

What happened is that the USB hard disk is not recognize in the boot sequence when the USB stick is removed. The USB hard disk is only recognized when I plugged in the USB stick and there I can select the USB hard disk as the primary boot. I really have no idea what to do because everything works well on my machine. My friend is really frustrated and already given up. 

[/QUOTE]

It sounds to me that the grub you're booting from is on your USB stick.  Is there also a grub on the USB hard drive?  Before I committed to Ubuntu on a full-time basis, I had Ubuntu working from a memory stick with grub on the stick.  My laptop was unchanged, so if the memory stick was plugged in, I got the choice of Windows or Ubuntu.  Without the stick in, it simply booted windows because the windows bootloader was never changed.  This is probably why the other responder wanted you to list a map of how you boot.

Thanks,
Dave

---

### Post by jadmaestro on 2010-04-29
> rizal@rizal-laptop:~$ cat /boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
rizal@rizal-laptop:~$ 
rizal@rizal-laptop:~$ sudo fdisk -l 
[sudo] password for rizal: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31543153

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1913    15366141    7  HPFS/NTFS
/dev/sda2            1914        4864    23703907+   f  W95 Ext'd (LBA)
/dev/sda5            1914        3443    12289693+   7  HPFS/NTFS
/dev/sda6            3444        4864    11414151    7  HPFS/NTFS

Disk /dev/sdb: 4009 MB, 4009754624 bytes
51 heads, 51 sectors/track, 3010 cylinders
Units = cylinders of 2601 * 512 = 1331712 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3011     3915204    b  W95 FAT32

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb86462b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866   82  Linux swap / Solaris
/dev/sdc2            2623       30401   223134817+   7  HPFS/NTFS
/dev/sdc3   *         244        2622    19109317+  83  Linux

Partition table entries are not in disk order


Here is the command...have any ideas what is going on? 
Still I have to plug in the USB stick to run Ubuntu on this machine ( HP DV1000) and I have to disable the USB stick boot option so then I can run the ubuntu USB disk drive without crashing up warning appeared.

And yes the GRUB is working on the USB disk drive. Tried on other notebook and works well instead of this notebook.

---

### Post by mikewhatever on 2010-04-29
Right, can you also post the output of *cat /boot/grub/grub.cfg*. I forgot to ask for it.
I suspect that what happens is the following - Grub looks for its files on sdc3, which is the linux partition, but when you don't plug in the usb stick, sdc becomes sdb, in which case grub can't find sdc3 with its files.

---

### Post by jadmaestro on 2010-04-29
> **mikewhatever said:**
> Right, can you also post the output of *cat /boot/grub/grub.cfg*. I forgot to ask for it.
I suspect that what happens is the following - Grub looks for its files on sdc3, which is the linux partition, but when you don't plug in the usb stick, sdc becomes sdb, in which case grub can't find sdc3 with its files.

> rizal@rizal-laptop:~$ cat /boot/grub/grub.cfg
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
set root=(hd1,3)
search --no-floppy --fs-uuid --set 9bea2a4c-3f98-4292-9d14-5ca33fda4c84
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
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9bea2a4c-3f98-4292-9d14-5ca33fda4c84
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9bea2a4c-3f98-4292-9d14-5ca33fda4c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 9bea2a4c-3f98-4292-9d14-5ca33fda4c84
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9bea2a4c-3f98-4292-9d14-5ca33fda4c84 ro single 
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
    search --no-floppy --fs-uuid --set 60449a084499e0d8
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

here the output.  I think maybe you are right. I completely have no idea how to solve this. I'm a total newbie here..

---

### Post by mikewhatever on 2010-04-29
> **jadmaestro said:**
> here the output.  I think maybe you are right. I completely have no idea how to solve this. I'm a total newbie here..

Should be fairly easy. 

```
gksudo gedit /boot/grub/device.map
```

delete everything from that file and put in the following:

```
(hd1) /dev/sdc
```

Save and exit.

---

