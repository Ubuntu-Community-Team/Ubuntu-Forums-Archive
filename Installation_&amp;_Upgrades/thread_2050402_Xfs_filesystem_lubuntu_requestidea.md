---
title: "Xfs filesystem lubuntu request/idea"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by Material Defender on 2012-08-30
Xfs lubuntu 12.(04 or 10? ...) 32 bit usb-install

To my understanding, lubuntu is the fastest (lightweight) of the Ubuntu distros, and the Xfs filesystem is very fast (est) ... i want both.. combined... perfect.

My problem is, lubuntu does not support Xfs from the installer. Xubuntu, Kubuntu, and Ubuntu does, but not lubuntu. I tried. I failed.

I tried installing the debian packed mkfs.xfs in live mode before running the os install and that allowed me to install lubuntu on my then newly created xfs partition, but after rebooting my pc, the   /   (root)  directory, the /temp  and so on, could not mount, and i wasn't able to start the system.

My request is to update the installer to support Xfs. I have no idea if this is super hard to do or if i'm wrong and it does indeed work already. Thank you in advance. This is my first thread.

ever.

---

### Post by ankspo71 on 2012-08-31
I just booted into my Lubuntu 12.04 32bit Live-USB and the XFS filesystem option is still there. I did not have to format any partitions in advance to see the XFS option either. (Edit: I did not attempt to install Lubuntu using XFS, so I don't know if XFS will work as expected)

[IMG]http://i45.tinypic.com/qq8oxy.png[/IMG]


If you are attempting to install Lubuntu 12.10, then Lubuntu 12.10 is in alpha stage and it should only be used for testing and debugging puposes, and from my past experiences with testing pre-releases of *ubuntu, I would expect to see some random missing features and components until they have been fixed or added. Here is the release schedule for *ubuntu 12.10: [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule)

Hope I was of some help.

---

### Post by Material Defender on 2012-09-01
Thank you for the quick response ankspo71. 

I am now sure it was a 12.04 install. The option for Xfs was there also when i ran the install as on your screenshot, but afterwards when it tried to partition or "Install Now", it failed. That's when i got mkfs.xfs. I'm pretty sure the error told me that this particular tool was missing. Installation proceeded after i installed the Debian package. And then failed on boot. I got it from here: [http://packages.debian.org/squeeze/xfsprogs](http://packages.debian.org/squeeze/xfsprogs) by the way. 

**Filesystem X**  :-)

Random system specs...
I'm now writing from xubuntu with the LXDE and Xfs on disk. I don't know if it is the same experience as having lubuntu, but it feels very fast and stable i think compared to Unity, Gnome, the KDE and microsoft windows. When i open 30 programs and while copying files it still feels like a mountainly freshershist boot. + 0 crashes. Athlon64 2,2Ghz, 3gb ram, ata disk, new but eco silent fanless nvidia.

---

### Post by ankspo71 on 2012-09-02
Hi Again,
Like you were saying, it doesn't appear that Lubuntu 12.04 supports XFS (at least not out-of-the-box anyways). I could be wrong, but I'm guessing that maybe the Lubuntu team decided to leave out additional filesystem support to free up some additional space in the Lubuntu ISO download.

That screenshot I posted above is sending a false message because it makes it appear that the Lubuntu 12.04 installer supports XFS by default, but it actually does not support XFS because xfsprogs is not installed. 

I made room on my hard drive to attempt to install Lubuntu 12.04 on an XFS filesystem. I used Gparted to create my XFS partition, but the xfs option was not available in Gparted until after I installed xfsprogs: 

```
sudo apt-get install xfsprogs
```

I opened Gparted again and finally created the XFS partition.

Next I installed Lubuntu on the XFS partition I created (and I told the installer not to re-format the partition again, just to see if that made any difference).

The installation was successful without errors, but after rebooting, I was greeted with an fsck error. It said something like "fsck: 'fsck.xfs' not found". Then I was given some options, and I choose the option to ignore the error, which allowed me to continue mounting the the partition to boot into Lubuntu desktop.

"fsck.xfs" is a part of the xfsprogs package, so I immediately installed xfsprogs again, but this time I was installing it on the installed Lubuntu.

```
sudo apt-get install xfsprogs
```

Then I rebooted a few times and the fsck error didn't return. I am using a pure Lubuntu 12.04 on an XFS filesystem to write this message.

---

### Post by Material Defender on 2012-09-03
1. Booted usb install

2. in terminal: sudo apt-get install xfsprogs

3. ran install from the desktop

4. partitioned the drive, xfs & swap

5. installed

6. "ignore" when the boot presents mounting error

7. and when i logged in i did the: sudo apt-get install xfsprogs    again

8. enjoying glorious success

9. Thank you ankspo71

---

### Post by marinara on 2012-09-06
yeah xfs is nice, and i've heard it makes your ssd last longer

---

### Post by Epodx64 on 2012-09-07
I personally use ext2 for /boot and ext4 for / & /home but I've heard that JFS is the fastest of the file systems I just don't really trust them XFS and JFS haven't really seen an update in years right? same with reiser and I won't use btrfs until its in RHEL

(ext2 for /boot makes it boot a little bit faster since ext2 isn't a journaling filesystem and its only accessed once when you boot then it does nothing so you really don't need a journaling filesystem for it.)

---

### Post by Insanemal on 2013-03-17
> **Epodx64 said:**
> I just don't really trust them XFS and JFS haven't really seen an update in years right? same with reiser and I won't use btrfs until its in RHEL


XFS is actually one of the most updated FS's there is. It has a dedicated dev team who work for RH these days. Your homework, I suggest you do it BEFORE you try and give people advice.

---

