---
title: "External HDD woes - can anyone advise?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Mr Mark on 2008-10-15
Afternoon all.

I've been monkeying with this for two days now - browsing the forums and googling up a frenzy.  I've been back-and-forth between Ubuntu, Xp and the Gparted LiveCD countless times and still I'm stuck!

Basically, I bought a Maxtor Basics 1.5tb external USB HDD yesterday.  I have four smaller HDDs that all run with no problems within Ubuntu.

I've been trying to figure out how to mount/format it.

The output of fdisk -l is as follows:

```
root@mark-desktop:/home/mark# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x483bfcc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    77352974    38676456    7  HPFS/NTFS
/dev/sda2        77352975   156296384    39471705    5  Extended
/dev/sda5        77353038   153292229    37969596   83  Linux
/dev/sda6       153292293   156296384     1502046   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010fce

   Device Boot      Start         End      Blocks   Id  System

```

Using sudo gparted /dev/sdb I can see the drive and so I attempt to re-format it to, for instance, fat32 (that'll work for storing .avi's okay, won't it?) and it appears to work until it then tries to re-scan for drives and gparted just hangs.  Furthermore, the terminal I ran it from has messages about it not having a fake msdos label, or something along those lines.

Could I ask one of you kind experts to guide me through this one?

Thanks in advance,

MC

[edit] Apologies - I've posted this in the incorrect forum, I think!  Could a kind mod' move it or should I re-post in the Hardware forum?

---

### Post by Mr Mark on 2008-10-15
An update:

Using QTparted I seem to have managed to format the drive properly.  Gparted now seems to have no trouble viewing it and fdisk -l is now peachy.

However, all I see in the "Computer" area is a USB Disk icon called "USB Disk" which, when selected, tells me "**Unable to mount location** Can't mount file".  In both the media folder and on the desktop, where my external HDDs usually are shown, there is nothing.

Hopefully someone knows how I can rectify this.

---

### Post by caljohnsmith on 2008-10-15
How about seeing if you can at least mount the drive manually:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
Does the above return any errors?

---

### Post by Mr Mark on 2008-10-15
Here's what I get:

```
mark@mark-desktop:~$ sudo mount /dev/sdb1 /mnt
mark@mark-desktop:~$ ls -l /mnt
total 16
drwx------ 2 root root 16384 2008-10-15 18:49 lost+found

```

Oh, and I've just noticed that after QTparted finished doing its thing there was another message in the terminal (3rd line):

```
mark@mark-desktop:~$ sudo qtparted
- FORMAT /dev/sdb1 ext3
Error: File system has an incompatible feature enabled.

```

Any clues?

---

### Post by caljohnsmith on 2008-10-15
I don't know what's going on, but at least you can mount it manually and use it that way it looks like. Have you tried saving anything to the drive yet? If you still have it mounted on /mnt, you could go to that directory in a file browser (Nautilus) and see if it will let you move some files there.

---

### Post by Mr Mark on 2008-10-15
Interesting.  Seems I've found my drive - the instructions you gave (excuse me being so slow on the uptake!) mounted it at /mnt.  I typed "/mnt" into the address bar in nautilus and it gave me an area with 1316.2GB free and a lost+found folder in it.  Double-clicking the folder tells me I don't have permission to see its contents.

[edit] Was typing this post while you posted yours - will try copying something there.

[edit 2] Result of this was message saying "Error opening file '/mnt/lost+found/new file': Permission denied"

[edit 3] I *can* copy stuff in there via gksudo nautilus.  What I really want to do is to have it auto-mount like my other external HDDs.

---

### Post by PauricTheLodger on 2008-12-15
Hey there,

I bought this one yesterday as well, only to discover the same problem :(

Did you ever get it working in the end? If so how?

Thanks

PTL

*Edit* I should probably mention - Got it mounting like above and everything, was just wondering about the the auto-mount :)

---

