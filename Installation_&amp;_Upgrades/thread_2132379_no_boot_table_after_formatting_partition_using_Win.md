---
title: "no boot table after formatting partition using Windows cd"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by guymic on 2013-04-04
Hello everyone.
I was trying to fix this problem for a long time now, with no luck.

There are two problems, which are related. I'll start from the beginning:
I'm using Ubuntu 12.10 on a 250Gb drive which is partitioned to 4 partitions. Looking like this, from the left:      
~60Gb FAT   |     ~60Gb EXT4 (ubuntu)     |   2Gb SWAP     |    NTFS (media files)

I want to install Windows on the first (left) partition.      After reformatting the FAT part. using Windows live-cd, my computer no longer recognize this part. and the 
boot/part. table is gone (it was located on the part. naturally). I reformatted because Windows won't let me install on that part. Will get to that later.

So now, this is what's going on:

-Ubuntu DOES work, and I also tried to use "boot-repair" to write the boot table again (no luck. It did know ubuntu is located far from the start of the drive though).
-GParted does NOT recognize the partitions. It says the whole drive is "unallocated".
-on Ubuntu boot, before it loads, it says something like: "can't mount drive xxxx,   press 's' to skip mounting   or 'M' to manually mount the drive".
 it refers to the FAT partition of course.
-when trying to mount from within Ubuntu, it says: 
  "Mount is denied because setuid and setgid root ntfs-3g is insecure with the external FUSE library....."
   although after searching the net it looks like this message doesn't relate to my problem, but Ubuntu doesn't know the real one.
-I ran "testdisk" to correct the table. this is what it says, only after using the "deeper search" (it looks to me much more complicated than the real thing):
[ATTACH=CONFIG]240956[/ATTACH][ATTACH=CONFIG]240955[/ATTACH]

This is pretty much all I know. The problem is that without GParted, I don't know how to fix/reformat that partition.
I would also like to know why couldn't I install windows. I think it's because I can't do more than 4 part.s, so windows can't either.
I thought maybe I should remove the SWAP, extand the Ubuntu part., and then try. But I can't do it with this problem:(
I also understand that it looks pretty dumb to part. the drive so much, and use 2 OS's on the same drive. But thats what I have right now, can't buy new one:\

Thank you very much. I'm sure you need more info. Just tell me what to look for and I'll post it.

---

### Post by guymic on 2013-04-04
Maybe that would help?
Using the "advanced" tools of "testdisk" I get this. Too afraid to try repair FAT :)
I also try rebuilding but it said "can't find sector size" or something like that.

[ATTACH=CONFIG]240957[/ATTACH]

---

### Post by darkod on 2013-04-04
Not sure if repairing the FAT is OK or not. You have to be careful when amnipulating partitions and disks with windows tools, especially XP tools. Windows knows about windows only, and doesn't care about other partitions.

Maybe it would have been better to use Gparted and format the first partition into ntfs, then you could have simply installed XP on it. I don't understand why did you have FAT partition at all, that's ancient filesystem.

Are you sure the first partition was 60GB and FAT? The testdisk deeper search seems unable to find FAT partition towards the start of the disk, but it does seem to find ntfs partition from cylinder 0 to cylinder 5124 and then your linux partition continues at 5124 until 12802, then the swap continues until 13072 and then the last ntfs continues until 30401, the end of the disk. That's what it looks like from the numbers but I can't be 100% sure especially since you seem convinced the first partition was FAT.

In the deeper search output you can highlight the second ntfs partition and hit P to try listing files on it. If it opens it and lists files, most probably the partition was really ntfs.

Or maybe this reported ntfs is a result of you formatting it as ntfs with the XP cd. Even in that case it would be good to write that partition table so that testdisk recovers it, then you can install XP and then restore grub2 on the MBR.

If you agree with this, in the deeper seach output you would need to highlight the four partitions one by one and use the left/right arrow to change the characteristic into:
the NTFS partition starting at 0 and ending at 5124, change the D in front into *
the Linux starting at 5124 ending at 12802, change D into P
the Linux swap, change D into P
the last NTFS starting at 13072 ending at 30401, change D into P

If you write that table it should make all partitions into primaries and the first one with the boot flag.

Before changing their characteristics you can use the P to list the files and check if the partitions are read fine, except the swap partition which wouldn't have any files stored anyway. But you can check the other three. Don't forget the "new" ntfs might be blank after you formatted it.

If the listing of files works, it should be safe to write that partition table.

---

### Post by guymic on 2013-04-04
wow thank you so much!! With your explanation I can even understand what I was doing!:P
You were right, it isn't FAT. I think it was long time ago, or maybe I accidently reformatted it as such when trying to install Windows.

For now it seems all is fine! It did say at startup that an other partition (i think the media) is not ready, but i pressed 's' and all seems to work fine.
GParted gets it right now as well.

Thanks again, so much. the bigger problem seems to be solved! I'll wait to see if anyone can help with the installation (or maybe I should do it in another post?) and then mark this one as solved.

Is there any chance you know how to install Windows on that 40Gb NTFS(yes, it is not 60 as I remembered)? Is the problem really that it can't make more partitions ? (Windows seems to need an extra 100Mb partition or something like that)

---

### Post by darkod on 2013-04-05
The win7 installer will only try to create the small 100MB partition if you make partitions with it. If installing on existant partition, it should work our fine.

Open Gparted from your ubuntu installation or live mode, and simply format sda1 as ntfs. Then boot with the win7 dvd and when it asks where to install, select the 40GB partition and that should be it.

Have your ubuntu live cd at hand since you will need to repair grub2 after windows deletes it.

As for sda4, the other ntfs partition, maybe something changed but as long as it's readable it's OK. You might need to modify fstab if you had it there and according to what the change was. For example, since the partitions on the disk don't have to be in order, like sda2 can be before sda1, maybe the partition had another device name and now with the new table it has different one so it doesn't match in fstab.

In any case it should be easy to sort out as long as the partition is readable and the data is there.

PS. Maybe it was better to make the linux partitions logical during the recovery of the table with testdisk. I didn't want to complicate it further and thought since the partitions were primary before it's better to recover them as primary again. If we had made them logical, it would have allowed you one more primary. But you can install win7 without it too, like explained above. I have used that procedure.

---

### Post by guymic on 2013-04-07
Thank you so much.   The mount issue probably has to do with the fact that I changed the fstab (i think it was it) so all drives will auto mount, and now something's changed.
I'll get to that sometime, it's not that important apparently.

About the Windows. I tried what you said (just like the other times) and I keep getting this same message (at the bottom):

[ATTACH=CONFIG]241051[/ATTACH]


Maybe making the Ubuntu part. logical would help?

thx!!

---

### Post by darkod on 2013-04-07
Strange. The boot flag seems there too, that's why it says System for partition 1. Try formatting it with the win7 installer, but only formatting it, not deleting it. Click on Driver Options and it will show option to format it. See if it will allow you to install after that.

For making partitions 2 and 3 logical, I guess it's best to use fixparts. There is a .deb to download and install, and after that you only start it in terminal. You can do all that from live mode too.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

That program can convert primary partitions to logical as soon as all partitions are next to each other physically on the disk. Then write the new table and after you reboot, the partitions will be logical. Win7 will be able to make the small partition after that if it still insists on it.

---

### Post by guymic on 2013-04-07
hey.
I tried formatting with Windows of course. It doesn't help...
here's the output of fixparts. looks like I can't make2,3 logical, right?


[ATTACH=CONFIG]241057[/ATTACH]

whats annoying is that I already did it before (but there was no SWAP, that's whats new).
Should I just remove swap? my RAM isn't that great. 2.8 GB

---

### Post by darkod on 2013-04-07
Hmm, strange. You should be able to make then logical since they are both toegther in the middle of the disk. I wonder if this is an issue after you needed to use testdisk to recover the partition table. The partitions are not seen as they need to be, and that might influence the win7 installer too.

I wonder if you use testdisk again, the quick serach should be enough this time since the partitions are not deleted. You can change the P in front to L or what ever it was for logical. At the bottom of the screen in testdisk you have the different charcteristic options. I think L was for logical.

If you make partitions 2 and 3 logical and save the partition table like that it should work.

---

### Post by guymic on 2013-04-07
nope, testdisk doesn't allow it either. looks like reformatting the 3 first part.s is inevitable:(

---

