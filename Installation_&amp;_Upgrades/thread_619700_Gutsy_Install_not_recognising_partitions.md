---
title: "Gutsy Install not recognising partitions"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by Annihilist on 2007-11-21
Hi all,

For the past year or so I have been dual-booting Fiesty and Vista. A couple of weeks ago I decided to upgrade to Gutsy, but because of size issues, I wanted to try and resize some partitions first. I resized a few vista partitions using the vista disk manager, and since then I havent been able to boot into Fiesty. I tried fixing grub but nothing I did could help.

I tried using the live cd to run gparted so I could resize the ubuntu drives as I needed and then worry about booting into fiesty to do the upgrade, but for some reason it doesnt recognise most of my partitions. It just displays them as unallocated. The Gutsy install disk does the same thing, even thou when I use 'fdisk -l' it lists all the drives. I'm not sure if it has anything to do with it but the 'fdisk' command gives me the same results as gparted and the install if I dont sudo the command, but when I do sudo it it finds all partitions perfectly.

My drives are set up as:

200gb - 50gb NTFS, 100gb NTFS, 50gb NTFS extended onto another drive

80gb - 40gb NTFS, 2gb swap, 5gb ext3, 25gb ext3

200gb - 200gb NTFS extended onto first drive

I realise its kind of a weird partition scheme, but I had my reasons for doing it when I set up the machine.

Any ideas would be very much appreciated.

---

### Post by rmemm on 2007-11-21
Regarding fdisk and gparted.  I think these have to be run under sudo anyway otherwise you can't access the drive to read data -- unless your on a special account with special permissions.

Regarding partitian schemes -- only thing I would say -- if you mean extended to mean a single partian spans multiple volumes.  I wouldn't recommended it as increases the changes of disk failure -- meaning if any on of the disks has a problem you loose the partitian.

I would have used a live CD myself to look at this.  Only other option is a smaller recovery CD that does not need SWAP -- I some times use those also.  I'd use one of these options and see if I could mount the partitian and see what's there.  You could try running a the disk scanner on it also.  Maybe also a good time to think about backup if you have something important out there -- at least think of recovery stratagy.

Rob

---

### Post by Annihilist on 2007-11-21
Thanks for the reply. When I use the live cd I can mount all of my partitions except the one which is spanned across multiple volumes. I'm trying to change it now using the vista partitioner but thats a different problem entirely.

So I can see the drives, I can mount them and explore them, its just when I use gparted or try and run the install of the live cd that the problem happens. I don't think I'm the only one either, cause I've seen a few posts around the net on this issue, but none of them have a solution thats worked for me.

---

### Post by rmemm on 2007-11-21
Kind of sounds like the Vista partitian editor writes a slightly different format than linux expects.

It's good that you can see the partitians under Linux -- that kind of says everything is there. I think I might take the opportunity to backup anything I wanted especially the partitian tables and boot blocks.  It would also be good to print out the fdisk layout both in cylinders and in blocks so you know where every partition is really located.

If you are pretty sure the fdisk layout is correct -- and that you have everything you really need backed up -- I would consider just rewriting the partitian table(s) with fdisk.  Maybe do one disk at a time and see if that fixes the problem.

There is some risk to rewriting the partition table -- so I'd only do that after thinking about that -- i.e. do I really want to do that.

Sorry - I'm not a vista guy so don't know about vista.

Rob

---

### Post by torgrot on 2007-11-21
This sound suspiciously like a Dynamic Disk.  We use them at work on our servers sometimes, but have had some problems with them.  As was mentioned if the Master disk fails everything on the Dynamic Disk is unavailable typically.  This is a windows scheme for dynamically extending a drive.  I don't think Linux is going to recognize that drive until you convert them to Basic Disks.  You can check out MSDN for more information regarding Dynamic Disks. [http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)

torgrot

---

### Post by rmemm on 2007-11-21
You know another thing you should check also.  Check to make certain they have the correct partitian type assigned.  Perhaps the Vista partitian editor does not like linux partitian types and resets them so something undesirable.

If I'm not being clear -- each partition as a numeric number assigned to it to tell the system what the partitian contains.  Like 83 is Linux data and 82 is swap.  There are also various codes used for the extended partitians.

Just a thought.

Rob

---

### Post by hidden_leaf_sasuke on 2007-11-22
I got the same problem as you. using fdisk every partition is listed (i have 3),but when i want to install ubuntu (gutsy),when it comes to manual partition,it just listed "unallocated space"...wtf,fdisk can view it why gparted cant. My hard disk is 80 gb,an have 3 (xp,empty,linux swap).id there anything i could do to make gparted "see" my partitions?

---

### Post by Annihilist on 2007-11-25
I think I read somewhere that the problem with gparted is that it uses libparted to determine the partitions, whereas fdisk doesnt. I'm not sure if the ubuntu install also uses libparted, but I'm gonna try one last time to get Ubuntu installed on this machine, and if I manage to do it I'll post how I did it. I really hope it works because otherwise I'm gonna have to get a seperate machine just to run Ubuntu haha.

---

