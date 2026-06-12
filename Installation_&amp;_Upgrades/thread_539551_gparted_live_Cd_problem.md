---
title: "gparted live Cd problem"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2007-08-31
The auto install function diden't create a home partition and a very large root partition.
I now want to shrink the root partition and make the free space into a root partition.
My Ubuntu install is on a SATA disk, windows Xp is on one of two IDE disks.

I downloaded the ISO of gparted and burned it.
When I boot it starts of well, but stops at the last screen before (according to the documentation of the website) it should swithch to graphical.
so I'm stuck with gparted ~#_

anyone have any idea what is going wrong, or does it just take very very long for it to swtich to graphical ?

Or should I be choosing one of the other startup choices in the first screen ?

---

### Post by Pumalite on 2007-08-31
Bad iso or Gparted doesn't like your hardware. Try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) It has a partitioner.

---

### Post by dabl on 2007-08-31
> **Hagar55 said:**
> 

anyone have any idea what is going wrong?

Does that version of GParted Live CD ask you to choose a display resolution?  Try picking something very "plain vanilla" like 640 x 480, if you can, or 800 x 600.  :)

---

### Post by Hagar55 on 2007-09-01
No it doens't ask for a resolution.
I think choose the latest version.
My hardware is rather plain, asus A7NX8_DE, AMD 2600+, 1Gig Mem, NVIDIA FX5200 AGP, and two maxtor HD on IDE and one Samsung disk on SATA (wich contains the Ubuntu partitios.

---

### Post by Pumalite on 2007-09-01
At boot, Gparted presents you with a boot prompt; in most cases hitting Enter will suffice.

---

### Post by Hagar55 on 2007-09-01
Sadly hitting the enter keyjust produces more prompts.....

---

### Post by Pumalite on 2007-09-01
I would do md5sum on the iso, burn again at 4x, check for CD corruption after burn. Also don't forget rescuecd; it has partitioner. Download a new iso if necessary. They are small downloads.

---

### Post by Hagar55 on 2007-09-02
I'll have to try that I guess...

---

### Post by Seisen on 2007-09-02
You need to edit xorg.conf and change it to "vesa" So open the file up by putting this in.

```
sudo vim /etc/X11/xorg.conf
``` and look for a line that says something like this

```
Section "Device"
    Identifier  "GEForce4 GO 440"
    Driver      "nv"
EndSection
```

change the driver part to say "vesa"

To change the file you need to press Shift+I and it should say Insert then once you change that do this

```
:wq
``` it will write the file and close it. Once you are done doing that type in startx and it should go graphical.

---

### Post by Hagar55 on 2007-09-07
I downloaded the version 0.3.4.7 (instead of 0.3.408).
Worked the first time around this time.
I shrinked my root partition and made the free space a new ext3 partition.

Now I have the second ext partition, how do I make it the Home partition ?

---

### Post by merlinus on 2007-09-07
Something along these lines should work in /etc/fstab:

/dev/sda2  /home ext3 defaults,errors=remount-ro 0 2

Substitute your partition fo sda2, which you can find out by:

```

sudo fdisk -l

```if you do not already know it.

And this assumes you formatted it as ext3.

-merlin

---

### Post by Hagar55 on 2007-09-07
when I go into file system and into the ext folder, there is no fstab file, or should I be looking in a terminal window ?

---

### Post by merlinus on 2007-09-07
/etc/fstab

Are you running from your hdd or the live cd?

If the latter, then you need to mount your ubuntu partition first.

-merlin

---

### Post by Hagar55 on 2007-09-08
Found fstab with the search funtion of nautilus.
This is what I get when I open the file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=88045bb0-815b-434f-b53e-86153c4cdb20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=df707aa2-2b63-443d-a09f-26c1ae025782 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I don't see any line referring to the home partition.

---

### Post by merlinus on 2007-09-08
You have to add the /home line yourself.

That's why I asked for results of [B]sudo fdisk -l

[/B]so we could see the partition number.

-merlin

---

### Post by Hagar55 on 2007-09-09
Ok, sorry not at all home in the linux world....feeling very useless actually.
This is the result of the command :

Schijf /dev/sda: 300.0 GB, 300069052416 bytes
255 koppen, 63 sectoren/spoor, 36481 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1       29321   235520901    7  HPFS/NTFS
/dev/sda2   *       29322       32601    26346600   83  Linux
/dev/sda3           36184       36481     2393685    5  Uitgebreid
/dev/sda4           32602       36183    28772415   83  Linux
/dev/sda5           36184       36481     2393653+  82  Linux wisselgeheugen

Partitietabel-items liggen niet in schijfvolgorde.

Schijf /dev/hdb: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/hdb1               1        6374    51199123+   7  HPFS/NTFS
/dev/hdb2            6375        9964    28836675    f  W95 Uitgeb. (LBA)
/dev/hdb5            6375        9964    28836643+   b  W95 FAT32

If I acces the properties of the partition in Nautilus,there is a tab marked volume.
If i acces the Advanced link on it, I can see blanck spaces with Mount Point, File system and Mount options. Can you fill in these spaces to let the drive mount on boot ?

And on the other tabs I see the drive is read only, with no way to change the permissions.
Will this only change once the drive is mounted on boot ?

Is there a place where I can find a detailed and deeper manual of the nautilus app. and linux in general ?

I don't like having to ask help on every simple issue I come across.....

---

### Post by merlinus on 2007-09-09
Looks like sda4 is the partition you are wanting to use for /home?

We need one more piece of info, so post the results of:

```

blkid

```

---

### Post by Hagar55 on 2007-09-10
/dev/hda1: TYPE="ntfs" 
/dev/hda5: LABEL="DSK1_BACKUP" UUID="0000-0E34" TYPE="vfat" 
/dev/hda6: TYPE="ntfs" 
/dev/hdb1: TYPE="ntfs" 
/dev/hdb5: LABEL="DSK2_BACKUP" UUID="DCDC-6F1C" TYPE="vfat" 
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="88045bb0-815b-434f-b53e-86153c4cdb20" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="df707aa2-2b63-443d-a09f-26c1ae025782" TYPE="swap" 

the requested info..

---

### Post by mkc on 2007-09-10
If I read right and you already have your system up and running then you need to edit /etc/fstab. There's a how to here [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html).

WATCH OUT though; if you set your drive to mount in /home then your system won't find your current home files, so before you mount it there you need to clone your current /home directory into your new drive. I'd suggest using a live CD to do all of this.

Incase I didn't explain that well:

1) boot your live CD

2)Copy /home from your root HD, into your new drive (cp -vr /(mount-point-of-your-current-drive)/home/ /mount-point-of-your-new-home-drive)
now you have two copies of your home folder.

3) edit /etc/fstab according to [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) so your new drive mounts as /home

4) reboot

If it doesn't work then you can just go back to live CD and put fstab back to how it was, before trying another way! 

Once you know everything is working well it's worth going back into Live anyway and removing the old copy of /home (the one on your root partition) so things don't get confusing later.

hth

---

### Post by Hagar55 on 2007-09-10
I diden't save anything myself in the current home folder, does the system put things there by itself ?

---

### Post by maybeway36 on 2007-09-10
Yes, when you first install Ubuntu for example you get an empty home folder, and config files get added as you launch programs.

---

### Post by merlinus on 2007-09-10
> **Hagar55 said:**
> /dev/hda1: TYPE="ntfs" 
/dev/hda5: LABEL="DSK1_BACKUP" UUID="0000-0E34" TYPE="vfat" 
/dev/hda6: TYPE="ntfs" 
/dev/hdb1: TYPE="ntfs" 
/dev/hdb5: LABEL="DSK2_BACKUP" UUID="DCDC-6F1C" TYPE="vfat" 
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="88045bb0-815b-434f-b53e-86153c4cdb20" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="df707aa2-2b63-443d-a09f-26c1ae025782" TYPE="swap" 

the requested info..

sda4 shows as linux from sudo fdisk -l, but does not show up in blkid.  What is on that partition, and is it indeed formatted as ext3?

---

### Post by Hagar55 on 2007-09-11
The installation only made 2 partitions for linux, the root partition and the swap partition.
I further shrunk the root with gparted and formatted it as ext3.
There is only one further partition on the drive and that is the big NTFS partition

What does the blkid command actually tell you ?

---

### Post by Pumalite on 2007-09-11
[http://linux.die.net/man/8/blkid](http://linux.die.net/man/8/blkid)

---

### Post by Hagar55 on 2007-09-12
Just a question, is it a problem that the home dir is located on the root parition ?
Can I just make the second ext 3 partition mount in the fstab file so I can read/write to it.
Or will leaving the home dir. in the root partition come back to bite me later ?

And should I add further partitions (formatted as ext3) to the system, what mounting point should I choose ?

---

### Post by Pumalite on 2007-09-12
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Hagar55 on 2007-10-04
Well I finnaly moved my home to it's own partition.
Is it correct that only the root as full acces to the home partition ?
I have acces to the user in the root partition but not the home partition itself ?

And why doesn't the partition show as a drive anymore ?

---

### Post by mkc on 2007-10-18
Yea that's correct - the idea being on multi-user systems that one user can't just go in and mess with other user's files.

If you particularly want full access to /home then you can edit the permissions of that folder using chmod, although I'd suggest leaving it as is.

You were asking ages ago about if the system adds it's own files to your home directory - if you want to see what it puts in then at a command line try;
ls .*
that'll list any files/folders with a . infront, which is how the system knows to keep them hidden. Alternatively if in Nautilus try ctrl&h which shows hidden files.

hth

---

