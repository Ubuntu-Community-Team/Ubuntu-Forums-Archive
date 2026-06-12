---
title: "How to modify the UUID of an NTFS or FAT32 partition?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2007-06-21
Does anyone know how to modify the UUID of an NTFS or FAT32 partition without destroying the contents?

Okay, if I could back up and then recover the contents how would I do it?

---

### Post by kidders on 2007-06-22
Hi there,

I'm not sure dosfstools provides a way of doing that. It's an odd request though ... can I ask why you want to do it?

---

### Post by moshuptrail on 2007-06-22
Why I want to:  Some time ago I cloned two partitions.  One was FAT32, the other NTFS.  Now, with Edgy and Feisty all but insisting on UUID designations in fstab the cloned partitions are causing problems.  Ubuntu does not expect duplicate UUID's and some modules behave badly when they are encountered.  For example, the Edgy upgrade fails to convert the fstab to UUID format.  I think I saw a note somewhere that the /dev/hdxx designations in fstab are no longer supported in Feisty.  Indeed, I've been having problems that I've narrowed down to the use of /dev/hdxx in fstab.  (fsck gets confused during boot-up resulting in Error 8 failures)

In short, I'd like to be using UUID designations in fstab for all drives, but can't until I can eliminate the duplicates.

See also:
[http://ubuntuforums.org/showthread.php?t=479848](http://ubuntuforums.org/showthread.php?t=479848)
and
[http://ubuntuforums.org/showthread.php?t=472443](http://ubuntuforums.org/showthread.php?t=472443)

---

### Post by kidders on 2007-06-23
Hey again,

I was afraid you were going to say something like that. :-( If it were me, I would probably just reformat one of the filesystems (silly as that seems), because by the time I'd figured out a smarter way of doing it, I'd be finished already. Hopefully another poster will chime in with more ... ehh ... sensible advice in the next hour or two though.

Incidentally, I would be horrified if any Linux distro dropped support for /dev node names any time in the next decade or so. It'd be a daft thing to do imo ... so I hope Ubuntu isn't planning it. Feisty is certainly happy to address block devices that way in /etc/fstab.

---

### Post by reiki on 2007-06-23
you can still use the /dev/node notation in fstab and unless you're doing a LOT of repartitioning all the time, the /dev/node designations will work. I have modified the UUID of cloned partitions, but they were not NTFS or FAT32 .

My advice would be to stick with the /dev/node style for those NTFS and FAT32 partitions.

---

### Post by moshuptrail on 2007-06-23
Than you reiki and kidders.   I recognize both names as coming from the thread "UUID Adventure"  which I have read and re-read.  I think I'll just use /dev/node in fstab for the non-Linux filesystems.

In reviewing my research on UUID vs. /dev/node designation I believe I have mis-interpreted something I read.  What is no longer supported is the use of /dev/hdxx to refer to IDE drives.  They are now mapped as /dev/sdxx.  I think that's what the document was trying to tell me.

Then, I was re-reading the man-page for fstab.  I can still use /dev/dsxx, but I can also use UUID or Label=<label> to identify a filesystem.  So how is UUID different from Label=<label>?  (UUID must be hex?, UUID is unique, but Label= is easy and readable)

In fact, why not use Label=<label> if your hardware config may re-map a drive to a different device.  Sure UUID is "unique", but then non-unique might be useful; slipping in a different /home filesystem for example.  Label="Slash Home" or something like that.

fstab entry:
Label="Slash Home" /home ext3 defaults 0 2

I assume you can't use Label= in menu.lst for grub though.

---

### Post by pxwpxw on 2007-06-23
man tune2fs

it says u can set uuid. not tried here though.

---

### Post by kidders on 2007-06-23
> **moshuptrail said:**
> So how is UUID different from Label=<label>?Labels, /dev paths & UUIDs are just examples of properties that a device may have. Hard disks also have other properties (such as input voltage, cylinder count, and so on), any of which can be used to identify them. Naturally, only some of these are of practical use in a file such as /etc/fstab.

Many filesystems support labelling. Labels can be anything you want, within the restrictions imposed by the designers of the filesystem you're using. UUIDs (universally unique IDs), by contrast, are typically lengthy numbers (as you pointed out), often generated using the **uuidgen** utility.

Why not use labels? No reason, afaik. You can write your /etc/fstab any way that suits your needs.

> **pxwpxw said:**
> man tune2fs**tune2fs** (as its name suggests) is only useful for Ext filesystems.

---

### Post by pxwpxw on 2007-06-23
yep sorry, should hav red the post properly

---

### Post by Howard Kaikow on 2007-06-23
> **moshuptrail said:**
> Does anyone know how to modify the UUID of an NTFS or FAT32 partition without destroying the contents?

Okay, if I could back up and then recover the contents how would I do it?

I'm not certain, but Partition Magic may allow you to change the drive's signature.
Perhaps, so does Gparted, or somthing like that?

---

### Post by kidders on 2007-06-23
> **Howard Kaikow said:**
> I'm not certain, but Partition Magic may allow you to change the drive's signature.
Perhaps, so does Gparted, or somthing like that?
That's an interesting idea. Gparted is an *exceptionally* poor application, but Partition Magic might be just the ticket. :-)

Alternatively, you could always go for the low-tech approach. Just as a little experiment, I dumped the first few k's of one of my filesystems to a file & took a look with a hex editor...
```
$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=jfs
ID_FS_VERSION=
ID_FS_UUID=38c3a49c-6432-4397-a35e-1298e48e0da8
ID_FS_LABEL=Feisty
ID_FS_LABEL_SAFE=Feisty
$ sudo head -n 5120 !$ > ~/test
$ ghex2 !$
```Sure enough, the filesystem's UUID (38c3 a49c ...) was easily visible. Anyone have an opinion on what would be wrong with simply altering the UUID as it appears in the bytecode, and dumping the result back onto the filesystem itself? Something like a **dd if=~/test of=/dev/sda1** ought to do the trick (provided appropriate precautions regarding block boundaries were taken, and the target filesystem remained dismounted throughout). Have I lost my marbles?

It seems infuriating to be forced to reformat a filesystem (as I previously ... and somewhat lazily ... suggested), simply because of a shortcoming in dosfstools, just to side-step the adverse affects of having cloned a filesystem at some time in the past.

**Edit:** My screenshot is of an Ext3 filesystem, which is a slightly more straightforward case than JFS. The UUID is e55c0b72-4c8d-4dc3-b1b4-ac4836ab07ae.

---

### Post by kidders on 2007-06-23
Sorry for replying to myself, but I had a free few minutes, and decided to go and do the above, with a view to finding a reliable stock solution to issues such as this in the future, and I thought it might be helpful to post the results...

**Procedure**[LIST=1]
[*]Create a small test vfat filesystem.
[*]Modify it's UUID.
[*]Check whether there are any unforseen side-effects.[/LIST][B]
Detail[/B]

[COLOR=DarkRed]**Warning:** *Even the slightest mistake (either by me or you!) in the following can cause **serious damage**. Please don't actually try this unless you know what you're doing.*

[/COLOR] Become root, to avoid having to constantly type **sudo**. _Extreme_ caution is required, when doing this. Note the final '$' in the prompt changing to a '#', to remind me what I've done.```
kidders@x2:~$ sudo su
root@x2:/home/kidders#
```Create a new partition, rescan my partition tables (to avoid having to reboot at this point), and format a small vfat filesystem.```
# cfdisk /dev/sda

[SIZE=1][COLOR=DarkRed] [ I created /dev/sda8 ][/COLOR][/SIZE]

# partprobe
# mkfs.vfat -n "Test" /dev/sda8
mkfs.vfat 2.11 (12 Mar 2005)
# vol_id !$
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=467D-63BC
ID_FS_LABEL=Test
ID_FS_LABEL_SAFE=Test
```As you can see, the automatically generated filesystem UUID is **467D-63BC**. I want to change it, but I'm not too keen on the idea of writing directly onto /dev/sda8 with a text editor/hex editor, so ...```
# mount /dev/sda8 /mnt/test
# echo "I sure hope I live through this" >/mnt/test/dummyfile
umount /mnt/test

# head -c 4096 /dev/sda8 > dump
khexedit dump
```First, I make a dummy file in the test filesystem, just for the sake of it. Then I dump exactly one block of the filesystem, and open it in a hex editor (see screenshot). It is critical that the target filesystem be dismounted first. I found the disk label ("Test") 47 bytes into the file, immediately preceeded by the UUID in reverse byte order... **bc 63 7d 46**. I decided to change the first (ie least significant) byte from "bc" to "bb", and dump the result back onto my hard disk.```
# dd bs=4096 if=dump of=/dev/sda8
1+0 records in
1+0 records out
4096 bytes (4.1 kB) copied, 0.000425 seconds, 9.6 MB/s
# vol_id /dev/sda8
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=467D-63BB
ID_FS_LABEL=Test
ID_FS_LABEL_SAFE=Test
```Wheee! I have the new UUID. But did I do any damage?```
# dosfsck -r /dev/sda8
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:bb/bc
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Perform changes ? (y/n) y
/dev/sda8: 2 files, 2/248510 clusters
# dosfsck -r /dev/sda8
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda8: 2 files, 2/248510 clusters
```So, the filesystem detects my tampering, and I am offered the choice to retain or reverse the changes. Naturally, I could have altered the boot sector backup as well, but why bother! Just to be paranoid, a final **dosfsck** confirms there is no damage. Now, I might as well take a look at my dummy text file...```
# mount /dev/sda8 /mnt/test
# cat !$/dummyfile
I sure hope I live through this
```Anyhow, it looks as though a quick, clean, error-free manual UUID change is possible. I figure a shell script could be designed to do this for a user who, for one reason or another, wants to change the UUID of an MS filesystem. Any thoughts?

---

### Post by moshuptrail on 2007-06-23
> Any thoughts?

Somebody has way too much time on his hands.  ;)

Seriously, it's impressive.  But, like you said, risky.  Now that I understand that I can use /dev/node, or even LABEL= in fstab instead of UUID I can manage my duplicate UUID's just fine!

---

### Post by Howard Kaikow on 2007-06-23
> **kidders said:**
> That's an interesting idea. Gparted is an *exceptionally* poor application, but Partition Magic might be just the ticket. :-)

Alternatively, you could always go for the low-tech approach. Just as a little experiment, I dumped the first few k's of one of my filesystems to a file & took a look with a hex editor...
```
$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=jfs
ID_FS_VERSION=
ID_FS_UUID=38c3a49c-6432-4397-a35e-1298e48e0da8
ID_FS_LABEL=Feisty
ID_FS_LABEL_SAFE=Feisty
$ sudo head -n 5120 !$ > ~/test
$ ghex2 !$
```Sure enough, the filesystem's UUID (38c3 a49c ...) was easily visible. Anyone have an opinion on what would be wrong with simply altering the UUID as it appears in the bytecode, and dumping the result back onto the filesystem itself? Something like a **dd if=~/test of=/dev/sda1** ought to do the trick (provided appropriate precautions regarding block boundaries were taken, and the target filesystem remained dismounted throughout). Have I lost my marbles?

It seems infuriating to be forced to reformat a filesystem (as I previously ... and somewhat lazily ... suggested), simply because of a shortcoming in dosfstools, just to side-step the adverse affects of having cloned a filesystem at some time in the past.

**Edit:** My screenshot is of an Ext3 filesystem, which is a slightly more straightforward case than JFS. The UUID is e55c0b72-4c8d-4dc3-b1b4-ac4836ab07ae.

I would not do that.

AFAIK, the  uuid is the same as the signature used by windows.
A number of apps rely on that value, in the case of Windows, it's stored in the registry.

I'd only change the signature using standard means: reformatting, using an image backup that allows for chaning the signature, using a partition management program that might allow the changing of the signature, and maybe others,

Like any GUID-like value, it's dangerous to manually change the critter unless one knows ALL the possible effects.

---

### Post by kidders on 2007-06-23
> But, like you said, risky. Now that I understand that I can use /dev/node, or even LABEL= in fstab instead of UUID I can manage my duplicate UUID's just fine!Hehe.

I agree. Having said that, it'd be nice to be able to say "Here... run this" to the next guy to encounter your problem, but at least your immediate issue is solved. :-)

---

### Post by kidders on 2007-06-23
> **Howard Kaikow said:**
> A number of apps rely on that value, in the case of Windows, it's stored in the registry.True, but reformatting the filesystem (at least in Linux) would leave the Windows registry in the lurch anyway.

Point taken however ... this kind of manual manipulation isn't always safe. :-)

---

### Post by Howard Kaikow on 2007-06-23
> **kidders said:**
> True, but reformatting the filesystem (at least in Linux) would leave the Windows registry in the lurch anyway.

Point taken however ... this kind of manual manipulation isn't always safe. :-)

When dealing with FAT32, NTFS on a multiboot system, reformatting of partitions has to be done when booted from Windows to reduce the damage.

---

