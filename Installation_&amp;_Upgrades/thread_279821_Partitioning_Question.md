---
title: "Partitioning Question"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by eskimokid on 2006-10-18
What format does Kubuntu need ?
NTFS or others ?
after creating a partition on windows does it need to be format before kubuntu using it ?

---

### Post by bulldog on 2006-10-18
Ubuntu uses ext3.

Just make enough free space and leave it unallocated [not formatted]

When you come to the partitioner let it use the unallocated space and it will be split up by Ubuntu.

---

### Post by eskimokid on 2006-10-19
I did leaving free space around 30GB and i tried more then once from installing kubuntu but everytime when the installation reach step 5 which is doing partitioning stuff...i choose to edit partitioning by myself and after I choosing that, it pop out and tell me that qtparted is crashed and asked me to choose automatic partitioning. 

i try to type qtparted in the terminal but the error said that baddevice 168, QtParted is unable to load.

so what should I do ?
if I choose the automatic partitioning, will all the data install into my C Drive but not into the free space ?

---

### Post by Sef on 2006-10-19
Did you md5sum the disk to make sure it downloaded correctly?  If you did, it could be a bad burn.  Also sometimes the Desktop CDs have had problems installing.  You might want to try downloading the [alternate cd]("http://www.kubuntu.org/download.php").  It is text based, but very easy to follow.  Just use the default option to install.

---

### Post by eskimokid on 2006-10-19
you meant that its the application crashed but not cause of the partitioning problem ?
ok, thanks guys;)

---

### Post by az on 2006-10-19
> **eskimokid said:**
> I did leaving free space around 30GB and i tried more then once from installing kubuntu but everytime when the installation reach step 5 which is doing partitioning stuff...i choose to edit partitioning by myself and after I choosing that, it pop out and tell me that qtparted is crashed and asked me to choose automatic partitioning. 


It is far safer to use the automatic partitioning.  Avoid partitioning yourself.

The automatic partitioning is very safe.

---

### Post by eskimokid on 2006-10-19
is it ?
but I wish to make 3 partition... 1 for swap 1 for system and 1 more for data
if I make auto partitioning...will it save into a used driver ? like my C drive

---

### Post by Kateikyoushi on 2006-10-19
Then it would be best to create a separate /home partition.
1 system, a swap and one /home for data.
It isn't really hard to partition the drive. You can find instructions with photos [here]("http://www.psychocats.net/ubuntu/installing").

---

### Post by eskimokid on 2006-10-19
oh...okay thanks 
but if I choose to edit myself it will take the unlocated/freespace or it will take the first scsi drive ?

---

### Post by Kateikyoushi on 2006-10-19
You can select where do you make the partitions.

---

### Post by randell6564 on 2006-10-19
> **eskimokid said:**
> oh...okay thanks 
but if I choose to edit myself it will take the unlocated/freespace or it will take the first scsi drive ?
I suggest that you read-up on S-ATA devices in relation to Linux before you start trying to partition your drives manually.

---

### Post by eskimokid on 2006-10-20
I tried to install it again...
and, the same problem is having, QtParted is crashed. I do selecting auto-partitioning but after installing kubuntu, my monitor black-out and it effect my windows xp also. My windows xp cant boot after that.And I have to format my windows XP also. Eventhough i re-download and burn 1 more iso image cd [desktop amd-64 version] and i do md5 checking and there's no problem. 

izzit i did something wrong on partitioning ?
i got C, D, E drive in for my windows xp and i leave around 35gig unlocated. so where's the problem I'm having ? 
As what randell said, what's relation between sata and linux ?

---

### Post by Kateikyoushi on 2006-10-20
Most likely you do not have to reinstall windows, you can restore the MBR.
If it didn't work out this way try to install after removing the windows drive.

---

