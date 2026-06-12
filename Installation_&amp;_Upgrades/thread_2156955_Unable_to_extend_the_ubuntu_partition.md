---
title: "Unable to extend the ubuntu partition"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by ChildRoar97 on 2013-06-23
I just freed up 50GiB from my Windows partition and I was wanting to extend the Ubuntu partition so I have more space for programs/file and such.

Not when i went ahead and booted from my starup disk i created, and open GParted and set the operation to "Move /dev/sda4 to the left and grow it from 11.71 GiB to 61.71 GiB" I was met by an error message. 

I have no idea why it not letting me extend the partition. I hope someone could help.

```
GParted 0.12.1 --enable-libparted-dmraid

 Libparted 2.3
  [TABLE]
[TR]
[TD="colspan: 2"] **Move /dev/sda4 to the left and grow it from 11.71 GiB to 61.71 GiB**  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda4  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda4
start: 463,732,734
end: 488,280,063
size: 24,547,330 (11.71 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] move partition to the left and grow it from 11.71 GiB to 61.71 GiB  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 463,732,734
old end: 488,280,063
old size: 24,547,330 (11.71 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]requested start: 358,873,088
requested end: 488,278,015
requested size: 129,404,928 (61.71 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *Unable to satisfy all constraints on the partition.*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *Can't have overlapping partitions.*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

---

### Post by grahammechanical on 2013-06-23
A screenshot of the partitioning scheme as shown by Gparted would help. But I will make a guess. I think that the Ubuntu partition (sda4) is inside an Extended partition. First enlarge the Extended partition to take up the unallocated space left by shrinking the Windows partition. That will create unallocated space inside the extended partition which sda4 can be expanded into.

Good guess? May be.

Regards.

---

### Post by ChildRoar97 on 2013-06-23
I try to move the unallocated space to the Extended partition named dev/sda4
so that under /dev/sda4, it lists the swap space and the ext4 ubuntu partitionand the unallocated space

I may even be doing it wrong. I'm first trying to move the unallocated space into sda4 and then extend the sda6 partition

[IMG]http://i.imgur.com/583ZJ3j.png[/IMG]





And then after i click "apply all operations" i get the error message i posted.

I can expand the Ubuntu partition after getting the space inside sda4, but the only problem is getting the space into sda4

---

### Post by oldfred on 2013-06-24
You have to move the extended partition left into the unallocated to get the unallocated into the extended.

You then will have to move swap left, then move ext6 left and can only expand it right.
Moving partitions takes time, but they are smaller so not too bad. I generally do not like moving partitions left as any power failure for any reason will corrupt data. So good backups are always important.

---

