---
title: "dd to move a partition and make it bootable"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by pr1mal on 2008-11-29
I am moving a partition.  Its XP

I currently have it on a HDD as a 2.9 gig partition along with another XP partition.
I need to move it onto a laptop that has vista on it and a blank 10 gig partition

I am using ubuntu :) live CD
i am using dd     unless you tell me otherwise

what are the commands to package the partition ie.hda1 into a file ie.tar

then when i move it to my other computer, how do i extracted it to the empty 10 gig partition?

also, how do i get the MBR on the laptop to see that there is a OS on the partition

thanks much

---

### Post by night_fox on 2008-11-29
dd if=/dev/sda1 of=sda1.bin
tar -cvvf sda1.bin sda1.tar

Move it across via ftp or a ruddy great memory stick or external hard drive
It has to be stored on something bigger than it (if you transfer it via LAN then you have to make a partition that is bigger than the backup)

To edit the MBR, boot from the live cd and mess around with the partition table using the gui.

---

### Post by night_fox on 2008-11-29
Carefully.

dd can write directly to the device. Ruining the MBR in one easy sudo statement.

---

### Post by pr1mal on 2008-11-29
dd if=/dev/sda1 of=sda1.bin

should the source and destination be the same device??
to untar it to the partition on the laptop what should I do
will that resize the 10gig empty fat32 to the copy 2.9gig

---

### Post by night_fox on 2008-11-30
Yeah thats a point.

that instance of the dd directly reads an entire device or partition and dumps it in a file. the path of the 'if' file has to be somewhere NOT on the partition you are dumping.

However, you can't just untar it to a partition. You have to untar it somewhere then use dd again to write it.

---

### Post by night_fox on 2008-11-30
Are you sure you want to move the entire partition? If you do, both partitions need to be the same size. I think you might want to only move the data.

If you wanted to do it to the entire partition, I think you should shrink your empty 10gb partition to 2.9gb, it has to be EXACT, then use dd, then expand it.

It would be much safer to only transfer the data.

---

### Post by pr1mal on 2008-12-01
How I am able to only copy over only the data??

---

### Post by Lupusceleri on 2008-12-01
> **pr1mal said:**
> How I am able to only copy over only the data??

That would seem pretty easy to me. Assuming you are using the 8.10 liveCD, graphical?

1) Plug in a bigass USB drive, wait for it to get mounted.
2) Open partition using live CD, iirc it automounts when you click the directory from Places. CTRL+A, CTRL+C.
3) Open USB drive (wherever it's mounted), go to the directory where you want to temp-store your data, and wait.

When it's done copying, start up with the liveCD on the other laptop. I assume your 'receiving' uses the same filesystem as the 'sending' partition? If not, you should probably use Gparted to format the partition to the right FS but correct me if I'm wrong.

Same routine as the move-to-USBdisk now:

1) Plug in a bigass USB drive, wait for it to get mounted.
2) Open USB drive (wherever it's mounted), go to the directory where you temp-stored your data, CTRL+A and CTRL+C.
3) Open partition you want the stuff on, iirc it automounts and stuff. CTRL-V, wait.

And done copying data?

---

### Post by caljohnsmith on 2008-12-01
Using "tar" is only relevant when you want to archive files/directories together; when you use the "dd" command to move a partition, it treats the partition as raw data or one huge single file, so tar will balk at archiving just one file. I think maybe the easiest solution for your situation would be to boot the Live CD, and open up gparted (System > Admin > Partition Editor); if you create some unallocated space on your destination drive, then you can simply copy/paste over the partition from the source drive to the destination drive. I know others who have used this method with success.

Also, if you are moving an XP partition, make sure the beginning point of the XP partition on the destination drive is exactly the same as on the source drive. So if the XP partition starts at say 82043955 sectors (~40 GB) on the source drive, you would want that to be the same on the destination drive or XP will for sure refuse to boot.

---

