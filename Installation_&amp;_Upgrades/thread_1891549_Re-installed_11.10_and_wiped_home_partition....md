---
title: "Re-installed 11.10 and wiped home partition..."
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by cSquall on 2011-12-05
I installed a new graphics cards and was having issues, even though the card worked fine with the Live disk. So, in my ultimate wisdom, I did a re-install and selected the option for manually defining partitions.  I have done this many times over the years without an issue, always re-mapping the partitions to the same ones.  Thus, I knew which partition was my home, and I selected that partition in the partitioner and gave the mount path as /home. In all previous versions, this did NOT overwrite my home partition. I warning came up saying it would overwrite system files, and I thought, naively, "I've done this before. I don't remember this warning, but then again, there aren't what I would consider to be system files in /home.

Anyway, now I've got an empty /home partition and would like to know:

1) Should I open a bug report on this, since there is no no longer an obvious way to re-install without destroying your home partition.

2) How do I restore the data? I have not been using Ubuntu on that machine since this happened, in the hopes of preserving date.

Help!

cSquall at sea in a lifeboat...

---

### Post by oldtimer7777 on 2011-12-05
> **cSquall said:**
> 
2) How do I restore the data? I have not been using Ubuntu on that machine since this happened, in the hopes of preserving date.
.

You can try using:

[https://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/](https://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/)

---

### Post by bluexrider on 2011-12-05
testdisk and photorec are good to recover that type of data. you can define your search too

---

### Post by kio_http on 2011-12-06
> **cSquall said:**
> I installed a new graphics cards and was having issues, even though the card worked fine with the Live disk. So, in my ultimate wisdom, I did a re-install and selected the option for manually defining partitions.  I have done this many times over the years without an issue, always re-mapping the partitions to the same ones.  Thus, I knew which partition was my home, and I selected that partition in the partitioner and gave the mount path as /home. In all previous versions, this did NOT overwrite my home partition. I warning came up saying it would overwrite system files, and I thought, naively, "I've done this before. I don't remember this warning, but then again, there aren't what I would consider to be system files in /home.

Anyway, now I've got an empty /home partition and would like to know:

1) Should I open a bug report on this, since there is no no longer an obvious way to re-install without destroying your home partition.

2) How do I restore the data? I have not been using Ubuntu on that machine since this happened, in the hopes of preserving date.

Help!

cSquall at sea in a lifeboat...

You should file a report. I once saw someone on IRC have the exact same issue. Did you make sure that the "use as" combobox had the correct filesystem and that "format" tickbox was not checked? Next time maybe try the alternate installer. I always prefered it and it never failed me. (The desktop installer used to crash for me in earlier releases)

---

### Post by darkod on 2011-12-06
I am using a separate /home since 9.10 and did most of the version as clean installs by keeping /home. I have installed 11.10 too this way on both my desktop and netbook. In both cases /home was just fine.
If it really is a bug I guess it would be difficult to locate and prove because I guess lot of conditions have to be met. It's not like it happens to all who do this type of setup. There would be much more reports on the forums.

---

### Post by almalaci on 2011-12-06
I have overwritten my /home partition in the exact same way. I even saw the Format box ticked but it was a greyed out tick.
I saw no apparent way to make sure my new home folder will be on that partition so I went ahead thinking that the installer will list the actions it would take and I can confirm before anything is written on the disk. Well, it didn't and now my original /home partition seems to have lost.
I'm pretty sure now that during the install I set the partition to be used as ext4 instead of ext3 which it was before.
 
I'm running photorec at the moment which is finding a lot of files but they all have non-descript names and just dumped all in the same folder.
I'm about to give testdisk a go but my new install created a home folder for the new user on the partition. Will testdisk bring back my old partition or whatever remained of it still?

---

### Post by darkod on 2011-12-06
This is just a wild guess, but I wonder if this happens if you select a different filesystem for /home in the Use As field, compared to the current filesystem it has. As one poster has already mentioned.
It does make little sense that it would try to format it if changing the filesystem. I would think it's too much to expect that it can change the filesystem without formatting it.

---

### Post by almalaci on 2011-12-06
Yes, you are right I'm pretty sure now that during the install I set the partition to be used as ext4 instead of ext3 which it must have been before. (Sorry I just re-edited my post to put this in).

I would really like to try testdisk but I'm not sure what it would do because the install now has written on the partition. 

In any case, I guess I should make an image of the partition first.
Any ideas? I'm getting paranoid about losing irreplaceable data now...

---

### Post by darkod on 2011-12-06
dd will do an exact image, but it takes long depending of the size. And the source is not mounted which is what you need so no further writes (overwrites) happen.
Get something like the System Rescue CD, and external usb hdd ready (or another internal hdd).

Boot with the system rescue cd and mount the destination partition (make sure it's bigger than the source). We are talking just partitions here, not disks.

You can mount it as /mnt for example.
sudo mount /dev/sdb3 /mnt

Then just copy all of your ex-home partition:
sudo dd if=/dev/sda2 of=/mnt/image.img

Of course, replace /dev/sdb3 and /dev/sda2 with the correct partitions in your case.

That will give you exact image as it is now, so you can try to play around with the hdd and still have a backup image.

---

### Post by almalaci on 2011-12-07
Many thanks darkod,

I'm going to do just that.
I'll need to get hold of another empty hd though. 

In the meantime I ran photorec on the partition but all I got was millions txt files, some mp3's and html fragments, mainly thumbnails but most importantly no photos or anything important.
I have about 200GB stuff on that partition with no backup whatsoever... :(

---

### Post by darkod on 2011-12-07
I'm not too big of an expert but it shouldn't get written unless you copy files to it or run the OS from it.

I always had the impression testdisk was a better tool for recovering whole deleted/formatted partitions, not photorec. Have you tried it? And the deep scan, not just the normal one?

Their example of recovering lost partitions (not sure if it applies to formatted too): [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by almalaci on 2011-12-08
You are probably right, testdisk seems more like the thing I need. I'm just too paranoid to run it before I dd'd the partition. I have to wait until the weekend to buy a big enough harddrive to do that but I couldn't wait, so in the meantime I'm using photorec. I tried a newer version which has now recovered seemingly all of my photos so I'm very-very pleased!! I'm doing one media type only at a time so files won't get too mixed up.
Hopefully early next week I'll manage to try testdisk finally.

---

### Post by almalaci on 2011-12-15
I've tried testdisk and it found my old home partition. I could even list some files but oddly enough only one user folder, not the one that had the data I was looking for. Is there a reason why testdisk would only find a more recently used user's folder and not older ones? Or is there a different reason why testdisk is not finding other folders that I am otherwise able to recover data from using photorec?

---

