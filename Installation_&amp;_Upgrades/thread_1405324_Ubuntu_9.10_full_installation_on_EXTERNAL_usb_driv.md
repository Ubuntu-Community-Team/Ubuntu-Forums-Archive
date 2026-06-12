---
title: "Ubuntu 9.10 full installation on EXTERNAL usb drive"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by lesodk on 2010-02-12
Dear readers,

Up till now i have used this guide to install ubuntu to an external hard drive.

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

The idea is to install grub on the external hard drive. The idea is to go to "/media/disk/boot/grub" and modify "menu.lst". Otherwise the grub loader will not correctly load ubuntu on startup. However, with Ubuntu 9.10 it seems that there are no menu.lst file.

My question is therefore, how do i modify so that i can boot correctly from the USB?

Best,

---

### Post by darkod on 2010-02-12
> **lesodk said:**
> Dear readers,

Up till now i have used this guide to install ubuntu to an external hard drive.

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

The idea is to install grub on the external hard drive. The idea is to go to "/media/disk/boot/grub" and modify "menu.lst". Otherwise the grub loader will not correctly load ubuntu on startup. However, with Ubuntu 9.10 it seems that there are no menu.lst file.

My question is therefore, how do i modify so that i can boot correctly from the USB?

Best,

With the new grub2 that uses UUID to locate the exact partition, I don't think you need to worry about that.
Just make sure you do the thing with checking advanced options and making sure grub2 is installed on the ext hdd. Then you can boot from it without any problem.
People that have done it haven't reported that they need to change the grub2 config files.
In case you do need to change something, you'll deal with it when it comes to that.

---

### Post by lesodk on 2010-02-12
Hey, and thanks for the quick answer.
Although i use the advanced button and set both my installation and grub on the dev/sdb disk it says "error: disk not found .... "
on startup. 

It goes to the grub menu when i boot from the usb, but when i select ubuntu it says "error: disk not found ...".

Any suggestions?

Best,

Thanks.

---

### Post by darkod on 2010-02-12
> **lesodk said:**
> Hey, and thanks for the quick answer.
Although i use the advanced button and set both my installation and grub on the dev/sdb disk it says "error: disk not found .... "
on startup. 

It goes to the grub menu when i boot from the usb, but when i select ubuntu it says "error: disk not found ...".

Any suggestions?

Best,

Thanks.

In order not to make assumptions, boot with the live desktop and with the ext hdd connected download the script in my signature, move it on desktop for example, and run it with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by lesodk on 2010-02-12
Thanks a lot for the quick reply. Here is the code

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84a503c0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   317,941,759   317,734,912   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00092118

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,761,004   476,760,942  83 Linux
/dev/sdb2         476,761,005   488,392,064    11,631,060   5 Extended
/dev/sdb5         476,761,068   488,392,064    11,630,997  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5A9602F49602D105                       ntfs       System Reserved               
/dev/sda2        68360A31360A0134                       ntfs                                     
/dev/sdb1        1e67da0d-20cb-4c26-9380-e6e490834c80   ext4                                     
/dev/sdb5        14d1cbff-1ff9-4716-a4f0-d48b4fe2149b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/1e67da0d-20cb-4c26-9380-e6e490834c80 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 1e67da0d-20cb-4c26-9380-e6e490834c80
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1e67da0d-20cb-4c26-9380-e6e490834c80
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1e67da0d-20cb-4c26-9380-e6e490834c80 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1e67da0d-20cb-4c26-9380-e6e490834c80
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1e67da0d-20cb-4c26-9380-e6e490834c80 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5a9602f49602d105
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=1e67da0d-20cb-4c26-9380-e6e490834c80 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=14d1cbff-1ff9-4716-a4f0-d48b4fe2149b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/core.img
  11.2GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz
```

---

### Post by darkod on 2010-02-12
It looks fine but I have one suspicion. When it gives the disk error, does it report one long number/letters? Can you post it here just to check something?

---

### Post by lesodk on 2010-02-12
I get the error: 

"error: out of disk

Press any key to continue..."

Any suggestions?

Thanks for helping me.

---

### Post by darkod on 2010-02-12
This seems to be some kind of bug and I haven't found why it happens. But I did find a fix that should work. Try the following (you'll need to write this down probably because you need to edit the grub menu):

1. Restart the computer and when the grub menu shows up, leave the ubuntu selected but DON'T hit enter, instead hit 'e'. That will show you a few lines of commands that are actually booting ubuntu.

2. You should be able to move the cursor with the arrows. Find and delete two lines which should look like:

recordfail=1
if [ -n ${have_grubenv} ]...

3. After deleting them hit Ctrl + X which should boot ubuntu successfully.

4. Once ubuntu boots up, open one of the grub2 config files with:

sudo gedit /etc/grub.d/10_linux

5. Find the same two lines and comment them out by putting the sign # at the beggining of the lines. That makes it ignore the rest of the line if it has # at the start.

6. In terminal run:

sudo update-grub

That should sort it out. Restart and just select ubuntu and see if it will boot. The above might sound complicated at first glance but don't worry, it's not that difficult. :)

---

### Post by lesodk on 2010-02-12
Thank you for the reply.

After deleting the two lines, and hitting CTRL+X i get the message:

"error: no such device: 1e67da0d-20cb-4c26-9380-e6e490834c80"

I can't really do anything from here.

Can you help?

Thanks!!

---

### Post by darkod on 2010-02-12
> **lesodk said:**
> Thank you for the reply.

After deleting the two lines, and hitting CTRL+X i get the message:

"error: no such device: 1e67da0d-20cb-4c26-9380-e6e490834c80"

I can't really do anything from here.

Can you help?

Thanks!!

:( I'm puzzled. That is the correct UUID identifier for your ubuntu root partition, you can clearly see that in your results file:
/dev/sdb1        1e67da0d-20cb-4c26-9380-e6e490834c80

The UUID is correct. I have no idea why it's complaining.

---

### Post by darkod on 2010-02-12
OK, new idea. Again restart and edit the ubuntu boot commands, delete the same two lines as before, but this time also delete the line starting with 'search' and ending with that long UUID string, and also in the line starting with linux amend root=/dev/sdb1 and one small change in set root=.
So, after all of this, the commands to boot should look like:

insmod ext2
set root=(hd0,1)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
boot

Those are the basic minimum commands I think. If it doesn't boot, try changing the second line to:
set root=(hd1,1)

and try again.

---

### Post by darkod on 2010-02-12
I've also asked someone more experienced to help, so hopefully he's smarter than me. :)

---

### Post by lesodk on 2010-02-12
dear darkod,

I am really glad that you are helping me. Unfortunatly it still says "error: out of disk", even with the changes.

I dont have a clue what is wrong.

Thanks for replying.

Best,

---

### Post by kansasnoob on 2010-02-12
Nothing at all wrong with what Darko is suggesting that I can see. Now, grub2 is getting better in Lucid and I wished I'd worked out a way to upgrade grub2's packages through a chroot but I haven't so for now I'd try this:

Boot into the live Ubuntu desktop and run the following commands (you must copy-n-paste):

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Just to be sure you're in Karmic run:

```
lsb_release -a
```

Since you're in Karmic/9.10 then resolve this bug:

[http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now we're down to business:

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common
```

```
apt-get install grub
```

```
update-grub
```

```
grub-install /dev/sdb
```

Now we have to use a grub shell:

```
grub
```

You should see the commad prompt change to grub> so then:

```
find /boot/grub/stage1
```

That should show (hd1,0) - and BTW that's a ZERO! So then:

```
root (hd1,0)
```

```
setup (hd1)
```

And you'll hopefully see:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Regardless you must run:

```
quit
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

then hopefully you can reboot and have Ubuntu with the external drive plugged in and just Win when it's not.

---

### Post by lesodk on 2010-02-12
Dear kansasnoob,

As you can read from my posts i am not really an experienced linux user. Can you therefore tell me, what you mean by resolving the bug?

I can't really try anything before i know what i should do at that step. However, thanks alot anyway for trying to help me. I hope to hear from you again.

Best,

Emil.

---

### Post by meierfra. on 2010-02-12
> As you can read from my posts i am not really an experienced linux user. Can you therefore tell me, what you mean by resolving the bug?

That was just a comment which you can ignore (the next two lines of code  will resolve that bug)


kansasnoob's instruction  will remove Grub 2 and install Legacy Grub. 

Let me know if  you are willing to try a few other things to get Grub 2 to work (although, it probably will fail)

---

### Post by lesodk on 2010-02-12
I could not get the solution from kansasnoob to work.
When i write "lsb_release -a", it says:

"No LSB modules are available".

Furthermore when i have removed grub and type ""apt-get install grub", it says:

Package grub has no installation candidate.

I am now stuck at this point and dont know what to do.

I would be very happy for a little help.

Thanks!

---

### Post by lesodk on 2010-02-12
I have solved the problem. I just needed to add the repos.
It works now.

Thanks for so many great comments!!!

---

