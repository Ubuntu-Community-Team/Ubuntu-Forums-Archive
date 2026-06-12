---
title: "Unable to format partition in 8.04 LTS"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by trp on 2010-05-11
Hi everyone  I have a Dell mini 9 with a 16GB SSD.  At one time I had Hackintoshed it to run OS X.  Went back to original OS(Ubuntu 8.04 LTS).  Had some issues installing 8.04, apparently MBR was lost, or corrupted, so had to re-install grub and was able to complete the install.  The issue is under partition ed. it shows dev/sda1 flagged as boot, with a yellow triangle, file system unknown, size 23.5 MB.  When you double click the partition it shows status as unmounted, reason 1.  file system damaged, 2. file system unknown to gparted, 3. no file system available (unformated).  So I decided to try to formate the partition with ext2, or ext3 it fails with no detailed info. as to why it has failed.  There is also no swap partition showing up?  Any ideas as to why this partition seems to be untouchable?  When you right click the partition the options are delete, format, and manage flags.  I am afraid to delete partition as this is flagged with boot, and cannot format.    Any help would be appreciated.  Thanks in advance.    Tom

---

### Post by srs5694 on 2010-05-11
Please post the output of the commands "sudo fdisk -lu" and "df -h" when typed at a command prompt. (Note that that's a lowercase -LU, not a digit -1u; and there's a space between "df" and "-h".) Please put the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string to improve legibility. These commands will just show us what you've got in terms of partitions and working filesystems.

---

### Post by trp on 2010-05-11
Here is the output. First on id sudo fdisk -lu               

Disk /dev/sda: 15.4 GB, 15434883072 bytes 
255 heads, 63 sectors/track, 1876 cylinders, total 30146256 sectors 
Units = sectors of 1 * 512 = 512 bytes
 Disk identifier: 0x0002944d     

    Device  Boot       Start                  End              Blocks          Id    System 
 /dev/sda1   *                    63                48194               24066          83     Linux 
/dev/sda2                        48195    30137939    15044872+      83     Linux 



tom@tom:~$ df -h 

Filesystem                         size      Used     Avail    Use%    Mounted on 
/dev/sda2               15G      3.0G     11G      23%      / 
varrun                    1009M   108K    1009M   1%       /var/run 
varlock                   1009M   0          1009M   0%      /var/lock 
udev                      1009M    44K      1009M   1%      /dev 
devshm                  1009M   56K      1009M    1%     /dev/shm 
lrm                         1009M   1.7M     1007M   1%     /lib/modules/2.6.24-27-lpia/volatile gvfs-fuse-daemon 15G 3.0G 11G 23% /home/tom/.gvfs




  Not sure about how to post as code string though?  Fairly new to this.  I hope this helps.  Thanks.

---

### Post by trp on 2010-05-13
Bump. 


 Does anyone have any ideas?

---

### Post by darkod on 2010-05-13
Does this prevent you from booting ubuntu or it works fine and you're just interested what this partition is?
If you can boot ubuntu, have you tried opening the partition, it should be in Places to see if any files are there and which?
You said it was Hackintoshed. I haven't used that, but from another post it mentioned having a small boot partition. Maybe that's why it's marked as boot but also unreadable to ubuntu. But it would have nothing to do with the ubuntu boot process.

PS. Apple and I guess hackintoshed too, was working with the newer type of partiton table, GPT, earlier than PCs and windows. I'm just guessing here, but maybe after ditching hackintosh you need to write a new partition table to the hdd of the old MBR type (or DOS type).

---

### Post by srs5694 on 2010-05-13
Assuming the fdisk output is complete, there are no traces of the GUID Partition Table (GPT) data on the disk. (Recent versions of fdisk squawk about it if they find it, but will still work.)

Your /dev/sda1 doesn't seem to be in use. It's marked as being a Linux partition, but fdisk doesn't peek inside it, so it's unclear what's actually in there. (You might be able to learn by typing "sudo blkid /dev/sda1".) That partition is only about 23.5MB in size, which is pretty small by modern standards. There's really not a whole lot you could use it for. Therefore, I recommend just leaving it alone. If you really wanted to use it, you could use a command-line tool, such as mkfs or mkswap, to prepare it for a particular use. (Type "man mkfs" or "man mkswap" to learn about these commands.) IMHO, it's not worth the risk to delete the partition and resize /dev/sda2 to reclaim that space as part of your root (/) filesystem.

Concerning the [noparse]```

```[/noparse] blocks, you just enclose text between those two strings. For instance, you'd type:

[noparse]
```

Column One      Column Two     Column Three
  77.2             23.3            49.7
  89.7             12.9            17.6

```
[/noparse]

I'm not sure if they'll come across in the forum post, but I've got spaces on the lines to create columnar output. The results in the final post look like this:

```

Column One      Column Two     Column Three
  77.2             23.3            49.7
  89.7             12.9            17.6

```

That's much easier to read for certain types of text-mode program output, such as the "sudo fdisk -lu" output I asked for; without the [noparse]```

```[/noparse] tags, the forum software tries to interpret the columns as ordinary text, therefore compressing them and making it hard to figure out what's in which column.

---

### Post by trp on 2010-05-14
Hello again!

The system does boot just fine as it is currently, and I have read that u really don`t need a swap partion.  My concern is I have tried in the past to upgrade to 9.04 and 9.1 (several times in fact) and the install always hangs after I choose which partion to install the new OS on.  I can not recall the exact text of the failure to install message (as I have not attempted to install 9.04 or 9.1 in a while) but it goes something like this:  The ext3 file system creation in partition X of SCS1, sda failed.  Then when I re-install 8.04, for some reason, I have to manually re-install grub and MBR, the install does not go as a normal install would.  So I suspected this unknown partition as a possible issue to the install process.  Any ideas what might be going on?  Or is there a way to toatally re-format the ssd and start with a fresh install.  

PS  These are not upgrade installs they were from dvd`s from Canonical and I have 2 of each and each gave the same results so I don`t think the disks are bad.

Cheers,

Tom

---

### Post by srs5694 on 2010-05-14
It's critical to know which partition failed on the formatting. If it was /dev/sda1, then there could be something odd about the partition (perhaps even an underlying hardware failure) that's causing the problems. If it was /dev/sda2, then any focus on /dev/sda1 is misplaced.

You could try again, but select the "advanced" or "manual" partitioning option (I don't recall which it's called) to set up your partitions. That will give you better control over what partitions are and are not used and in what way they're used.

---

### Post by darkod on 2010-05-14
> **srs5694 said:**
> 
You could try again, but select the "advanced" or "manual" partitioning option (I don't recall which it's called) to set up your partitions. That will give you better control over what partitions are and are not used and in what way they're used.

If the OP tries to upgrade again, there are no choices like that I believe. Upgrade keeps the same partitioning. Those options are presented in a clean install.

> 
Or is there a way to toatally re-format the ssd and start with a fresh  install.  


There is always a way to do a clean install. :) Backup all your data, and just do what ever you want with your disk (partitions) after that.

---

### Post by trp on 2010-05-14
Hello again, and thank you both for your input on this issue.

Looking over my notes, it was sda/1 ( the partition with the unknown file system) that was indicated in the failure of the ext3 file system.  So this leads me to believe that the 24 or so MB file on that partition is causing some type of problem.  I have gone into Gparted and tried to formate this partition with ext3 and 4 unsuccessfully, and have tried to do clean installs with both 9.04, and 9.10 unsuccessfully.  Being rather new to Ubuntu, how can I wipe ( or re-format) the drive to insure this potentially problematic partition is removed once and for all.  I am not sure how to do this with Ubuntu since I am a relative Noob.  If you could provide any details of how to do this, it would be greatly appreciated!  Just keep in mind my skill level at this point.  I have purchased 2 books on using terminal commands but know just enough to be dangerous.  

Thanks,
 
Tom

---

### Post by darkod on 2010-05-14
If you have data you need on the disk, back it up furst.
If you don't, even easier.

There are mainly two options:
1. Use the automatic method. In the installer, in step 4, select Erase And Use The Whole disk. That will wipe the disk and set up root and swap partitions automatically. But you can't control how big they will be.

2. Use manual partitioning (I always prefer this). In step 4 select Specify Partitions Manually (Advanced). That will open a window with your current partitions. Select them one by one, bottom to top, and click Delete after selecting each partition to delete it.
Once all partitions are deleted, click on the unallocated space and click Create to create a new one. Use which ever filesystem you prefer, ext4 or ext3, set the mount point as /.
You are not using a swap partition right now so I guess you will want to do the same. If you want you can create a swap partition too, but this way you can control its size.
Also, you can consider creating separate /home partition and then in future you can do clean installs by keeping your settings and personal data untouched.

---

### Post by srs5694 on 2010-05-14
> **darkod said:**
> If the OP tries to upgrade again, there are no choices like that I believe. Upgrade keeps the same partitioning. Those options are presented in a clean install.

The post to which I was replying specified that the original failed attempts were "not upgrade installs."

[quote=trp]how can I wipe ( or re-format) the drive to insure this potentially  problematic partition is removed once and for all.[/quote]

Type "sudo fdisk /dev/sda", then type "d" at the prompt and select partition 1. Type "p" to view the partition table and verify that partition 1 is gone, then type "w" to save your changes. If by some chance something in your system depended on that partition (say, if a boot loader was installed there without your knowledge), your system will now fail to boot; however, you won't run into problems with the installer being unable to create a new filesystem on the partition because it will no longer exist.

In fact, if you're planning to burn your bridges and do a completely clean re-install, I'd recommend deleting *both* your partitions in this way. You can then create new partitions (including swap) when you do your fresh install. If you use the manual partitioning option, you'll be able to create a separate /home partition, too. Of course, this will wipe out everything, including your user data.

---

### Post by trp on 2010-05-14
Thanks again to both of you for your input!  

I will try and delete both partitions this weekend and do a fresh install of 9.10 or 10.04 as my new dvd from Canonical arrived today!  Just one quick question, would you recommend 10.04 or should I stick with 9.10?  I heard 10.04 still has some pretty severe bugs.  Not sure if those bugs are manifestrations of upgrading through update manager or fresh installs.  Any thoughts on that?  

Again, thank you both for your help addressing this issue!  I have always found the degree of help & professionalism on this forum to be very high, and you both have continued that tradition.  Hopefully someday, as I gain in knowledge, I can give back to our community.

Best regards,

Tom

---

### Post by darkod on 2010-05-14
It's up to you. Yes, there are lot of threads about problems, but most seem to be when upgrade is done, not clean install. Also, don't forget that forums are for problems. :) Users who have it all working don't visit here. :)

10.04 is LTS release (Long Term Support) which means it will have support for the next 3yrs. Usually the next LTS is scheduled in 2yrs. So, once you set up LTS release the way you want it, you don't need to worry about the versions in between. It's supported longer and no need to upgrade until the next LTS. By then you would probably want to have the new version anyway. :)

9.10 as 'standard' release will have support for 18 months, and it's already 6 months old.

Personally, I did a clean install of 10.04 over my 9.10 last weekend, and all is good. I think it even boots significantly faster. Also, there are few improvements to software that I like compared to 9.10.

---

