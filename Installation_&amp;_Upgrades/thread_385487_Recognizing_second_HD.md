---
title: "Recognizing second HD"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by daveman77 on 2007-03-15
Thanks for all the help so far guys. My first foray into Linux was only made possible by the kind people here.

Now I have another issue. I have 2 hard drives. On the first HD is my Ubuntu/XP dual boot. On the second HD (sata) is all my media I used with my previous XP-only PC. When I log into my XP Partition it recongnizes the second HD and I can play music, etc. When I log into Ubuntu I have no idea how to find the second HD containing all my media.

How do I find it? :confused:

---

### Post by zvacet on 2007-03-15
I´m not promissing anything,but try places>computer

---

### Post by wpshooter on 2007-03-15
> **daveman77 said:**
> Thanks for all the help so far guys. My first foray into Linux was only made possible by the kind people here.

Now I have another issue. I have 2 hard drives. On the first HD is my Ubuntu/XP dual boot. On the second HD (sata) is all my media I used with my previous XP-only PC. When I log into my XP Partition it recongnizes the second HD and I can play music, etc. When I log into Ubuntu I have no idea how to find the second HD containing all my media.

How do I find it? :confused:

If that second hard drive is in a NTFS, then you have to have a special driver in order to get Ubuntu to see the drive.  I forget the name of it but search around a bit and I am sure you will find it.

Good luck.

---

### Post by daveman77 on 2007-03-15
Its not there. :(

---

### Post by mikesignguy on 2007-03-15
in a terminal type


cat /etc/fstab

and give us the results

---

### Post by daveman77 on 2007-03-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d9fce05c-fec2-4eee-ba4d-e6beca46dda9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ed67036e-3e62-4c54-976e-899578f9dc2b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by mikesignguy on 2007-03-15
good now did you format the drive in window or linux?

now , in a terminal type 

mount

---

### Post by daveman77 on 2007-03-15
I formatted the sata HD in windows

I typed "mount" and got this:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by mikesignguy on 2007-03-15
now type 

sudo  fdisk -l


sorry i keep posting the command in different posts ... i was busy till now

compare the mount output to the fdisk output

the ouput of mount shows you disks that are mounted (accessably)

the output of fdisk shows you the unmount drives (basically)

now with the unmount drive you need to mount it

(cont)

---

### Post by daveman77 on 2007-03-15
Heres what I got from sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4416    14988645   83  Linux
/dev/sda3            4417        4500      674730    5  Extended
/dev/sda5            4417        4500      674698+  82  Linux swap / Solaris

[B]Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326    7  HPFS/NTFS[/B]


I'm assuming the bold is my sata HD. What do I need to do next?

(thanks for all the help btw)

---

### Post by mikesignguy on 2007-03-15
great  
the /dev/sda1 is the ntfs drive   

*warning NTFS is a windows only thing ** the linux gods are trying to get read and write access to these drives....they are still working on it
i have had good luck using them for read only...

i would suggest formating it for ext3 ... but that is later

now you need to make a place to mount the drive  ...in linux you can mount it anywhere but lets try and put it on your desktop

terminal type to make the mountpiont

sudo mkdir  /Desktop/storage

now mount it

sudo mount /dev/sda1 /Desktop/storage

---

### Post by daveman77 on 2007-03-15
I'm getting:

mkdir: cannot create directory `/Desktop/storage': No such file or directory

---

### Post by mikesignguy on 2007-03-15
sudo mkdir Desktop/storage

it should ask you for a password...don't forget the sudo

if that doesn't work IM me....

---

### Post by confused57 on 2007-03-15
Here's how to mount a Windows partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

or

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by daveman77 on 2007-03-15
I seem to have gotten it mounted but when I click to open the "storage" folder it says "Folder contents could not be diplayed. You do not have the permissions necessary to view the contents of "storage". :frown:

---

### Post by confused57 on 2007-03-15
Did you mount it with something like this?:

```
sudo mount /dev/sdb1 /media/windows -t ntfs -o nls=utf8,umask=0222
```

substitute /media/windows with whatever directory you selected to mount it to.

---

### Post by daveman77 on 2007-03-15
Awesome! That did it! Do I need to keep doing this or can I access my media from now on on my second HD?

Thanks to you both for helping me through this!

---

### Post by daveman77 on 2007-03-15
Now how the heck do I watch my videos? :confused: lol This Totem thing won't play them I'm such a noob.:(

---

### Post by confused57 on 2007-03-15
> **daveman77 said:**
> Awesome! That did it! Do I need to keep doing this or can I access my media from now on on my second HD?

Thanks to you both for helping me through this!

You'll need to add an entry to your /etc/fstab to have the partition automatically mount:

```
sudo cp /etc/fstab /etc/fstab_backup
```
this will create a backup of your fstab

then add an entry to your /etc/fstab:
```
gksudo gedit /etc/fstab
```

add an entry similar to this:
```
 /dev/sdb1     /media/windows   ntfs  nls=utf8,umask=0222      0       0
```

again, substitute your mountpoint for /media/windows in the above entry.

---

### Post by mikesignguy on 2007-03-15
read about fstab editing and you will have it every time you boot


[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)


psychocats rule!!!!!

---

### Post by confused57 on 2007-03-15
> **daveman77 said:**
> Now how the heck do I watch my videos? :confused: lol This Totem thing won't play them I'm such a noob.:(

Check out the multimedia section of this link:
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

The automatix site doesn't seem to be working at the moment, but automatix2 is a great way to install different media players and codecs:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Until the automatix site is up and running, you might try the first link & manually install.

---

