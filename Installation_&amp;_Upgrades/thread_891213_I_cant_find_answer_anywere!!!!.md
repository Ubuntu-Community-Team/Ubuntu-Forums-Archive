---
title: "I cant find answer anywere!!!!"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by linuxnoob1982 on 2008-08-15
OK I have tried everything I could find.  I have a maxtor drive that is format through windows as ntfs.  I can't install ubuntu.  I gives me different errors depending on if I use the automatic partitioner or manuel.  If I go to live cd destop, i can't mount nor install from there.  Gparted and fdisk cant find my drive.  PLEASE HELP!!!

---

### Post by dje on 2008-08-15
from the live cd please open a terminal (applications >> accessories >> terminal) and type:
```
sudo fdisk -l
```
and paste the output here (that is a lowercase L on the end not a 1 ;) )

dje

---

### Post by Sef on 2008-08-15
1) Do you want to dual boot?

2) Have you checked the disk for defects?  It is below run the Live CD, install, etc.

3) What errors are you getting?

---

### Post by linuxnoob1982 on 2008-08-15
> **dje said:**
> from the live cd please open a terminal (applications >> accessories >> terminal) and type:
```
sudo fdisk -l
```
and paste the output here (that is a lowercase L on the end not a 1 ;) )

dje


I get nothing, it just goes to a new line.

At install if I do the Automated Partition it says that the swap file on partition #5 failed. "not an exact qoute".

If I do the manual it says that it can't create ext3 file.

I also can't mount it.

---

### Post by dje on 2008-08-15
ok please post the output of:
```
sudo lshw -C disk
```

dje

---

### Post by linuxnoob1982 on 2008-08-15
This is what I get

ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom                 
       description: CD-R/CD-RW writer
       product: LG CD-RW CED-8083B
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       logical name: /cdrom
       version: 1.10
       serial: 1999/12/29
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hda
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-disk
       description: ATA Disk
       product: Maxtor 6Y120P0
       vendor: Maxtor
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: YAR41BW0
       serial: Y3PJ6Q6E
       size: 114GiB (122GB)
       capacity: 114GiB (122GB)
       capabilities: ata dma lba iordy smart security pm apm
       configuration: apm=off mode=udma6 smart=on
ubuntu@ubuntu:~$

---

### Post by dje on 2008-08-15
strange it has assigned /dev/hda to your cd drive anyway, try this:
```
sudo mkdir /mnt/mydisk
sudo mount /dev/hdd1 /mnt/mydisk
```

dje

---

### Post by linuxnoob1982 on 2008-08-15
/dev/hdd1: can't read superblock 

Thats what I get after that.  Now that you mention it, and as stupid as its sounds, I may have my cable in the wrong spot!!! Or its because I am using the live cd right now.

---

### Post by dje on 2008-08-15
i'm not sure hard drives are usually assigned /dev/hda or /dev/sda with cd drives getting /dev/dvd or /dev/cdrom. if you think you have a cable in wrong it would be no harm to switch it around and see if it works :D

dje

---

### Post by linuxnoob1982 on 2008-08-15
Well install still didn't work, but I did make some progress. I entered the 

sudo lshw -C disk 

and..

 *-disk                  
       description: ATA Disk
       product: Maxtor 6Y120P0
       vendor: Maxtor
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: YAR41BW0
       serial: Y3PJ6Q6E
       size: 114GiB (122GB)
       capacity: 114GiB (122GB)
       capabilities: ata dma lba iordy smart security pm apm
       configuration: apm=off mode=udma6 smart=on
  *-cdrom
       description: CD-R/CD-RW writer
       product: LG CD-RW CED-8083B
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       logical name: /cdrom
       version: 1.10
       serial: 1999/12/29
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hdc
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted

then entered 

ubuntu@ubuntu:~$ sudo mkdir /mnt/mydisks
ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /mnt/mydisk
mount: /dev/hdb1: can't read superblock

---

### Post by loell on 2008-08-15
```
sudo mount /dev/hdc /mnt/mydisk
```

---

### Post by linuxnoob1982 on 2008-08-15
Ok  here is what I get now.


mount: block device /dev/hdc is write-protected, mounting read-only

---

### Post by loell on 2008-08-15
heh, atleast its now mounting and you can now browse it. ;)

install **ntfs-config** by typing or pasting 

```
sudo apt-get install ntfs-config
``` 

then run it by ```
sudo ntfs-config 
``` , and check **external write supportfor external device**

---

### Post by linuxnoob1982 on 2008-08-15
Here is what I get


ubuntu@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
ubuntu@ubuntu:~$

I found the package online, but after I install it, it says this program needs to be run in root.

---

### Post by linuxnoob1982 on 2008-08-15
ok, so I was able to get past the root thing and here is what I get after running ntfs-config

Error reading bootsector: Input/output error
Failed to mount '/dev/hdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by oldos2er on 2008-08-15
> **linuxnoob1982 said:**
> 
I found the package online, but after I install it, it says this program needs to be run in root.

 To run as root use the command: sudo ntfs-config

---

### Post by linuxnoob1982 on 2008-08-15
I was able to run ntfs-config and I checked external.

Now what?  I still can't partition the drive.  Gparted still can't see it.

ERRR.

---

### Post by loell on 2008-08-15
oh noes, i'm really really sorry

after re-reading the previous page, it was suppose to be

```
sudo mount /dev/hdb /mnt/mydisk
```

---

