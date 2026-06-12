---
title: "Need suggestions partitioning two HD"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by polype on 2010-10-27
Hi,

I'm a beginner: 2 months with Ubuntu

Got a new computer to-day

hardisk's
1. Western Digital 600GB SATA III 10000RPM 32MB VelociRaptor
2. Western Digital 1TB SATA II 7200RPM 32MB Caviar Blue

8 GB RAM DDR3
AMD Phenom II X4 965 3,4 GHz AM3

I want to install Ubuntu 10.04 AMD 64 bit only NO other OS
-maybe later a Virtual Box with Windows to run a language course
and eventually photoshop CS5-
And I also  would like to reserve a space to test other versions of Linux.

I'm a bit (a lot in fact!) lost with the partitioning /root /swap /home etc...

How would you partition these 2 disks for yourself ?

Thanks for your time
P.

---

### Post by scott1541 on 2010-10-27
Personally I would partition the larger of the two hdd's into a main partition and a swap partition. Then if I were going to be testing other OS's then I would partition the smaller hard drive into a storage drive with a smallish (20-30gb) partition for testing, no need to go over the top with the size of the testing partition.

EDIT: 
Thinking about it, with the speeds you have I might go with all partitions on the 10k rpm one with the 7200 rpm one used for storage.

---

### Post by for.i.am.root on 2010-10-27
Hi:

Personally I would set it up using cryptoLuks and encrypt both. Then use an external key to decrypt them using /etc/crypttab and /etc/fstab to auto decrypt when the key is inserted.

Barring that option I would do this:

I would use a small ( < 1GB ) partition for /boot
~20 GB for /
Seems how it's a desktop you don't need double ram for swap (Unless you want hibernate?) so I would do 1/2 RAM
And the rest /home.

/dev/sda1 512MB     /boot
/dev/sda2 20480MB   /
/dev/sda3 4096MB    SWAP
/dev/sda4 REST      /home

I would set up the second hdd in a similar fashion for testing diff OS's.

My current set up is (Asus EEEPC 1005HAB):

/dev/sda (internal 500GB HDD)
/dev/mapper/root ~10GB
/dev/mapper/swap ~5GB
/dev/mapper/home ~450GB

/dev/sdb (external 16GB USB)
/dev/sdb1 ~15.9GB  spoof
/dev/sdb2 ~128MB   /boot
/dev/sdb3 ~1MB     /hidden cryptoluks key

I then boot my laptop using the key (which requires manual decryption using my password) and then a keyscript to automagically decrypt /home and /root. Swap is a random key generated on boot (dd if=/dev/urandom of=swapkey bs=1 count=256). Then I umount the drive.

Thanks!

---

### Post by oldfred on 2010-10-27
I do not think you need a separate /boot for a desktop. If you do the raid or lvm then it may be better to have it.

Advantages & disadvantages of LVM - srs5694
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I used to prefer a separate /home and it is a good idea if that is where most of your data will be. But now I create /data partition(s), and agressively move all data folders out of /home. It makes /home easy to backup as it is small.

I also like to have many 20-25GB system partitions (I then can mount the /data into any or all of them where I could not do that with /home). I have my old Ubuntu, current Ubuntu and next (usually about beta & later) Ubuntu for testing, making sure it works for my system. I still have some more 20GB partitions as I plan on trying some other distributions.

I have three drives and scatter my installs around on the drives and have MBR set to boot the same drive as the install. That way any one drive failure will not prevent me from booting. I also have bootable liveCD & USB installs.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by polype on 2010-10-28
> **oldfred said:**
> 
Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
[l]("http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html")

One partiion then..?

Tank you all for your comments.

But I'm still lost, I'm a near total beginer (girl, 17 years old and not blond).
I was really looking for somebody" to do the work for me" :) , meaning a list of partitions for my two drives. 

I know you probably will say that it depends what I want to do.
I explained it in my initial message.

I want, for the time been, a system that works  the best possible way.
And with the time, I expect to become more efficient with Ubuntu, trial and error a.s.o...

Also, sorry for my poor english (I'm french speaking).

Amitiés,
P.

---

### Post by oldfred on 2010-10-28
Everyone has different opinions on partitioning. Choose one that is reasonable and after you have used it, you will find you want something different. I usually buy another drive every 3 or 4 years, so then I reorganize & change things around.

My standard recommendations.
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

No separate /boot unless old computer, server, encrypted or btrfs system partition.

In your case I would create a 25GB / (root), a 8GB swap since you have 8GB of RAM and lots of hard drive space( I still think it is large) and the rest as /home. You can then on the second drive create partitions for /data and perhaps a backup partition. I do not like to have extremely large partitions.

You also do not have to fully partition initially. I still have part of my latest drive unallocated. If you do that just make sure you have the extended partition at the end of the drive as that would be where you could add partitions. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by polype on 2010-10-30
> **oldfred said:**
> 
My standard recommendations.
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

No separate /boot unless old computer, server, encrypted or btrfs system partition.

In your case I would create a 25GB / (root), a 8GB swap since you have 8GB of RAM and lots of hard drive space( I still think it is large) and the rest as /home. You can then on the second drive create partitions for /data and perhaps a backup partition. I do not like to have extremely large partitions.

You also do not have to fully partition initially. I still have part of my latest drive unallocated. If you do that just make sure you have the extended partition at the end of the drive as that would be where you could add partitions.

Thanks for your suggestions, but it is still a lot confusing for me.
Could I abuse your time and ask you to write a detailed partition table for me in the form "/dev/hda , /dev/hda1 ...a.s.o." for my TWO drives, and with the names "main" or "extended" .
In the form of a table.

The best posible, in your opinion, something you would do for yourself.

Something that should keep me going for the next months.
I do not know anybody at school or in my family who could help me, they all use Windows.

Do not hesitate to tell me I'm abusing.

Regards,
P.

---

### Post by polype on 2010-10-30
[QUOTE=polype;10047142]main&quot; or &quot;extended&quot; .
In the form of a table.

 correction:  and also where "primary" and where "logical"...  P.

---

### Post by oldfred on 2010-10-31
Under MBR(msdos) partitions you can only have 4 primary partitions, but you convert one primary to an extended partition which can have many logical partitions. sda1 thru sda4 will be primary. sda5 & up will be logical inside the extended. I have extra future roots as I install new versions of Ubuntu in a new root and keep 3 copies in rotation. That way I have an old system to boot if necessary, my current system and a place for the next version to test on my system. I usually start about beta, but reinstall RC & final even though I could update from beta, just to learn about installing. While grub does not use boot flag I would still put a boot flag on sda1 as some BIOS will not let you boot without it.

One suggestion using MBR.
600GB drive:
sda1 25GB Mountpoint / primary beginning ext4
sda2 25GB none primary beginning ext4   (Future root for another system)
sda3 remaining drive extended
  sda5 (all but 8.5GB) /home ext4
  sda6 8.5GB swap
1TB drive:
sdb1 25GB Mountpoint primary beginning ext4 (Future root for another system)
sdb2 25GB none primary beginning ext4   (Future root for another system)
sdb3 remaining drive extended
  sdb5 approx 200GB /data ext4
  sdb5 approx 200GB /backup ext4
  sdb7 8.5GB swap
Rest unallocated for now, after you have used system you may want to reorganized and this will give space.

I also suggest labels for partitions so you can tell what they are. You can do all of this with gparted from a liveCD. Then use manual install and choose sda1 as / (root) and sda5 as /home, it will find swap on its own.

Since you have two larger drives and no plans for windows, you may also want to consider gpt rather than MBR. gpt allows up to 128 primary partitions. If you want to try gpt, use it on your 1TB drive but also create an additional small bios_grub partition as sdb1 of 8MB.
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

Attached is a screenshot of my gpt drive that I am testing gpt on.

---

### Post by polype on 2010-11-01
Hi OldFred,

Thanks very much for all the hard work, it will help me a lot.
I'm a bit ashamed that I had to ask for this, but I was really lost.
Nevertheless, it was very sweet from you.

Regards,
P.

---

