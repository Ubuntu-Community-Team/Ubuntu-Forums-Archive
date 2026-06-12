---
title: "After the installation of the latest Ubuntu 14, the old files are missing"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by Gins on 2014-09-19
Hi Friends

I had the latest Ubuntu 14 desktop version.
There was a small problem.
So I reinstalled it. I have it on a DVD.
During the reinstallation, it told me that there will not be a problem with my existing documents.
I accepted it and went ahead with installation of the Ubuntu 14.

By the way, during the installation there was not formatting of the hard drive.

I have some important letters on the Libre wordprocessor.
Now I can't see those letters.
I opened the wordprocessor. It seems the installation has installed a clean new program.
**I badly need those documents.**

How can I retrieve those documents?

The same problem exsists with Firefox browser and Google Chrome browser.
The bookmarks are not there. How can I retrieve them?

I profoundly appreciate your advice on this matter.

---

### Post by fantab on 2014-09-19
You can try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") to find your lost files.

It seems all your config files too got overwritten by the new install. This is one disadvantage if your don't have a separate /home partition.
Haven't you synced your firefox and chrome profiles? You must always... it keeps your browser bookmarks and other settings safe.
I use **xmarks** firefox/chrome extension to keep my bookmarks synced across all my devices...

---

### Post by ajgreeny on 2014-09-19
Let's start at the start.


[LIST=1]
[*]Do you have a separate /home partition or just a home folder within the root partition?
[*]Do you have any backups?
[*]Are you still using the same username on the new installation?
[*]Did you overwrite the old partitions or make new ones when you installed?
[/LIST]

More info is needed before it is possible to tell exactly what happened, but show us the output of ```
sudo fdisk -l
```or if this is a UEFI system use ```
sudo parted -l
```and also ```
df -h
```to show disk usage.

You could also use the find command if you know the exact name of one of your missing files with ```
find -name filename
```even using wildcards such as * if you remember only part of the name.

---

### Post by Gins on 2014-09-19
**Thanks for the excellent replies.**

I use the same username for the new installation.

I allowed the installation to overwrite the old partition.

I didn't allow to format; because it will erase everything.


**I have Ubuntu on 'sda1' partition. **

So when I start the computer, Ubuntu comes to the screen.

I have Fedora Linux on 'sda5'. It works fine.

All the other partitions are empty. I will install other Linux programs like SuSE, when time permits.

I had a problem.** It was Ubuntu didn't come to the screen. **

So I reinstalled it on the belief it would fix the problem.

Now I think the problem lies in the graphic card. **I will buy a new graphic card next week.**

Today, I don't have money to buy hardware.

[COLOR="#FF0000"]I appreciate all your comments.[/COLOR]

&#8230;....................................................................

[ I had a file under the name ' French124.odt '. ]

nissanka@nissanka-desktop:~$ find -name French124.odt
nissanka@nissanka-desktop:~$ 

**As you can see, the 'find' command did not find it.**
I doubt very much whether the command 'find' is able to find files written using the 'Libre' wordprocessor program.
As far as I understand, it will find '*txt' files.



nissanka@nissanka-desktop:~$ sudo fdisk -l
[sudo] password for nissanka: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003928d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   157290495    78644224   83  Linux
/dev/sda2       157292476   976771071   409739298    5  Extended
/dev/sda5       157292478   314584829    78646176   83  Linux
/dev/sda6       314584893   471877244    78646176   83  Linux
/dev/sda7       471877308   629169659    78646176   83  Linux
/dev/sda8       629169723   786462074    78646176   83  Linux
/dev/sda9       956772352   976771071     9999360   82  Linux swap / Solaris
/dev/sda10      786462720   956766207    85151744   83  Linux

Partition table entries are not in disk order


nissanka@nissanka-desktop:~$ sudo parted -l
Model: ATA MAXTOR STM350032 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  80,5GB  80,5GB  primary   ext4            boot
 2      80,5GB  500GB   420GB   extended
 5      80,5GB  161GB   80,5GB  logical   ext4
 6      161GB   242GB   80,5GB  logical   ext2
 7      242GB   322GB   80,5GB  logical   ext2
 8      322GB   403GB   80,5GB  logical   ext2
10      403GB   490GB   87,2GB  logical   ext4
 9      490GB   500GB   10,2GB  logical   linux-swap(v1)




nissanka@nissanka-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        74G  4,0G   66G   6% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            2,0G  4,0K  2,0G   1% /dev
tmpfs           396M  1,2M  394M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            2,0G  156K  2,0G   1% /run/shm
none            100M   36K  100M   1% /run/user
nissanka@nissanka-desktop:~$

[COLOR="#FF0000"]-------------------------------------------------------------------------------------------------------------------------------[/COLOR]
The testdisk program created a file under the name 'testdisk-7.0-WIP' .
I don't know how to use the file.
The original file was 'linux26.tar.bz2'.
The 'k3b' program is installed.
So I can copy it onto a CD.
**Please let me know how to go ahead with the file**.

---

### Post by ajgreeny on 2014-09-21
Sorry I can not help with testdisk as I have never used it and have no experience of its use by anyone else.

If the file was present on disk the find command would have found it with no problem; it does not work on .txt files only but will find anything as long as you get the name correct or use appropriate wildcards.  If you're not sure of the case of the filename use -iname instead of -name in the options.
See my examples below
```
user@Xubuntu:~$ find -name Choc-Rasp-Torte*
./Documents/Choc-Rasp-Torte.odt
./Quicknotes/Choc-Rasp-Torte.txt
user@Xubuntu:~$ find -iname choc-rasp-torte*
./Documents/Choc-Rasp-Torte.odt
./Quicknotes/Choc-Rasp-Torte.txt
user@Xubuntu:~$ find -iname *oc-*sp-*rte*
./Documents/Choc-Rasp-Torte.odt
./Quicknotes/Choc-Rasp-Torte.txt
```

---

### Post by Gins on 2014-09-21
Thanks ajgreeny for the help.

As you see, it did not find.
[B]I appreciate all your help. 
So please tell me all the other available avenues to get my files back.[/B]

nissanka@nissanka-desktop:~$ find -iname French124
nissanka@nissanka-desktop:~$

---

### Post by ajgreeny on 2014-09-21
Are you sure the French124 file did not have a file suffix of some sort, eg .txt or .doc etc etc?

Just to be sure try ```
find -iname French124*
```
If that doesn't work I can not really help more as I honestly don't know how to recover deleted files.

You have a lot of partitions with Linux filesystems on your disk; do you know what they all are?
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   157290495    78644224   83  Linux
/dev/sda2       157292476   976771071   409739298    5  Extended
/dev/sda5       157292478   314584829    78646176   83  Linux
/dev/sda6       314584893   471877244    78646176   83  Linux
/dev/sda7       471877308   629169659    78646176   83  Linux
/dev/sda8       629169723   786462074    78646176   83  Linux
/dev/sda9       956772352   976771071     9999360   82  Linux swap / Solaris
/dev/sda10      786462720   956766207    85151744   83  Linux
```
It is possible that the missing files could be on one of those partitions which are no longer mounted at boot as you have a newly written /etc/fstab file.

---

### Post by Gins on 2014-09-22
Thanks ajgreeny

nissanka@nissanka-desktop:~$ find -iname French124*
nissanka@nissanka-desktop:~$ 

**No, it did not find.**
I hope to install other Linux flavours on other partitions.
I hope I will find time for it.

Ubuntu is on 'sda1' partition.
Fedora is on 'sda5' partition.

---

