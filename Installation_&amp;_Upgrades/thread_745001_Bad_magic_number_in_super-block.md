---
title: "Bad magic number in super-block"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Samuell.sk on 2008-04-04
Hi

If you first think that this is ordinery post as those others with bad magic number..... Than you are wrong.

Situation:
I have tried ghost/driveimage on my disk to move it to new raptor hd (original is 80gb , new 74gb). I was unable to ghost it nor imagedrive it. (thats not my problem anymore). So i installed new system on new hdd , setup everithing and than wanted to add old hdd and copy some old files. Hdd was not mounted (not a problem fdisk still might work) NO, it donst.

fdisk -l

I am albe to see /dev/hda and of course its partitions /hda1 ....
If i want to mount it manualy there is no such file or directory, if i run a fsck or e2fsck it will return:
No such file or directory whisle trying to open /dev/hda1

When I try to /dev/hda i get:
Couldn't find ext2 superblock , trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda

And if someon want to give me advice like in these links:
[http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup](http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup)
[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm)
[http://ubuntuforums.org/showthread.php?t=728618&highlight=bad+magic+superblock](http://ubuntuforums.org/showthread.php?t=728618&highlight=bad+magic+superblock)
[http://www.bellevuelinux.org/superblock](http://www.bellevuelinux.org/superblock)
...
and so on, than DONT EVEN TRY. Google works for me.

---

### Post by wieman01 on 2008-04-04
So what exactly do you expect? What have you tried so far? Let us know what advice you want to hear... Otherwise it will be very tough to help you.

---

### Post by Samuell.sk on 2008-04-04
Well, i would like to know how can i fix it. If you want to know what i tried so far, you can check those link what i posted in 1st post. I searched throught ubuntu forums, and googled for the problem.

for example:
[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm)
in this post you will find how to restore magic number for a superblock on AIX (its still working on nix so far) , when I was comparing superblock and "backup block" (lets say another one) it was the same.

[http://www.bellevuelinux.org/superblock](http://www.bellevuelinux.org/superblock)
In this post you will find out what are superblock, their purpose..... and of course how to restore them ( I was unable to pass "dumpe2fs device_name | less" ) error:
Bad magic number in super-block while trying to open /dev/hda
Couldn't find valid filesystem superblock

So I ended with this one. And if you look on other links , google for them you will actually relize that its the same.

I was kinda iritated in the first post, i m trying to solve this problem since yesterday morning and its a important maschine.

---

### Post by Herman on 2008-04-04
Well one of your problems is that you are using the commands wrong.
'/dev/hda' is a hard disk, or, more specifically, the MBR of your first hard disk.
There are no file system blocks anywhere close to the hard disk's MBR. The MBR does not belong to any file system.

Try aiming your command at a partition, such as '/dev/hda1', or '/dev/hda2', or '/dev/sda5', or something like that.

You need to know which partition number to use, look at your 'sudo fdisk -lu' command to try to find out ot remember which one it is, or use 'sudo parted /dev/hda p'
Then include the appropriate partition number in your command and hopefully things will start to seem a lot easier for you.

Regards, Herman :)

---

### Post by Samuell.sk on 2008-04-04
Ok i tried and saw those partitions (fdisk -f will show them to me too so no big diference between fdisk -ls or -l ) Than i tried:

parted /dev/hda p

I saw everything looks good (it still looks as same the fdisk -l to me) But there was:

Information: Don't forget to update /etc/fstab , if necessary  (i know what is in fstab) byt i do not quite understand how this command works "parted /dev/hda p"  (i will "man" later).
Regarding your "Then include the appropriate partition number in your command and hopefully things will start to seem a lot easier for you." I m not quite sure waht you mean. Try some example syntax. I tried parted /dev/hda1 p and parted /dev/hda p 1 the last one give me:
Error: File system has an incompatible feature enabled.

Any ideas ?

---

### Post by Herman on 2008-04-04
> So i installed new system on new hdd , setup everithing and than wanted to add old hdd and copy some old files. 

Hdd was not mounted (not a problem fdisk still might work) NO, it donst.

fdisk -l

I am albe to see /dev/hda and of course its partitions /hda1 .... So far if I'm understanding you correctly, you have a new hard drive with Ubuntu newly installed in it and you have now also plugged the old hard dirve in to the same computer and you are having trouble mounting the file system(s) in the old hard drive?
> (not a problem fdisk still might work) NO, it donst.

fdisk -l

I am albe to see /dev/hda and of course its partitions /hda1 ....
If i want to mount it manualy there is no such file or directory, if i run a fsck or e2fsck it will return:
No such file or directory whisle trying to open /dev/hda1

 Okay, before you can mount a file system, you need to create a 'mount point' to mount it to. 
A 'mount point is just an empty folder somewhere. It can be anywhere, but it's traditional to make mount points in /mnt in most Linux distros, or in /media if you're using Ubuntu. Most Ubuntu users like /media because then we will be automatically given a nice icon on our desktop which is very convenient.
To make a mount point in /media. we use 'sudo' before the command, because we need to be 'root' (have administrative priveledges), to be allowed to work in /media.
```
sudo mkdir /media/hda1
```Now you should be able to run a 'mount' command and mount your file system from your old hard disk in /media/hda1.
```
sudo mount -t ext3 /dev/hda1 /media/hda1
```I'm presuming now that your new hard drive must be /dev/sda or /dev/hdb or something else then?
If you posted your output from 'sudo fdisk -lu' or 'sudo parted hda -p' I could be more helpful. Nevermind, I'll make do.
> When I try to /dev/hda i get:
Couldn't find ext2 superblock , trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda Yes, as I said, if you/re trying to run a file system check, (I guess that's what you mean, you would need to indicate a file system, not just a hard disk, so you would run a command like,
```
sudo e2fsck -C0 -p -f -v /dev/hda1
```NOTE: You should only run a file system check on a file system that's not mounted, so if you mounted it, dismount it with the umount command before running any file system check.
That above command would run a file system check on your file system in /dev/hda1.

Is this working for you, or making sense to you so far?

---

### Post by Samuell.sk on 2008-04-05
OK , lets start again.

On new HDD, is new system, on old hdd, is old system. Now we are running on new hdd with new system. I pluged old hdd, becouse i need data from it. I know how fdisk works , fstab works , and yes, mount also. Problem  is that, that i can see hda1 , hda2 from fdisk -l , but if i try them mount to /media/storage (and yes, storage folder exists, and all users have rights to acces it) it will say:

Unknown device (well if i look to the disk / by uuid , i can see there only my new hdd (scsi). So , stop posting something about hda1 , hda2 ... hdaX , its no use. becouse its not there.I ll need first to see them.  If it was so easily , I ll wasn't be posting here a problem.

---

