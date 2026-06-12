---
title: "Can I keep my RAID intact after installing Ubuntu on other drive?"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by PowerMan572 on 2011-09-18
Been running Ubuntu 11.04 on my laptop for a few days and loving it. Want to move it to my desktop now. Only 1 problem. I have a RAID setup (hardware RAID, not software RAID) and I have about 900GB of data. I don't want to have to wipe the RAID and lose all my data. I do have the data backed up on a remote server, but to have to redownload almost 1TB would put a strain on my bandwidth.

Please note: I'm not going to be installing Ubuntu on the RAID. The RAID is used to just hold data. The OS goes on another stand-alone hard drive.

When I put the Ubuntu disc in the CD-ROM of the desktop and I got to "Computer" I don't see the RAID there, I didn't think I would. Next, I go to System > Disk Utility and I can see the 4 hard drives over in the left-hand column under a RAID, but if I right click, left click, etc. I don't have any options.

So, with that being said, can I install Ubuntu and not mess up the RAID and NOT lose any of the data?


Thanks!

---

### Post by YesWeCan on 2011-09-18
You want to move your 11.04 OS from your laptop to its own HD on your desktop PC, and your desktop PC also has a hardware RAID with data on it?

You should not have a problem installing Ubuntu to its own HD. Make absolutely sure you manually select the boot loader (Grub) installation location and that it is the Ubuntu drive and not one of the raid disks.

It is disconcerting that the RAID does not automatically show up in a consistent manner but that's probably ok. I *suspect* your RAID is what's called a SATA RAID or Windows RAID or Fake RAID; it uses hardware support on the mobo but is not a full hardware RAID.

Obviously, belt and braces approach would be to unplug the power to the RAID disks when you install Ubuntu.

---

### Post by PowerMan572 on 2011-09-18
Sorry, guess I should clarify. My laptop hard drive is going to stay where it's at :-)

My desktop has 5 hard drives. 4 are in a hardware RAID and the other is for the OS. 

I am using a PCI Express hardware RAID controller that I had bought from an electronics store.

So say I install Ubuntu on the hard drive that is meant for the OS, how do I get Ubuntu to see the RAID so that I can go into "Computer" and see all my data that is on the RAID?

---

### Post by YesWeCan on 2011-09-18
It may depend on the RAID card. I am not too familiar with how PCI RAID cards work with Ubuntu but it should be possible to mount the array in Ubuntu. What is the make and model of the card?

Would you boot live CD and open a terminal and post the output of
[COLOR="DarkSlateBlue"]sudo sfdisk -luS[/COLOR]
and also
[COLOR="DarkSlateBlue"]sudo dmraid -s[/COLOR]
This should list your RAID if Ubuntu can detect it. If so, it may just be a case of activating it so it shows up in the Places menu:
[COLOR="DarkSlateBlue"]sudo dmraid -ay[/COLOR]

Otherwise you might need to find drivers for your PCI card.

---

### Post by PowerMan572 on 2011-09-18
After running sudo sfdisk -lus:

```
ubuntu@ubuntu:~$ sudo sfdisk -lus
unrecognized format - using sectors

Disk /dev/sda: 13985 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 224671743  224464896   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 182401 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/256/63 (instead of 182401/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1             1 4294967295 4294967295  ee  GPT
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdc: 182401 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type
No partitions found

Disk /dev/sdd: 182401 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdd: unrecognized partition table type
No partitions found

Disk /dev/sde: 182401 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sde: unrecognized partition table type
No partitions found

Disk /dev/dm-0: 194759 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/dm-0: unrecognized partition table type
No partitions found

```
Here's what shows up after doing sudo dmraid -s:

```
ubuntu@ubuntu:~$ sudo dmraid -s
/dev/sde: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdd: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdc: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdb: "sil" and "pdc" formats discovered (using pdc)!
*** Active Set
name   : pdc_chdccaaejg
size   : 3128815104
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 4
spares : 0

```The RAID card is a 6-Port SATA II 150 PCI Host Card w/ RAID. Made by Vantec. Model: UGT-ST310R

Thank you for the help!

---

### Post by PowerMan572 on 2011-09-18
Also, when I did the sudo dmraid -ay, I got this:


```
ubuntu@ubuntu:~$ sudo dmraid -ay
/dev/sde: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdd: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdc: "sil" and "pdc" formats discovered (using pdc)!
/dev/sdb: "sil" and "pdc" formats discovered (using pdc)!
RAID set "pdc_chdccaaejg" already active

```

---

### Post by YesWeCan on 2011-09-18
Your 115GB or so sda drive is fine for installing Ubuntu. You'll have to shrink your Windows partitions to make space.

I don't know enough about the type of RAID controller you are using to comment on the array. It reports being activated so it ought to be visible in the Places/Computer window, but I'm not sure.

---

### Post by PowerMan572 on 2011-09-18
> **YesWeCan said:**
> Your 115GB or so sda drive is fine for installing Ubuntu. You'll have to shrink your Windows partitions to make space.

I don't know enough about the type of RAID controller you are using to comment on the array. It reports being activated so it ought to be visible in the Places/Computer window, but I'm not sure.

Okay, thanks for the help. Well I won't be keeping Ubuntu with Windows on the HD. My SSD will be all for ubuntu :-)

Since the RAID is showing active, I'll try and research further of how I can access the files / see it show up under Computer or Places. 

If anyone else has ideas/suggestions, please let me know. I'll be working on this the rest of the day :-)

Thanks!

<3 Ubuntu.

---

### Post by tgalati4 on 2011-09-18
I would pull out the pci express RAID card.  Install Ubuntu on the remaining drive.  Set it up the way you want.  Then shut down and reinsert the card.  Then post:

sudo fdisk -l

If the drives show up, then you should be able to mount them and browse the files.

If the boot drive is one of those SATA channels on the pci express card, then disconnect the RAID drives completely and try a standard installation on the single drive.

Then plug the drives back in--preserving the ports that you removed them from and see if they show up.

---

### Post by PowerMan572 on 2011-09-18
> **tgalati4 said:**
> I would pull out the pci express RAID card.  Install Ubuntu on the remaining drive.  Set it up the way you want.  Then shut down and reinsert the card.  Then post:

sudo fdisk -l

If the drives show up, then you should be able to mount them and browse the files.


Sorry if this is a dumb question, but how do I mount the drives? If the system is already seeing the RAID now, can I just mount them to see if it works? Thx...

---

### Post by YesWeCan on 2011-09-18
> **PowerMan572 said:**
> Sorry if this is a dumb question, but how do I mount the drives? If the system is already seeing the RAID now, can I just mount them to see if it works? Thx...
The device files usually show up under /dev/mapper/ so have a look here and you might find pdc_chdccaaejg. Not sure tho. If so, try
```
mkdir /media/array
sudo mount /dev/mapper/pdc_chdccaaejg /media/array
```and you should get an icon on the desktop

Then also run
```
df -h
```and check the size of the array looks right. Do not write to the array unless everything looks right.

---

