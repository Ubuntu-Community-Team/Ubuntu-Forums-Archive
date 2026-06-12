---
title: "[SOLVED] Cant install ubuntu (to dualboot xp) because something will not unmount"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by syaoran05 on 2007-11-08
I tried to install Ubuntu as a second OS in my Win XP machine, to dualboot.

Everything goes well until the actual installation part, where a dialog box pops up and says:

[The dialog starts here]
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/Local\040Disk

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?
[End of dialog]

My hard disk is partitioned this way:

Graphic representation:
{  [WinXP Partition 10GB] [Unallocated space 10GB] [NTFS Partition for storing files 20GB]  }

the first partition has my WinXP, the second one is unallocated space where i want to install Ubuntu to, and the third is an NTFS formatted partition to store ALL my files.

Both the WinXP and NTFS Data Partition are called Local Disk (C:) and Local Disk (D:), respectively.

My hard disk has a total capacity of 40GB. I will NOT wipe my drive, whatever happens. I do not want to lose my data on the NFTS Data Partition.

Please help me with this problem, i appreciate any help you'd give.

---

### Post by logos34 on 2007-11-09
Have you tried unmounting them manually? 

places>computer or home folder>right-click windows>unmount volume

---

### Post by bulldog on 2007-11-09
And definetely **backup your valuable data** when you're going to mess around with partitions!

---

### Post by syaoran05 on 2007-11-09
> **logos34 said:**
> Have you tried unmounting them manually? 

places>computer or home folder>right-click windows>unmount volume

i have tried unmounting the Local Disk (D:), which appears as "Local Disk" in Ubuntu. It will not unmount. There is no dialog box; i will rightclick>unmount, then the contextual menu will just disappear, and Local Disk will not unmount.

Local Disk (D:) contains my data. If I unmount it, will it still be there? imean, can XP still detect it again (ergo, visible and accessible in My Computer) when i boot to windows, or will it become nothing?

---

### Post by bulldog on 2007-11-09
Can you post the output of```
sudo fdisk -l
``` to the forum?
[live cd will do nicely]

**Friendly WARNING**
Don't mess with your partitions if you have no idea what you're doing!!
One wrong click and your data is gone,be very carefull and don't apply anything in this stage.

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> And definetely **backup your valuable data** when you're going to mess around with partitions!

Not to worry, i do back up when doing these stuff. 

Its just that four people use this machine, my mom dad and sister all of them working daily and frequently and they save in numerous locations. i can only be sure of my data but not theirs.

And i cant mess with partitions until theyre asleep, because in my place, doing everything non-Windows GUI is like assembling a bomb. They even reprimand me when they see me using the DOS command line to search for files (coz i believe its faster than Windows Search). That way, I cant ask them where they put their files, so im never sure when they have something new to back up.

---

### Post by bulldog on 2007-11-09
Okay,I think it's time you get your own computer :)

But how about the fdisk? so we can have a look how your partitions are ordered.

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> Can you post the output of```
sudo fdisk -l
``` to the forum?
[live cd will do nicely]

**Friendly WARNING**
Don't mess with your partitions if you have no idea what you're doing!!
One wrong click and your data is gone,be very carefull and don't apply anything in this stage.

I will post the output, later when i get to play with Ubuntu. 
I am only stealing PC time, my sister is using this now, she just stepped out for a while.
I also would want to know what ```
sudo fdisk -l
``` means: "sudo" "fdisk" and "-l". I do like to understand how things work so that i won't just complain and instead get to work better, thank you. :)
by the way, is that a small L, or a number 1?

Do not worry, I just reinstalled XP earlier this week because of a missing system file. It's all clean and i think i still have a back up of everything. I will do a backup again before trying to install. Thank you for the friendly warning :) . The system failure is the main reason why i want to dualboot this machine with Linux.

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> Okay,I think it's time you get your own computer :)

But how about the fdisk? so we can have a look how your partitions are ordered.

I am currently a freshman in college, and i belive i badly need my own portalbe computer, my schoolwork is suffering! I am planning to get a Macbook to be triplebooted to windows and Ubuntu, If my dad doesnt go cheap on me. Macbooks here cost 20% more, relatively.

ANYWAY. Like i said, i can only look later, so i dont have this information at hand right now. However, i do have some information about the partitions. I dont know if these are what youre looking for, but anyway, here goes..

my XP partition is on hda1, and my Local Disk (D:) which is the data disk, is on hda5 (i may be wrong, but i think its most probably right). Ubuntu wants to install itself  on "Partition #3" and the swap on "Partition #6" (that's what the installer said.)

I THINK Local Disk (D:) is a logical drive under an extended partition. Im not sure about this information.

---

### Post by bulldog on 2007-11-09
sudo fdisk -l  [lowercase L ] will give a report of the hdd and how it's partitoned,this is mine:
```
Schijf /dev/sda: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xc0c274e7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306        5222    31463302+   5  Uitgebreid
/dev/sda3            5223        5483     2096482+  82  Linux wisselgeheugen
/dev/sda4            5484       38913   268526475   83  Linux
/dev/sda5   *        1306        2611    10490413+  83  Linux
/dev/sda6            2612        3916    10482381   83  Linux
/dev/sda7            3917        5222    10490413+  83  Linux

Schijf /dev/sdb: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x13781378

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1        3891    31254426    7  HPFS/NTFS
/dev/sdb2            3892       21401   140649075    7  HPFS/NTFS
/dev/sdb3           21402       38913   140665140    7  HPFS/NTFS

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x0007a1d7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1   *           1       26108   209712478+  83  Linux
/dev/sdc2           26109       52217   209720542+  83  Linux
/dev/sdc3           52218       60801    68950980   83  Linux

```

Now you have some idea what it does [it's in Dutch I'm afraid]

Some tutorials for the command line [terminal] and general stuff

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

[http://www.linux.org/lessons/beginner/l1/lesson1d.html](http://www.linux.org/lessons/beginner/l1/lesson1d.html)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> sudo fdisk -l  [lowercase L ] will give a report of the hdd and how it's partitoned,this is mine:
```
Schijf /dev/sda: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xc0c274e7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306        5222    31463302+   5  Uitgebreid
/dev/sda3            5223        5483     2096482+  82  Linux wisselgeheugen
/dev/sda4            5484       38913   268526475   83  Linux
/dev/sda5   *        1306        2611    10490413+  83  Linux
/dev/sda6            2612        3916    10482381   83  Linux
/dev/sda7            3917        5222    10490413+  83  Linux

Schijf /dev/sdb: 320.0 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x13781378

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1        3891    31254426    7  HPFS/NTFS
/dev/sdb2            3892       21401   140649075    7  HPFS/NTFS
/dev/sdb3           21402       38913   140665140    7  HPFS/NTFS

Schijf /dev/sdc: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x0007a1d7

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1   *           1       26108   209712478+  83  Linux
/dev/sdc2           26109       52217   209720542+  83  Linux
/dev/sdc3           52218       60801    68950980   83  Linux

```

Now you have some idea what it does [it's in Dutch I'm afraid]

Some tutorials for the command line [terminal] and general stuff

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

[http://www.linux.org/lessons/beginner/l1/lesson1d.html](http://www.linux.org/lessons/beginner/l1/lesson1d.html)

[http://linuxcommand.org/](http://linuxcommand.org/)


i see, thank you! :) what does "sudo" stand for, and what does the argument "-l" mean?

---

### Post by bulldog on 2007-11-09
sudo stands for administrator rights and when you're on a command line in most cases you have to put a suffix at it to do what you want faster or more specific.
Try in a terminal sudo -h or aptitude -h this will give you some help about the use of it.

In general you have to read and learn the command line,this is much more powerfull than any app with GUI.
But it takes time to learn.

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> sudo stands for administrator rights and when you're on a command line in most cases you have to put a suffix at it to do what you want faster or more specific.
Try in a terminal sudo -h or aptitude -h this will give you some help about the use of it.

In general you have to read and learn the command line,this is much more powerfull than any app with GUI.
But it takes time to learn.

I appreciate your help, thank you very much! :)

did you see the information about my disks? Its  somewhere on page 1 of this thread.

I hope its enough, because i wont touch linux until 6 hours later.

---

### Post by bulldog on 2007-11-09
I need the fdisk command executed,so I can see how ubuntu  set your partitions.
So do it when you have the time.
We'll be around :) or give me a PM if you're in a hurry and I'm online that is.

---

### Post by syaoran05 on 2007-11-09
> **bulldog said:**
> I need the fdisk command executed,so I can see how ubuntu  set your partitions.
So do it when you have the time.
We'll be around :) or give me a PM if you're in a hurry and I'm online that is.

i already have the output of the fdisk you asked from me

```

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            2551        4869    18627367+   f  W95 Ext'd (LBA)
/dev/hda5            2551        4869    18627336    7  HPFS/NTFS

```

i believe hda2 and hda5 are one and the same...

---

### Post by syaoran05 on 2007-11-10
it turns out that the Local Disk only mounts when I access the "Computer" in places. I tried installing it without browsing any volume first, and it installed without problems.

---

