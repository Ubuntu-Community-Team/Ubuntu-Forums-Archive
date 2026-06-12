---
title: "BOOTMGR gone, wont boot to Ubuntu from CD"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by BorgCymru on 2008-06-18
OK I had Ubuntu 7.10 64 and Vista on this box but Ubuntu started to play up. So I downloaded the newest Ubuntu CD and did another install over the old one. Not formatting the HOME folder or / folder.

Now when I try and boot I see the GRUB but if I select Vista it says BOOTMGR is missing.

I can boot into Vista from the Ubuntu CD but not into Ubuntu. I really don't want to lose my settings on the Ubuntu partition.

---

### Post by Pumalite on 2008-06-18
Use Super Grub. You can boot Vista, fix its MBR, etc. Then reinstall Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by BorgCymru on 2008-06-18
OK used the Vista repair disk, couldn't make head nore tails of that Supergrub.exe thing.

Now I get 

ERROR 22 PARTITION is missing

when I try to boot to Ubuntu.

---

### Post by SeePU on 2008-06-18
Windows is not an other-OS-friendly OS.  Its bootloader only looks after the related OS.  I think when you installed the new Ubuntu, your Grub setup got messed up and the new Grub/new Ubuntu needs to be edited.  When you try to boot Vista, your Grub bootloader is not  looking after this OS loading so Vista thinks the bootloader for Vista is 'missing.'

I'm just guessing at all this so I advise you to search here for any instances of Vista/Ubuntu dual boots and even Windows (XP, for e.g.) dual booting with Ubuntu.

---

### Post by wpshooter on 2008-06-18
> **BorgCymru said:**
> OK I had Ubuntu 7.10 64 and Vista on this box but Ubuntu started to play up. So I downloaded the newest Ubuntu CD and did another install over the old one. Not formatting the HOME folder or / folder.

Now when I try and boot I see the GRUB but if I select Vista it says BOOTMGR is missing.

I can boot into Vista from the Ubuntu CD but not into Ubuntu. I really don't want to lose my settings on the Ubuntu partition.

Boy, I sure do see a lot of instances of this very same problem on these forums !!!

I suppose that is just one of the reasons that I don't use M/S windows.

BUT after all this time, you would think someone would have come up with a solution to this problem !!!

And I know Ubuntu can't control what Windows does but it looks like to me if they know what it is doing, they could fix Ubuntu to work its way around the problem.

---

### Post by Pumalite on 2008-06-18
Read Super Grub's Documentation. It can do just about everything for you if you learn to use it.

---

### Post by BorgCymru on 2008-06-18
Vista is working fine, its the Ubuntu that has the problems. It says it's not there. or hiding. I really want to update it from the live CD so I don't lose my info and stuff. How can I do that now ?

---

### Post by SeePU on 2008-06-18
Doesn't that mean your grub entry is messed up?  You have to re-edit your menu.1st file and put in your new Ubuntu install location?  Your new install probably over-wrote your previous file?

Someone else should recognize the problem.  I'm just learning so I will know how to partition and use grub.  I want to have around 4 or 5 operating systems ultimately so I'm trying to learn a lot about grub etc.

---

### Post by Pumalite on 2008-06-18
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by BorgCymru on 2008-06-18
I've just done another install of Ubuntu, and I still get the error 22 . This time I DID format the / partition. Still wont load from GRUB or live CD boot for first HDD options.

---

### Post by Pumalite on 2008-06-18
Boot your Live CD and post the command I gave you.

---

### Post by BorgCymru on 2008-06-18
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009fceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   163846934    40965750   83  Linux
/dev/sda3       163846935   976768064   406460565    f  W95 Ext'd (LBA)
/dev/sda5       163846998   206499509    21326256   83  Linux
/dev/sda6       206499573   471057929   132279178+   7  HPFS/NTFS
/dev/sda7       471057993   475154504     2048256   82  Linux swap / Solaris
/dev/sda8       475154568   976768064   250806748+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07f52619

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   240117759   120057856    7  HPFS/NTFS

---

### Post by Pumalite on 2008-06-18
You have Linux in sda2 and sda5. Which one is Ubuntu or which one contains the file system?

---

### Post by BorgCymru on 2008-06-18
/dev/sda2 81915435 163846934 40965750 83 Linux is /


/dev/sda5 163846998 206499509 21326256 83 Linux is /HOME

---

### Post by Pumalite on 2008-06-18
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
Post:
cat /media/sda2/boot/grub/menu.lst

---

### Post by BorgCymru on 2008-06-18
ubuntu@ubuntu:~$ cat /media/sda2/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bca47d71-58a7-454c-b6eb-b24e9e59aedc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bca47d71-58a7-454c-b6eb-b24e9e59aedc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bca47d71-58a7-454c-b6eb-b24e9e59aedc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Pumalite on 2008-06-18
Edit menu.lst and change 'groot' and 'root' of Ubuntu to (hd0,1)

---

### Post by BorgCymru on 2008-06-19
how do I do that through the live CD ?

Thanks

---

### Post by Pumalite on 2008-06-19
sudo nano /media/sda2/boot/grub/menu.lst
Make changes,
Save: Ctrl+o
Exit: Ctrl+x
Reboot.

---

### Post by BorgCymru on 2008-06-19
Ahh here might be the problem. that file is blank

---

### Post by Pumalite on 2008-06-19
It cannot be blank. You just post it.Review your commands. Copy and paste in the Terminal.

---

### Post by BorgCymru on 2008-06-19
Thats exactly what I did and it came up as NEW DOCUMENT

I thought it was very strange seeing as I had posted the contents before.

---

### Post by Pumalite on 2008-06-19
sudo mount -t ext3 /dev/sda2 /media/sda2
Enter
now try again.

---

### Post by BorgCymru on 2008-06-20
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/sda2
mount: mount point /media/sda2 does not exist
ubuntu@ubuntu:~$

---

### Post by BorgCymru on 2008-06-26
Sorry for slow reply.

OK after getting nothing I re ran the first lot of code you said.

> ubuntu@ubuntu:~$ sudo fdisk -lu


 I noticed that it now said HDa instead of SDa. So following the instructions but using hda I can now boot into Ubuntu.

BUT

I can no longer see my home partition.

---

### Post by Pumalite on 2008-06-26
Post:
df -h
mount

---

### Post by BorgCymru on 2008-06-26
Tried a new instal again still getting ERROR 22 now again :(


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07f52619

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   240117759   120057856    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009fceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sdb3        81915435   976768064   447426315    f  W95 Ext'd (LBA)
/dev/sdb5       206499573   471057929   132279178+   7  HPFS/NTFS
/dev/sdb6       471057993   475154504     2048256   82  Linux swap / Solaris
/dev/sdb7       475154568   976768064   250806748+   7  HPFS/NTFS
/dev/sdb8        81915561   101450474     9767457   83  Linux
/dev/sdb9       101450538   120985514     9767488+  83  Linux

Partition table entries are not in disk order


ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1007M   13M  995M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1007M   13M  995M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1007M  100K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   68K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
tmpfs                1007M   16K 1007M   1% /tmp
gvfs-fuse-daemon     1007M   20M  988M   2% /home/ubuntu/.gvfs
/dev/sdb8             9.3G  2.2G  6.6G  25% /media/disk
/dev/sdb9             9.3G  150M  8.7G   2% /media/disk-1
/dev/sdb8             9.3G  2.2G  6.6G  25% /media/sdb8
/dev/sdb9             9.3G  150M  8.7G   2% /media/sdb9


ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb8 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb9 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8 on /media/sdb8 type ext3 (rw)
/dev/sdb9 on /media/sdb9 type ext3 (rw)

---

### Post by Pumalite on 2008-06-26
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by BorgCymru on 2008-06-26
I'm going to re partition the whole drive I think, seems its got a bit messed up. I'll get another drive to back things up and start again.

---

### Post by Pumalite on 2008-06-26
Good luck.

---

### Post by BorgCymru on 2008-06-26
Thanks :)

---

