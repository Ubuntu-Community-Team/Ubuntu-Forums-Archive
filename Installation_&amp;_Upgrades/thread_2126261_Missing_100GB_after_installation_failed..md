---
title: "Missing 100GB after installation failed."
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by Thursday9000 on 2013-03-16
I tried to install Ubuntu multiple times yesterday with no avail. I have a brand-new 1.5TB HDD and had 870GB left on it. 
During the first step of installation (resizing partition using 100GB) I got this error:

Ubiquity:5851): Gtk-CRITICAL **: gtk_widget_draw: assertion '!widget->priv->alloc_needed'  failed

I then turned my PC off and booted back into windows to see there was 100GB missing. I looked at my partitions within windows AND Ubuntu 'try' mode. There's no partitions and Ubuntu didn't install... I really would like to get my 100GB back, can anyone help?

---

### Post by darkod on 2013-03-16
Is there a 100GB unallocated space? If the partitions were never created, that would leave the space as unallocated. Windows might have issues seeing it since it was done by linux tools, but Gparted or cfdisk or parted in ubuntu live mode should see it fine.

Also, don't resize your windows partition with the ubuntu installer. Use the windows Disk Management tool. Winodws doesn't like other tools touching its system partition. Once you have the unallocated space created by the windows shrink, you can install ubuntu using the automated or the manual method, as you wish.

---

### Post by Thursday9000 on 2013-03-16
> **darkod said:**
> Is there a 100GB unallocated space? If the partitions were never created, that would leave the space as unallocated. Windows might have issues seeing it since it was done by linux tools, but Gparted or cfdisk or parted in ubuntu live mode should see it fine.

Also, don't resize your windows partition with the ubuntu installer. Use the windows Disk Management tool. Winodws doesn't like other tools touching its system partition. Once you have the unallocated space created by the windows shrink, you can install ubuntu using the automated or the manual method, as you wish.
I used Gparted and there's only like 10MB unallocated.

---

### Post by darkod on 2013-03-16
Can you post a screenshot of Gparted?

---

### Post by Thursday9000 on 2013-03-21
Sorry I didn't reply faster. Here's a screenshot
[img]http://i.imgur.com/9ZLx42d.png[/img]

---

### Post by Cheesemill on 2013-03-21
What makes you think you have 100GB missing?

All of your space is accounted for by the 2 NTFS partitions

---

### Post by Thursday9000 on 2013-03-21
> **Cheesemill said:**
> What makes you think you have 100GB missing?

All of your space is accounted for by the 2 NTFS partitions
Maybe because before attempting installation I had 880GB and after it failed, I only had 750.

---

### Post by darkod on 2013-03-21
I have no idea what you are talking about, is it the free space you see inside the C: partition in windows?

Your disk is 1.36TiB which is approx correct for a disk of 1.5TB and as mentioned above, all space is accounted for.

Now, how much unsued space you see inside C:, that is a different subject and is up to windows. That red warning symbol on sda2 usually means you need to run chkdsk in windows. So, boot windows and run chkdsk on C:.

---

### Post by ManamiVixen on 2013-03-21
The 100GB's isn't missing...
[http://ubuntuforums.org/showthread.php?t=2105707](http://ubuntuforums.org/showthread.php?t=2105707)
The failed install may of made a filesystem overhead for the etx4 partitions which isn't counted as a partition but instead part of the filesystem table.

---

### Post by Cheesemill on 2013-03-21
> **ManamiVixen said:**
> The 100GB's isn't missing...
[http://ubuntuforums.org/showthread.php?t=2105707](http://ubuntuforums.org/showthread.php?t=2105707)
The failed install may of made a filesystem overhead for the etx4 partitions which isn't counted as a partition but instead part of the filesystem table.

That has nothing to do with it.

The 5% reserved space issue is for ext4 filesystems, which the OP doesn't have.

---

### Post by Thursday9000 on 2013-03-22
> **darkod said:**
> I have no idea what you are talking about, is it the free space you see inside the C: partition in windows?

Your disk is 1.36TiB which is approx correct for a disk of 1.5TB and as mentioned above, all space is accounted for.

Now, how much unsued space you see inside C:, that is a different subject and is up to windows. That red warning symbol on sda2 usually means you need to run chkdsk in windows. So, boot windows and run chkdsk on C:.
I checked before installation and I had 890GB free space, I then attempted to install Ubuntu via a USB made with Fedora LiveUSB and tried to partition within Ubuntu. The installer glitched and wouldn't work nor partition right, so I turned my computer off. After booting into Windows again, I noticed that I only had 770GB free space left.

Note: My partition size was 100gb...

---

### Post by darkod on 2013-03-23
I understand that but according to the gparted screen you posted no 100GB partition was made, right? Windows might be only confused about the size of its partition since thr installer started partitioning it but never finished. So run the chkdsk first.
Another thing, are you using 7 or XP? If using 7 do the resize with windows Disk Management, not the ubuntu installer.

---

### Post by Thursday9000 on 2013-03-28
I've ran chkdsk many times, I've also tried defragging and it said there was 100gb fragmented files. But after completing it, nothing happened. 
Windows 7, and I'll see.

---

### Post by darkod on 2013-03-29
I'm not sure if win7 can get that confused because of the started (and failed) repartitioning attempt. Gparted seems to show that no ubuntu partition of any kind was created, all space on the disk belongs to win7.

Open Disk Management in win7 and check what that says. Does it have any unallocated space or all space belongs to the win7 ntfs partition?

---

### Post by Thursday9000 on 2013-03-31
[IMG]http://i.imgur.com/59evB2T.png[/IMG]
I'm still 100% sure it was Ubuntu, because I hadn't downloaded or installed anything that large.

---

### Post by andrew.46 on 2013-03-31
> **Thursday9000 said:**
> I then turned my PC off and booted back into windows to see there was 100GB missing. 

Don't nobody leave this room!!

:)

---

### Post by darkod on 2013-03-31
There you go, all the space is accounted for.

How much free space does win7 show inside it, that's win7 problem. From a partitioning point of view, it's all there. This might be a case of a large temp file or something that you need to find and delete. Try running Disc Cleanup, and emptying your recycle bin, etc.

You can also try some program that scans the disk and shows you the size of files and folders, to help you find some weird large file/folder that shouldn't be there. Once you find it, you can delete it.

---

