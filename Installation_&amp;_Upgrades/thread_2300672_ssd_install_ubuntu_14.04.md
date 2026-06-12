---
title: "ssd install ubuntu 14.04"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by tmy on 2015-10-27
Hi 
I have bought a 250 GB SSD I have an existing ubuntu 14.04 install on a 1TB conventional drive

can anyone explain how I can use my new 250 GB  SSD and keep everything else the same 

Or install a clean install of Ubuntu 14.04 on the SSD and have a 2 TB conventional drive do I have to do anything to the 2 TB drive before I can use it from the box ?

As you can tell I'm clueless please be gentle and kind

regards tmy

---

### Post by TheFu on 2015-10-27
1) partition the ssd - websearch for "ubuntu gparted"
2) Format each partition you choose to have with a file system - ext4 is probably best - websearch for "ubuntu mkfs"
3) edit the fstab file and add each partition you'd like mounted inside there - websearch for "ubuntu fstab"
4) don't forget to create an empty directory to be used as the "mount point" - it can be anywhere.

You didn't say how you wanted to use the ssd. For new stuff, it is easy.  For existing stuff, it is more complex.

You'll want to use UUIDs - those can be listed with **sudo blkid**
You didn't say whether you wanted to use LVM or not. If you don't know, do a little reading about it [https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) there are pros/cons to using LVM. Only you can decide if it fits.  If you choose to use LVM, create 1 partition and don't format it with a file system.

If you desire to make the new SSD the primary OS/application disk, then installing a fresh 14.04.1 disk would be best. 5 yrs of support. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) notice how not every 14.04 release gets 5 yrs of support? We have to be careful.

---

### Post by tmy on 2015-10-27
Hi The Fu thank you for your reply ,
my title should have been 14.04 NOT 10.04 sorry guys 
I have bought a 250 GB SSD I have an existing ubuntu 14.04 install on a 1TB conventional drive

can anyone explain how I can use my new 250 GB  SSD and keep everything else the same 

Or install a clean install of Ubuntu 14.04 on the SSD and have a 2 TB  conventional drive do I have to do anything to the 2 TB drive before I  can use it from the box ?

As you can tell I'm clueless please be gentle and kind

I just want to use the SSD for the ubuntu os and carry on as is because everything is working well

regards tmy

---

### Post by yancek on 2015-10-27
Do you want to leave Ubuntu on the 1TB drive since it is already installed there?
Do you want to use the SSD for data storage?
If the answers to the above are yes, then either use GParted Partition Manager which is on the Ubuntu installation medium or download it from the Software Center and then create a partition or partitions on the SSD.  If you are not familiar with GParted, the link below is to the manual written by the developers which you can review.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

It might clarify things if you can boot Ubuntu and run the command below posting the output here.  Make sure the SSD it attached before running the command.

> sudo fdisk -lLower Case letter L in the command.

---

### Post by TheFu on 2015-10-27
Not all fdisks are safe with GPT disks.

Please use **sudo parted -l** instead.

TMY, you haven't answered my questions - how do you want to use the new SSD? You have to be specific.

---

### Post by tmy on 2015-10-28
Hi The Fu,
thank you for helping me, I might be wanting the  impossible, the set up I have at the moment is ubuntu 14.04 running on a  1TB conventional harddrive. I keep getting the screen go grey and  computer will temporarily freeze the light on the harddrive activity  with light up like it is really trying to do something I can't do  anything then it will come back fine but slow 

I just reboot and everything is good again

I  wanted to use the SSD for the os and the 1TB to store all my downloads  and docs and photos etc, maybe it's just not possible now to separate  the two

I hope that all makes sense 

regards 
and many thanks

tmy

---

### Post by TheFu on 2015-10-28
tmy - you can certainly do that, but my explanation skills are not to that level to explain all the steps and tiny details you would likely need explained. Sorry. 

I can offer an overview of what needs to happen, which is really quiet simple.

Linux/Unix is dumb. If the storage is placed onto the correct location, with the correct files and directories and owner, group, permissions, then the OS will be happy. All you need to do is move the everything except /home to the new SSD. This assumes you've left all the large files and (non-OS and non-application files) in the normal places.  

There could be complexities. LVM and/or encryption would make the steps harder. Actually, if there is encryption, I would punt myself and start with a fresh install on the SSD.

After the files are all moved to the new storage, you'll need to fix the /etc/fstab to recognize /, swap, and /home storage mounts. May need to fix /boot too - if that is separate. It might not be.

Then you'll need to fix the bootloader, grub.  **grub-install** and **update-grub** are the tools for that. There is a **boot-repair** tool which might "just work" too.

The only hard part about all of this is that you need to perform all these tasks from a live-boot, not from the currently installed OS. 

Minus the time it takes to copy everything over,  the partitioning, editing, boot fixes would take someone who knows what they are doing about 5 minutes. Sadly, it may be an impossible task for someone without extensive partitioning, booting, and other Linux skills. 

For someone with minimal skills, just unplug the old disk and leave only the SSD connected, then do a fresh install. After, connect the old disk and mount /home where you need it by editing the /etc/fstab. This is fairy easy. Be certain to use **sudoedit** whenever editing system files.  Then cleanup the old OS files from the big disk.

To begin, let's see what you are working with. Please post the **cmd** and **output** from each of these:
```
$ lsblk
$ df  -h
$ sudo parted -l
$ more /etc/fstab
```

Use code-tags so things line up.

It should go without saying, but moving all this data around and partitioning are destructive commands. Make a mistake and everything could be lost. Backup everything you cannot lose to a different disk, disconnect it, move the backup to a different room. You've been warned.

---

### Post by yancek on 2015-10-28
Certainly the option to do a new install of Ubuntu to the SSD would not be difficult and is probably the safest option given your level of experience.  There are also ways to copy the entire Ubuntu to the SSD but that will be much more difficult for an inexperienced user.  The first step, in any case is to give the information requested showing your drive/partition structure.

---

### Post by tmy on 2015-10-28
Hi guys,
thanks The Fu and Yancek,
fallen at the first hurdle the commands just didn't work. If I can pull this off anyone can do it I promise. I have played around with Linux but not having anyone who I can turn to it's been painful and slow forums are great and I appreciate everyone's time I really do, but it's painfully slow and drawn out 

I know a program in Windows ( I know hiss boo  :-) ) but it's called Fabs auto back up it does everything anyone would need but in Linux situations like this people are on their own as nothing is written. I wish in  situations were this scenario  must be common, programs or code could be written

I digress though, I fancy installing ubuntu on the ssd and then plug the big old conventional drive back in but after that  I would get lost. The ssd is only 250 GB so it can't hold the contents of my old conventional drive.

Here is what happened to those commands when I ran them :


```
stan@stan-System-Product-Name:~$ $ lsblk
$: command not found
stan@stan-System-Product-Name:~$ $ df  -h
$: command not found
stan@stan-System-Product-Name:~$ $ sudo parted -l
$: command not found
stan@stan-System-Product-Name:~$ $ more /etc/fstab
$: command not found
stan@stan-System-Product-Name:~$ $ lsblk
$: command not found
stan@stan-System-Product-Name:~$ 
```

Cheers guys I hope your not getting fed up with me 


Regards

tmy

---

### Post by ubfan1 on 2015-10-28
You are typing the "$" -- don't, that is just the prompt.

---

### Post by lisati on 2015-10-28
> **tmy said:**
> 
my title should have been 14.04 NOT 10.04 sorry guys 


I've edited your thread title for you.

---

### Post by tmy on 2015-10-28
Thank you ubfan1

feeling stupid  :-(

regards 

tmy

---

### Post by tmy on 2015-10-28
Ok I managed to get the info after help from ub fan 1 thank you mate I'm hopeless but really want to learn so it's embarrassing :


```
 stan@stan-System-Product-Name:~$ lsblk
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                            8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                         8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                         8:2    0     1K  0 part 
&#9492;&#9472;sda5                         8:5    0 931.3G  0 part 
  &#9500;&#9472;ubuntu--vg-root (dm-0)   252:0    0 925.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1) 252:1    0     6G  0 lvm  [SWAP]
sr0                           11:0    1  1024M  0 rom  
stan@stan-System-Product-Name:~$ df  -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  911G  813G   52G  95% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         2.9G  4.0K  2.9G   1% /dev
tmpfs                        591M  1.3M  589M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         2.9G  3.3M  2.9G   1% /run/shm
none                         100M   60K  100M   1% /run/user
/dev/sda1                    236M  185M   39M  83% /boot
stan@stan-System-Product-Name:~$ sudo parted -l
[sudo] password for stan: 
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 6371MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  6371MB  6371MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 994GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  994GB  994GB  ext4


stan@stan-System-Product-Name:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e29fa5ed-0c55-479e-85a9-66301cada51a /boot           ext2    defaults      
  0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
stan@stan-System-Product-Name:~$ 
```
 

regards 

tmy

---

### Post by 1clue on 2015-10-28
tmy,

What you want to do is very possible, and not really all that complicated.  But given your level of experience it's probably going to be a challenge.

I'm going to explain what needs to happen in layman's terms.

First, when you put the output of a command into your post, it helps to put code tags around it so it's easier to read and so we know where the output stops.  Code tags are created when you use the **#** button on the post editor.

Here's what needs to happen:
[LIST=1]
[*]You need to partition the SSD.
[LIST=1]
[*]You could use the same layout as your spinner has.
[*]You could do something else, like lvm filesystems.
[/LIST]

[*]You need to format the SSD partitions.
[LIST=1]
[*]You probably will want ext4.
[/LIST]

[*]You need to mount the SSD partitions in a temporary location.
[LIST=1]
[*]**/mnt** is a typical place
[/LIST]

[*]You need to copy the data you want onto the temporary location.
[LIST=1]
[*]Since your SSD is smaller than your spinner, you'll have to be careful to not overfill the disk.
[*]**sudo cp -rax / /mnt** for example
[/LIST]

[*]You need to adjust the /etc/fstab file on your temporary location to use the new partition scheme.
[*]You need to adjust your boot loader to point to use the SSD as /.
[/LIST]

---

### Post by QIII on 2015-10-28
Hello!

Please use code tags when posting terminal commands and results.  That will preserve any formatting and also make your post easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.



There is absolutely no reason to feel embarrassed here.  We exist for the purpose of providing support.  We want people to be able to learn without the "newbie scorn" you may find elsewhere.  We simply don't tolerate it.  

Ask questions.  While we do ask that users first search for an answer previously provided on the Forums or a simple question that might be answered by a web search, we do not close threads when people ask a question already asked and answered.  We may direct you to a similar thread that was solved or a resource on the web, but we also know that everyone's situation is different and that an answer previously given may not exactly apply to you.  We want you to feel free to come back to the thread and say "Hey, that didn't work!"  This isn't a StackExchange forum where threads are closed because the question has already been asked elsewhere.

If you don't understand an answer given, ask for clarification.  It is easy for those of us who have been using Linux since the '90s to forget that what seems trivial to us is often inscrutable to those just starting out -- even if we try hard not to do that.  Don't let us go over your head.  Don't feel embarrassed to say we went over your head.  That's our failure, not yours.  

We want people to learn here.  We don't want them to feel put down.  If you get an answer like that, please report it and the Staff will deal with it.

Every time we help someone solve a problem, we leave a record of that solution for someone else with a similar problem to find.  We're continuously building a "knowledge base" of sorts.

Cheers!

---

### Post by tmy on 2015-10-28
Hi 1 Clue,
thank you so much for taking time to reply and help out

I think I'm doomed what you have explained is like talking in Chinese and really disappointing as I was looking forward to having a crack at this project. Thank you again 

regards 

tmy

---

### Post by 1clue on 2015-10-28
If you're willing to give it a try, there will be plenty of people here familiar with what needs to happen.

We were all new users once.  Somebody helped us out in the beginning and I'm pretty sure all of us still get help fairly frequently too.  Don't be shy.

Most of this you can do without altering your original install.  Which means you could still reboot and it comes back with exactly what you have right now, and your SSD is waiting for you to finish.

---

### Post by TheFu on 2015-10-29
tmy - happy you posted the results. It shows that the 1TB disk is mostly full.  Making 950G fit into 250G SSD isn't possible. That means you have to know what are and are not the OS files and how much storage they require, if we try to move the install from 1T to 250G.

Your install is using LVM. Not a bad thing, but it does complicate things.

**At your current level of skill, I'd strongly recommend unplugging the 1T disk and doing a fresh install onto the SSD. ** I'll assume that going forward. You should specifically ask the question here to get other opinions about going in this direction. It will be 10x easier than the alternatives and you won't be without a booting system.

When you connect the 1T drive back up, you'll need to rename the volume group and logical volumes to prevent conflicts with the new install.  I've never done this, but it looks easy.   A little reading about LVM would be good, so you don't get confused with all the commands.

Hopefully someone who has done this will say if **vgexport** is required before the first disconnection or not. Then **vgrename** will be required. VGs cannot have the same name on a system. These are just names, not important in any other way.  Similar requirement for LVs - the names are just names, but should be unique. **lvrename**.

Anyway, let us know which way you'd like to proceed.

---

