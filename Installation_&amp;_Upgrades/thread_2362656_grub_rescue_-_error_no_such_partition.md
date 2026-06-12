---
title: "grub rescue - error: no such partition"
date: 2017-05-31
forum: Installation &amp; Upgrades
---

### Post by sleuvins on 2017-05-31
Hi, I'm using my first Ubuntu installation (16.04) in dual boot with  windows 7, everything was working until today, when I accidentally  booted windows recovery. I quit the soonest I could, but now I'm just  unable to boot anything, stuck at the grub rescue screen.

From the information I've gathered I tried to find my linux partition, here's what I got from trying few 'ls' :

```
ls 
(hd0) (hd0,msdos5) (hd0, msdos3) (hd0, msdos2) (hd0, msdos1)
grub rescue>ls (hd0,1)
unknown filesystem
grub rescue>ls (hd0,2)
unknown filesystem
grub rescue>ls (hd0,3)
unknown filesystem
grub rescue>ls (hd0,4)
error: no such partition
grub rescue>ls (hd0,5)
unknown filesystem
grub rescue>ls (hd0,6)
error: no such partition
```

So  I boot a liveUSB with the same ISO image I used for my installation  (but on a new liveUSB mount) and I tried the boot repair utility, it  said that it succeeded, but I'm still unable to boot anything except the  liveUSB. Strangely, in the liveUSB I couldn't open any of the tabs  "grub location" or "grub options" in the advanced options... Here's the  boot-info: [https://paste.ubuntu.com/24728243/](https://paste.ubuntu.com/24728243/)

Some commands output:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda -l
Disque /dev/sda : 465,8 GiB, 500107862016 octets, 976773168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb955b955

Périphérique Amorçage     Start       Fin  Secteurs   Size Id Type
/dev/sda1                  2048  24578047  24576000  11,7G 27 Hidden NTFS WinRE
/dev/sda2    *         24578048  24782847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda3              24782848 336556652 311773805 148,7G  7 HPFS/NTFS/exFAT
/dev/sda4             336558078 976771071 640212994 305,3G  f Étendue W95 (LBA)
/dev/sda5             629737472 976771071 347033600 165,5G  7 HPFS/NTFS/exFAT

ubuntu@ubuntu:~$ sudo df -Th
Sys. de fichiers Type     Taille Utilisé Dispo Uti% Monté sur
udev             devtmpfs   1,9G       0  1,9G   0% /dev
tmpfs            tmpfs      382M    6,2M  376M   2% /run
/dev/sdb1        vfat       1,9G    1,5G  464M  76% /cdrom
/dev/loop0       squashfs   1,4G    1,4G     0 100% /rofs
/cow             overlay    1,9G    334M  1,6G  18% /
tmpfs            tmpfs      1,9G    680K  1,9G   1% /dev/shm
tmpfs            tmpfs      5,0M    8,0K  5,0M   1% /run/lock
tmpfs            tmpfs      1,9G       0  1,9G   0% /sys/fs/cgroup
tmpfs            tmpfs      1,9G    148K  1,9G   1% /tmp
tmpfs            tmpfs      382M     88K  382M   1% /run/user/999
/dev/sdc1        fuseblk    466G    258G  208G  56% /media/ubuntu/Seagate Expansion Drive
/dev/sda3        fuseblk    149G    107G   43G  72% /media/ubuntu/ACER
```


My  linux partition should be sda4, and the sda5 is the partition I used to  share my data between the two OS. sdb1 is the liveUSB, but what does it  means that "The integrity check of Syslinux failed"? sdc1 is my external ssd, could have ejected it before running these... (Also, I've  attached a screenshot of gparted if it helps)

I've tried to mount sda4 anyway and of course:

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda4

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /media/sda4
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

ubuntu@ubuntu:~$ dmesg | tail 
[  863.047575] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  863.048022] sd 7:0:0:0: [sdc] 976773167 512-byte logical blocks: (500 GB/466 GiB)
[  863.049144] sd 7:0:0:0: [sdc] Write Protect is off
[  863.049150] sd 7:0:0:0: [sdc] Mode Sense: 4f 00 00 00
[  863.050945] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  863.114951]  sdc: sdc1
[  863.118555] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 6230.193387] EXT4-fs (sda4): unable to read superblock
[ 6230.193451] EXT4-fs (sda4): unable to read superblock
[ 6230.193499] EXT4-fs (sda4): unable to read superblock


```

I  believe that my filesystem got corrupted somehow and is unable to be  read or would it be my kernel that is broken? It made me think that I should just reinstall ubuntu, is it the  best I can do? How to do it properly?

---

### Post by oldfred on 2017-05-31
Windows has done this for years. And when you upgrade to Windows 10, if you keep MBR(msdos) it will do it again.
It rewrites partition table and "forgets" to write the Linux partitions. We consider it a bug, but Microsoft has not fixed and it has been there since Windows 7 and it still there. They probably consider it a "feature". 

 /dev/sda4             336558078 976771071 640212994 305,3G  f Étendue W95 (LBA)
/dev/sda5             629737472 976771071 347033600 165,5G  7 HPFS/NTFS/exFAT 

Your sda4 is the extended partition which is not mountable, it is just a container for all the logical partitions.
And you now show a gap between start of extended and start of sda5 which is probably where your Linux partitions was. Your sda5 also probably was renumbered and that may not be critical as now UUID is primarily used.

      
 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors ( your fdisk above showed sectors, so may not be required) :
sudo parted /dev/sda unit s print 

    
You can use testdisk or parted rescue. Those with only one partition found parted rescue easier, not sure with two. You probably need to know size of each Linux partition or else it may try to recover one partition and you have to recover two.
      
 Used parted rescue
[URL="http://ubuntuforums.org/showthread.php?t=2315405"]http://ubuntuforums.org/showthread.php?t=2315405
[/URL]
 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 

[URL="http://ubuntuforums.org/showthread.php?t=2315405"]
[/URL]

---

### Post by sleuvins on 2017-06-01
Many thanks! It seems I was not looking in the right threads.
Finding my missing partitions was easy, using parted:

```
$ parted
$ unit s
$ rescue [start of sda4] [end of sda4]

```

It found my linux partitions and I had to do it again for my linux swap partition (starting from the end point of linux partition to the end point of sda4).

Maybe I've overcomplicated myself, but I've then done a boot-repair so I could be assured when I find my bootInfo file, which is here: [https://paste.ubuntu.com/24735376/](https://paste.ubuntu.com/24735376/)

Now the boot give me another grub error: "file '/boot/grub/i386-pc/normal.mod' not found", mounting linux partition and doing a grub install from command line solved it:

```
$ sudo mount /dev/sda6 /mnt
$ sudo grub-install /dev/sda --root-directory=/mnt
```

Now it's working again, thank you!

---

