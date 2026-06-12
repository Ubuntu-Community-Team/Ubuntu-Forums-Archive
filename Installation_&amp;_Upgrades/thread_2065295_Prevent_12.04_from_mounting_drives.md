---
title: "Prevent 12.04 from mounting drives"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by Tranas on 2012-10-01
12.04 configured to dual boot with XP/2000. Have a functional Windows fakeraid array that I do not want Ubuntu to access either read or write.  Is there a simple way to do this? TIA

---

### Post by sandyd on 2012-10-01
post the output of 
```

sudo fdisk -l
sudo blkid

```

You can add entries to fstab to prevent their mounting.


For example, adding the noauto flag like this will prevent automounts

Example:
```

UUID=6fe347eb-2318-4bd2-9131-879ead0b2dad /               ext4    errors=remount-ro,noauto 0       1
```

---

### Post by Tranas on 2012-10-02
Not clear how the following will help, but the requested info follows [the tx2300 is not attached to keep Ubuntu from trashing the raid]....

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 
sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63f220e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    25173854    12586896    7  HPFS/NTFS/exFAT
/dev/sda2        25173855  1911574349   943200247+   7  HPFS/NTFS/exFAT
/dev/sda3      1911574528  1931106303     9765888   83  Linux
/dev/sda4      1931108350  1939300351     4096001    5  Extended
/dev/sda5      1931108352  1939300351     4096000   82  Linux swap / Solaris


and 


/dev/sda1: LABEL="OS" UUID="0EB4E248B4E231BF" TYPE="ntfs" 
/dev/sda2: LABEL="Data" UUID="EAD4F9E8D4F9B6C3" TYPE="ntfs" 
/dev/sda3: UUID="370a94d7-2021-4df5-9114-05dc3abc413e" TYPE="ext4" 
/dev/sda5: UUID="2d72f6aa-05b5-49f7-a0c3-e39fe68cc10c" TYPE="swap"

---

### Post by darkod on 2012-10-02
Ubuntu never mounts any windows partition by default, unless you tell it to do it. So, it will never mount them.

As for accessing the array, if that's what you meant, if ubuntu is on the fakeraid also then it has to access it so it can work, but it will not mount the windows partition which are also on the fakeraid.

Why are you under the impression that it's mounting them and you need to prevent it?

---

### Post by Tranas on 2012-10-02
Since Ubuntu sees fakeraid array as two separate drives, I want to prevent a windows fakeraid array from being mounted by Ubuntu unless *forced* to do so by editing some configuration setting.

Ubuntu is not on a fakeraid drive - it is on SDA3. 

I want to DENY Ubuntu access to any attached fakeraid set. I want to leave a fakeraid card and drives attached and functional and ONLY accessible via the dual boot Windows OS. 

Boot Windows - you see the raid [array] as a single drive. Boot Ubuntu - you do NOT see the raid array even if you look for it or try [without editing some configuration setting] to mount it.

I am not under the impression of anything. Ubuntu sees and will mount an attached Windows fakeraid array as two separate disks. That is the behavior I want to prevent by making it as difficult as possible.

---

### Post by darkod on 2012-10-02
Ubuntu does see a fakeraid array correctly as single disk but if you activate it. That's how it can install on a fakeraid otherwise it would be impossible.

Even if it sees the two disks as separate, until you try to mount them it doesn't touch them.

If the question here is preventing users from attempting to mount any other disk, there is probably a way to limit their permissions. Otherwise, separate disks or not, if anyone actually tries to mount it, it will mount.

I would start investigating how to block mounting of disks with relevant permissions. I'm sure Google will throw something up.

---

### Post by Tranas on 2012-10-02
Thanks for the suggestions.

I understand that there is limited support for fakeraid, however [as best I have been able to find] installing such support is not part of the 12.04 standard install disk and is a truly byzantine process at best. 

Seems the folks at Ubuntu have little interest in supporting such cards, although if they spent as much time working on compatibility as they do ragging on how useless fakeraid is [to them], it would make for a better user experience for the 2% that try Ubuntu. YMMV

I certainly may have missed something obvious, and if you have a link to a simple way of adding a driver to 12.04 for a Promise TX2300 raid card, such would be appreciated.

The permissions solution would be unlikely as a solution - seems there is quite a bit more granularity in Windows permissions for NTFS than Ubuntu supports, too much likelihood of conflicts.

I find exceedingly odd that when attempting to install Ubuntu on drives that had previously been part of a fakeraid set, Ubuntu install sees neither the drives nor their partitions - will not install because you cannot manipulate the partitions from the install disk. [You helped me solve that issue with the sudo dmraid_-E_-r_/dev/sda command - TYVM ;)] 

So evidently, Ubuntu can hide Raid drives from itself but not from itself.... lol

NRFPT

---

### Post by darkod on 2012-10-02
I can't say for that exact model of card, but the fakeraid (package dmraid) IS included in the standard live cd. In fact, because it is included it often creates confusion since people can see the array and try to install on it but the live cd is not so good at installing grub2 to the array. It often fails and without grub2 you can't boot ubuntu.

The Alternate cd has much more raid support, including support for more cards (my assumption) and is recommended for both fakeraid/hardware raid and software raid.

So, when installing on fakeraid it's much better to use the alternate cd right away, but even using the standard one can help if it sees the array and installs. If grub2 fails to install you can add it from a live session later.

Those are basically the options.

Since you already have installed ubuntu on separate disk, and it does contain dmraid (it should by default), it should be able to activate the array with:
sudo dmraid -ay (or -ya I can never remember tham)

After that fdisk and parted should show the /dev/mapper/.... device which is what fakeraid is called.

But all of this has nothing to do with blocking the mounting of the array. That's a separate subject.

Or you were only afraid of mounting it as single disk and you are OK with mounting it as array?

PS. When I was talking about permissions, I didn't mean permissions on the ntfs partitions. We don't want to mount those, right. I was talking about permissions what a user can or can not do. If we find some permissions (or limitation rather) saying something like "does not have permission mounting devices" that would be a block to mount any disk with any partition, single disk or fakeraid.

---

### Post by Tranas on 2012-10-02
For me, the basic reason for having a fakeraid array is to save data in the event of disk failure. That TX2300 handles that quite well. You will know about a failed array before anything boots and you can deal with the issue as you choose. If you need the WebPAM utility, you just boot Windows and use it.

If Ubuntu can see that particular raid array as a single drive [as you described as „activated“] that would be great - particularly if it would be as simple as a single line in Terminal.

As for the semantics of *array* - I mean the *array* to be 2 drives acting as single visible drive configured as raid-1. 

If Ubuntu can see that on the local machine by using the dmraid {-a|--activate} {y|n|yes|no} I am good with that. 

12.04 obviously sees the card and can execute dmraid commands. 
When Ubuntu is freshly installed it sees the set as 2 single SATA drives [attached to a card] on the local machine. I am NOT good with that, as that configuration will be trashed in short order by Ubuntu by simply copying a file from either drive in the *array* - triggering a 8+ hour rebuild of the 1.5 TB array.

So if I understand correctly -

Ctrl+Alt+T
sudo dmraid -ay
shut down
install card with functional [in Windows] *array*
boot to Ubuntu 12.04

and that should make the *array* visible as a single drive in Ubuntu?

---

### Post by darkod on 2012-10-02
No, you run it with the card installed, it needs to detect it with the array on it. No need to disconnect anything.

Now I am not sure if there was a space between the -a and the 'y' for yes, but try without and then with space:
sudo dmraid -ay
sudo dmraid -a y

After that the /dev/mapper/... device should appear in ubuntu.

---

### Post by Tranas on 2012-10-02
TYVM

If any issues, I will post

---

