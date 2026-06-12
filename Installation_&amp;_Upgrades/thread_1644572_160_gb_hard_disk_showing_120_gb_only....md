---
title: "160 gb hard disk showing 120 gb only..."
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by vagrantjoe on 2010-12-13
I'm using Meerkat in my Inspiron 1525... 160gb hard disk...
But nautilus is showing that the disk capacity is 120gb... So should I update my BIOS? If yes, how do I do it? I tried searching the net and my brain's dead... Kindly help me fellow ubuntuans...

---

### Post by dabl on 2010-12-13
What is the output of ```
sudo fdisk -lu
``` and ```
sudo df -h
```?

---

### Post by vagrantjoe on 2010-12-14
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef590




and




Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   299808767   149903360   83  Linux
/dev/sda2       299810814   312580095     6384641    5  Extended
/dev/sda5       299810816   312580095     6384640   82  Linux swap / Solaris
joseph@joseph-Inspiron-1525:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   21G  113G  16% /
none                  2.0G  296K  2.0G   1% /dev
none                  2.0G  2.6M  2.0G   1% /dev/shm
none                  2.0G  104K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/home/joseph/.Private
                      141G   21G  113G  16% /home/joseph/Private


Thanks for showing interest mate...

---

### Post by vagrantjoe on 2010-12-14
is everything ok with the pc?

---

### Post by dabl on 2010-12-14
Is swap active?  Show the output of 

```
sudo mount
```

If it is, that's probably where the rest of your "missing" space is.  Remember, the drive OEM's "160G" is 160 billion bytes. It is not (1024 x 1024 x 1024 x 160) bytes.  Linux (and other OS's) measure in Kbytes, Mbytes, and Gbytes, which are multiples of Kilobytes which are 1024 bytes each.

I think your drive is fine.

---

### Post by vagrantjoe on 2010-12-14
joseph@joseph-Inspiron-1525:~$ sudo mount
[sudo] password for joseph: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/joseph/.Private on /home/joseph/Private type ecryptfs (ecryptfs_sig=8f9887d2339cafb0,ecryptfs_fnek_sig=6c1163e7e94b46d9,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/joseph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joseph)

so is swap active? and what is swap? don't bother to explain if it's too complicated... I wish I knew linux well enough to contribute like you and other guys here do... I'm only a month old linux ubuntu baby... lol!!!

---

### Post by dabl on 2010-12-14
I don't see swap mounted, but I do see an encryped fs. I wonder how much disk space that hides?

Try, in the terminal, issuing ```
sudo swapon
```

let's see if it throws an error.

---

### Post by vagrantjoe on 2010-12-15
Usage:
 swapon -a [-e] [-v] [-f]             enable all swaps from /etc/fstab
 swapon [-p priority] [-v] [-f] <special>  enable given swap
 swapon -s                            display swap usage summary
 swapon -h                            display help
 swapon -V                            display version

The <special> parameter:
 {-L label | LABEL=label}             LABEL of device to be used
 {-U uuid  | UUID=uuid}               UUID of device to be used
 <device>                             name of device to be used
 <file>                               name of file to be used




I did create a private folder using the below steps


Setting-up the encrypted folder is simple. First, if you haven’t already, update your system software as described at the beginning of this chapter. Then open a terminal window (Applications  Accessories Terminal) and type the following commands:

sudo apt&#8208;get install ecryptfs&#8208;utils 
ecryptfs&#8208;setup&#8208;private 

You’ll need to type your login password when prompted after typing the second of the commands. You’ll also be invited to create a mount passphrase. This can be anything from a few words to a sentence, and can include numbers and symbols such as punctuation marks. Ensure you remember what you type because you might need it at a future date 124  : Securing the System 
to manually unlock the filestore! Alternatively, you can simply hit Enter to have a passphrase generated automatically, but you should print out the passphrase and store it in a secure location. Once the commands have completed, log out and back in again. When the desktop appears, you’ll find you have a new /private folder within your /home folder. As mentioned, this can be used just like a standard folder—files and folders can be stored there, and you will see no sign that the contents of the folder are in fact encrypted.

---

### Post by dabl on 2010-12-15
Let's see the output of ```
cat /etc/fstab
```

and also try to turn swap on again with the -f flag:

```
sudo swapon -f
```

---

### Post by vagrantjoe on 2010-12-16
joseph@joseph-Inspiron-1525:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3a63a867-217c-4ee7-9c5c-9d6bbf6de6a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bff9ddbc-070f-4222-889c-a1a52b5e57ff none            swap    sw              0       0

and....


joseph@joseph-Inspiron-1525:~$ sudo swapon -f
[sudo] password for joseph: 

Usage:
 swapon -a [-e] [-v] [-f]             enable all swaps from /etc/fstab
 swapon [-p priority] [-v] [-f] <special>  enable given swap
 swapon -s                            display swap usage summary
 swapon -h                            display help
 swapon -V                            display version

The <special> parameter:
 {-L label | LABEL=label}             LABEL of device to be used
 {-U uuid  | UUID=uuid}               UUID of device to be used
 <device>                             name of device to be used
 <file>                               name of file to be used

---

### Post by owiknowi on 2010-12-16
maybe you have already tried this:
boot from a gparted or pmagic cd and look what kind of partitions are shown.

there might be a hidden system partition?

---

### Post by dabl on 2010-12-16
> **vagrantjoe said:**
> 
# swap was on /dev/sda5 during installation
UUID=bff9ddbc-070f-4222-889c-a1a52b5e57ff none            swap    sw              0       0



So you do (or did) have a swap partition defined in /etc/fstab.

I'd like to see the output of ```
sudo blkid
```

I'm wondering if somehow the UUID of that partition has been subsequently changed.

---

### Post by psusi on 2010-12-16
It is because of the definition of a gigabyte.  The computer industry long ago defined a kilobyte to be 1024 bytes, a megabyte to be 1024 kb, and a gigabyte to be 1024 mb.  Because of this you actually have a 149 GB drive, but hard drive manufacturers decided to define a gb as 1,000,000,000 bytes and mislabel their drives to be larger than they are.

On top of that the filesystem has a bit of overhead, and on top of that, ext[234] reserves 5% of the space for root by default.

---

### Post by vagrantjoe on 2010-12-16
joseph@joseph-Inspiron-1525:~$ sudo blkid
[sudo] password for joseph: 
/dev/sda1: UUID="3a63a867-217c-4ee7-9c5c-9d6bbf6de6a2" TYPE="ext4" 
/dev/sda5: UUID="bff9ddbc-070f-4222-889c-a1a52b5e57ff" TYPE="swap" 


so psusi what you're saying that my pc is fine?

---

### Post by akand074 on 2010-12-16
> **vagrantjoe said:**
> joseph@joseph-Inspiron-1525:~$ sudo blkid
[sudo] password for joseph: 
/dev/sda1: UUID="3a63a867-217c-4ee7-9c5c-9d6bbf6de6a2" TYPE="ext4" 
/dev/sda5: UUID="bff9ddbc-070f-4222-889c-a1a52b5e57ff" TYPE="swap" 


so psusi what you're saying that my pc is fine?

It looks to me like your pc is just fine.

---

### Post by psusi on 2010-12-17
> **vagrantjoe said:**
> 
so psusi what you're saying that my pc is fine?

Yes.

---

### Post by vagrantjoe on 2010-12-17
thanks guys... thanks a lot...

---

