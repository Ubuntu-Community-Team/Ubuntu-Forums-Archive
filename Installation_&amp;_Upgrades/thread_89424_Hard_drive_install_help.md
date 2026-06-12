---
title: "Hard drive install help"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Zedd on 2005-11-12
In Windows I made a new partition and put the whole Ubuntu CD on it. I booted with a GRUB boot floppy and had it run this

```
 
  root (hd0,4)
  kernel (hd0,4)/install/vmlinuz
  initrd (hd0,4)/install/initrd.gz
```

It looks like it starts to work, then I get this error;

> Please appent a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

Please help!

---

### Post by aysiu on 2005-11-12
The relevant part of my Grub config looks like this ```

title           Ubuntu Linux
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
``` See how there's a part that says root= ?

---

### Post by Zedd on 2005-11-12
Trying that now. Although I think it may have something to do with the initrd file. Fedora has initrd as a .img, is the .gz right for Ubuntu's installer?

Edit:

Tried   

  Root (hd0,4)
  kernel (hd0,4)/install/vmlinuz root=/dev/hda5
  initrd (hd0,4)/install/initrd.gz


Same error.

---

### Post by aysiu on 2005-11-12
I doubt the image is just vmlinuz, and I doubt the initrd is just initrd.gz. Can you get to a command prompt at all? Or you said Grub is on the floppy? Can you go in there in a folder called */boot* and find out what the contents are? For example, in my /boot directory, this is what I get: ```
/boot$ ls
abi-2.6.12-9-386     initrd.img-2.6.12-9-386  vmlinuz-2.6.12-9-386
config-2.6.12-9-386  memtest86+.bin
grub                 System.map-2.6.12-9-386
``` You have to call up the exact name of the file. My image is called vmlinuz-2.6.12-9-386, not just vmlinuz. I don't know what yours is called, but it's probably also got a bunch of numbers after it.

---

### Post by Zedd on 2005-11-12
Maybe you don't understand what I'm trying to do. I'm installing Ubuntu on a very old laptop. So old that it won't boot from a CD. I've copied the contents of the Ubuntu CD to a partition on the hard drive and am trying to install from the hard drive. On the Ubuntu CD there is no /boot folder. However there is an /install folder which contains the /netboot folder as well is the files initrd.gz, initrd.list, mt86plus, readme.sbm, sbm.bin, and vmlinuz.

I did the exact same thing with Fedora Core 4 and everything worked, the installer even started. However when it realized the laptop only had 32 MBs of RAM it said there was not enough RAM to install and quit.

---

### Post by jkil on 2005-11-13
> [B]Please appent a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)  [/B]

hi:

i met the same problem, let me tell you all about i've tried.

first, i have 40G maxtor (just contains OSs)
 160G maxtor for program + 20G st for data
and existing OSs:
hda1  fat32      Winxp pro
hda2  boot(ext3)   FC3
hda3  / (ext3)       FC3
hda5  / (ext3)       Mandrakelinux10.1
hda7  / (fat32)      free (to be Ubuntu5.1)
hda8  / (reiserfs)    Magic Linux2.0RC1

i tried two ways:
1) because my default GRUB can list all these(even ubuntu is pre-listed), i press the C to the command mode:
>root (hd1,0)     ////the  ubuntu.iso, initrd, vmlinuz, preseed, *.cfg,all here
>kernel (hd1,0)/vmlinuz   (ro ramdisk_size=32768 vga=791)
>initrd (hd1,0)/initrd.gz
>boot

it goes fine, seems to work as i install the magiclinux, however, it hangs with the warning above.

it seems the "root" is not well set? well, i have appended "preseed/file=(hd1,0)/ubuntu-5.1-install-i386.iso/preseed" for another try, and even use different initrd.gz in its different directories as well !!man~hell!!

2)i use a win98nd bootable-disk to the pure dos mode, use a setup.bat which contains **loadlin vmlinuz root=/dev/ram initrd=initrd.gz ramdisk_size=32768 ro vga=788 **,like i did for mandrakelinux.
 it goes even finer, goes into the installation mode, set the nation,keyboard,net-stat, but [color=red]CANNOT[/color] load from cdrom...

it certainly could not! but from the hdd! how can i tell it to do this? append parameters??

all this matters i think, to the ubuntu is. it lacks a *.img to install directlyfrom the hdd, like Mandrakelinux,FC,etc.

to me, i lack a dvd burner!!!

what a precious weekend for the Ubuntu!!
i thought i' experienced enough to handle it, however, i was hurt....

any solutions ?? appreciated if any help~~~

---

### Post by jkil on 2005-11-13
to Zedd:

hi:

i now calm enough to consider the whole thing about it.

as to the error "kernel panic: root..' , it is because we haven't load the kernel fully, there is some conflicts.
[B]what we should do is: edit a *.bat as i did, put *.iso, vmlinuz, initrd to the partition root directory, then enter the dos mode to excute the *.bat", then it works.

however, the Ubuntu5,1 haven't offered its vmlinuz-hd.gz yet, which prevent us to install directly from the approach i mentioned above. so ...[/B]

as the link "how to install Ubuntu5.1 from hdd" is broken, so i give up the attempt now.
i only wonder how he/she managered that.edit the *.cfg???

good luck~to us :)

---

