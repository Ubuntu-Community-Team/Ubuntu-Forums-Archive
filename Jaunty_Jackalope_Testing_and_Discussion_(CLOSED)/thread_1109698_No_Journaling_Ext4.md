---
title: "No Journaling Ext4?"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Chemical Imbalance on 2009-03-29
I have an eeepc with an ssd that I want to help preserve by turning off journaling in Jaunty on my ext4 partition.

I have found some documentation which says the option to mount it as writeback (nonjournaling) mode is

data=writeback

Which I'm assuming you add to the defaults line in fstab.

I've tried adding this and each time I get a read-only partition (due to a default setting in fstab that upon errors mounts read-only) and an Xorg failure to load.

I have to load a livesession to edit my fstab back.



Can anybody help me figure out why this is mounting with errors?  Do I have to apply a patch to allow writeback mode?  What am I doing wrong?

---

### Post by dcstar on 2009-03-29
> **Chemical Imbalance said:**
> I have an eeepc with an ssd that I want to help preserve by turning off journaling in Jaunty on my ext4 partition.
.......

[http://ubuntuforums.org/showthread.php?t=1063499](http://ubuntuforums.org/showthread.php?t=1063499)

---

### Post by hyper_ch on 2009-03-29
I wouldn't use Ext4 yet...

---

### Post by Chemical Imbalance on 2009-03-29
> **hyper_ch said:**
> I wouldn't use Ext4 yet...

I realize the risk, I just want a solution.

Data loss isn't a big issue on this 4gb ssd for me :)

I just use it for internet surfing and small tasks.  The boot up time is very much improved with ext4

---

### Post by Chemical Imbalance on 2009-03-30
I came across someone mentioning that one has to upgrade to a newer kernel to get this functionality.  I guess solved.

---

### Post by rsambuca on 2009-03-30
> **Chemical Imbalance said:**
> I came across someone mentioning that one has to upgrade to a newer kernel to get this functionality.  I guess solved.

Do you know which kernel version you need for this?

---

### Post by Yashiro on 2009-03-30
If you're going to disable journalling you might as well use ext2.

---

### Post by Kow on 2009-03-30
The 2.6.29 kernel supports ext4 w/o a journal.

---

### Post by rsambuca on 2009-03-30
> **Yashiro said:**
> If you're going to disable journalling you might as well use ext2.

Wrong.

If you read the ext4 kernel developers mailings, ext4 without a journal is much quicker than ext2, and with many other benefits.

---

### Post by Yashiro on 2009-03-30
Along with much less testing and real world use.

---

### Post by vahnx on 2009-03-31
I'm using ext4 and it's blazing fast and working fine for me :D

---

### Post by antistress on 2009-04-08
Data Mode
=========
There are 3 different data modes:

* writeback mode
In data=writeback mode, ext4 does not journal data at all.  This mode provides a similar level of journaling as that of XFS, JFS, and ReiserFS in its default mode - metadata journaling.  A crash+recovery can cause incorrect data to appear in files which were written shortly before the crash.  This mode will typically provide the best ext4 performance.
	
* ordered mode
In data=ordered mode, ext4 only officially journals metadata, but it logically groups metadata information related to data changes with the data blocks into a single unit called a transaction.  When it's time to write the new metadata out to disk, the associated data blocks are written first.  In general, this mode performs slightly slower than writeback but significantly faster than journal mode.

* journal mode
data=journal mode provides full data and metadata journaling.  All new data is written to the journal first, and then to its final location.
In the event of a crash, the journal can be replayed, bringing both data and
metadata into a consistent state.  This mode is the slowest except when data
needs to be read from and written to disk at the same time where it outperforms all others modes.  Curently ext4 does not have delayed allocation support if this data journalling mode is selected.

[http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt#313](http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt#313)

---

### Post by Chemical Imbalance on 2009-04-09
> **antistress said:**
> Data Mode
=========
There are 3 different data modes:

* writeback mode
In data=writeback mode, ext4 does not journal data at all.  This mode provides a similar level of journaling as that of XFS, JFS, and ReiserFS in its default mode - metadata journaling.  A crash+recovery can cause incorrect data to appear in files which were written shortly before the crash.  This mode will typically provide the best ext4 performance.
	
* ordered mode
In data=ordered mode, ext4 only officially journals metadata, but it logically groups metadata information related to data changes with the data blocks into a single unit called a transaction.  When it's time to write the new metadata out to disk, the associated data blocks are written first.  In general, this mode performs slightly slower than writeback but significantly faster than journal mode.

* journal mode
data=journal mode provides full data and metadata journaling.  All new data is written to the journal first, and then to its final location.
In the event of a crash, the journal can be replayed, bringing both data and
metadata into a consistent state.  This mode is the slowest except when data
needs to be read from and written to disk at the same time where it outperforms all others modes.  Curently ext4 does not have delayed allocation support if this data journalling mode is selected.

[http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt#313](http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt#313)

I already knew this, thanks though

And the question has been solved, writeback mode can only be enabled in the 2.6.29 kernal AFAIK

---

### Post by KhaaL on 2009-04-09
> **Chemical Imbalance said:**
> I already knew this, thanks though

And the question has been solved, writeback mode can only be enabled in the 2.6.29 kernal AFAIK

can you tell me if this is a correct way to disable the journal in ext4:

UUID=04cfdee9-af03-44c1-b313-71e328fa174e /               ext4    data=writeback,errors=remount-ro 0       0

Because like you, i had trouble enabling it and i got onto a read-only filesystem.

Tip: if you want even faster performance add the noatime,nodiratime switches in fstab ;)

---

### Post by Chemical Imbalance on 2009-04-09
> **KhaaL said:**
> can you tell me if this is a correct way to disable the journal in ext4:

UUID=04cfdee9-af03-44c1-b313-71e328fa174e /               ext4    data=writeback,errors=remount-ro 0       0

Because like you, i had trouble enabling it and i got onto a read-only filesystem.

Tip: if you want even faster performance add the noatime,nodiratime switches in fstab ;)

Like I said, you need the .29 kernel, so I guess you will have to compile one.

I already use noatime instead of relatime, but what does nodiratime do?

---

### Post by KhaaL on 2009-04-09
no need to compile, you can get one from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

nodiratime turns off updates for folders, but i think that noatime includes that (can someone confirm?)

---

### Post by Chemical Imbalance on 2009-04-09
> **KhaaL said:**
> no need to compile, you can get one from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

nodiratime turns off updates for folders, but i think that noatime includes that (can someone confirm?)

Ahhh, thanks for the link!  I didn't realize there were debs available

It sounds like nodiratime is a bit extreme.  I don't think folder updates would affect performance that much, do you?

---

### Post by KhaaL on 2009-04-09
noatime is more extreme than nodiratime since it disables for the whole filesystem, IMO if you're disabling accesstime for files you might aswell do it for directories :) I use that switch to keep HD writes to a miminum since I'm affected by a kernel bug that puts my computer to a standstill when there is HD activity.

---

### Post by Kow on 2009-04-09
> **Chemical Imbalance said:**
> I already knew this, thanks though

And the question has been solved, writeback mode can only be enabled in the 2.6.29 kernal AFAIK

Are you sure? Via "tune2fs -o journal_data_writeback <device>" with ubuntu's 2.6.28 kernel I get this when EXT4 is mounted:

"[    3.305576] EXT4-fs: mounted filesystem with writeback data mode."

Perhaps this is lying to me until 2.6.29?

---

### Post by Chemical Imbalance on 2009-04-09
> **Kow said:**
> Are you sure? Via "tune2fs -o journal_data_writeback <device>" with ubuntu's 2.6.28 kernel I get this when EXT4 is mounted:

"[    3.305576] EXT4-fs: mounted filesystem with writeback data mode."

Perhaps this is lying to me until 2.6.29?

I guess I heard wrong...why does everyone have to be so *smart*-*ssed?

It didn't work for me or the op in this thread.

Please tell us exactly what you did...

---

### Post by Jordanwb on 2009-04-12
This thread is relevant to my interests. When I make an ext4 filesystem is makes a journal even if you don't want one. Is it possible to tell it not to make a journal?

---

### Post by Sarvatt on 2009-04-12
You need to change the journaling option with tune2fs instead of through fstab, it mounts the partition through grub first and then remounts it rw through fstab but its too late to change journaling type by that point. the same problem exists for changing the journaling type on ext3 in fstab.

---

### Post by weeman7007 on 2009-04-12
> **Sarvatt said:**
> You need to change the journaling option with tune2fs instead of through fstab, it mounts the partition through grub first and then remounts it rw through fstab but its too late to change journaling type by that point. the same problem exists for changing the journaling type on ext3 in fstab.

how would I do that?

---

### Post by Jordanwb on 2009-04-12
> **weeman7007 said:**
> how would I do that?

I've never used tune2fs but I would guess:

```
tune2fs /dev/sda1 -o data=writeback
```

The man page for tune2fs reports it works only on ext2/3 FS's.

---

### Post by sgosnell on 2009-04-12
I'm not sure why everyone is so concerned with wearing out the SSD.  The EEE will be long obsolete before you could possibly wear out the SSD, even with constant writes.  Boooooguuuusssssssssssssssss.

---

### Post by Kow on 2009-04-12
> **Chemical Imbalance said:**
> I guess I heard wrong...why does everyone have to be so *smart*-*ssed?

It didn't work for me or the op in this thread.

Please tell us exactly what you did...

```
sudo tune2fs -o journal_data_writeback /dev/whatever
```

Replace 'whatever' with your hard disk 3 letter abbrev and the partition (ex: /dev/sda1) After that, reboot. But, this is NOT running ext4 without a journal. Per tune2fs manpage:
> 
                          When  the  filesystem  is  mounted  with journalling
                          enabled, data may be written into the main  filesys&#8208;
                          tem  after  its  metadata  has been committed to the
                          journal.  This may increase throughput, however,  it
                          may  allow old data to appear in files after a crash
                          and journal recovery.


---

### Post by Chemical Imbalance on 2009-04-13
> **sgosnell said:**
> I'm not sure why everyone is so concerned with wearing out the SSD.  The EEE will be long obsolete before you could possibly wear out the SSD, even with constant writes.  Boooooguuuusssssssssssssssss.

Some of us are more cautious (read: paranoid) then others :).

I guess with my cheap and slow ssd an SD-card might be an upgrade if it ever wears out :lolflag:

---

### Post by Sarvatt on 2009-04-13
> **weeman7007 said:**
> how would I do that?

tune2fs -O ^has_journal /dev/sd?

no idea if it'll cause problems though.

---

### Post by charcer on 2009-04-15
I'm also interested in ext4 without journal for my acer aspire one with ssd drive.
At the moment I have xubuntu 9.04 beta with kernel 2.6.29.1

First I booted to xubuntu live usb-disk and run
tune2fs -O ^has_journal /dev/sda1

It gave no errors, but when rebooted the laptop gave me initramfs prompt, and a message "Alert! /dev/disk/by-uuid/xxxxxxxx does not exist. Dropping to a shell!"
It was the same with kernel .28 and with safe modes.

The I booted to live disk again, and run 
tune2fs -O has_journal /dev/sda1

which reverted the situation, and I was able to boot again.


Lastly I booted to live disk and run
sudo tune2fs -o journal_data_writeback /dev/sda1

and that seemed to work in a way that there wasn't any errors and I could boot normally.


But I'm still curious if that's the right method, is there some way I can check if a journal exists?
And also does /fstab need any special mount options when i have run the tune2fs -o journal_data_writeback command?

---

### Post by Sarvatt on 2009-04-18
> **charcer said:**
> I'm also interested in ext4 without journal for my acer aspire one with ssd drive.
At the moment I have xubuntu 9.04 beta with kernel 2.6.29.1

First I booted to xubuntu live usb-disk and run
tune2fs -O ^has_journal /dev/sda1

It gave no errors, but when rebooted the laptop gave me initramfs prompt, and a message "Alert! /dev/disk/by-uuid/xxxxxxxx does not exist. Dropping to a shell!"
It was the same with kernel .28 and with safe modes.

The I booted to live disk again, and run 
tune2fs -O has_journal /dev/sda1

which reverted the situation, and I was able to boot again.


Lastly I booted to live disk and run
sudo tune2fs -o journal_data_writeback /dev/sda1

and that seemed to work in a way that there wasn't any errors and I could boot normally.


But I'm still curious if that's the right method, is there some way I can check if a journal exists?
And also does /fstab need any special mount options when i have run the tune2fs -o journal_data_writeback command?

you should have to e2fsck manually before rebooting to remove the journal..

sudo dumpe2fs /dev/sdawhatever shows the info

ext4 should mount writeback by default on 2.6.29.

it might actually need an update to e2fsprogs before you can do it looking at the git repo.

[http://git.kernel.org/?p=fs/ext2/e2fsprogs.git;a=shortlog](http://git.kernel.org/?p=fs/ext2/e2fsprogs.git;a=shortlog)

[http://git.kernel.org/?p=fs/ext2/e2fsprogs.git;a=commit;h=a90f5391dda78f7bc4a8196a78355584ace0adf5](http://git.kernel.org/?p=fs/ext2/e2fsprogs.git;a=commit;h=a90f5391dda78f7bc4a8196a78355584ace0adf5)

---

