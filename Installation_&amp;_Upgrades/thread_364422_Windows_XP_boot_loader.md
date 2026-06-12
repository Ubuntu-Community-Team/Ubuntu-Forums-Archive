---
title: "Windows XP boot loader"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by sweetmax on 2007-02-18
Hi all

I am tottaly new in linux world, I installed latest release of Ubuntu then decided to have multiple os therefore installed windows server 2003 too, but after installing it  I couldn't start Ubuntu any more.How should myboot.ini  looks like  in order to start Ubuntu:

my boot.ini:
[PHP][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Enterprise" /fastdetect[/PHP]
Ubuntu has been installed on F partition.I attached image of my HD. could you please tell me how I can start Ubuntu again?

---

### Post by willc0de4food on 2007-02-18
you can't.
you have to use a boot loader that's not tied to M$ :]

see if this works..
boot to the livecd. once at the desktop, open a terminal.
enter:
sudo fdisk -l
if it lists entries of /dev/hda# for your partitions, enter:
sudo grub-install /dev/hda
otherwise you probably have a SATA drive so you'd see entries of /dev/sda# for your partitions, in which case you'd enter:
sudo grub-install /dev/sda

it should output something like the devices it mapped and that it worked. reboot and you should have the ubuntu bootloader back.

---

### Post by sweetmax on 2007-02-18
thanks for the fast reply,
yes my hd is sata.. i'll try your suggestion will se what's happening :)
thanks again

---

### Post by willc0de4food on 2007-02-18
awesome. post back if it works..i've never tried it, so i'm not sure if it'd work from the livecd..but it should in theory? lol

---

### Post by bulldog on 2007-02-18
Won't work I'm afraid,you'll have to use (hd0) or (hd1) instead of sda.
Here's a complete reinstall of grub with the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by sweetmax on 2007-02-18
unfortunately it doesn't worked in my case if u take a look at screenshot  you'll see the error massage that i got which is>

Could not find device for /boot: not found or not a block device

---

### Post by sweetmax on 2007-02-18
> **bulldog said:**
> Won't work I'm afraid,you'll have to use (hd0) or (hd1) instead of sda.
Here's a complete reinstall of grub with the live cd.
Boot into the live Ubuntu cd.....

and that\s what i got>
[HTML]       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,2)

grub> setup (hd0)

Error 12: Invalid device requested

grub> setup (hd0,2)

Error 12: Invalid device requested

grub> setup (hd2)

Error 12: Invalid device requested

grub> [/HTML]
actually I have some important backups on that partition. how about reinstalling ubuntu and shrink old ubunto partition which is on /dev/sda3. can I have access to old files then?

---

### Post by bulldog on 2007-02-18
There are several errors on your hard disk.
I suggest to try to make a backup of your important files on another device!
If you have done so,use the Gparted live cd and wipe the whole disk clean and repartition it.

To backup you can use the live ubuntu cd and mount your important partition to backup.

---

### Post by sweetmax on 2007-02-18
how can i take backup?

thanks alot for your help

---

### Post by bulldog on 2007-02-18
To backup you'll have to boot from the live ubuntu cd.
Than you'll have to make some mountpoints [dir's] and mount your existing partition to one of the mountpoints.

Example:
Assuming you have a partition called sda2 which you want to backup,you have to do the following.
```
sudo mkdir /mnt/sda2
sudo mount /dev/sda2 /mnt/sda2
```
This works if sda2 is a linux partition [ext3]
If it's a NTFS partition the second command should be ```
sudo mount -t ntfs /dev/sda2 /mnt/sda2
```
Or in case of a FAT32 partition```
sudo mount -t fat32 /dev/sda2 /mnt/sda2
```

You can try to have a look at your mounted partition in the Filesystem/mnt/sda2 directory.
I can't guarantee you can access this partitions of yours,due to the errors you've got.

---

