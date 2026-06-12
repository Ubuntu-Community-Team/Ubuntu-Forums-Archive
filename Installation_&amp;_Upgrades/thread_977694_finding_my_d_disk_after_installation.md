---
title: "finding my d disk after installation"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by mroels on 2008-11-10
Hello dear ubuntu users,

Yesterday MS Windows decided to crash down my laptop just after I had seen a brilliant film called 'Ghandi'. The film ends with Ghandi saying something like '[...]in the end all tyrants fall down. Think about that.' A accepted the falling down of the MS tyrant and installed a new order you all know ... ubuntu. Everything went smooth (maybu too smooth). Now I have a new OS but I just can't find my old D disk which contains plenty of files. 

Could someone explain me how I can integrate my D HD in Ubuntu? As I installed ubuntu on my first hard disk (C) I suppose ubuntu doesn't recognise the MS "infected" D disk. 

All help is very welcome! 

Thanks in advance,

Maarten

---

### Post by Otustelija on 2008-11-10
The partition is probably in NTFS format - see eg. [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) or [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/) for instructions on how to use it with Linux.

---

### Post by logos34 on 2008-11-10
> **Otustelija said:**
> The partition is probably in NTFS format - see eg. [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) or [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/) for instructions on how to use it with Linux.

mroels,

ubuntu now comes with ntfs-3g driver support out-of-the-box, so all you need to do is follow step 3 on the first link Otustelija provided--'automatic configuration':

sudo apt-get install ntfs-config

sudo ntfs-config

then check the box for 'internal' disk support (i.e. your 'D drive')

Now you have read+write access to your windows files

---

### Post by mroels on 2008-11-10
> **logos34 said:**
> mroels,

then check the box for 'internal' disk support (i.e. your 'D drive')

Now you have read+write access to your windows files

Hi there,

Thanks for the quick reply. I executed the steps, but when I open the Applications > System Tools > NTFS Configuration Tool I can only click on "Enable write support for external device". I can see the one for internal device, but I can't click it.

Any idea how to proceed from here? 

Cheers,

Maarten

---

### Post by logos34 on 2008-11-10
post output of these commands:

sudo fdisk -l

mount


sometimes rebooting helps

---

### Post by mroels on 2008-11-11
> **logos34 said:**
> post output of these commands:

sudo fdisk -l

mount


sometimes rebooting helps

Ok.After some ree ading on the web, I discovered I may have simply formatted my D disk too. I choose 'use complete disk space' when installing ubuntu as I believed that to mean only the total C disk space would be used. I wasn't aware yet that there are not really two separate disks, but just two partitions ...

Anyway here are the outputs:

_sudo fdisk -l:_

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc114c114

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7120    57191368+  83  Linux
/dev/sda2            7121        7296     1413720    5  Extended
/dev/sda5            7121        7296     1413688+  82  Linux swap / Solaris


_mount:_

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mroels/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mroels)

Thanks for the guidance!

Maarten

---

### Post by logos34 on 2008-11-11
yep, "C drive", "D drive", etc. is windows-speak for partitions, not separate physical disks.  

Looks like windows is completely gone.  Linux takes up the entire disk space.  "Use entire disk" means ubuntu overwrites the whole HDD.

You could try to recover your files/data that were on the (NTFS) D: partition using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), or PhotoRec (which contrary to its name can recover non-images as well).  But that would mean having to reinstall ubuntu because the restore process will overwrite the linux installation.  If you do restore D:, since it's a non-bootable my docs partition, you could boot up the ubuntu live cd, mount the partition and copy the files to usb flash drive

good luck

---

### Post by mroels on 2008-11-15
Thanks. I've decided to live with the loss. My most recent back-up will do. It's amazing how much one may learn through this forum in little time. Can't believe to have been such a blind windows consumer for all these years.

Another crazy thing that happened is that windows transformed all my music files into wma files. I'm now trying to find out how to transform the files to ogg or other and how to copy my cd's to flac using free software. All hints are welcome ;-)

Take care!

Maarten

---

