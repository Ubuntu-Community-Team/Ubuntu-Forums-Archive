---
title: "can't resize partition"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by tommaso3 on 2014-08-19
Hello!
I installed Xubuntu 14.04 on my notebook after formatting it completely. So i have only the partition ext4 with xubuntu and a partition for swap, on a disk of 250 gb.
I want to install another so in dual boot with xubuntu, but i can't resize the main partition in order to create new space, even if there's a lot of free space. I've tried with the partion tools, in live mode, of xubuntu, ubuntu, lubuntu and kubuntu; and i have also tried to reinstall, after formatting, x/k/l/ubuntu. But i still have the same problem:  i resize with gparted the main partion in order to create new free space (at the right of it), then click "apply". After 2 minutes of "shrinking file system", i get the message "impossible to apply the changes".
Why? THere's no apparent reason! thank you for your answers!

---

### Post by plucky on 2014-08-19
> **tommaso3 said:**
> Hello!
I installed Xubuntu 14.04 on my notebook after formatting it completely. So i have only the partition ext4 with xubuntu and a partition for swap, on a disk of 250 gb.
I want to install another so in dual boot with xubuntu, but i can't resize the main partition in order to create new space, even if there's a lot of free space. I've tried with the partion tools, in live mode, of xubuntu, ubuntu, lubuntu and kubuntu; and i have also tried to reinstall, after formatting, x/k/l/ubuntu. But i still have the same problem:  i resize with gparted the main partion in order to create new free space (at the right of it), then click "apply". After 2 minutes of "shrinking file system", i get the message "impossible to apply the changes".
Why? THere's no apparent reason! thank you for your answers!

Post a screenshot of your gparted window.

When you run gparted,it has to be from a Live DVD/USB as it won't allow you to resize a mounted partition.

If it is inside an extended partition you have to turn swap off.Swap partition is mounted on a Live DVD/USB.

Good Luck

---

### Post by tommaso3 on 2014-08-19
I'm using kde partition manager (from live usb, and with swap off), it's the same of gparted. This is the situation:
[IMG]http://i60.tinypic.com/zt9dag.png[/IMG]
And this is error i get:
[IMG]http://i59.tinypic.com/149o9so.png[/IMG]
I tried to use the command that is suggested in the error message (to repair the file system), but it's useless.

---

### Post by yancek on 2014-08-19
You have a 228GB partition (sda1) and then an Extended partition of 4GB which contains the 4GB swap partition so you need to shrink sda1.  The error you posted shows that it is unable to move the partition sda1 to the right by 6.84GB and fails.  You need to move it to the left to create free space after sda1.  If you try to create free space at the beginning by moving to the right you may end up with an unbootable computer.  It's pretty difficult to read your images so I'm not sure I am reading this correctly.

---

### Post by tommaso3 on 2014-08-19
No..i don't understand why that thing is written in the error message, but i was trying to free the space at the end (so at the right) of the main partion, not at the beginning. I don't understand what means the thing of "6.84 gb".

---

### Post by Daniel_Evans on 2014-08-19
If you don't mind wiping all the data you could just start over and create all the partitions before you install, that might be easier.  But I'm confused about that error message as well.  Seems to come out of no where.

---

### Post by Daniel_Evans on 2014-08-19
Yeah I get what he's saying now, try moving to left instead of right like you've been doing.

---

### Post by tommaso3 on 2014-08-19
So i shoulf try to free the space at the left? This will not delete all the file system?

---

### Post by yancek on 2014-08-19
> So i shoulf try to free the space at the left? This will not delete all the file system?         

No.  That is what I though you were doing and suggested not to do as it 'could' render your machine unbootable.  According to your post immediately after my other post, you were doing it correctly but  obviously something went wrong.  Shrinking from the right where you have no data is going to be much less dangerous.  If you use GParted on a Live CD/USB, you can enter the size you want the partition in MB or you can use the slider.  Moving the mouse to the right of the box at the top of the Resize window when you have the two tiny horizontal arrows which you can slide left.  This is usually what I do and don't have problems with it.  If you are doing that and it is not working, I don't know what else the problem could be.

---

### Post by plucky on 2014-08-19
The error you are getting is because you are trying to resize the start of a partition. (/dev/sda1)

You have to select the rear of the partition if you want to shrink the partition. The un-allocated space will then be at the rear of /dev/sda1.

Once the un-allocated space is the size you want,you will be able to create another partition.

Good Luck

---

### Post by plucky on 2014-08-19
[ATTACH=CONFIG]255657[/ATTACH] [ATTACH=CONFIG]255658[/ATTACH]

You can only resize the rear of a partition.

If you try to resize the start of the partition you will get the error

Good Luck

---

### Post by tommaso3 on 2014-08-20
@Plucky Thank you for your reply, but that's exactly what i am trying to do: i am trying to resize the end of the partition, the part before the swap to be clear. This is the reason why i don't understand that error message.
I show you better the situation on gparted. As you can see, im doing it correctly, apparently.
[IMG]http://i59.tinypic.com/2drxjix.png[/IMG]

And these are all the details of the error, maybe they can be useful. Even if im not resizing the start of the partition, as you say the error says that i am resizing the file system,why?
```
GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
 Libparted 2.3
  [TABLE]
[TR]
[TD="colspan: 2"] **Shrink /dev/sda1 from 228.89 GiB to 136.72 GiB**  00:04:13    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda1
start: 2048
end: 480012287
size: 480010240 (228.89 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sda1 for errors and (if possible) fix them  00:00:11    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***e2fsck -f -y -v -C 0 /dev/sda1***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
                                                                               
      218844 inodes used (1.46%, out of 15007744)
         202 non-contiguous files (0.1%)
         183 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 179668/45
     4295712 blocks used (7.16%, out of 60001280)
           0 bad blocks
           1 large file

      151533 regular files
       23045 directories
          57 character device files
          25 block device files
           0 fifos
           6 links
       44173 symbolic links (39039 fast symbolic links)
           2 sockets
------------
      218841 files
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]e2fsck 1.42.9 (4-Feb-2014)
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] shrink file system  00:04:02    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***resize2fs -p /dev/sda1 143360000K***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]Resizing the filesystem on /dev/sda1 to 35840000 (4k) blocks.
Begin pass 2 (max = 2821446)
Relocating blocks             XXXXXX----------------------------------[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]resize2fs 1.42.9 (4-Feb-2014)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
Please run 'e2fsck -fy /dev/sda1' to fix the filesystem
after the aborted resize operation.[/I][/TD]
[/TR]
[/TABLE]
[/TD]
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

### Post by plucky on 2014-08-20
> resize2fs 1.42.9 (4-Feb-2014)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
Please run 'e2fsck -fy /dev/sda1' to fix the filesystem
after the aborted resize operation.

I think you have a badblock somewhere in the file system that is causing the resize to abort.

You will have to get rid of that badblock before you can continue.

The [Ultimate Boot Cd](http://www.ultimatebootcd.com/) has a number of utilities for testing various hard drives.

Also look at the command line tool **badblocks** from a terminal window.

Or a complete format and re-install might fix the problem.

Good Luck

---

### Post by tommaso3 on 2014-08-21
Ok, as i understand, to fix bad blocks i must format all the disk...but i'm not sure that i want to do that! So i think that will give up and install only one os on the disk.  But thank anyway for your replies, you have been very nice!

---

### Post by yancek on 2014-08-21
> Ok, as i understand, to fix bad blocks i must format all the disk

No, you don't.  You need to run the command shown in the output:  Please run 'e2fsck -fy /dev/sda1' to fix the filesystem, the part in single quotes.  Might need to preface it with sudo.  Anyhow, that what is being suggested and of course not from the installed system but from a Live DVD or flash drive.

---

