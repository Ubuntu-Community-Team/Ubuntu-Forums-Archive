---
title: "Accidental Format"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by JoE oH on 2010-11-28
Hey. I was putting ubuntu onto another computer and it asked for a swap partition. I assumed this meant it wanted some space on a partition to use for swap. Instead it formatted the entire partition (The windows one O.o) So all the documents and the OS are gone. But for 40gb-ish of space it appeared to format quickly. So I assume something might be recoverable. But its in the swap format now instead of windows. I would appreciate some help on how to recover some of my files :)

Joe

---

### Post by Rubi1200 on 2010-11-29
Hi and welcome to the forums :)

Sorry to hear about your troubles.

Whatever you try, do not write to the disk!

Instead using a LiveCD, boot the computer then download and install Testdisk on the CD.

Run it and try and recover the partition and/or data:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Good luck!

---

### Post by JoE oH on 2010-11-29
Thanks. Ill give it a shot :)

---

### Post by endotherm on 2010-11-29
for this kind of problem, testdisk is the best bet for unformatting. just make sure that you have a second hard disk, capable of storing the entirety of the formatted disk. do not attempt to recover data to the disk that it was lost off. 

if you need to look into other recovery methods, this page is very comprehensive:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

is the disk in question healthy? if so, the data should be reasonably easy to recover, (if it has not been overwritten too much), but if the disk is of questionable health, then the best bet is to make an image of it immediately, before attempting any type of recovery. otherwise the recovery operation might push the drive over the edge into full mechanical failure. had that happen myself last week. wouldn't want you to make the same mistake.

---

### Post by JoE oH on 2010-11-30
Thanks. Another issue is that TestDisk has no Swap partition option to restore. What should I do at this point?
Thanks

---

### Post by endotherm on 2010-12-01
> **JoE oH said:**
> Thanks. Another issue is that TestDisk has no Swap partition option to restore. What should I do at this point?
Thanks
are you saying you would like to recover teh swap? why would you want to do that? swap never has any data to be persistently stored, so you shouldn't miss anything there.

---

### Post by JoE oH on 2010-12-01
> **endotherm said:**
> are you saying you would like to recover teh swap? why would you want to do that? swap never has any data to be persistently stored, so you shouldn't miss anything there.

Im trying to recover a NTFS which got formatted to Swap.

---

### Post by endotherm on 2010-12-01
> **JoE oH said:**
> Im trying to recover a NTFS which got formatted to Swap.
just use gparted to remove the partition table (do not format anything, or create volumes within the drive). then tell testdisk to operate on the whole disk.

---

### Post by JoE oH on 2010-12-01
> **endotherm said:**
> just use gparted to remove the partition table (do not format anything, or create volumes within the drive). then tell testdisk to operate on the whole disk.

Sorry, could you tell me how to remove the partition table, i dont see an option :KS
Thanks

---

