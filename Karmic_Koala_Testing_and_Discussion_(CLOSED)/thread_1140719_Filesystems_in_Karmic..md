---
title: "Filesystems in Karmic."
date: 2009-04-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-04-27
Is it just me or are there others here that feel Ubiquity could do with a bit of a clean up? At the moment we have Fat16, Fat32, Ext2, Ext3, Ext4, XFS, JFS and ReiserFS. IMO Fat16, Ext2 and either XFS or JFS should be dropped. What do you guys think?

Ive included a poll to see which you guys think should stick around. It is therefore multiple choice.



I havent included Btrfs in the poll for obvious reasons. We would all like it there ASAP.
I also havent included Reiser4 in the poll because last i knew it was still in development with uncertainty of it ever being released.

---

### Post by b@sh_n3rd on 2009-04-27
Hey, aren't XFS and JFS supposed to be better? I'm experimenting with XFS and there seems to be a noticable change in HDD performance

---

### Post by Simian Man on 2009-04-27
Ext2 is still nice for solid-state drives where you want to reduce wear and tear.  The fact that it has no journaling reduces the number of writes made increasing the drives lifetime.  I agree on Fat16; the others I don't know much about.

---

### Post by Ericyzfr1 on 2009-04-27
It does not bother me and there may be some users that still needs these files systems on their machine.

---

### Post by Slug71 on 2009-04-27
> **b@sh_n3rd said:**
> Hey, aren't XFS and JFS supposed to be better? I'm experimenting with XFS and there seems to be a noticable change in HDD performance

Im not sure myself as i havent used either. Last i knew though you couldnt boot from a XFS partition. At least not with Grub Legacy. From what ive heard and briefly read about them, they seem pretty similiar.

---

### Post by b@sh_n3rd on 2009-04-27
ahuh, I read about the prob with XFS as the boot partition only after formatting it in exactly that order. The mount points, /boot, /home and / are XFS. I panicked when I thought that I might have to re-partition and re-install Jaunty. Nevertheless, My Jaunty installation came out fine and my system boots without further ado. All I say is "straaange". Either my comp is acting weird, Jaunty is acting weird, or that prob has been solved??

**EDIT:** When I was doing research on XFS, the articles also said that, to avoid the above mentioned problem, format the "/boot" partition in another filesystem such as, Ext3 or Ext4.

**EDIT2:** I take that back, XFS seems to be on top of the list, not JFS, which is kinda low.
>  *Quoted from: [http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/](http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/)*

**Our Final List:**

**Boot Time:**
1. Tie between Ext4 and XFS.
2. Ext3
3. JFS
4. ReiserFS (Reiserfsck makes the boot chart look like an EKG&#8230;..We&#8217;re losing him! CLEAR!!!)

**Disk Throughput:**
1. XFS (by a mile)
2. ReiserFS
3. Ext3
4. Ext4
5. JFS (Again, ouch!)

---

### Post by scheuri on 2009-04-28
Linux is about choice...

Drivers and tools for all available file systems are/need to provided anyway. So why not make it a choice?
Most of the choosing is done by a "default" (which is ext3 as of now). So users without much background will likely take that.

I am not sure about ext4 to be honest. I will stick to ext3 even with karmic and after.
If Debian makes it default, THEN I am sure it is stable...;)

---

### Post by b@sh_n3rd on 2009-04-28
> **scheuri said:**
> 
I am not sure about ext4 to be honest. I will stick to ext3 even with karmic and after.
If Debian makes it default, THEN I am sure it is stable...;)

It seems ext4 has a few bugs but currently, karmic seems to be effected by 'em more than jaunty. It's ok and boot up time is faster than before.

---

### Post by Gina on 2009-04-28
> **scheuri said:**
> Linux is about choice...

Drivers and tools for all available file systems are/need to provided anyway. So why not make it a choice?
Most of the choosing is done by a "default" (which is ext3 as of now). So users without much background will likely take that.

I am not sure about ext4 to be honest. I will stick to ext3 even with karmic and after.
If Debian makes it default, THEN I am sure it is stable...;)I agree - that sums it up for me too.  I'll test with ext4 but otherwise stick to ext3 for now.

---

### Post by olskar on 2009-04-28
I hope bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824) will be fixed so EXT4 is usable for me

---

### Post by Tom Mann on 2009-04-28
Where is btrfs?

I'd love to give it a go...

---

### Post by Slug71 on 2009-04-28
> **Tom Mann said:**
> Where is btrfs?

I'd love to give it a go...


Should hopefully be optional with Karmic.

---

### Post by jerrylamos on 2009-04-28
EXT 4 has been blamed for a lot (!) of lost files on the jaunty forum.  Has that been cleaned up?

Thanks, Jerry

---

### Post by gnomeuser on 2009-04-28
> **jerrylamos said:**
> EXT 4 has been blamed for a lot (!) of lost files on the jaunty forum.  Has that been cleaned up?

Thanks, Jerry

the forum search is that way next time but let me answer it anyways.

Yes and no, upstream for ext4 added (as well as btrfs) added some handling to retain the behaviour in ext3. This is though not fixing every filesystem in Linux, you will experience the same problem on xfs e.g.. The required change is to get every application to adhere to the correct way of handling files. Often this is a change low in the stack such as in glib and isn't as daunting a task as it sounds. 

One day we will switch back to the correct behaviour according to the POSIX spec. Till that happens there are lots of issues to fix such as applications and libraries needing updating. There is also work needing to be done to make the fsync call less expensive which is a major application developer concern. 

The issue is not gone, it is however not a problem that will eat your data anymore. You need not worry about it.

---

### Post by ssam on 2009-04-28
> **Simian Man said:**
> Ext2 is still nice for solid-state drives where you want to reduce wear and tear.  The fact that it has no journaling reduces the number of writes made increasing the drives lifetime.

ext4 has a no journalling mode.

---

### Post by Simian Man on 2009-04-28
> **ssam said:**
> ext4 has a no journalling mode.

Really?  Well that's pretty nice.  I wonder if that would be available under the format option of the installer.  It would be a great option for those installing Linux on solid-state drive netbooks.

---

### Post by VMC on 2009-04-28
> **ssam said:**
> ext4 has a no journalling mode.

Yes it does. Read [this]("http://beginlinux.com/server_training/8-ubuntuadmin/1255-crash-testing-ext4-on-ubuntu/")

---

### Post by SKLP on 2009-04-28
I'd say ext4 should be default, FAT16 and FAT32 should not be available (obviously it should be supported on say pen drives, but not in the installer). Ext2, JFS, XFS and ReiserFS should be marked as "not recommended for new filesystems" maybe with a word such as "obsolete". Btrfs should be added and marked as experimental.
So a list like this:
```
Ext4 (recommended)
Ext3
Btrfs (experimental)
Ext2 (obsolete)
JFS (obsolete)
ReiserFS (obsolete)
```
Also, it might be unnecessary to even show those filesystems in the list( the ones marked experimental and obsolete) unless the user does something like press-and-hold ALT while starting the formatter (or similar)

---

### Post by edm1 on 2009-04-28
A cleanup??? The more filesystems the better. They don't get in the way and people shouldn't be changing from the default unless they know what they're doing.

---

### Post by Slug71 on 2009-04-28
> **SKLP said:**
> I'd say ext4 should be default, FAT16 and FAT32 should not be available (obviously it should be supported on say pen drives, but not in the installer). Ext2, JFS, XFS and ReiserFS should be marked as "not recommended for new filesystems" maybe with a word such as "obsolete". Btrfs should be added and marked as experimental.
So a list like this:
```
Ext4 (recommended)
Ext3
Btrfs (experimental)
Ext2 (obsolete)
JFS (obsolete)
ReiserFS (obsolete)
```
Also, it might be unnecessary to even show those filesystems in the list( the ones marked experimental and obsolete) unless the user does something like press-and-hold ALT while starting the formatter (or similar)

Not FAT32, Its good to use as a shared partition between Windows and Linux.

---

### Post by Slug71 on 2009-04-28
> **edm1 said:**
> A cleanup??? The more filesystems the better. They don't get in the way and people shouldn't be changing from the default unless they know what they're doing.

I just dont see the point to having FAT16 and EXT2 in there.

---

### Post by Mehall on 2009-04-28
> **Slug71 said:**
> I just dont see the point to having FAT16 and EXT2 in there.

As just pointed out, it's needed if you want to make a partition for sharing with Windows.

and if you have FAT32, why not have FAT16?

---

### Post by Gina on 2009-04-28
Yes, I use FAT32 for sharing with Windows.  I found pen drives had to be FAT16 to use as boot device.  I presume this hasn't changed.

I still say leave it as it is with a choice - why change anything there?  Just default to the best current file system.

---

### Post by amano on 2009-04-28
Ext3 is dead. Ext4/Btrfs is the future. With 2.6.30+ ext3 is using an unsafe mode itself, thus there is no reason to stick with ext3. Let's hope that applications start to use fschk() more extensively to gain speed AND reliability (above all GVFS has to use it soon).

---

### Post by Mehall on 2009-04-28
ext4 is the future, yes, but ext3 is hardly dead.

---

### Post by SKLP on 2009-04-28
Why use FAT32 for sharing file in a dual-boot setup, when the NTFS works read-write? 
Fat32 could hardly be considered a modern file system.

---

### Post by Mehall on 2009-04-28
ntfs-3g fails if the drive is improperly unmounted from Windows, which is hardly ideal.

Also, we still offer ext2 when installing, why not offer these others?

---

### Post by SKLP on 2009-04-29
> **Mehall said:**
> ntfs-3g fails if the drive is improperly unmounted from Windows, which is hardly ideal.

Also, we still offer ext2 when installing, why not offer these others?Why would we offer ext2 for new installs? Ext4 with no journal is superior, AFAIK.

---

### Post by Simian Man on 2009-04-29
> **SKLP said:**
> Why would we offer ext2 for new installs? Ext4 with no journal is superior, AFAIK.

Yes but does the partitioner actually allow you to set flags like this when formatting?

---

### Post by super.rad on 2009-04-29
Yeah I'd say FAT16 and EXT2 could be removed without anyone missing them, but then again do they actually take up any extra space on the install disc? If not then not much point in getting rid of them

---

### Post by SKLP on 2009-04-29
> **Simian Man said:**
> Yes but does the partitioner actually allow you to set flags like this when formatting?It could, but I don't think it does atm.

---

### Post by nanog on 2009-04-29
btrfs is the future but its i/o performance is exasperatingly slow. ext4, however, is fun, fun, fun (15-30% performance boost on my nfs raid arrays).

and such a pity that gpl zealotry prevents us from mainlining zfs.

---

### Post by malachi1990 on 2009-05-02
You can on the alternater installer (at least on the jaunty alpha I tried).  When you get to the step just before writing the changes to disk, you can make custom changes, and i think you can set these flags from there, though I don't remember completely.

---

### Post by BlueSkyNIS on 2009-05-02
I made a mistake: I checked everything I DON'T use. :(

---

### Post by eyelessfade on 2009-05-02
As long as there isn't a size problem all should be included. And more even. Maybe hide them in a advanced tab? I use the following fs on my systems: ext3, reiserfs3, xfs and jfs. fat32 and ntfs is also used but that is more windows fault then mine.

last time I installed ubuntu (and reformated) from disk on one of my computer I was a bit frustrated that I could use the installer to set up my /home with xfs.

---

### Post by ghindo on 2009-05-04
> **nanog said:**
> and such a pity that gpl zealotry prevents us from mainlining zfs.With the acquisition of Sun by Oracle, who knows what's in store for ZFS. :)

---

### Post by artir on 2009-05-04
> **nanog said:**
> btrfs is the future but its i/o performance is exasperatingly slow. ext4, however, is fun, fun, fun (15-30% performance boost on my nfs raid arrays).

and such a pity that gpl zealotry prevents us from mainlining zfs.

Btrfs is in alpha state, wait for it to be finished.
I'll  kick ZFS's *** for sure.

---

### Post by Phreaker on 2009-05-04
ext4!

---

### Post by Slug71 on 2009-05-04
Judging from the poll and comments so far we should have:

FAT32
EXT3
EXT4(with an option to turn off journalling for SSD)
ReiserFS
XFS
replace JFS with ZFS
Btrfs when available.

---

