---
title: "Unwanted install over ntfs partition: testdisk finds ntfs but wouldn't recover"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by kakao on 2007-12-30
First of all let me say I have done some reading already but that didn't lead to a solution for me; among others that were:
[http://ubuntuforums.org/showthread.php?t=478149](http://ubuntuforums.org/showthread.php?t=478149)
[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)
[http://ubuntuforums.org/showthread.php?t=397631](http://ubuntuforums.org/showthread.php?t=397631)
[http://ubuntuforums.org/showthread.php?t=478149](http://ubuntuforums.org/showthread.php?t=478149)

My situation:
I installed Ubuntu on a friends Laptop with XP installed (NTFS) and was going to use the resize option which did the job for me before. This time though I don't know what went wrong but I ended up with Ubuntu installed on top of that very NTFS partition formated as ext3 and swap (the defaults I guess, I don't have the exact info any more but it used the whole drive). I didn't realize that XP partition was missing untill I booted freshly installed Ubuntu from hard drive for the first time. I don't think any changes have been made to the disk since than as I've booted from Live CD ever since.

After deleting all partitions via cfdisk (see below) fdisk -l sais:

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b7323fb

   Device Boot      Start         End      Blocks   Id  System

testdisk says:
Disk /dev/sda - 99 GB / 92 GiB - CHS 12137 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 11759 254 63  188924337
D HPFS - NTFS              0   1  1 12136 254 63  194980842
D Linux Swap           11760   1  1 12136 254 63    6056442

I imaged the whole hard drive via dd_rescue right after I notied XP was missing:
dd_rescue /dev/sda /media/usb/dd.img

Testdisk, when I continue Enter -> Search! tells me there is a deleted ntfs partition:
D HPFS - NTFS        0 1 1 12136 154 63 194980842

But when I select that partition and press Enter I get "No partition found or selected for recovery". Do I do something wrong? Or is there really no way to recover that partition not even partly even though testdisk shows it? I would guess testdisk finds some back up inode table or such somewhere on the drive. So I thought that should be enough to restore that partition?!? Also I can not get a file listing using 'C'.

Most texts talk about some "Deeper Search" option which I cannot find (eg. [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)). Is that because of older versions (I'm using 6.6 and 6.8) of testdisk or am I going the wrong way?

Then I deleted ext3 and swap partitions in hope for testdisk to show me more options. I guess that was stupid thinking. Anyway, nothing has changed since then.

I then manually edited the partition table via sudo fdisk to match data listed by testdisk, i.e. the whole disk as one partition with type 07 (HPFS/NTFS). Now testdisk lists it right from the start but still wouldn't list files. Right now I cannot reboot to watch boot messages nor what's beeing said after a reboot and thus fdisk's changes have taken effect.

What are my options? I would really like to give the owner of that laptop at least part of his data back (on which I'm working with other tools on a copy of that image I "ddrescued") if not a working XP partition! And thus really appreciated advise! Thanks heaps in advance!

---

### Post by Pumalite on 2007-12-30
You can take it to a Hard Drive Recovery Shop. Very expensive.

---

### Post by kakao on 2007-12-31
> **Pumalite said:**
> You can take it to a Hard Drive Recovery Shop. Very expensive.

Thanks, Pumalite, for your answer. What can they do what I cannot do? I mean, don't they use software just like I do maybe just other software? Please excuse my bullishness but I'd rather not give up yet.

Cheers.

---

### Post by Craigus on 2007-12-31
Try Get data back (it's windows software, so you would have to connect the laptop drive to a windows machine with an adaptor):

[http://www.runtime.org/]("http://www.runtime.org/")

The free trial version shows you what can be recovered. To get the data, you have to buy the product.

---

