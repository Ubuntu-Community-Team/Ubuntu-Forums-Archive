---
title: "Too many primary partition's"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by nalmeth on 2006-05-25
I'm trying to install Dapper after resizing my old (defunct) breezy partition. I resized it with gparted liveCD. My table looks like this:
hda = 200 Gigs
```
[hda1-EXT3(primary)=116 gigs] + [hda4-FREE SPACE(somehow primary)=32 gigs] + [hda3-FAT32(primary)=48 gigs] + [2 swap partition's, 1.5 gig's each]
```

I had formatted it as reiserfs just for fun, and thought the installer could handle formatting it, and setting it up.

The guided partitioner doesn't give me an option to use this partition, so I go manual. I format the partition as EXT3, but I get red-screen:
```
NO ROOT FILESYSTEM DETECTED
``` weird, I'm sent back to manual partitioning. 
So I format it, let it be blank space.
Go back to guided partitioning, and pick "Largest Continuous Space"
I get red-screen again, saying:
```
TOO MANY PRIMARY PARTITIONS
``` It format's it as EXT3, and leaves a 1.2 gig chunk of unusable space.
So I delete the partition again, and it's back to square one.

What am I missing here? Where have I gone wrong?

---

### Post by simonn on 2006-05-25
You can only have 4 primary partitions.

However, if one of the primary partitions is an extended partition you can have other partitions in this e.g. my partition scheme is roughly:

sda1 - ubuntu
sda2 - Another linux distro 
sda3  - extended
sda4 - swap

The extended partiton contains:

sda5
sda6
...
sdaN

Will the installer let you use reiserfs? Breezy certainly did not allow me to use XFS, so I had to install it using ext3, then move it off to another partition, reformat the partition, move it back and do the initrd thing.

---

### Post by nalmeth on 2006-05-25
I did not know this, thank you simonn

I picked reiserfs in gparted just for the hell of it, intending to format it later anyway.

I will have to rethink this setup I guess, but so far I only have 3 primary partitions, shouldn't I be allowed to add another? can I change the fat32 to logical (it's a data partition)?

---

### Post by daschl on 2006-05-25
for example a good setup (for me :D)

hda1 /boot
hda2 / (ubuntu)
hda3 / (gentoo)
hda4 extended
hda5 swap
hda6 /home

if you only have 2 primary partitions and you create a extended one, then the logical partitions start with 5 (regardless how many primary partitions you have)

---

### Post by Sef on 2006-05-25
> I picked reiserfs in gparted just for the hell of it, intending to format it later anyway.

I like reiserfs.

> I will have to rethink this setup I guess, but so far I only have 3 primary partitions, shouldn't I be allowed to add another? can I change the fat32 to logical (it's a data partition)?

You should be able to set up one more primary partition.  AFAIK, to change a primary to a logical partition, you have to reformat the partition.

---

### Post by nalmeth on 2006-05-25
Thanks for responses guys.
I tried the install again this morning before work.
I got the same "probably too many primary partition's" message, but went ahead anyway. 
Then I got a "No swap partition created" I said screw it, I'll set it up later. I've got 512 meg's so I'll be OK for now.
The install was going OK, until the screen went black during base installation.
I sighed, and went for some breakfast. Came back, same screen. I hit enter twice (remembering grub message, and reboot confirmation), and lo-and-behold the CD popped out. Hit enter again, and rebooted into my dapper system.

Mixed success I guess. Since I'm not using the *slow* swap, the system is quite fast, but I'm not doing very arduous task's at this point. 

I didn't even try to mount the other partition's, will try tonight after work.

All I have to do now is setup the swap partition.

Anyone have quick access to a link outlining this process? If not no biggie, I'll STFW :D

Thanks again guys

---

### Post by simonn on 2006-05-25
[QUOTE=nalmeth]
Anyone have quick access to a link outlining this process? If not no biggie, I'll STFW :D
[/QUOTE]

It is just a matter of creating a partition (say 1Gb) and using mkswap.

e.g.

```

mkswap /dev/hda4

```

Then add it to fstab:

e.g.

```

...
/dev/hda4      none            swap    sw              0       0
...

```

---

### Post by nalmeth on 2006-05-25
Awesome, thanks for that simonn

I already have an extra swap partition hanging around anyway (from previous dapper install).

You just made my life a lot easier.

Cheers

---

