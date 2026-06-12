---
title: "grub broke after installing updates/patches  Ub9.10"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by nicolaas3 on 2010-01-17
As suggested by Kansasnoob, I've openene a new thread. 
I've run the boot-info-script and the result file (Results.txt) has been attached bij this Tread.

---

### Post by Leppie on 2010-01-17
Hoi Nicolaas3,
you seem to have some fs error on your linux partition.
please do a check with fsck:
```
sudo fsck /dev/sdb2
```run it twice to make sure the issue has been resolved.

---

### Post by nicolaas3 on 2010-01-17
fsck doesn't to solve the problem. I still can't mount /dev/sdb2. See below

ubuntu@ubuntu:~/Downloads$ sudo fsck /dev/sdb2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb2: clean, 211864/5922816 files, 7599442/23673785 blocks
ubuntu@ubuntu:~/Downloads$ sudo fsck /dev/sdb2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb2: clean, 211864/5922816 files, 7599442/23673785 blocks
ubuntu@ubuntu:~/Downloads$ sudo fsck /dev/sdb3
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?
ubuntu@ubuntu:~/Downloads$ sudo mount /dev/sdb2 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~/Downloads$

---

### Post by ranch hand on 2010-01-17
sdb2 certainly looks screwed to me.  There is no uuid for it on the script results.

Would you run;
```

sudo blkid

```
just to double check that lack of uuid?

---

### Post by nicolaas3 on 2010-01-17
The results of sudo blkid:

 
ubuntu@ubuntu:~/Downloads$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DE7C248F7C24648D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="7ED0263FD025FDD1" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="1EBC287CBC285117" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="FECC22FDCC22AFB7" LABEL="000000" TYPE="ntfs" 
/dev/sdb5: UUID="14990c90-fc64-4c97-ad7a-da831b0fac6b" TYPE="swap" 
ubuntu@ubuntu:~/Downloads$

---

### Post by drs305 on 2010-01-17
You might be able to use TestDisk to analyze the partition. One of the things it can do is change the type of partition, which may be necessary since the system currently can't tell what it is.

Here is a good guide on using TestDisk:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

```

sudo apt-get install testdisk
sudo testdisk

```

---

### Post by Leppie on 2010-01-17
it may be some hw issue, try testing the hd's health with utils you can find on [Ultimate Boot CD]("http://www.ultimatebootcd.com/")

---

### Post by nicolaas3 on 2010-01-17
[FONT=monospace]Couldn't find package testdisk (see below)[/FONT]
[FONT=monospace]

ubuntu@ubuntu:~/Downloads$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

[/FONT]

---

### Post by drs305 on 2010-01-17
Before I posted, I checked and testdisk is in the *universe* repository, which is normally enabled. You can check to make sure you have the repository enabled via Synaptic, Settings, Repositories.

If you still can't find it, you can get it from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by kansasnoob on 2010-01-17
I have a dumb question. Why are you cd Downloads in all of your commands:

> ubuntu@ubuntu:~/Downloads$

Every command you show you've run you were running from the Downloads folder????????????

Like look what I just did:

> lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ 


But why would you be running those commands from the Downloads folder?

Close the terminal. Then reopen the terminal and go back to post #2 and start over.

---

### Post by ranch hand on 2010-01-17
> **kansasnoob said:**
> I have a dumb question. Why are you cd Downloads in all of your commands:



Every command you show you've run you were running from the Downloads folder????????????

Like look what I just did:



But why would you be running those commands from the Downloads folder?

Close the terminal. Then reopen the terminal and go back to post #2 and start over.
It is a good thing some one is watching.

Do this.

---

### Post by meierfra. on 2010-01-17
> But why would you be running those commands from the Downloads folder?
One can run "fsck" from any directory, won't make a difference. 


> sudo fsck /dev/sdb2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb2: clean, 211864/5922816 files, 7599442/23673785 blocks

This means that e2fsck is not aware of any problems, but did not actually run a file system check. Try

```
sudo e2fsck -fyv /dev/sdb2
```

---

### Post by nicolaas3 on 2010-01-17
I change from the download folder to another folder but it doesn't change anything.
I have run testdisk. No errors and wrote the partition tables to disk. But this didn't brought the solution. 
But somebody must know what should be the problem when I want to mount to /dev/sdb2 and I got the message " mount: you must specify the filesystem type "
Somebody who knows or can read the code of the " mount"  command, could say when one got that message.

---

### Post by ranch hand on 2010-01-17
The fact of the matter is that your entire sdb drive comes up with some real strange results in the boot script.

I would really like to see the results of the "sudo blkid" command.

I would also like to know how you partitioned the sdb drive.  Was it done from the live CD?  Was it done from sda?  Was it done from sdb?  Was gparted used?

---

### Post by nicolaas3 on 2010-01-17
The results of  sudo e2fsck -fyv /dev/sdb2:

buntu@ubuntu:~$ sudo e2fsck -fyv /dev/sdb2
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  211864 inodes used (3.58%)
     707 non-contiguous files (0.3%)
     156 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 187922/62
 7599442 blocks used (32.10%)
       0 bad blocks
       3 large files

  154947 regular files
   26742 directories
      68 character device files
      26 block device files
       0 fifos
     404 links
   30064 symbolic links (23768 fast symbolic links)
       8 sockets
--------
  212259 files
ubuntu@ubuntu:~$

---

### Post by nicolaas3 on 2010-01-17
The results of sudo blkid, after booting and reopening Terminal.
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DE7C248F7C24648D" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="7ED0263FD025FDD1" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="1EBC287CBC285117" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="FECC22FDCC22AFB7" LABEL="000000" TYPE="ntfs" 
/dev/sdb5: UUID="14990c90-fc64-4c97-ad7a-da831b0fac6b" TYPE="swap" 
ubuntu@ubuntu:~$ 

I Installed Unbuntu 9.10 from Live Cd and did the partioning with that procedure (Live CD).

---

### Post by ranch hand on 2010-01-17
Well now we know that the boot script was all right on that.

This seems, to me, to indicate the underlying problem of mounting the drive.  There is no uuid readable from that partition.  This seems to me to indicate a basic problem with that partition in identifying itself.

Someone may have, I hope so as I would like to know it, a better solution but I would back up any data from the Ubuntu in stall and start over with partitioning.

I would use the LiveCD and delete sdb2 and sdb3 (this would get rid of sdb5 too).  Create, using all that space, one extended partition.  Then create a small swap at the end of that (1Gb).  Then another logical at the beginning of the extended for your / (root) partition ext4 (15Gb).  Then make the rest of it another logical for /home partition ext4.

Then install using the manual option in the installer partitioner and designate sdb6 as / and sdb7 as /home.  sdb5 will automatically be picked up as swap.  The partition numbers above are assuming that you partition in the order that I gave, if not make note of the partition numbers.

When installation is done do not reboot.  Open gparted again and label your / and home partitions as it will make chrooting a lot easier if it is needed.  then reboot.

This will give you a cleaner partition table and a better installation.  The separate / and /home partitions make dealing with problems such as this one a lot easier on you and your data.

---

### Post by meierfra. on 2010-01-17
Your e2fsck output looks normal.  So there does not seem to be a problem with the file system. 

Your RESULTS.txt shows traces of Wubi. Did you used to have Wubi? Are you trying to convert Wubi to  regular Ubuntu?


Lets see whether you can mount /dev/sdb2 if you specify the files system type:


```
sudo mount -t ext4 /dev/sdb2 /mnt
```

---

### Post by nicolaas3 on 2010-01-17
The next command  did work! The mount succeeded and I can see and get my files But how to go on? So I can boot agian?
sudo mount -t ext4 /dev/sdb2 /mnt

---

### Post by drs305 on 2010-01-17
The next step you could try would be to assign the partition a UUID via tune2fs. Run the second command to see if the first one was successful.
```

sudo tune2fs -U random /dev/sdb2
sudo blkid -c /dev/null

```

---

### Post by meierfra. on 2010-01-17
Try drs305 suggestion first,  but I not sure it will make a difference.  I have seen  some rare case where random data on the first two sector of a partition can cause mounting problems. So I suggest to clear those  two sectors:

```
sudo dd if=/dev/zero of=/dev/sdb2 count=2
```

Be very careful with the "dd" command.   It should finish instantly. So if it runs for more than  a couple of second, kill the process with "Ctrl+c"

If none of this helps, could you tell us about the updates and patches your were doing before grub broke?

---

### Post by nicolaas3 on 2010-01-19
Hurray,

It works again. Thank you all for helping me.

It seems to me that the following command puts everything (the missing File System type) on the wright place again. 
I didn need to the command in #20

---

