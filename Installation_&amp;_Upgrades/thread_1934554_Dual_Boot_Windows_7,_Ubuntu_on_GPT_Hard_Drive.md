---
title: "Dual Boot Windows 7, Ubuntu on GPT Hard Drive"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by Vulgotha on 2012-03-02
I can provide the details here and I even know what's wrong.. Just not on how to fix it. 

My 1TB hard drive is GPT, which has alot of compatibility issues with various OS's. Windows 7 was tricky to install when I first got this PC but I resolved that problem within an hour or two. This was  a year ago.

Since then I've tried tackling installing Ubuntu twice. Each time the installer will boot up, detect a 10000MB (you get the gist) NTFS partition... With absolutely nothing written on it. In reality Windows takes up roughly 600GB of the 1TB hard drive. 

Ubuntu will not grant me any option other than to take the *whole *thing,  or various partitioning options. All of which are dangerous in my eyes since the OS cannot detect Windows. 

Just last night I created a separate EXT2 250GB partition from Windows  7. Took hours. This morning I go in to see if Ubuntu will at least  recognize that partition... Nope. Still 1TB of free space on an NTFS  filesystem. 

So how do I go about dual booting Ubuntu and Windows 7 on a GPT hard drive with Windows already installed on it? 


Please keep in mind I want to** Dual Boot. **Not install Ubuntu as an app using Wubi, or use VMware/etc. 

Other details: 
Both Ubuntu and Win7 are 64 bit editions.
PC has 12GB of DDR3 1600 Vengeance RAM.
Intel i7 950 processor (quad, 8 threads)
MSI motherboard

---

### Post by darkod on 2012-03-02
If no partitions are shown on the disk, it might mean some error or corruption in the partition table. Windows often ignores errors but linux doesn't.

Have you tried listing your partitions with parted, like:

sudo parted /dev/sda print

Also, try running fixparts on the disk, it might find something and it usually fixes smaller problems.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Vulgotha on 2012-03-02
> **darkod said:**
> If no partitions are shown on the disk, it might mean some error or corruption in the partition table. Windows often ignores errors but linux doesn't.

Have you tried listing your partitions with parted, like:

sudo parted /dev/sda print

Also, try running fixparts on the disk, it might find something and it usually fixes smaller problems.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Well, it will list one partition- NTFS. But it has no idea how much space it's using.

Or is that not what you meant?

---

### Post by darkod on 2012-03-02
Does it say it is 1TB NTFS partition, or you are saying it's NTFS because you know?

The word "free" might also mean unallocated space, which is the symptom when it doesn't recognize any partitions, it says you have the total disk unallocated (or free).

But in order not to guess, see what the parted command prints out, and post it here.

---

### Post by Vulgotha on 2012-03-02
> **darkod said:**
> Does it say it is 1TB NTFS partition, or you are saying it's NTFS because you know?

The word "free" might also mean unallocated space, which is the symptom when it doesn't recognize any partitions, it says you have the total disk unallocated (or free).

But in order not to guess, see what the parted command prints out, and post it here.

It's telling me it's NTFS.

---

### Post by darkod on 2012-03-03
Then you have a single 1TB ntfs partition taking up the whole disk. Maybe there is only 600GB data on it and the rest is free, but that doesn't matter. You need unpartitioned space not belonging to any partition so that ubuntu can create partitions with its own filesystem. You will need to shrink the 1TB ntfs partition using win7 Disk Management.

If you are in doubt, and to double check, I will say again. Run the parted command I suggested and it will show all the partitions on the disk, their sizes and filesystems. We can't help guessing around.

---

### Post by Vulgotha on 2012-03-03
> **darkod said:**
> Then you have a single 1TB ntfs partition taking up the whole disk. Maybe there is only 600GB data on it and the rest is free, but that doesn't matter. You need unpartitioned space not belonging to any partition so that ubuntu can create partitions with its own filesystem. You will need to shrink the 1TB ntfs partition using win7 Disk Management.

If you are in doubt, and to double check, I will say again. Run the parted command I suggested and it will show all the partitions on the disk, their sizes and filesystems. We can't help guessing around.

No, no. I've already partitioned a huge swath (250GB) to a new partition that is EXT2 that has no space taken up.

Ubuntu cannot even recognize that partition exists. It still says 1TB of NTFS free. 

I think I mentioned that above.


Also, I'm not 'guessing' around. I've already used the Ubuntu boot disc to stream the OS and I used two Ubuntu disk management tools- both report that there is only, and I repeat, ONLY 1 partition. 1TB NTFS free.

It's evident you haven't been reading my posts. The OP mentioned that I created this secondary EXT2 partition and that Ubuntu did not detect it.

I also stated that "it is telling me it's NTFS" in direct response to your comment stating I should use the disk management utilities in Ubuntu. I had already performed this check on both Ubuntu and Windows prior to posting a thread here.

---

### Post by darkod on 2012-03-03
Hey man, I am only trying to help.
You wrote three long posts instead of posting one simple result of parted.
I asked for parted because some ubuntu disk tools doesn't work correctly with gpt. For example fdisk. I am not sure about the Disk Utility or Gparted since I have never used them with gpt (I have only msdos tables).
On top of that, you did say you created ext2 partition but from windows. With what tool? Windows can't do that by default. I wouldn't put too much faith in windows creating ext2 partitions, but it's up to you if you want to use that approach.

Bottom line, parted understands both msdos and gpt tables and couldn't hurt if you post the results here so people that want to help can have a look. Who knows, you might even be surprised if it shows something different that other tools showed you.

---

### Post by oldfred on 2012-03-03
If you have only one NTFS partition and are booting Windows you can not be using gpt. With gpt and Windows you have to boot with UEFI. Then you have an efi partition, a Windows boot partition and the main install. Only with MBR can you have one partition although Windows 7 still normally installs to a 100MB boot partition and a main install.

So as Darko suggested we need from the Ubuntu liveCd a list of partitions so we really know what we are dealing with. I typically include the s parameter to be in sectors but that is not vital now.

```
sudo parted /dev/sda unit s print
```

---

### Post by Vulgotha on 2012-03-03
> **darkod said:**
> Hey man, I am only trying to help.
You wrote three long posts instead of posting one simple result of parted.
I asked for parted because some ubuntu disk tools doesn't work correctly with gpt. For example fdisk. I am not sure about the Disk Utility or Gparted since I have never used them with gpt (I have only msdos tables).
On top of that, you did say you created ext2 partition but from windows. With what tool? Windows can't do that by default. I wouldn't put too much faith in windows creating ext2 partitions, but it's up to you if you want to use that approach.

Bottom line, parted understands both msdos and gpt tables and couldn't hurt if you post the results here so people that want to help can have a look. Who knows, you might even be surprised if it shows something different that other tools showed you.

Gparted output:

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? yes                                                               
Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
OK/Cancel? ok                                                             
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

ubuntu@ubuntu:~$

---

### Post by darkod on 2012-03-03
I don't know all the details about gpt but from what I have seen this can show up if the disk was used (or it came with) a gpt table and you created a new blank msdos table. Windows deletes the main gpt table and creates a msdos, but it doesn't create the backup gpt table. In these cases linux gets confused if the table is msdos or gpt and what is true or false.

You seem to know your computer. Are you using msdos or gpt table? If you are using msdos and the problem is that windows didn't delete the backup gpt table, fixparts (mentioned earlier) can fix this. Just run it, it detects that you are using msdos but that you have backup gpt table and will ask you if you want to delete it. That should sort out the issue.

If you are using gpt it seems something got corrupted. Not sure what's best to do in that case.

---

### Post by oldfred on 2012-03-04
It looks like you had the gpt table and when installing Windows in MBR mode it deleted the primary gpt table.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

