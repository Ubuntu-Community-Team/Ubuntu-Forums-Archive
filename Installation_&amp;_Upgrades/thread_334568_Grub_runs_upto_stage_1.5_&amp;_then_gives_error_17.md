---
title: "Grub runs upto stage 1.5 &amp; then gives error 17"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2007-01-09
Hi all, 
 I have one 80 GB HDD which has Windows XPSP2 (NTFS based) & Ubuntu 6.06 upgraded to Ubuntu 6.10 (ext2). It had GNU GRUB 0.97 running underneath it all. Everything was running fine & suddenly yesterday it gave me error 17. Looking in Grub Legacy came to know tht error 17 means :- 

_[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)_

17 : Cannot mount selected partition 
   This error is returned if the partition requested exists, but the 
   filesystem type cannot be recognized by GRUB. 

 Now in such should I re-install everything or is there some sorta hack which can make it good without re-installing the whole thing. Its a dual-boot box.

             Any idea when we should be able to see Grub2 being used in  main-stream distros.

   Also if I need to find if my partition is ok or not, how or wht steps/procedure should I do to find out the same. Looking forward to help/assistance

---

### Post by hal10000 on 2007-01-09
Before re-installing you may boot from live cd and then try to mount your ubuntu partition. Post wether this works or not.

There might be some kind of damaged partition, but with a little luck you may be able to fix the problems, e.g. using the command fsck.ext2 (or fsck.ext3) - use this only while the partition is **not** mounted.

Are you really sure it is ext2, not ext3?

---

### Post by pegasusgr on 2007-01-09
I'm having exactly the same problem. I booted from livecd and tried to mount my main partition both as ext2 and ext3 and this is what i got:

```
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/hdc1 /old
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```and 
```
ubuntu@ubuntu:/$ sudo mount -t ext2 /dev/hdc1 /old
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```my dmesg|tail output is:
```
[17185619.196000] Buffer I/O error on device hdc, logical block 7
[17185620.908000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17185620.908000] hdc: dma_intr: error=0x40 { UncorrectableError }, LBAsect=63, sector=56
[17185620.908000] ide: failed opcode was: unknown
[17185620.908000] end_request: I/O error, dev hdc, sector 56
[17185934.184000] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17185934.184000] hdc: dma_intr: error=0x40 { UncorrectableError }, LBAsect=63, sector=63
[17185934.184000] ide: failed opcode was: unknown
[17185934.184000] end_request: I/O error, dev hdc, sector 63
[17185934.184000] EXT3-fs: Can't read superblock on 2nd try.


```then, i decided to run fsck.ext3 and fsck.ext2 and that's what I get:

```
ubuntu@ubuntu:/$ sudo fsck.ext2 /dev/hdc1
e2fsck 1.39 (29-May-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdc1
Could this be a zero-length partition?
```I hope this helped because I NEED SOME HELP!!

---

### Post by hal10000 on 2007-01-09
@pegasusgr:
it seems that your disk has a (hardware) damage. --->{ UncorrectableError }
You might run the [COLOR="Red"]testdisk [/COLOR]tool and see what it can do.

Try the [COLOR="Red"]badblocks [/COLOR]command too.

Maybe you can do a low-level formatting on your disk, but i can't help you in that case, i have no expierience with low-level formatting.

---

### Post by clypp on 2007-01-11
I have the same error.  The thing is with me, I know roughly what the problem is but I do not know how to correct it.  I am somewhat of a Linux n00b.

I upgraded Dapper to Edgy through the update manager.  It worked fine but is always said at boot "Swap space signature could not be found"  I think this will cause my computer to run slow even though it was not too slow.  Looking online I saw others with the problem and someone recommended something like this command line, "sudo mkswap /hd4"

It returned that hd4 was 15GB so this was actually my Ubuntu partition.  After this I found I could not write to disk anymore.  I rebooted to try clear this but now I get Error 17 at GRUB. (Dual boot with XP)  

Anyway I can change my partition from being considered swap to ext3? (IIRC I formated to ext3) The command took no time at all so few file were changed.

---

