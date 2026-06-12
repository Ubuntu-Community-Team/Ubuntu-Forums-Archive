---
title: "Grub 2 - USB External HDD"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by joshedmonds on 2009-12-30
I have a fairly simple scenario that was quite easy pre-9.10 with legacy Grub, but is a bit beyond me with Grub2.

I want to have a full 9.10 install on my external USB hard-drive, that I can boot. I want a full system, and am not interested in a persistent live install. The external drive cannot be installed in the PC.

Until 9.10, this would involve a clean install to an internal hard-drive, using a live CD to copy the install wholesale to the external drive, then running the following:

sudo grub
grub> find /boot/grub/menu.list
[gives an output of all drives where that file can be found e.g. (hdx,y)]
grub>root (hdx,y)
grub>setup (hdx)
grub>quit

This would install Grub onto the external drive, and use the menu.lst from that drive to boot. All that is left then is to edit menu.lst manually to add UUIDs and the drive will boot.

As the external hard-drive has Grub2 on it with 9.10, Grub cannot be installed in this way from a 9.04 install. I have tried copying the /boot/grub folder to the drive however I still get an error 6.

With Grub2, some of these commands have been replaced with variables, and it seems I have to chroot into the external drive from a 9.10 install in order to install Grub2.

This leaves me fairly well confused. Even if I chroot in, I am unsure how I would configure Grub2 properly. Does anyone have any experience with this? My preference is to properly use Grub2 on the external, however I would certainly settle for Grub.

Thanks

---

### Post by Herman on 2009-12-30
:) The easiest way to do it would have been to just use the installation CD and install Ubuntu in your USB drive, click the ''Advanced" button in the last stage of the installation, step 7 of 7 I think, and select to install GRUB to MBR in whatever drive is your USB drive, sdb probably. Ubuntu will install in your USB as good as gold. 
You don't need to re-install GRUB. I don't know where you got that idea from?
Just install GRUB to the proper location in the first place. :)

---

### Post by Herman on 2009-12-30
:) Anyhow, seeing as you've made it this far already, I suppose it'll be easiest to keep on going and chroot into it and set up your GRUB2, right?

---

### Post by joshedmonds on 2009-12-30
Thanks Herman

The reason I installed that way is that the basic premise of my previous linux installations is that I could simply copy them wherever I wanted, with all customisations to date in place. In Grub, the menu.lst was a plain text file, with easy syntax, and took about 3 minutes to get right. I have in fact already made extensive customisations to the original install, and I just want to be able to boot it from an external drive!

I am unable to find any documentation that explains, in plain English, how I can use UUIDs to have Grub2 boot that OS. I have tried the chroot method, however without knowing how to correctly structure the configuration files it was not successful (although it reported no errors).

Grub2 is a stupidly complex solution to what was never really a problem for 99% of users.

---

### Post by Herman on 2009-12-30
I'm not really sure what part you need help with if you are able to chroot alright.
The rest of it's pretty easy, all you need to do is run 'sudo grub-install /dev/sdx', and then 'sudo grub-mkconfig -o /boot/grub/grub.cfg', and you should be all set. It only takes about three seconds with GRUB2! :)

I can't think why that wouldn't work but I'll run through it myself shortly just to make sure.
If you copied the entire installation as a whole partition with a dd command and the original partition is still present in an internal hard drive it might cause some confusion with the UUID numbers. You might want to edit the file system UUID in one of your partitions with 'sudo tune2fs' and change the UUID number of one of them a little, just so they're not identical.

---

### Post by joshedmonds on 2009-12-30
The drive was cp'd rather than dd'd, but the other drive has now been swapped out (just to add to the confusion), however it should make no difference.

[These are the chroot'ing instructions I have followed]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe78be78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         637     5116671    7  HPFS/NTFS
/dev/sda2             638        8327    61769925    b  W95 FAT32
/dev/sda3            8328        9602    10241437+   5  Extended
/dev/sda4            9603        9729    1020127+  82  Linux swap / Solaris
/dev/sda5            8328        9347     8193118+  83  Linux
/dev/sda6            9348        9602     2048256   83  Linux

Disk /dev/sdb: 639.4 GB, 639432130560 bytes
255 heads, 63 sectors/track, 77739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00048410

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         784     6297448+  83  Linux
/dev/sdb3             785       77739   618141037+   7  HPFS/NTFS

```

The short answer is that sdb1 is my new 9.10 install. sda contains, amongst others, an old 9.04 and Windows XP.

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

All good so far.

```
root@ubuntu:/# sudo grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:/# 
```

This is where it starts to fall apart. Why should Grub2 care what the device mapping is in this format if I can provide UUIDs. Can I put UUIDs in the device.map file? As far as it goes, it seems OK, as the external drive would be sdb to a system with one internal drive.

```
root@ubuntu:/# sudo grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# 
```

The wiki instructions ask for a update grub, then a grub-install. My understanding was the the grub-install updated the cfg file. Is this message actually a failure or a success? Will reboot and be back shortly.

---

### Post by Herman on 2009-12-30
Well I'm back after testing to make sure that would work and it seemed to work okay for me. I had a bit of extra messing around to do because I have an encrypted file system in my USB, but basically I followed this, [Recover Grub 2 via LiveCD]("https://wiki.edubuntu.org/Grub2#Recover%20Grub%202%20via%20LiveCD").

If you need detailed help or there's a place where you're stuck let me know as best you can where you got up to and what seems to be wrong, but really GRUB2 should be easier than Legacy GRUB. It does everything by itself, you just need to run the commands.

EDIT: Ah, simultaneous post. Sorry.

---

### Post by Herman on 2009-12-30
> This is where it starts to fall apart. Why should Grub2 care what the device mapping is in this format if I can provide UUIDs. Can I put UUIDs in the device.map file? As far as it goes, it seems OK, as the external drive would be sdb to a system with one internal drive.Good question, I don't know the answer to that.
Actually, I got an error because I pulled mine out of a computer with only one hard drive in it and plugged it into another one with four hard drives and another USB to chroot into it and try those commands. I got a complaint about not having mapping for sdg or something like that, so I just ran 'grub-mkdevicemap', and it was happy again.

Then I ran grub-install, and grub-mkconfig, I forget which order.

I don't know why the device.map makes any difference.

---

### Post by Herman on 2009-12-30
> The wiki instructions ask for a update grub, then a grub-install. My understanding was the the grub-install updated the cfg file. Is this message actually a failure or a success? Will reboot and be back shortly.I don't think it matters which one we do first. 

The update-grub command runs grub-mkdevice.map and grub-probe and then generates a new grub.cfg file.

The grub-install command refreshes files in the /boot/grub directory and runs a few other scripts designed to make sure everything will be alright and up to date and installs GRUB to MBR in a disk.

---

### Post by joshedmonds on 2009-12-30
Without wanting to sound whiney (no, really), doesn't it seem stupid that with legacy Grub I could have a fully mobile installation, yet with Grub2 it is such a pain. Why should it matter if you plug the root drive into a PC with extra internal hard-drives?

My drive gave me a Grub2 screen, yet failed on the first option. I pressed 'e' to edit the entry, and it contained a UUID that (on cursory glance, I didn't write it down) was that of the external drive, however with nothing to seemingly edit I tried booting again and again had it hang.

I will try Grub2 once more, and if that doesn't work, I'll chroot the drive, apt-get grub, and see if I can't get it working the good old fashioned way.

Thanks for your help.

---

### Post by joshedmonds on 2009-12-30
Herman, do you think you could post your grub.cfg file so I can have a look?

---

### Post by Herman on 2009-12-30
Ubuntu in a USB is still fully portable, at least I haven't noticed any problems with it.

Interestingly, the terminal feedback I have in my multiple disk computer here shows the menu entry having been made with root as (hd5,1),
```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=**(hd5,1)**
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
```

But now that I've booted it up as a single disk in a different PC on its own, it looks like the grub.cfg has changed,
```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=**(hd0,1)**
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
``` Can this be right? Or am I seeing things? Maybe I'm due for some sleep? :lolflag:

---

### Post by Herman on 2009-12-30
> Herman, do you think you could post your grub.cfg file so I can have a look? 	 Sure,
```
herman@ocz-karmic:~$ cat /boot/grub/grub.cfg
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
search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ee1e3a3-f03a-4690-8310-7c3236786563
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2ee1e3a3-f03a-4690-8310-7c3236786563 ro single 
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
```
```
herman@ocz-karmic:~$ cat /boot/grub/device.map 
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sde
(hd5)    /dev/sdg
```

---

### Post by Herman on 2009-12-30
It's strange that it didn't include entries for all of the operating systems I have in this other computer. The USB's own boot entires are all I want in it anyway though.

---

### Post by joshedmonds on 2009-12-30
```
sudo mount /dev/sdb1 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
apt-get install grub
sudo grub
root (hd1,0)
setup (hd1)
exit
^D
sudo cp /media/old9.04install/boot/grub/menu.lst media/thisinstall/boot/grub/
sudo gedit /media/thisinstall/boot/grub/menu.lst
exit
```

Tada. Thanks for your help Herman, but Grub2 is made for better men than I.

---

### Post by Herman on 2009-12-30
Okay, all the best then.

---

### Post by the_sane_one on 2010-02-14
I also use external USB HD to install ubuntu and this happens everytime to me. I would have to reboot to a live cd, find the right hd<X> and change grub.cfg by hand.

IMHO, Grub 2 is a stupidly complex software written for vanity than anything else. 

But, will this be addressed in Lucid release? :)

---

### Post by Herman on 2010-02-14
It works perfectly correctly every time for me.

---

