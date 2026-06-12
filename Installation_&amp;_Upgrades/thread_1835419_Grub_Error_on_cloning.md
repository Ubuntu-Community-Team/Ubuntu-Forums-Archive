---
title: "Grub Error on cloning"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by zak_neutron on 2011-08-29
Hi

I'm running: ```
Linux ******** 2.6.35-30-generic #56-Ubuntu SMP Mon Jul 11 20:01:08 UTC 2011 x86_64 GNU/Linux
```I recently tried cloning my 160 GB HDD to 500 GB HDD. My plan was as follows:


[LIST=1]
[*]Clone the HDD as it stood with Clonezilla
[*]Boot from the new 500 GB HDD to ensure all worked
[*]Move/resize partitions to gain more space for partitions (mainly /home /xp)
[*]My partitions are not very logical and I want to move to get the best set up.
[/LIST]

My current partition on the 160GB is as follows:

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS ("XP")
/dev/sdb2         102,398,310   155,155,769    52,757,460   b W95 FAT32 ("Shared")
/dev/sdb3         177,410,048   246,355,967    68,945,920  83 Linux ("/")
/dev/sdb4         246,356,775   312,580,095    66,223,321   5 Extended
/dev/sdb5         246,356,838   304,412,671    58,055,834  83 Linux ("/home")
/dev/sdb6         304,414,720   310,620,159     6,205,440  82 Linux swap / Solaris
/dev/sdb7         310,622,208   312,580,095     1,957,888  83 Linux ("/boot") 
```my current setup mount points in brackets

I ran into difficulty after the 1st step. The new 500GB complained of Grub Error unknown file system.

I have downloaded and used the boot shell script and attached the file (PLEASE IGNORE SDC HDD - that is another unused 160GB and has no boot capability).

Please note this attachment is AFTER the clonezilla.

I have also taken the sda (500GB) and sdb (160GB) and put into separate files and ran "diff" to look for differences.

There are differences - but I'm not sure what I do about it :(

My first intention is to make any changes to sda (500GB) drive to make it bootable then look at moving/re-organising the partitions. Any helpful pointers would be greatly received.

With Thanks

Zak

---

### Post by dino99 on 2011-08-29
uuid is different after each partitionning/formatting/resizing/...

so boot on a livecd, open a terminal to grab the new uuid:

sudo blkid

take note of it, then on the next boot from hdd, edit the boot line to set the new uuid (hold "shift" key down at bios end process to get the grub menu on a single OS system), then ctrl+x to continue to boot.
When logged , run:

sudo update-grub

---

### Post by YesWeCan on 2011-08-29
Have you got both the new and old drives connected at the same time?
This will confuse everything because all the cloned partitions UUIDs are the same.

```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0B2B4EDE756AAB02                       ntfs       xp
/dev/sda2        A933-F09F                              vfat       shared
/dev/sda3        6cfa264c-302a-48e9-a704-e4b7f0a187ff   ext4       
/dev/sda5        e6717623-6cf5-4e10-a6aa-9834c70959bb   ext4       
/dev/sda6        ae919eb6-59b5-4cbd-a3e8-4ec3a1f42d1f   swap       
/dev/sda7        dca08693-9e38-435c-879a-c5176bedd92d   ext3       
/dev/sdb1        0B2B4EDE756AAB02                       ntfs       xp
/dev/sdb2        A933-F09F                              vfat       shared
/dev/sdb3        6cfa264c-302a-48e9-a704-e4b7f0a187ff   ext4       
/dev/sdb5        e6717623-6cf5-4e10-a6aa-9834c70959bb   ext4       
/dev/sdb6        ae919eb6-59b5-4cbd-a3e8-4ec3a1f42d1f   swap       
/dev/sdb7        dca08693-9e38-435c-879a-c5176bedd92d   ext3       
/dev/sdc1        4C78-526A                              vfat       FAT_STORAGE
/dev/sdc2        E234DA1434D9EB93                       ntfs       ntfsstorage
```

---

### Post by zak_neutron on 2011-08-29
Thanks. Yes, both drives were connected at the same time. The 500 GB (sda) was connected via USB/Pata bridge and none of the partitions were mounted.

dino99: I was not able to get to any grub line to edit - it just said "Unknown file system".

I have tried to boot with supergrub rescue disk 2.0 (livecd) and that presents lots of options. Do suggest the ubuntu live CD instead?

---

### Post by oldfred on 2011-08-29
As long as you have both drives connected with identical UUIDs you will not be sure which partition you are using if you get it to work. Some have had it boot to one, first time then to the other second time. Huge problems.

If you want to keep 160GB drive you have to change UUIDs, edit fstabs, and reinstall grub2. While all this can be done and if you know what you are doing can do it relatively quickly, I suggest just starting over, partition the way you want and do a total new install. No duplicates, clean install without all the cruft from the old install. If you have data/settings in /home then you can just copy that data with rsync or cp -a commands.

You can also export list of installed applications and reinstall. I only do clean installs of each new version and many of the alpha/betas. I converted the process to a script and now can reinstall and reconfigure in less than an hour, but that took a bunch of tries to get it working well.

---

### Post by zak_neutron on 2011-08-29
Oldfred I'm attracted to what you are saying of the fresh install.

/home partition - like you say fairly easy
/ partition - I have a ton of stuff, some installed by apt. Other compiled directly
and unfortunately I have winbloze on my HDD (for the kids playing Sims 3!!). How would I deal with that?

I agree the

/boot
/swap

is no problem and is fairly generic (apart from telling grub to find winbloze)

---

### Post by YesWeCan on 2011-08-29
I don't understand why you feel you need both drives connected at the same time. If you just unplug the 160GB drive the new one should boot just fine (IF Clonezilla has cloned everything - see next paragraph) and then you can resize partitions and so on. Just don't have both connected at the same time.

The other thing is I don't know how Clonezilla does its cloning. Does it copy the MBR area as well as the partitions? Maybe **oldfred** knows. I always use dd to clone disks.

If it doesn't you'll need to clone the MBR area too:

sudo dd if=/dev/sdx of=/dev/sdy bs=512 count=60

where x is the letter of your 160GB disk and y is the letter of your 500GB disk. Check the letters using sudo fdisk -l before you start.
[COLOR=Red]**warning:**[/COLOR] the dd command is ruthless and if you get anything wrong you could trash the data on either disk.

---

### Post by oldfred on 2011-08-29
I have never used Clonezilla and have not paid attention to details.

As YesWeCan says you need to unplug 160GB drive. I avoid dd as he says it is too easy to damage things if you make a typo.

You worst case should just have to reinstall grub to the MBR after you disconnect the 160GB drive.

If you have complied your own programs that makes a clean install less desirable. I have just about only installed from apt or synaptic. But when I chnaged to 64 bit from my 32 bit that I had upgraded in place for years I found a lot of old stuff disapeared. Old programs, log files and not sure what else but I liked new install so much I started with clean installs all the time.

---

### Post by wackenroader on 2011-08-29
Boot in live cd, mount your partition with nautilus and go to folder /media an see the name of mount-point ex: 1abf3sd34lg56... copy the name of these folder, open the terminal and type: sudo su  and press enter, before type: sudo chroot /media/1abf3sd34lg56... before login type: mount /proc press enter, mount /sys, mount /dev, now run the command dpkg-reconfigure grub-pc press enter in two first option before select the disk you prefer and press space and enter, grub will reinstall with default configuration and detect all installations of any hard disks.

---

### Post by YesWeCan on 2011-08-29
As oldfred says, a reinstall of Grub is a good alternative to dd if the 500GB drive won't boot.

Just boot a live CD/USB (of the same Ubuntu version as on your hard drive)
[COLOR=Navy]sudo fdisk -l[/COLOR]
to check the drive name of the 500GB, it will probably be sda but check. I'll assume sda.
You have a separate boot partition in sda7, so mount this partition first
[COLOR=Navy]sudo mount /dev/sda7 /mnt[/COLOR]
and then reinstall Grub
[COLOR=Navy]sudo grub-install --boot-directory=/mnt /dev/sda[/COLOR]
then reboot.

---

