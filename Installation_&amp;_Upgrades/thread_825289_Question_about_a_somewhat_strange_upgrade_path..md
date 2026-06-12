---
title: "Question about a somewhat strange upgrade path."
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by mawxcarroll on 2008-06-10
Hi,
  I've got a somewhat strange plan to upgrade to 8.04, and I was looking for some advice.  Currently I have a 250GB hard drive with 7.10 installed and an 80GB WinXP hard drive.  My machine dual boots, with the important boot info on the 80GB drive.

My plan is to ditch the WinXP drive, which is old and almost totally unused.

I'd like to do a clean install of 8.04, as the Ubuntu drive has seen multiple upgrades already.

I have an additional 160GB hard drive available (both the 250 and the 160 are SATA).  Here's what I would like:

-Ubuntu and other system files on the 160GB drive
-/home with user files on the 250GB drive

I was thinking of doing something like this:

1. Clean install to the 160GB drive,
2. Copy all files and data from 250GB drive over to 160GB drive.  (Is there an easy way to import my old user stuff?  Or should I just do it app by app (firefox, amarok, etc)?)
3. Reformat 250GB hard drive.  Can anyone point me in the right direction on how to then mount it as my /home?

Does my plan seem reasonable?  Is there a better way to do this?

Thanks for your help!

-tom

---

### Post by Yuki_Nagato on 2008-06-10
This would be easier if you had an external hard drive that you could copy /home and /usr to, but I am assuming that this is not the case.

First off, and this is just speculation, (wait for someone to confirm it) I would install Hardy onto the 160GB.  As it was installing, I would point the new Hardy OS to look for /home and /usr on the 250GB.  Then you could take the files on the 250GB, pack them up into .tar.lzma "balls," and deposit them on the 160GB, (Perhaps in /boot or /).  Then you need to reformat the 250GB hard drive, and resize it how you like.  But before you do that, write down the numbers of all the partitions, because you will need to have to numbers stay the same afterwards, so the 160GB OS can find them after the reformat.  Even if this means creating "dummy" partitions with 6 MBs on them.  After the reformat, unpack the /home and /usr files to their respective partitions again.

But please, wait for some other ideas from other people.

---

### Post by Bruce M. on 2008-06-10
> **mawxcarroll said:**
> Here's what I would like:

-Ubuntu and other system files on the 160GB drive
-/home with user files on the 250GB drive

I was thinking of doing something like this:

1. Clean install to the 160GB drive,
2. Copy all files and data from 250GB drive over to 160GB drive.  (Is there an easy way to import my old user stuff?  Or should I just do it app by app (firefox, amarok, etc)?)
3. Reformat 250GB hard drive.  Can anyone point me in the right direction on how to then mount it as my /home?

Does my plan seem reasonable?  Is there a better way to do this?

Thanks for your help!

-tom

Hi Tom...

**FIRST** - BACKUP!! 

Backup your system. -See QuickStart in my sig for one simple program to do that. There are other ways but this is easy to use and does a great job. Then copy the three backups ( 1. /  2. /home  3. Config files ) to a CD-RW or some other storage media you have to have them available

You mention "other system" files, do you mean WinXP? If so it will be easier if you install that first, on say (example) 100G. Leave the 60G for Ubuntu 8.04 System.

Next do a clean install of 8.04 using the "Alt CD".

When you get to the Partition editor it will see the installed 250G HD.

Set the root partition on the 60G partition of the 160G HD and the /home partition onto the 250G drive.

When done you'll have a duel boot system with 8.04 "system" on the 160 and you /home on the 250G drive.

Run QS and restore your backup of /home.

You're up and running.

More questions just ask.
Bruce

---

### Post by mawxcarroll on 2008-06-11
Hi Bruce,
  Thanks for the advice.  QS looks like a great tool.

I will not be setting up a WinXP partition (finally going totally Windows free!).  Given that, should I use the regular 8.04 CD or the alt CD?

I have many 10s of GBs of data on my drive, probably close to 100GB.  Do you have a suggestion for how to easily back that up?  Optical media are too small.  I have a couple of options though:

1. I could add a 500GB drive to my mythbuntu box and back up over the network.

2. I could add another hard drive to this box...but that seems a little too self-referential to work.

Again, thanks for your help!

-tom

---

### Post by Bruce M. on 2008-06-12
> **mawxcarroll said:**
> Hi Bruce,
  Thanks for the advice.  QS looks like a great tool.

It's saved my bacon a few times. For such a small program it does wonderful things.

> **mawxcarroll said:**
> I will not be setting up a WinXP partition (finally going totally Windows free!).  Given that, should I use the regular 8.04 CD or the alt CD?

I'd suggest the ALT CD, it gives you greater control during the setup, especially with the partitioning.

> **mawxcarroll said:**
> I have many 10s of GBs of data on my drive, probably close to 100GB.  Do you have a suggestion for how to easily back that up?  Optical media are too small.  I have a couple of options though:

1. I could add a 500GB drive to my mythbuntu box and back up over the network.

2. I could add another hard drive to this box...but that seems a little too self-referential to work.

Again, thanks for your help!

-tom

Now if I'm reading this right, you are going to ditch the 80G HD that Windows is on and do a clean install of 8.04 on the 160G HD that now has 7.10 on it and want to use the 250G HD for your /home directory, but that drive has about 100G of data you want to save. And I'm assuming that 7.10's /home directory is on the 160G HD now, and you will want FF's bookmarks, emails and other personal stuff from there as well.

If you can I would definitely backup that 100G of data files you want to keep as per your step #1. That should free up the 250G HD.

Then backup your 7.10 /home directory and put it somewhere safe as well.

Now you have 7.10 on the 160G backed up, and a free 250G HD to use.

Using the ALT CD (for reasons above) here's what I would do:

160G

20G for 8.04 root directory (mine only uses 2.65G of a 15G partition)
40G for /home partition here, mine is only 614.33MB of 15G, because I put everything I "create" or save, etc. on my second "data" drive.)
100G - data

250G - I'd create two partitions here:

150G - use for /home if you don't like what's above or data
100G - data


If you keep "everything" in your /home directory then yes, you will need a "larger" partition.

For an example here are my two disks:
```
bruloo@bruloo:~$ sudo fdisk -l /dev/sda
[sudo] password for bruloo: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002692a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sda2            1217        9729    68380672+   5  Extended
/dev/sda5            1217        3040    14651248+  83  Linux
/dev/sda6            3041        4864    14651248+  83  Linux
/dev/sda7            4865        9545    37600101   83  Linux
/dev/sda8            9546        9729     1477948+  82  Linux swap / Solaris
bruloo@bruloo:~$ sudo fdisk -l /dev/sdb
[sudo] password for bruloo: 

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc25e477

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
bruloo@bruloo:~$ 

```
And what they are:

80G:

/dev/sda1 - Windows 2000 (10G, only because my ISP doesn't support Linux)
/dev/sda2 - Extended Partition
/dev/sda5 - / (15G) - Used: 2.62 GB
/dev/sda6 - /home (15G) - Used: 614.39 MB -yes: MB
/dev/sda7 - data (38G) - Used: 748.9 MB
/dev/sda8 - swap (2G)

40G:

/dev/sdb1 - data - Used: 13.82 GB

Something you might like to look at is: [psychocats.net]("http://www.psychocats.net/ubuntu/index.php") (a recommended "bookmark this")

Specifically these:
[LIST]
[*][Plan Partitions]("http://www.psychocats.net/ubuntu/partitioning"); and
[*][Make a /home Partition]("http://www.psychocats.net/ubuntu/separatehome")
[/LIST]

If you need more just ask.
Bruce

---

