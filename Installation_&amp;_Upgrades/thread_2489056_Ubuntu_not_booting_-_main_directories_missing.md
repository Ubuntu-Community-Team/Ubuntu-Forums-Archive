---
title: "Ubuntu not booting - main directories missing?"
date: 2023-07-17
forum: Installation &amp; Upgrades
---

### Post by ubu-boot134-324 on 2023-07-17
Hello everyone

My Ubuntu Server isn't booting anymore.

I come as far as this: (see attached image *boot.jpg*)

It says *run-init* can't execute '*/sbin/init*', '*etc/init*', '*bin/init*' and '*bin/sh*'.

I booted an Ubuntu Desktop Live USB to diagnose the problem.

I tried to check if the files still exist. But here I encountered my first problems.

*lsblk* gives me the following result:
```

[COLOR=#000000][FONT=&amp]root@ubuntu:~# lsblk[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]NAME                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop0                 7:0    0   2.5G  1 loop /rofs[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop1                 7:1    0     4K  1 loop /snap/bare/5[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop2                 7:2    0  63.3M  1 loop /snap/core20/1822[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop3                 7:3    0 346.3M  1 loop /snap/gnome-3-38-2004/119[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop4                 7:4    0 240.6M  1 loop /snap/firefox/2356[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop5                 7:5    0  91.7M  1 loop /snap/gtk-common-themes/1535[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop6                 7:6    0   304K  1 loop /snap/snapd-desktop-integration/49[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop7                 7:7    0  45.9M  1 loop /snap/snap-store/638[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]loop8                 7:8    0  49.8M  1 loop /snap/snapd/18357[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sda                   8:0    0 111.8G  0 disk [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9500;&#9472;sda1                8:1    0   512M  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9500;&#9472;sda2                8:2    0     1G  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9492;&#9472;sda3                8:3    0 110.3G  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  &#9492;&#9472;ubuntu--vg-ubuntu--lv[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]                    253:0    0  55.1G  0 lvm  [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sdb                   8:16   1   7.2G  0 disk [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9500;&#9472;sdb1                8:17   1   4.6G  0 part /cdrom[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9500;&#9472;sdb2                8:18   1   4.9M  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9500;&#9472;sdb3                8:19   1   300K  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]&#9492;&#9472;sdb4                8:20   1   2.6G  0 part /var/crash[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/var/log
[/FONT][/COLOR]
```

As you can see my 120GB disk has 3 partitions.
The largest is */dev/sda3* and I assume this is where all my files should be.
But only 55GB of this third partition are accessible through */dev/ubuntu-vg/ubuntu-lv* 

To have a look at the files I tried to mount all partitions but I was only successful with *sda1* and *sda2*:
```

[COLOR=#000000][FONT=&amp]root@ubuntu:~# mkdir /mnt/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mkdir /mnt/sda2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mkdir /mnt/sda3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mount /dev/sda1 /mnt/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mount /dev/sda2 /mnt/sda2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mount /dev/sda3 /mnt/sda3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mount: /mnt/sda3: unknown filesystem type 'LVM2_member'.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# ls /mnt/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]EFI[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# ls /mnt/sda2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]config-5.15.0-70-generic      lost+found[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]config-5.15.0-76-generic      System.map-5.15.0-70-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]efi                           System.map-5.15.0-76-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]grub                          vmlinuz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]initrd.img                    vmlinuz-5.15.0-70-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]initrd.img-5.15.0-70-generic  vmlinuz-5.15.0-76-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]initrd.img-5.15.0-76-generic  vmlinuz.old[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]initrd.img.old[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# ls /mnt/sda3[/FONT][/COLOR]

```

I mounted */dev/ubuntu-vg/ubuntu-lv* and the contents of this device look like this:
```

[COLOR=#000000][FONT=&amp]root@ubuntu:~# mkdir /mnt/ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# mount /dev/ubuntu-vg/ubuntu-lv /mnt/ubuntu/[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# ls /mnt/ubuntu/[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]boot [/FONT][/COLOR][COLOR=#000000][FONT=&amp]dev [/FONT][/COLOR][COLOR=#000000][FONT=&amp]proc [/FONT][/COLOR][COLOR=#000000][FONT=&amp]run [/FONT][/COLOR][COLOR=#000000][FONT=&amp]swap.img [/FONT][/COLOR][COLOR=#000000][FONT=&amp]sys [/FONT][/COLOR][COLOR=#000000][FONT=&amp]tmp [/FONT][/COLOR][COLOR=#000000][FONT=&amp]var
[/FONT][/COLOR]
```

I only see the folders *boot*, *dev*, *proc*, *run*, *sys*, *tmp*, *var*.
But the folders *bin*, *etc*, *home*, *lib*, *sbin*, *usr*, ... are missing.

**The boot problem is that *run-init* can't execute '*/sbin/init*', '*etc/init*', '*bin/init*' and '*bin/sh*'. Which makes sense, because I can't see these directories either.**

I'm not sure but it seems that some part of the data went missing. Since the logical volume */dev/ubuntu-vg/ubuntu-lv* is only 55GB, I guess there should be another logical volume with the directories *bin*, *etc*, *home*, ...

But doing a *pvscan*, *vgscan* and a *lvscan* only show me this:
```

[COLOR=#000000][FONT=&amp]root@ubuntu:~# pvscan[/FONT][/COLOR][COLOR=#000000][FONT=&amp]  PV /dev/sda3   VG ubuntu-vg       lvm2 [<110.29 GiB / 55.14 GiB free][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Total: 1 [<110.29 GiB] / in use: 1 [<110.29 GiB] / in no VG: 0 [0   ][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# vgscan[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Found volume group "ubuntu-vg" using metadata type lvm2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# lvscan[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# vgchange -a y[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  1 logical volume(s) in volume group "ubuntu-vg" now active[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# lvscan[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]ACTIVE[/FONT][/COLOR][COLOR=#000000][FONT=&amp]'/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit
[/FONT][/COLOR]
```


I'm already 3 days into this and I'm really frustrated -.-
Therefore, any hint or any help would be greatly appreciated!!

Thank you!




------

Additional info:

I don't know if it helps, but here is the pastebin I created with boot-repair: [https://paste.ubuntu.com/p/tZPr4Z4Z58/](https://paste.ubuntu.com/p/tZPr4Z4Z58/)

The last thing I did before I encountered this error was to move files from *$HOME/myuser/test/* to *$HOME/* (this was an accident the destination should have been *$HOME/myuser/* ).
I don't know if this action corrupted something.

---

### Post by oldfred on 2023-07-17
Please do not post screen shots of terminal output. Use Code Tags.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

You still show a Windows UEFI boot entry. Was Windows overwritten. If so you can delete it.

Did you turn on UEFI Secure Boot?
Or did you do an UEFI update which reset UEFI settings all to defaults?
Check settings in UEFI.

---

### Post by MAFoElffen on 2023-07-17
You have another thread going, RE: [https://ubuntuforums.org/showthread.php?t=2489038&p=14151076#post14151076](https://ubuntuforums.org/showthread.php?t=2489038&p=14151076#post14151076)

In that hread you posted your boot-info report URL. On line #55, it said your SecureBoot setting was enabled Did you disable and try it yet?

---

### Post by MAFoElffen on 2023-07-17
Reviewing your errors, here, in this thread...

It's a corrupted initramfs image, that is, after failure, dumping you out the the initramfs command prompt.

Try this booted from the LiveUSB media:
```

sudo su -
fdisk -lu | grep '/dev/mapper/'
pvscan
vgscan
vgchange -a y
lvscan | grep 'ACTIVE'
# Output of this from Line # 213 of your boot-info report was
#   ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit
mount /dev/ubuntu-vg/ubuntu-lv /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi || true
mount /dev/sda1 /mnt/boot/efi
chroot /mnt /bin/bash --login
mount -a

ls

```
If your output of the last is not simular to this
```

root@ubuntu:/# ls
bin   data  etc   lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
boot  dev   home  lib32  libx32  media       opt  root  sbin  srv   tmp  var

```
Then stop and post back. 

If it is like that, then do:
```

update-initramfs -c -k all

```

---

### Post by ubu-boot134-324 on 2023-07-17
> **oldfred said:**
> Please do not post screen shots of terminal output. Use Code Tags.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

I'm sorry I don't have an internet connection on that device. I wasn't happy with that either.  Thus the screenshots. (But I could probably connected to a hotspot from my phone... I'll do that next time).

EDIT: I just replaced the screenshots with Code Tags.

> **oldfred said:**
> 
Did you turn on UEFI Secure Boot?
Or did you do an UEFI update which reset UEFI settings all to defaults?
Check settings in UEFI.
I haven't changed anything on that system lately. I updated some apt packages a couple days ago. But without any problems.
What settings should I check specifically?

> **MAFoElffen said:**
> On line #55, it said your SecureBoot setting was enabled Did you disable and try it yet?
Yes I tried that. Didn't work. Same result.

> **MAFoElffen said:**
> 
It's a corrupted initramfs image, that is, after failure, dumping you out the the initramfs command prompt.

Try this booted from the LiveUSB media:
```

sudo su -
fdisk -lu | grep '/dev/mapper/'
pvscan
vgscan
vgchange -a y
lvscan | grep 'ACTIVE'
# Output of this from Line # 213 of your boot-info report was
#   ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit
mount /dev/ubuntu-vg/ubuntu-lv /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi || true
mount /dev/sda1 /mnt/boot/efi
chroot /mnt /bin/bash --login
mount -a

ls

```
If your output of the last is not simular to this
```

root@ubuntu:/# ls
bin   data  etc   lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
boot  dev   home  lib32  libx32  media       opt  root  sbin  srv   tmp  var

```
Then stop and post back.


Thank you for analyzing and for your reply.
I tried all your commands from the Live USB, but without success.

Here is my result:

```

[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ sudo su[/FONT][/COLOR][COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# fdisk -lu | grep '/dev/mapper/'[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 55.14 GiB, 59210989568 bytes, 115646464 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# pvscan[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV /dev/sda3   VG ubuntu-vg       lvm2 [<110.29 GiB / 55.14 GiB free][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Total: 1 [<110.29 GiB] / in use: 1 [<110.29 GiB] / in no VG: 0 [0   ][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# vgscan[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Found volume group "ubuntu-vg" using metadata type lvm2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# vgchange -a y[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  1 logical volume(s) in volume group "ubuntu-vg" now active[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# lvscan | grep 'ACTIVE'[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount /dev/ubuntu-vg/ubuntu-lv /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount --make-private --rbind /dev  /mnt/dev[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mount:  /mnt/dev: mount point does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount --make-private --rbind /proc /mnt/proc[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount --make-private --rbind /sys  /mnt/sys[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mount:  /mnt/sys: mount point does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount --make-private --rbind /run  /mnt/run[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mount:  /mnt/run: mount point does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/boot[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mkdir /mnt/boot/efi || true[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mkdir: cannot create directory &#8216;/mnt/boot/efi&#8217;: File exists[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# chroot /mnt /bin/bash --login[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# mount -a[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# ls[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Desktop  Documents  Downloads  Music  Pictures  Public  snap  Templates  Videos[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:/home/ubuntu# ls /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]boot  dev  proc  run  swap.img  sys  tmp  var[/FONT][/COLOR]

```

---

### Post by ubu-boot134-324 on 2023-07-19
I just realized there is another error shown during boot (see boot.jpg from original post):

```

Begin: Running /scripts/init-bottom ... mkdir: can't create directory '/root/lib/': Read-only file system

```

Is this something worth pursuing?

---

### Post by MAFoElffen on 2023-07-19
That usually occurs when there is a filesystem error... That usually can be corrected with fsck...

Before I tell you what to do next:
Do you have recent backup?
Do you see the grub menu when you boot?

---

### Post by ubu-boot134-324 on 2023-07-19
> **MAFoElffen said:**
> That usually occurs when there is a filesystem error... That usually can be corrected with fsck...

Before I tell you what to do next:
Do you have recent backup?
Do you see the grub menu when you boot?

I don't have a backup.

Yes, I see the grub menu when I boot.

And I already tried fsck (I don't know if I have done it correctly...)
I tried following this: [https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox/817660#817660](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox/817660#817660) 

But when I type *exit* in *[FONT=var(--ff-mono)]initramfs [/FONT]*[FONT=var(--ff-mono)]the system completely crashes (I can get a picture of the error later, if that helps..?)[/FONT]

---

### Post by MAFoElffen on 2023-07-19
Yes. That would help... But this time add it as an attachment, using the "Go Advanced" button.

---

### Post by MAFoElffen on 2023-07-19
The AskUbuntu answer you linked to had the wrong instructions for a filesystem within an LVM2 Volume Manager...

Try this (from a LiveUSB):
```

sudo su -
vgchange -a y
lvscan | grep 'ACTIVE'
# Output of this from Line # 213 of your boot-info report was
#   ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit
fsck -fy /dev/ubuntu-vg/ubuntu-lv

```

---

### Post by MAFoElffen on 2023-07-19
haven't heard back from you. I am really hoping that last post helps...

If what is contained in the last post does not fix the filesystem... There are errors where whole required directories or their mount points are not showing up at all. If fsck does not repair that, then it is dead.

If so, then use the LiveUSB to recover what you can from the installed system, and re-install the OS...

Backups are your fallback point. Without backups, your acceptance of risk is of losing everything (100%). That is okay for some. Devastating for others.

---

### Post by ubu-boot134-324 on 2023-07-20
Thank you for your reply!

I tried this:

```

[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ sudo su -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# vgchange -a y[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  1 logical volume(s) in volume group "ubuntu-vg" now active[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# lvscan | grep 'ACTIVE'[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]root@ubuntu:~# fsck -fy /dev/ubuntu-vg/ubuntu-lv [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]fsck from util-linux 2.37.2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]e2fsck 1.46.5 (30-Dec-2021)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 1: Checking inodes, blocks, and sizes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Inode 2935663 extent tree (at level 1) could be shorter.  Optimize? yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Inode 2935670 extent tree (at level 1) could be shorter.  Optimize? yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 1E: Optimizing extent trees[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 2: Checking directory structure[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 3: Checking directory connectivity[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/lost+found not found.  Create? yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 3A: Optimizing directories[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 4: Checking reference counts[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Pass 5: Checking group summary information[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/mapper/ubuntu--vg-ubuntu--lv: ***** FILE SYSTEM WAS MODIFIED *****[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/mapper/ubuntu--vg-ubuntu--lv: 490208/3620864 files (0.9% non-contiguous), 11347769/14455808 blocks[/FONT][/COLOR]

```

but I still get the same error during boot.


Attached you'll find a picture of the initramfs console after I typed 'exit'

---

### Post by MAFoElffen on 2023-07-20
Ouch! My condolences. I am sorry, but we have made a good faith effort to recover the system. Anyting more, and I fear we are just trying to regain life support, which I feel it would not have a good quality of life expectancy.

I would use the LiveUSB media to boot from, mount the LVM  /dev/ubuntu-vg/ubuntu-lv volume, and then try to recover what you can to another drive. I would say that maybe mount the installed system, once before nuking it, to chroot into it and run the UbuntuForums 'system-info' script. That way you have a report of what it was, and if you look near the end of it, it will have a "User Installed" list section of what you installed to it since the system was originally installed. That list will help you get back to where you were. 

Then reinstall fresh. Afterwards, you can take your time to reload your data and reset your settings. Further, on this next install, I would recommend splitting out your User Home to it's own partition, so that your own data, which is most important to most Users, is safe and unaffected by the what-may-happen's to the OS... And then come up with a plan to do Backups, every once in a while. That would have helped you this time if you had.

---

### Post by ubu-boot134-324 on 2023-07-23
> **MAFoElffen said:**
> I would say that maybe mount the installed system, once before nuking it, to chroot into it and run the UbuntuForums 'system-info' script. That way you have a report of what it was, and if you look near the end of it, it will have a "User Installed" list section of what you installed to it since the system was originally installed. That list will help you get back to where you were.

I already tried to chroot the system and I posted my result in this post: [https://ubuntuforums.org/showthread.php?t=2489056&p=14151139#post14151139](https://ubuntuforums.org/showthread.php?t=2489056&p=14151139#post14151139)
Here it is again:
> **ubu-boot134-324 said:**
> 

Here is my result:

```

[COLOR=#000000]ubuntu@ubuntu:~$ sudo su[/COLOR][COLOR=#000000]root@ubuntu:/home/ubuntu# fdisk -lu | grep '/dev/mapper/'[/COLOR]
[COLOR=#000000]Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 55.14 GiB, 59210989568 bytes, 115646464 sectors[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# pvscan[/COLOR]
[COLOR=#000000] PV /dev/sda3   VG ubuntu-vg       lvm2 [<110.29 GiB / 55.14 GiB free][/COLOR]
[COLOR=#000000] Total: 1 [<110.29 GiB] / in use: 1 [<110.29 GiB] / in no VG: 0 [0   ][/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# vgscan[/COLOR]
[COLOR=#000000] Found volume group "ubuntu-vg" using metadata type lvm2[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# vgchange -a y[/COLOR]
[COLOR=#000000] 1 logical volume(s) in volume group "ubuntu-vg" now active[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# lvscan | grep 'ACTIVE'[/COLOR]
[COLOR=#000000] ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [55.14 GiB] inherit[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount /dev/ubuntu-vg/ubuntu-lv /mnt[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount --make-private --rbind /dev  /mnt/dev[/COLOR]
[COLOR=#000000]mount:  /mnt/dev: mount point does not exist.[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount --make-private --rbind /proc /mnt/proc[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount --make-private --rbind /sys  /mnt/sys[/COLOR]
[COLOR=#000000]mount:  /mnt/sys: mount point does not exist.[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount --make-private --rbind /run  /mnt/run[/COLOR]
[COLOR=#000000]mount:  /mnt/run: mount point does not exist.[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt/boot[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mkdir /mnt/boot/efi || true[/COLOR]
[COLOR=#000000]mkdir: cannot create directory ‘/mnt/boot/efi’: File exists[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/boot/efi[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# chroot /mnt /bin/bash --login[/COLOR]
[COLOR=#000000]chroot: failed to run command ‘/bin/bash’: No such file or directory[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# mount -a[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# ls[/COLOR]
[COLOR=#000000]Desktop  Documents  Downloads  Music  Pictures  Public  snap  Templates  Videos[/COLOR]
[COLOR=#000000]root@ubuntu:/home/ubuntu# ls /mnt[/COLOR]
[COLOR=#000000]boot  dev  proc  run  swap.img  sys  tmp  var[/COLOR]

```

Do you see any other chance how I could *chroot* it?

---

### Post by MAFoElffen on 2023-07-24
No. 

This is what yours showed...
```

boot  dev  proc  run  swap.img  sys  tmp  var

```
This is what is shown on my latop
```

bin   cdrom  etc   lib    lib64   lost+found  mnt  opt   root  sbin  sys  usr
boot  dev    home  lib32  libx32  media       nfs  proc  run   srv   tmp  var

```
Doing a filesystem repair didn't recovery where all those directories went. Look how many is missing. It is broken.

Thankfully, your Home folder is there. Hopefully you can get whatever you need backed up off there... After that, you could either install fresh, then restore your data, or...

If you feel lucky, you could boot from an Ubuntu LiveUSB and go to install... When it gets to the installation type, see if it offers to repair the existing system.

If that doesn't offer that, there is another way...

---

### Post by ubu-boot134-324 on 2023-07-28
Okay, thank you for the help!

I just reinstalled the whole system.

But still it would be interesting to know why this happend...?

---

