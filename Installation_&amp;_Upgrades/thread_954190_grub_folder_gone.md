---
title: "grub folder gone"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by snowangyl on 2008-10-20
A virus on my windows partition got smart and apparently went into the /boot/grub folder in my mounted fsdriver linux partition and vaporized everything there.:mad:
How do i get it back? 
Everything is still in the /boot folder thankfully except for the grub folder

Now the grub cannot reinstall because it cannot find the stage1 file

And can i reinstall it without recompiling grub kernel files?


P.S. : When did the viruses start acting like this. I never saw a windows virus delete files on my linux drive deliberately since the time i started using ubuntu.:confused:

---

### Post by jpkotta on 2008-10-21
Try reinstalling grub.  You can use a live CD to boot into Ubuntu and chroot (probably called "recover" or something, I can't remember) into the hard disk installation.  Manual chroot commands are below.


```
sudo -i
mount /dev/sdXY /mnt
mount -o bind /proc /mnt/proc
mount -o bind /sys /mnt/sys
mount -o bind /dev /mnt/dev
chroot /mnt

```

```
sudo aptitude reinstall grub
```

Then lock down Windows or stop using it.

---

### Post by caljohnsmith on 2008-10-21
Unfortunately, reinstalling the Grub package will not actually regenerate all your Grub files in the /boot/grub folder; you have to use the "grub-install" command to create all the Grub boot files, and then the "update-grub" command to create a new menu.lst. Here are the steps you can do from a Live CD (it assumes your Grub package is still installed in Ubuntu):
```
sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub
cat /boot/grub/menu.lst
exit
sudo fdisk -lu
```
Replace "sdaX" with your Ubuntu partition, and also please post the output of all the above commands in case your menu.lst needs tweaking. :)

---

### Post by snowangyl on 2008-10-21
Aparently grub is still not installing.....:(

ubuntu@ubuntu:/dev$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:/dev$ sudo grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:/dev$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:/dev$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:/dev$ sudo chroot /mnt /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y

Not creating /boot/grub/menu.lst as you wish

root@ubuntu:/media/disk-1# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
root@ubuntu:/media/disk-1# exit
exit
ubuntu@ubuntu:/dev$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76767676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155   312576704   130688775    5  Extended
/dev/sda3       215046153   312576704    48765276    7  HPFS/NTFS
/dev/sda5        51199281   212796989    80798854+  83  Linux
/dev/sda6       212797053   215046089     1124518+  82  Linux swap / Solaris
ubuntu@ubuntu:/dev$

---

### Post by caljohnsmith on 2008-10-21
> **snowangyl said:**
> 
```
ubuntu@ubuntu:/dev$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76767676

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155   312576704   130688775    5  Extended
[COLOR="Red"]/dev/sda3       215046153   312576704    48765276    7  HPFS/NTFS[/COLOR]
/dev/sda5        51199281   212796989    80798854+  83  Linux
/dev/sda6       212797053   215046089     1124518+  82  Linux swap / Solaris
ubuntu@ubuntu:/dev$
```
OK, I think I see the crux of your problem; your HDD's partition table is corrupt, because it shows sda3 as inside the extended partition sda2, yet sda3 is marked as a primary partition. Also fdisk complains about sda5 being an empty partition, when it clearly isn't since it is your main Ubuntu partition. That's most likely why Grub is not installing correctly right now.

To fix your partition table you can use testdisk. If you want help with it, then first post:
```
sudo fdisk -l
```
Note that it is "-l" this time instead of "-lu" like you posted above. Then install and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen too and we can work from there. :)

---

### Post by snowangyl on 2008-10-21
ok, it seems that the 8MB that was NOT partitioned were bad sectors that i had deliberately not partitioned.

Then, on the livecd, i noticed it listed my linux drive in "COmputer" icon.

So i clicked on it and lo and behold, all the data that was on my linux partition popped up!

I did some modifications to the commands you got me to type to reinstall grub (replacing /mnt with ./media/disk) and aparently it works now.

Seems that theres a problem mounting drives from terminal :(

ubuntu@ubuntu:/media/disk$ sudo grub-install --root-directory=/media/disk /dev/sda
The file /media/disk/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:/media/disk$ sudo mount --bind /dev /media/disk/dev
ubuntu@ubuntu:/media/disk$ sudo mount --bind /proc /media/disk/proc
ubuntu@ubuntu:/media/disk$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) Y

Not creating /boot/grub/menu.lst as you wish

root@ubuntu:/#  update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) N

Not creating /boot/grub/menu.lst as you wish

root@ubuntu:/#  update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done



Thanks!

---

### Post by caljohnsmith on 2008-10-21
Snowangyl, it is pointless to try and get Grub to install right now when your partition table is clearly corrupt; just because you can access your Ubuntu partition does not mean your partition table is not a problem, and that is most likely why you are having problems with Grub. And unfortunately, it is almost for sure you will have more problems in the future if you choose not to try and fix your partition table.

I'm only trying to help, so if you choose not to do anything about your partition table, I'm not going to further assist you with Grub, because I know at some point you will just have more problems. If you want to wait for someone else to pick up this thread and help you, I'm certainly not going to be offended; all I'm saying is I'm not going to help you with Grub unless you first try and fix your partition table. It's up to you. :)

---

### Post by snowangyl on 2008-10-21
i know
i just needed to start up the linux  that was installed on the hard drive b/c/ the livecd keeps on freezing when i run apt-get, and i needed FileZilla on there for some urgent work that i needed to do for a clients computer.

i'm currently running disk fixing software (spinpoint) on the computer already and its already detecting my messed up partition tables.

---

