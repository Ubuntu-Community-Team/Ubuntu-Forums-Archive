---
title: "Side-by-side hard drive issues"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by Karandr on 2010-04-13
Sorry for the vague title, it's sort of hard to sum it up in a few words.
I'm installing Ubuntu 10.04 on my laptop, switching from XP. I'm still keeping XP on a small partition for some programs I need. Anyway, after clearing out most of my XP installation, I'm having trouble now that I'm ready to install Ubuntu. See the screenshot below:

[[IMG]http://i633.photobucket.com/albums/uu51/kar0010/th_Screenshot-3.png[/IMG]](http://s633.photobucket.com/albums/uu51/kar0010/?action=view&current=Screenshot-3.png)

The hard drive has a capacity of 40 GB. The Windows installation is taking up 17.2 (see below), but Ubuntu seems to think it's taking up the whole drive.

I'm entirely new to Ubuntu (and Linux, for that matter). Could someone please help me with this? I'm really eager to get into Ubuntu.

[[IMG]http://i633.photobucket.com/albums/uu51/kar0010/th_hard-drive-space.png[/IMG]](http://s633.photobucket.com/albums/uu51/kar0010/?action=view&current=hard-drive-space.png)

---

### Post by Mark Phelps on 2010-04-13
OK, but is that 17+ GB a separate partition? Or is it the portion of the one partition that has been used?

IF the second, XP IS taking up your entire disk.

Since 10.04 is still in beta testing, it's possible that there are some problems still with the installer and disk partitioning.

Would recommend you download and burn a GParted LiveCD (from distrowatch.com) and at least boot with that to confirm that you actually have free space outside the XP partition.

If you do, you could do the partitioning with the GParted LiveCD and then select manual partitioning to install Ubuntu.

---

### Post by Karandr on 2010-04-13
Oh, I see. So even though Windows isn't using that 20-something-GB, it's still claiming it, right? That's pretty shifty, but I can sort of understand it. I'll give GParted a try and let you know how it works.

---

### Post by Mark Phelps on 2010-04-14
> **Karandr said:**
> Oh, I see. So even though Windows isn't using that 20-something-GB, it's still claiming it, right? That's pretty shifty, but I can sort of understand it. I'll give GParted a try and let you know how it works.

It's not "shifty" -- it's the way that space is reported in ANY OS. Windows us using the whole partition; it's just filled up only part of it.

If you had an Ext4 partition, it would report the space the same way.

---

### Post by srs5694 on 2010-04-14
To elaborate a bit on some fundamentals, Disks are split into *partitions* at a very low level. If your disk is like a filing cabinet, and your directories and files are like the folders and papers kept in the filing cabinet, then a partition is like a drawer in the filing cabinet. The main difference is that you can set up partitions of varying size and number on a hard disk when you first get it. It's also possible to resize partitions after they've been created, although this can sometimes take hours to do and there's a small risk of trashing the whole partition when you do it.

Most partitions contain *filesystems,* which are low-level data structures that facilitate placing files on the disk. Windows uses a filesystem called NTFS. Linux mostly uses filesystems called ext2fs, ext3fs, ext4fs, ReiserFS, JFS, XFS, or Btrfs. Normally, each partition holds just one filesystem. (There are exceptions to this rule, but they don't really change the analysis I'm presenting.) Thus, Windows and Linux must each have their own boot partition. You can access Windows partitions from Linux and you can access some types of Linux partitions from Windows; thus, you can set aside a partition for sharing files between OSes. (Some people use their main Windows boot partitions for this purpose, but this runs the risk of accidentally damaging Windows from Linux.)

So, as Mark says, it's not "shifty" that Windows is using the whole disk; it's just the way *any* OS uses the disk. There are ways to install Linux without repartitioning, such as using WUBI; however, it's usually best to either repartition or buy a new hard disk when you install any new OS.

---

