---
title: "did I destroy my ntfs partition?"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by phogen on 2005-11-06
So apparently I misread how the partition manager works.  

I choose to create a partition in the free space I had left over on a windows ntfs formated drive.  I thought that this would act like partition magic, and not touch my current partition, but when I booted back into windows, it says that drive is not formated.

I know the data is still there because i can view it in ubuntu.  Does anyone know what happened, and if I can get my partition back in windows without loosing all my data.  If worse comes to worse, I guess I can try and burn all the data onto cd's from linux, and then bring them over to windows, but it's around 100 GB of data so I don't wanna do that.

any ideas?

---

### Post by aysiu on 2005-11-06
Maybe [reinstalling Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113) might fix it?

---

### Post by phogen on 2005-11-06
i dont' see why this would work.  Grub works fine, and boots into windows and ubuntu.  The hard drive in question is a second hard drive in windows (not the boot drive) and it has ubuntu installed on there.


Perhaps it's because i set both partition to be primary on that drive.  WOuld that do it?  For example... hdb1 and hdb2 are both primary.  ?? Should I change hdb2 ubuntu partition to be logical?

---

### Post by aysiu on 2005-11-06
Let me see if I've got this straight.
You've got two separate hard drives.

#1. Just Windows
#2. A Windows partition / A Ubuntu partition

Is that correct? And the idea is that when you boot into Windows (#1), it doesn't recognize the other Windows partition on the second hard drive as a valid partition?

---

### Post by phogen on 2005-11-06
that's it exactly.

---

### Post by aysiu on 2005-11-06
I'm not expert on file formats.
My guess is that it's either one of two things:

#1. The partition is properly formatted as FAT32. For some strange reason, Windows still doesn't recognize it.
#2. The partition isn't formatted as FAT32. It's some Linux format (like Ext3) that Windows doesn't natively recognize.

Either way, you may end up having to reformat it somehow. I believe there's some kind of program that allows Windows to read Ext3 partitions (I don't know how well this works).

What happens when you type ```
sudo fdisk -l
``` in a terminal?

---

### Post by phogen on 2005-11-06
well the windows partitions are ntfs .. not fat32


fdisk -l gives this :
```

Disk /dev/hda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2494    20033023+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       16709   134215011    7  HPFS/NTFS
/dev/hdb2           16710       18533    14651280   83  Linux
/dev/hdb3           18534       18655      979965   82  Linux swap / Solaris
```


hdb is the drive i'm not getting in windows...but it seems to still be formated ntfs, so i'm not sure why it's not showing up.

---

### Post by aysiu on 2005-11-06
[QUOTE=phogen]well the windows partitions are ntfs .. not fat32[/quote] Sorry. My brain's not functioning properly right now.

> hdb is the drive i'm not getting in windows...but it seems to still be formated ntfs, so i'm not sure why it's not showing up. Yeah. hdb1 is NTFS all right. I don't know what to tell you. Hopefully someone more knowledgeable about partitions than I am will chime in...

---

### Post by Herman on 2005-11-06
Well I don't know as much as Aysiu does, but I think it might be because your swap partition is on the end of your drive instead of being in the middle. If your NTFS partition is a logical partition then it needs to be inside the 'extended' partition, and so does your swap partition. You can't have them seperated by the Ubuntu Primary partition in the middle. Normally the Ubuntu partitioner automatically senses the other logical partition and installs swap on the correct side of Ubuntu (primary). I don't know if you can use Qtparted on a knoppix disk to fix it, but you might be able to. Otherwise it might be easier to just re-install Ubuntu.
                                                                                                     (Herman)

---

### Post by Herman on 2005-11-06
> Perhaps it's because i set both partition to be primary on that drive. WOuld that do it? For example... hdb1 and hdb2 are both primary. ?? Should I change hdb2 ubuntu partition to be logical?

Ubuntu would need to be primary, but is the other partition primary too? Has it got another operating system on it? Or just file storage? It might be better off set as logical, maybe that's what fooled the partitioner into not putting 'swap' on the other side of Ubuntu. (Or am I reading this all wrong?)

---

### Post by phogen on 2005-11-06
[QUOTE=Herman]Ubuntu would need to be primary, but is the other partition primary too? Has it got another operating system on it? Or just file storage? It might be better off set as logical, maybe that's what fooled the partitioner into not putting 'swap' on the other side of Ubuntu. (Or am I reading this all wrong?)[/QUOTE]


Yes, the other partition is set as primary as well, and it is just file storage.


you you mean it should look like this...

hdb1 - ntfs file storage
hdb2 - swap
hdb3 - ubuntu linux

---

### Post by phogen on 2005-11-06
also, i didn't defrag the drive before doing this, so the ext linux filesystem must be spread out over the whole drive.  That might be confusing windows..not sure. 

When I created the partitions during ubuntu install, i did the linux partition first and put it at the "begining" of the free space, and then did the swap and put it at the "begining" of the left over space.

If i go to reinstall ubuntu, and just delete both these partition, how should I set it up to work?  Just create the swap first, and change the existing ntfs partition to logical?

---

### Post by SickTwist on 2005-11-06
It should not matter (to Linux) whether Ubuntu's root and swap partitions are on primary or logical partitions. I'm not sure if so many primary partitions would confuse Windows or not.

Do you have space to copy the hdb1 data to the other partitions? If so, you could reformatt hdb1 from Windows and copy the data back to it. I've had to do that sometimes.

Also, you could set up your second drive as one large extended partition if you wanted. There is no need to have any primary partitions on it. (This would require formatting the entire drive which you may not want to do.) If decide to try that, the partitions would be accessed from Linux as  /dev/hdb5, /dev/hdb6, and /dev/hdb7 (Linux automatically jumps to 5 for the first logical partition).

---

### Post by phogen on 2005-11-06
I don't have room to copy the files somewhere else.  Perhaps I'll run out and buy an external drive.  That would solve all my problems.  I could just move all the files to the external drive from ubuntu, and then have access to them from both ubuntu and windows.  I could then dedicate the drive in question to linux.

hmph.

---

### Post by Herman on 2005-11-06
If you didn't defrag the drive it's okay now, the partitioner as 'smart enough' to just refuse to do anything if there's a block of Windows data in its way and you'll have to go back and defrag before it will work.  It sounds like you got that part done okay. :D 
Was your Windows partition on hdb1 already set as primary before? if it has no operating system and is just for storing files in it should be okay just as a 'logical' one, I think so anyway. You can have up to four primary partitions per disk, or three primary ones and one 'extended' one. The 'extended' one is like a box and it can hold logical partitions inside it. You can have as many logical partititions as you want, as long as they are all 'contiguous'. (one after the other all together in one string on your hard drive)(so they can all be inside the 'box'). Your 'swap' partition belongs in your 'extended' partition (box)too. Normally, if you just choose 'automatically partition the free space', when you are using the Ubuntu partitioner to install Ubuntu, it will do it all for you and you don't have to worry about a thing.
But was the hdb1 set as logical or primary before you began? I haven't got experience with more than one disk, so I'm a bit worried in case I'm telling you things I'm not sure about here. If it was set as 'primary' originally, I'd be checking for other opinions before doing anything more. maybe I'm 'barking up the wrong tree', so to speak.
Normally a primary partition is what I install an operating system in, and a logical partition is just for file storage, for me anyway. (for single hard disk).
But if it was set as 'primary' before you began, I'd hate to get you to do a lot of work and then find out I'm wrong and it's something to do with having two disks, which is a subject that I'm not experienced with as yet.
I did notice the lack of an 'extended' partition in your 'fdisk' output that Aysiu had you post. I think that's a sign that what I'm saying could be right.
There should be an 'extended' partition and it should include the same series of numbers as your swap partition as well as any logical partitions. (Those should all be in the same 'box', (extended partition). :p  (Herman)

---

### Post by Herman on 2005-11-06
Just disregard my last post, it sounds like you've already got the best plan while I was busy typing.:p

---

