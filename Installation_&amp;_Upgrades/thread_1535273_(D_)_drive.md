---
title: "(D: ) drive?"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by II Luis II on 2010-07-20
Right ive posted a few topics and I always forget to ask something, so I just want something cleared up so i can try Ubuntu. Within my (D: ) drive (which is highlighted in black on the bottom of the image) is a short cut to my (C: ) Drive where everything is stored on my laptop. Would it be ok to use Wubi to install Ubuntu with 30GB installation size, into that (D: ) Drive? Would this have an effect on my Vista, is it likely to ruin it? And would this mean that the hard drive is partitioned? (BTW it came like this I havent partitioned it myself) 

[IMG]http://i27.tinypic.com/211vyhk.jpg[/IMG]
Thanks.

---

### Post by bcbc on 2010-07-20
> **II Luis II said:**
> Right ive posted a few topics and I always forget to ask something, so I just want something cleared up so i can try Ubuntu. Within my (D: ) drive (which is highlighted in black on the bottom of the image) is a short cut to my (C: ) Drive where everything is stored on my laptop. Would it be ok to use Wubi to install Ubuntu with 30GB installation size, into that (D: ) Drive? Would this have an effect on my Vista, is it likely to ruin it? And would this mean that the hard drive is partitioned? (BTW it came like this I havent partitioned it myself) 

[IMG]http://i27.tinypic.com/211vyhk.jpg[/IMG]
Thanks.

wubi won't partition your hard drive. It will create a large virtual disk (d:\ubuntu\disks\root.disk). It will treat this virtual disk as if it were a partition, and will not use any other part of the D: drive.

Since you have the D: drive sitting there doing nothing, I recommend partitioning it (from windows) and installing ubuntu direct.

Neither method will damage windows. Wubi will use the default windows boot manager (and grub4dos) to mount and boot the wubi install. A direct install means that grub2 will replace the windows bootloader and you'll have to boot windows from the grub2 menu.

---

### Post by II Luis II on 2010-07-21
So just to test Ubuntu for a bit before properly installing it I should just use Wubi onto the (D: ) drive. Is it possible to change between Operating systems whilst using one, so if I were using linux I could swap to windows during a session or do i have to restart my pc.

---

### Post by Mark Phelps on 2010-07-21
Word of advice -- NEVER force the installation of Ubuntu onto an untried machine.

Instead, boot from the CD and use the LiveCD mode to try out Ubuntu first.  That will indicate how well Ubuntu loads the proper drivers for your machine.

As to disk shrinkage, I'm guessing you're using Win7 on the ACER, or maybe Vista? Either way, if you want to install using traditional dual-boot (with each OS in its own partitions), use the built-in Disk Management utility to shrink the "D" drive to make room for Ubuntu.  Do NOT allow the Ubuntu installer to shrink the partition.  Doing so is asking for trouble later.

Finally, if you're running Win7, take the time to use the Backup feature of creating and burning a Win7 Repair CD.  It will come in handy later should you need to repair or restore the Win7 boot loader.

---

### Post by II Luis II on 2010-07-21
Im using Vista, is there a backup to disk thing with that? Also how big does the disk need to be? What do you mean by force install and how can I partition my drive? Also to create a live CD what sort of disk do I need?

Sorry to be a noob.

---

### Post by DrMelon on 2010-07-21
Boot from the CD instead of booting into windows to test ubuntu without installing anything on your machine. Your BIOS will have boot-order settings.

---

### Post by II Luis II on 2010-07-21
What sort of CD to I need? how much space?

---

### Post by bcbc on 2010-07-21
> **II Luis II said:**
> So just to test Ubuntu for a bit before properly installing it I should just use Wubi onto the (D: ) drive. Is it possible to change between Operating systems whilst using one, so if I were using linux I could swap to windows during a session or do i have to restart my pc.

You have to restart the pc to change operating systems (unless you are using a virtual machine).

To create an Ubuntu CD, download the image from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"). It includes instructions on burning a CD and trying it in live CD mode as well as installing. It's faster if you download with bit torrent.

You'll need a 700MB CD.

---

