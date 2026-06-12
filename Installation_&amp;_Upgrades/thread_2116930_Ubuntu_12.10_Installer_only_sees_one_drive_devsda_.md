---
title: "Ubuntu 12.10 Installer only sees one drive: /dev/sda and not all of my drives"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by shikhargpt on 2013-02-17
I have a 320 GB harddrive. Last time I installed Ubuntu, I created a 40 GB install space for it. It is /dev/sda6. Stuff happened and now from a live CD, I want to completely reinstall Ubuntu over the old partition for it. However, there is a hitch.

Terminal command sudo fdisk -l can identify all the drives from there, but GParted and the Ubuntu Installer only see the 320 GB HDD as a whole. I do not want to create another partition. I simply want to use /dev/sda6. What can I do?

---

### Post by darkod on 2013-02-17
There are few options. If the disk has been used in raid (unlikely from what you say), it has meta data present and the installer is ignoring it. But Gparted should see the partitions correctly in this case.

If there is an error in the partition table, it might not recognize the partitions properly but this would apply to fdisk too. You seem to say fdisk sees the partitions.

Can you poste the output of:
sudo parted -l

---

### Post by dino99 on 2013-02-17
if you have several devices, then look at the dropdown menu on top right corner into gparted, and select the desired device. Otherwise it maight complaint/warn and show a red or orange icon.

to reinstall inside sda6, then follow the manual installer choice "Something Else"

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: ALWAYS use gparted (& all other formatting tool) with unmounted partition.

---

### Post by shikhargpt on 2013-02-17
> **darkod said:**
> There are few options. If the disk has been used in raid (unlikely from what you say), it has meta data present and the installer is ignoring it. But Gparted should see the partitions correctly in this case.

If there is an error in the partition table, it might not recognize the partitions properly but this would apply to fdisk too. You seem to say fdisk sees the partitions.

Can you poste the output of:
sudo parted -l
Here.

"Error: Can't have overlapping partitions.                                 

Model: Slimtype DVD A DS8A5SH (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  3160MB  3159MB  primary               boot, hidden"

I am running this from a live CD.

---

### Post by shikhargpt on 2013-02-17
> **dino99 said:**
> if you have several devices, then look at the dropdown menu on top right corner into gparted, and select the desired device. Otherwise it maight complaint/warn and show a red or orange icon.

to reinstall inside sda6, then follow the manual installer choice "Something Else"

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: ALWAYS use gparted (& all other formatting tool) with unmounted partition.
As I said. Only /dev/sda (298 GB) appears there. The same case with the installer. :(

---

### Post by darkod on 2013-02-17
> "Error: Can't have overlapping partitions. 

This seems to be your problem, if you pasted the result correctly. You have an error in the table, overlapping partitions.

Try fixparts to sort it out, in many cases it can do it automatically for you.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

PS NOTE:Once you have linux partitions on the hdd be very careful when doing partitioning. If you do it from windows (you said you had this ubuntu partition from long ago and haven't used it a lot), because it can't understand linux partitions it can mess up the disk partitions. Try to do it with linux tools, even if you are not using the currently installed linux, you can always do it from live mode.

---

### Post by shikhargpt on 2013-02-17
> **darkod said:**
> This seems to be your problem, if you pasted the result correctly. You have an error in the table, overlapping partitions.

Try fixparts to sort it out, in many cases it can do it automatically for you.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

PS NOTE:Once you have linux partitions on the hdd be very careful when doing partitioning. If you do it from windows (you said you had this ubuntu partition from long ago and haven't used it a lot), because it can't understand linux partitions it can mess up the disk partitions. Try to do it with linux tools, even if you are not using the currently installed linux, you can always do it from live mode.
Which one do I download?

---

### Post by dino99 on 2013-02-17
from the ubuntu livecd/liveusb, use gparted, it have the option to rebuilt the partition table, and then you have to format the partition

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by shikhargpt on 2013-02-17
> **darkod said:**
> This seems to be your problem, if you pasted the result correctly. You have an error in the table, overlapping partitions.

Try fixparts to sort it out, in many cases it can do it automatically for you.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

PS NOTE:Once you have linux partitions on the hdd be very careful when doing partitioning. If you do it from windows (you said you had this ubuntu partition from long ago and haven't used it a lot), because it can't understand linux partitions it can mess up the disk partitions. Try to do it with linux tools, even if you are not using the currently installed linux, you can always do it from live mode.
I am getting this: 

FixParts 0.8.4

Loading MBR data from /dev/sda

Problem: MBR partitions 5 and 6 overlap!


Now what?

---

### Post by darkod on 2013-02-17
> **shikhargpt said:**
> Which one do I download?

I think there is a .deb for ubuntu. Install it and run it from terminal.

Gparted might have an option like dino says but I have never used it much. Not sure if it can do the same and rebuild the table without hurting existing partitions.

---

### Post by darkod on 2013-02-17
> **shikhargpt said:**
> I am getting this: 

FixParts 0.8.4

Loading MBR data from /dev/sda

Problem: MBR partitions 5 and 6 overlap!


Now what?

Does it offer to repair it?

If not, print the table in fixparts as it is, and see how much they overlap (the start/end of all partitions). I guess there is an option in fixparts to resize one of them so they don't overlap any more.

---

### Post by shikhargpt on 2013-02-17
> **dino99 said:**
> from the ubuntu livecd/liveusb, use gparted, it have the option to rebuilt the partition table, and then you have to format the partition

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

Doesn't that mean I'll create a new partition??

---

### Post by shikhargpt on 2013-02-17
> **darkod said:**
> Does it offer to repair it?

If not, print the table in fixparts as it is, and see how much they overlap (the start/end of all partitions). I guess there is an option in fixparts to resize one of them so they don't overlap any more.

This is what I get:

```
** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 625142448 sectors (298.1 GiB)
MBR disk identifier: 0xE0C5913D
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    63     45062324   primary              Y      0x1C
   2      *       45062325    201342644   primary              Y      0x07
   5             201349120    543221909   logical     Y        Y      0x07
   6             543221760    621043711   omitted                     0x83
   7             621045760    625139711   logical     Y        Y      0x82
```

---

### Post by darkod on 2013-02-17
Number 6 is omitted. Try converting it to logical by pressing 'l', I think it will ask you for the partition number after that.

In any case, fixparts changes are not saved until you press 'w'. So, first try making it logical, print the list again and see how it looks. When you try to make it logical it might sort out the size issue for you. Now it's omitted and #5 ended up over it.

PS. And when posting output it's better to do it in code tags so that it keeps the formatting and is easier to read.

---

### Post by dino99 on 2013-02-17
> **shikhargpt said:**
> Doesn't that mean I'll create a new partition??

no, it only rebuilt the table of the selected partition (easy & quick). Then format again the partition.

---

### Post by shikhargpt on 2013-02-17
> **darkod said:**
> Number 6 is omitted. Try converting it to logical by pressing 'l', I think it will ask you for the partition number after that.

In any case, fixparts changes are not saved until you press 'w'. So, first try making it logical, print the list again and see how it looks. When you try to make it logical it might sort out the size issue for you. Now it's omitted and #5 ended up over it.

PS. And when posting output it's better to do it in code tags so that it keeps the formatting and is easier to read.
```
Loading MBR data from /dev/sda

Problem: MBR partitions 5 and 6 overlap!

Specified change is not legal! Aborting change!

```Now what..?

---

### Post by dino99 on 2013-02-17
> **shikhargpt said:**
> ```
Loading MBR data from /dev/sda

Problem: MBR partitions 5 and 6 overlap!

Specified change is not legal! Aborting change!

```Now what..?

well, as said it "overlap", meaning you need to resize either the 5 or 6 partition: one cant start before the previous have ended  :lolflag:

---

### Post by shikhargpt on 2013-02-17
> **dino99 said:**
> well, as said it "overlap", meaning you need to resize either the 5 or 6 partition: one cant start before the previous have ended  :lolflag:
Sorry, noob here. So, how do I go about doing this?

---

### Post by darkod on 2013-02-17
I'm reading the fixparts tutorial and unfortunately it doesn't seem to have delete option to try and delete sda6.

Try to see if cfdisk will show all partitions, or not. Only open the disk with it and see the list it shows. Check if all partitions are there comparing to the fixparts output.

sudo cfdisk /dev/sda

If it does list the partitions, try deleting sda6 and then create new swap partition in the unallocated space. Only then write the changes and exit cfdisk. That should create a new partition that fits into the unallocated space and doesn't overlap with sda5.

Also, if you do create new partition, go into the option to change the code and change it to 83.

---

### Post by darkod on 2013-02-17
OK, I just found this in the fixparts tutorial, didn't see it earlier:
> Note that omitting the partition does not immediately remove it from the partition list; it will still appear in the list when you type p, but it will be coded as omitted under the Status column. When you save your changes, omitted partitions will not be saved and so will be lost.

So, when you get the listing and sda6 is marked as omitted, if you do the write option with 'w' it should get deleted. That is how it deletes a partition.

I suggest you change sda7 to primary partition because when you delete sda6 it will leave empty space between sda5 and sda7 and I'm not sure how fixparts can handle that. After you create new logical partition in the unallocated space you can convert sda7 back to logical.

That is what I would try. To summarize:
1. Open fixparts again. Convert sda7 to primary.
2. Write the changes with 'w'. That will delete sda6 marked as omitted.
3. Create new logical partition in the unallocated space, with parted or cfdisk.
4. Open fixparts again and convert sda7 (it might be called different but you can see according to the position start/end sectors) back to logical. Write the changes again.

---

### Post by shikhargpt on 2013-02-17
Thanks! It worked!

---

