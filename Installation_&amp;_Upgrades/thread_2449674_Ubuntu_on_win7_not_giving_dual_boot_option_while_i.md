---
title: "Ubuntu on win7 not giving dual boot option while installation"
date: 2020-08-31
forum: Installation &amp; Upgrades
---

### Post by kewl_123 on 2020-08-31
Hi,
I am installing Ubuntu from USB stick. (I formatted USB stick to FAT32)
It booted from the USB but when I started installation, it didnt give me the dual boot option.
So I tried following from a website:
1) Select "something else"
2) Next will be partitions window, select your intended partition, format it to ext4, and set mount point as "/".
3) You may/may not create a swap partition, depends on you.
4) Post that screen set your login details etc.
5) Once installation is finished on restart you will see grub menu with Windows and Ubuntu Listed.

The first step was available. But there were some other options also which I didnt know what to do and it again gave some error/warning.
Please help me install Ubuntu with already existing win7 as dual boot.

---

### Post by oldfred on 2020-08-31
If an older BIOS/MBR system, you may have used all 4 primary partitions?
Post this from live installer's terminal:
sudo parted -l

My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by kewl_123 on 2020-08-31
Hi OldFred,
Thank you for your reply.
In the first link, point #2 is:  "Step 2. Shrink the Windows C drive, and use Ubuntu installer LiveCD(or on USB) to create an extended partition there"
But I have already shrunk drive F and now in windows it shows 73 GB when earlier it was 200+ GB.
Windows is on C drive and very little space is left on that.

---

### Post by oldfred on 2020-08-31
With NTFS, you need to leave about 30% free or Windows will be very slow. At 10% free, you just about have no space for a defrag.

If you have used all 4 primary partitions, you cannot create another.

---

