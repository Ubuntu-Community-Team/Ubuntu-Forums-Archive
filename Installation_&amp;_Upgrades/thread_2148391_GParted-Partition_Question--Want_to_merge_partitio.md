---
title: "GParted-Partition Question--Want to merge partitions to increase space"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by Qualtrough on 2013-05-25
Background: 

I have a dual-boot with Windows XP/Ubuntu Lynx 12.04. Gparted shows that my 320 GB (?) hard drive is partitioned as follows and in this order from left to right:

/dev/sda 1 97.5 GB (this contains windows XP and files) File system fat32
/dev/sda 7 100.47 GB (empty) File system ext4
/deve/sda 5 97.18 GB (this is where all my file and Ubuntu are located) File system ext4 

There is also a small 3.2 GB swap partition at the very end.

Issue/problem:

I would like to merge sda7 and sda5 as I am running out of space in sda 5.

However, the Gparted Resize/Move option is not active when I rightclick on sda 5. 

I also cannot unmount sda 5, I get this message: *Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually. *Not sure if that needs to be done, just letting you know. sda7 is umounted.

I screwed around with Gparted a bit last night and woke up to find Grub> when I rebooted my computer. Miraculously I was able to access the Internet on my cell phone to fix that, and the computer now reboots to Ubuntu as previously and everything is working well.

Although I have been using Ubuntu for more than 4 years, it should be obvious that I am pretty much a neophyte, so if you have any solutions pleases bear that in mind when explaining!

Thanks in advance for any assistance.

---

### Post by Cheesemill on 2013-05-25
Can you post a screenshot of gparted so we can see exactly how your partition are set up please.

---

### Post by darekch on 2013-05-25
If you will have more questions please provide output of following:
```

sudo fdisk -l /dev/sda
sudo parted /dev/sda print

```

1) Hmm... first of all... if you want to resize partitions all that partitons must be unmounted. Thus you need to do that from windows or (better option) from some linux live cd. Live cd will allow you to unmount every partition on your disk and resize option should be available. This is general rule for some serious operations on drives - serious operations usually needs unmounted partitions.

2) Resizing partitions, if they contain data, can be very long. I remember that once it took one night and one day! Thus much better approach would be to borrow some empty disk, copy whole data and then clean partitions and resize/merge or better just perform new installation.

3) In such situations, where merging partitions causes that one partition will be removed and other will be renumbered, can lead to problems in booting you linux. Then you will neet to start live cd and correct /etc/fstab and maybe update-initrams -u -k all. Looking at your /dev/sda list I guess that this case should not touch you.

4) Resizing/merging partitions is serious operation and can be interrupted due to some errors. Thus state of partitons can be unknown which will propably need to reinstall your linux.

5) If you want check 2) and 4) just plug some big ~8GB flash drive, make few partitions (primary/extended/logical), fill it with some random files... and play with gparted. And hdd operations takes much more time than on flash drive!

6) The option resize/move is also not available as I guess that sda7 is a logical partition (within extended partition) and sda5 is primary partition. Thus you need to remove sda7 partition, then you need to resize/shrink extended partition that previously contained removed sda7. Then free space will appear to extend sda5 and resize/move option should be available. But to be sure look at "sudo parted /dev/sda print" output or at gparted. The trick is that to resize partition there must be empty space. So you need to shrink (resize down) some other partition or just delete them.

Please backup your data. Despite gparted is super toy I usually had serious problems using it.

---

### Post by coffeecat on 2013-05-25
> **darekch said:**
>  if you want to resize partitions all that partitons must be unmounted. Thus you need to do that from windows or (better option) from some linux live cd.

Live CD agreed. Windows - no. Windows itself cannot resize partitions formatted with Linux filesystems and although there are Windows-based partitioning tools (such as Acronis) which can cope with Linux filesystems, what the OP needs is better achieved with Gparted. 

> **darekch said:**
> I guess that sda7 is a logical partition (within extended partition) and sda5 is primary partition.

They are both logical partitions - you can tell by the numbers. In the MBR partition table system primary partitions are numbered 1 to 4. An extended partition would also lie in the range 1-4 as this is simply a specialised type of primary partition. Logical partitions are numbered 5 and upwards. However, we need more information from the OP, which you have asked for - thanks - and I will ask for in my next post.

---

### Post by coffeecat on 2013-05-25
Before getting to the real issue, an important point:

> **Qualtrough said:**
> I have a dual-boot with Windows XP/Ubuntu Lynx 12.04.

Ubuntu Lucid Lynx is 10.04, not 12.04, and is now end-of-life. Please confirm which you are running. Although running an unsupported version of Ubuntu will not affect how you go about re-partitioning, you need to think about upgrading or even re-installing.

> **Qualtrough said:**
> However, the Gparted Resize/Move option is not active when I rightclick on sda 5. 

I also cannot unmount sda 5, I get this message: *Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually. *

Are you running Gparted from your permanent Ubuntu installation? You cannot resize the root partition of a system from the running system. You need to use Gparted from the live CD.

> **Qualtrough said:**
> 
 Gparted shows that my 320 GB (?) hard drive is partitioned as follows and in this order from left to right:

/dev/sda 1 97.5 GB (this contains windows XP and files) File system fat32
/dev/sda 7 100.47 GB (empty) File system ext4
/deve/sda 5 97.18 GB (this is where all my file and Ubuntu are located) File system ext4 

There is also a small 3.2 GB swap partition at the very end.


The information is incomplete. We need to see if sda7 and sda5 are really contiguous and where your extended partition begins and ends. Also, if sda7 and sda5 are out of numerical order, this looks as though you have done some repartitioning before this. Not that this makes much difference now, but we need more information. As others have already asked for, please post a screenshot of the Gparted window and the output of this terminal command:

```
sudo fdisk -lu
```

A couple of last points. **If** sda7 and sda5 are contiguous, you would need to delete sda7 and then resize sda5 to the left into the freed space. This will take a long time and has the potential for going wrong with data loss. Backup important data before you do anything.

---

### Post by Qualtrough on 2013-05-26
Thanks everyone for trying to help, and sorry for the delay in getting back. While I digest that, I will paste the info requested below. I am just looking for the best (and simplest/easiest way is to add disk space available in Ubuntu which is in sda 5, however that can be accomplished.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


sudo fdisk -l /dev/sda:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x139eec58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   c  W95 FAT32 (LBA)
/dev/sda2       204796681   625141759   210172539+   f  W95 Ext'd (LBA)
/dev/sda5       415496192   619307007   101905408   83  Linux
/dev/sda6       619309056   625141759     2916352   82  Linux swap / Solaris
/dev/sda7       204800000   415494143   105347072   83  Linux

Partition table entries are not in disk order

sudo parted /dev/sda print:

Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  105GB  105GB   primary   fat32           boot, lba
 2      105GB   320GB  215GB   extended                  lba
 7      105GB   213GB  108GB   logical   ext4
 5      213GB   317GB  104GB   logical   ext4
 6      317GB   320GB  2986MB  logical   linux-swap(v1)

[IMG]http://i.imgur.com/wvWRfEY.jpg[/IMG]

---

### Post by coffeecat on 2013-05-26
An earlier poster mentioned possible booting problems after you &#8220;merge&#8221; sda7 and sda5. (You don't actually merge them, but we'll come to that.) This is unlikely to happen, because although the stanza booting Ubuntu in your grub.cfg file will have a line referring to sda5, it also uses UUIDs and in my experience a &#8220;wrong&#8221; partition number in the set root line makes no practical difference. And, besides, in your situation, the sda5 partition is unlikely to be renumbered. However, emphasis on &#8220;unlikely&#8221;. In case you do have problems after you have done the repartitioning, please post the information asked for below before you do any partition work in case we need this to pick up the pieces.

[list][*]The contents of /boot/grub/grub.cfg. Either open this in a text editor and copy and paste it into your post, or run:

```
cat /boot/grub/grub.cfg
```
[*]The contents of /etc/fstab. Either from a text editor as before or from:

```
cat /etc/fstab
```
[*]The output of this terminal command:

```
sudo blkid
```[/list]

Please post these outputs between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Now to the re-partitioning:

**Backup anything important before you start**

[list=1][*]Do this from Gparted in the live CD session. You cannot do this from your permanent installation.
[*]Once in the live desktop, open Gparted, right-click on the sda6 swap partition and choose &#8220;swapoff&#8221;.
[*]Delete the empty sda7 partition. Make sure it really is empty first and there is no data that you need to backup. Remember to click the green &#8220;apply&#8221; button.
[*]Highlight the sda5 partition, and then from the Partition menu, choose move/resize. Either use the slider or the free space preceding field to enlarge it to the left. Click on the green apply button.
[*]Now you have to wait anything upward of several hours. This will be a lengthy process.
[*]Once it's finished &#8211; hopefully successfully &#8211; reboot into your permanent installation and let us know whether everything works.[/list]

This following bears repeating. Resizing a partition requires that the fileystem is rebuilt. There is a real potential for something going wrong. If there is a power-out, for example, you could lose everything. Hence the need for backups.

---

### Post by Qualtrough on 2013-05-26
A question: Would it speed the repartioning process if I were to backup and then delete my files before partitioning, and then restore them once partitioning is completed? I ask because I can usually back those up in something like an hour or so.

---

### Post by darekch on 2013-05-26
> **Qualtrough said:**
> A question: Would it speed the repartioning process if I were to backup and then delete my files before partitioning, and then restore them once partitioning is completed? I ask because I can usually back those up in something like an hour or so.
Yes. If you're sure about your backup, meaning you are sure that it will contain all data that you want, then deleting all files and reformating partitions before merging/resizing will let you do that process in about 5-10 minutes. Beside backup is rather 'must' if you want to resize partition.

Hmm... looking at your gparted's image I think that in your case resizing partiton without deleting files should also be fast (about 10 minutes), as you will expand one partion with empty space so no data should be moved. However I can't guarantee that.

And one word more about backup... remember to check if your backup contain hidden files/directories from you $HOME. If you use thunderbird then remember to backup ~/.thunderbird. Firefox usually keep you profile in ~/.mozilla.

---

### Post by coffeecat on 2013-05-26
> **Qualtrough said:**
> A question: Would it speed the repartioning process if I were to backup and then delete my files before partitioning, and then restore them once partitioning is completed?

You are not talking about simply backing up a few data files, you are talking about backing up a working operating system and then restoring it to a working state. That could be a whole different level of complexity. Is this what you want to do?

---

### Post by Qualtrough on 2013-05-27
> **coffeecat said:**
> You are not talking about simply backing up a few data files, you are talking about backing up a working operating system and then restoring it to a working state. That could be a whole different level of complexity. Is this what you want to do?

Sorry for any confusion. What I want to do is create more space for files in my Ubuntu partition, using the partition that is empty. It looks like I misunderstood the other day and what I will be backing up with be ALL files including operating systems files in the partition containing Ubuntu--which will take some time. Do have that right?

---

### Post by Qualtrough on 2013-05-27
> **darekch said:**
> Yes. If you're sure about your backup, meaning you are sure that it will contain all data that you want, then deleting all files and reformating partitions before merging/resizing will let you do that process in about 5-10 minutes. Beside backup is rather 'must' if you want to resize partition.

Hmm... looking at your gparted's image I think that in your case resizing partiton without deleting files should also be fast (about 10 minutes), as you will expand one partion with empty space so no data should be moved. However I can't guarantee that.

And one word more about backup... remember to check if your backup contain hidden files/directories from you $HOME. If you use thunderbird then remember to backup ~/.thunderbird. Firefox usually keep you profile in ~/.mozilla.

Thank you for your advice. From Coffeecat's response it looks like I might be confused about what I will be backing up? In any case, what I want to do is increase the amount of space I have for saving files in my Ubuntu operation, using the partitition that doesn't contain anything. I think I am still a bit confused about how this operation is going to work!

---

### Post by coffeecat on 2013-05-27
> **Qualtrough said:**
> Sorry for any confusion. What I want to do is create more space for files in my Ubuntu partition, using the partition that is empty. It looks like I misunderstood the other day and what I will be backing up with be ALL files including operating systems files in the partition containing Ubuntu--which will take some time. Do have that right?

To try to clarify. When I advised to backup, I really meant only your personal files. Ideally, it would be advisable to backup your whole operating system, but this is a more complex operation than simply copying all the constituent files. In fact you can use the terminal command cp to backup and restore a working operating system - I have done so on many occasions - but you need to know what you are doing; there are a number of factors to take into account, and it is a more complex operation than just copying the files and then copying them back again.

What is it you are trying to achieve? Do you wish to save time when resizing the partition, or to have a backup of your whole operating system? My advice - forget the time saving. If you are in a hurry when wanting to resize a partition, then don't even attempt to do it.

> **Qualtrough said:**
> From Coffeecat's response it looks like I might be confused about what I will be backing up? In any case, what I want to do is increase the amount of space I have for saving files in my Ubuntu operation, using the partitition that doesn't contain anything. I think I am still a bit confused about how this operation is going to work!

How it's going to work? You will end up with a larger partition that will work just like your current sda5, but it will be bigger.

---

### Post by Qualtrough on 2013-05-27
> **coffeecat said:**
> To try to clarify. When I advised to backup, I really meant only your personal files. Ideally, it would be advisable to backup your whole operating system, but this is a more complex operation than simply copying all the constituent files. In fact you can use the terminal command cp to backup and restore a working operating system - I have done so on many occasions - but you need to know what you are doing; there are a number of factors to take into account, and it is a more complex operation than just copying the files and then copying them back again.


What is it you are trying to achieve? Do you wish to save time when resizing the partition, or to have a backup of your whole operating system? My advice - forget the time saving. If you are in a hurry when wanting to resize a partition, then don't even attempt to do it.



How it's going to work? You will end up with a larger partition that will work just like your current sda5, but it will be bigger.

OK, thanks much for the clarification and advice. I plan to follow your instructions over the weekend when I can devote the time needed! I will report back, hopefully with good results!

---

### Post by Qualtrough on 2013-06-01
Tonight I thought I burned a Live CD and it appeared to be successful. The file name is ubuntu-12.04.2-desktop.i386.iso and the file size is 727.0 MB and it says it is a raw CD image. However, even though I set my computer to boot from the CD, all it does is light up the CD drive a bit before shifting over to my regular hard drive boot up. The disk is a DVDR, so is that the problem? I dug up an old CD R disk I have here but it is only 700 MB, so I don't see how that can work. Probably a dumb question or two there, but....

OK, did some more research and it looks like I burned it as data rather than an image. I will redo and see if that works!

---

### Post by ibjsb4 on 2013-06-01
The download is 693MB.  Something is not right with your download if its 727MB.

[ATTACH=CONFIG]243383[/ATTACH]

---

### Post by Mark Phelps on 2013-06-01
Recent versions of Ubuntu are too large to fit on CDs anymore; instead, you have to "burn" the ISOs to DVDs.

---

### Post by Qualtrough on 2013-06-01
Success! The problem I experienced was indeed because I burned the CD as a data file, not an image file. I made a new one and selected burn image, and that one booted up fine. I then followed coffeecat's very clear instructions on page 1 of this thread to the letter and bingo, it seems to have worked. I was able to boot up again without issue, and I now have an additional 100 + GB of disk space. [B]Thank you everyone who offered help here!
[/B]
One follow-up question if I may--related to this issue. I have another partition that contains Windows and some files. I do not use Windows anymore and I don't even think it will boot up correctly. Can I follow the same instructions from coffeecat some day to delete that partition and use that space for Linux? After removing or moving any files of course.

---

### Post by coffeecat on 2013-06-01
> **Qualtrough said:**
> 
One follow-up question if I may--related to this issue. I have another partition that contains Windows and some files. I do not use Windows anymore and I don't even think it will boot up correctly. Can I follow the same instructions from coffeecat some day to delete that partition and use that space for Linux? After removing or moving any files of course.

Sort of, but there's a complication. If you are referring to /dev/sda1, then that is a primary partition. If you delete that and want to use the space by enlarging what is probably now your sda5 partition, you would need to enlarge the extended partition first. Your sda5 is a logical partition and the extended partition is used as a container for logical partitions. You would end up with something a bit odd - a hard drive with no primary partitions, just one extended partition containing logicals. Although odd, it would work.

An alternative option would simply be to reformat sda1 with the ext4 fileysystem and use it as a data partition. There would be some permissions issues to consider, but they are easily dealt with and there are plenty of people who could help you with that, if you need it.

---

