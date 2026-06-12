---
title: "Ubuntu Installer (and GParted) don’t properly recognize drive."
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by garywclem on 2011-12-07
I am trying to install Ubuntu 11.10 on a 320 GB drive partitioned as a 15GB Primary Partition and a 283 GB Logical drive.  The 15GB Primary partition is FAT32 (empty) which I created for Ubuntu.  The other (Logical partition) formatted as NTFS contains about 220 GB of data, and is accessed by various Windows OS’s as a backup drive.  My problem is that neither Ubuntu installer nor GParted recognize the partition setup.  All they see is one partition of 298.09 GiB with Partition unallocated and File System unallocated.  Windows 7 Disk Management sees them properly, and marks them as healthy.  I ran diskcheck on both partitions.  Ubuntu installer only allowed me the option of formatting the 298 GiB unallocated partition to install Ubuntu.

As background, this box contains 3 physical drives.  One drive contains XP on a Primary, with several supporting logical drives in an extended partition.  The second drive contains W7 Home Premium on a Primary, with several supporting logical drives in an extended partition.  Both the XP and W7 drives were unplugged for the Ubuntu install.  I prefer each drive to be capable of stand-alone operation.  I then use EasyBCD to construct the multi-boot menu. 

I have used Microsoft since Dos 3 but have almost no knowledge of Linux.  Any suggestions regarding the above problem will be appreciated.

---

### Post by leclerc65 on 2011-12-07
Fat32 for Ubuntu ? No, you should format it as EXT4, or just delete it, and configure it during installation.

---

### Post by garywclem on 2011-12-07
Thanks for the reply.  The 15 GB partition originally was unallocated and freespace, but Ubuntu said it was 298 GiB of unallocated.  That's why I formatted it, to see if it made any difference.

---

### Post by bluexrider on 2011-12-07
Ubuntu doesn't like FAT 32 but plays well with NTFS. You can even install Ubuntu in NTFS if you wanted.

---

### Post by oldfred on 2011-12-07
Ubuntu needs Linux partitions to support ownership & permissions. An install in NTFS is wubi and is just one file that has the full Ubuntu stuffed in it. Since you have room, you need to do a full install.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")


Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2011-12-08
If the disk is not seen properly there is something wrong with it, or the way it's set up.

Windows and Linux sometimes do differ in what they mind on a disk, and what not.

Few basic things that windows ignores and ubuntu doesn't are:

1. Is the disk maybe a dynamic disk? That is a windows feature and ubuntu will not work on it. Check in Disk Management, it should be Basic.

2. Has the disk been used in fakeraid (mobo raid) earlier? In that case it keeps raid meta data even after formatting which windows ignores but ubuntu not.

Also if you did any resizing for example with some program in windows, it might have been done in a way that windows considers "normal", but ubuntu picks up some error on it and refuses to use it.

---

### Post by coffeecat on 2011-12-08
> **garywclem said:**
> My problem is that neither Ubuntu installer nor GParted recognize the partition setup.  All they see is one partition of 298.09 GiB with Partition unallocated and File System unallocated.

Is Gparted showing the whole drive as unallocated, rather than an unformatted partition? If the former, this is almost certainly due to a partition table irregularity which needs fixing before you can proceed. Windows Disk Utility and some Windows partitioning apps seem to tolerate partition table problems, which is not really a good thing.

Let's take a closer look at your partition table. Boot up the Ubuntu 11.10 live CD and choose "try Ubuntu" to get to the live desktop. Open a terminal and run this command:

```
sudo fdisk -lu
```

Post the fdisk output between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. Also, if you highlight the output with the mouse, you can right-click -> copy so that you can paste it into your post.

---

### Post by garywclem on 2011-12-08
Coffeecat - here is fdisk output:

```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x5ba61be1 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63    31503464    15751701    b  W95 FAT32 
/dev/sdb2        10522575   625137344   307307385    f  W95 Ext'd (LBA) 
/dev/sdb5        31503528   625137344   296816908+   7  HPFS/NTFS/exFAT 
ubuntu@ubuntu:~$ ^C
``` 

> [COLOR="Red"]Post the fdisk output between ```
 and 
``` tags for clarity. The simplest way of doing this is to highlight the output and then click on the button in the message toolbar.[/COLOR]

Don't see a # in the message tool bar.  What am I missing?

Oldfred - Thanks for the great links.

---

### Post by coffeecat on 2011-12-08
> **garywclem said:**
> ```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x5ba61be1 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63    [COLOR="Red"]31503464[/COLOR]    15751701    b  W95 FAT32 
/dev/sdb2        [COLOR="Red"]10522575[/COLOR]   625137344   307307385    f  W95 Ext'd (LBA) 
/dev/sdb5        [COLOR="Red"]31503528[/COLOR]   625137344   296816908+   7  HPFS/NTFS/exFAT 
ubuntu@ubuntu:~$ ^C
``` 

There's a really nasty illegality in your partition table. I've highlighted the relevant figures in red. The start sector of your sdb2 extended partition is showing as inside your sdb1 primary partition, which is completely impossible. Fortunately, the start sector of the logical sdb5 partition comes after the end sector of sdb1. The start sector of sdb2 should be somewhere between 31503464 and 31503528. I have a strong suspicion that the Windows Disk Utility is responsible for this - I've seen worse. Whatever - this needs repairing before you do any partitioning.

I'm fairly sure that fixparts will deal with this. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

There are both Windows and Linux (which you can run from the live CD session) versions. Have a read through and post back if you have any questions. If you feel confident enough to proceed, OK, but do backup everything of importance first. Manipulating partition tables has the potential for further trouble.

> **garywclem said:**
> Don't see a # in the message tool bar.  What am I missing?

Have a look at my screenshot. There are several useful toll icons in the toolbar.

---

### Post by garywclem on 2011-12-08
Coffeecat – (and all others), Thanks for the help.  Fixparts seems to have fixed the problem.  Both partitions are now visible in Ubuntu installer and GParted as well as windows.  I had to use Fixparts from Windows, as I seem to lack the knowledge to run it in Ubuntu.

As to the # symbol, I used the “Quick Reply” instead of the “New Reply” box.

---

### Post by coffeecat on 2011-12-08
Excellent. I'm glad fixparts did the trick.

Going back to an earlier comment. As someone has already pointed out, your sdb1 FAT32 partition won't be suitable for Ubuntu unless you format it with a Linux filesystem such as ext4. Also - you will need a separate swap partition.

---

