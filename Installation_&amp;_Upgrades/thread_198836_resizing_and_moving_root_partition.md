---
title: "resizing and moving root partition"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2006-06-17
i originally installed ubuntu in a 5 gigabyte partition, but since i use it much more then windows now id like to have extra room for more programs and games...
i'm using the gparted on ubuntu LiveCD to resize my NTFS partition (for some reason it wont allow me to do anything using the gparted ive installed on my regular ubuntu...)

so i changed the NTFS partition to be 10Gigabyte smaller, and i have them unallocated just before my "/" partition starts, i need to move the "/" partition to the end of the NTFS one and resize it, but i can't seem to move it... theres an option called "resize/move" but it only resizes.... and because i dont have any spare room after the "/" partition it wont allow me to resize (i.e. it can't resize backwards...)

so my questio is, how can i resize my "/" prtition?

---

### Post by Herman on 2006-06-17
This is a common problem. You are lucky you have Ubuntu installed in one piece and not with a seperate '/' (root) and /home type of install, then it would be even more complicated to carry out your resizing.

Linux partitions are fixed at the start point, but you can resize them from the 'end' easily. Linux operating sysem partitions cannot be 'moved' like many other types of partitions can, but they can be copied and pasted.

I prefer to use a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") for this type of work, but someone else reported that GParted on the Ubuntu 'Desktop (live/install)CD' worked just as well.
First you should shrink your partitions as much as possible. You may need to remove a lot of data and save it to some other media to get them small enough. The idea is to make a lot of free sapce on your disk for copying and pasting things around.

The next problem is that when you copy a partition and paste it, it gets a different partition number which then makes it unbootable until you [re-install GRUB]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29"). Fortunately that's quite easy to do. Then you boot and edit /etc/fstab with your new partition numbers and after that you will be fine.

There's an easier way. Copy the shrunken (Ubuntu) partition to an empty space out of the way, (not where you want it to finally end up), and delete the original. Then copy the copy, and paste it where you do really want it to reside. It will (should) get it's original partition number back again, left vacant from deleting the original. That's the way I prefer to do it, I call that 'partition leapfrog'.

A good tip is to make it easier for yourself for next time by shrinking and moving Windows away from the beginning of your disk. Then paste a shrunken copy of Ubuntu to the very end of your disk. Delete the original Ubuntu. Copy the copy, and paste it to the *start* of your disk. If you have plenty of disk space, leave the copy of Ubuntu at the end of your disk as a backup copy. Then resize both Ubuntu and Windows back to normal size. Next time it will be easier to resize Ubuntu because it will already be the start of your disk, no need to 'move' it. You can always 'move' Windows easily anyway whenever you want to resize again. The beginning of your disk is faster as well, so Ubuntu will work better. It will be a better setup all around.
Good luck with it, if you need more specific help, please post again with the results of ```
sudo fdisk -lu
``` or a screen cap of GParted. 
Regards, Herman

---

### Post by fargoth on 2006-06-17
wow, i didn't expect it to be that complicated...

while i was waiting for an answer i used partition magic, and it DID MOVE the "/" partition... (well, maybe it did the copy&paste without my knowledge, but i didn't have to re-install GRUB or even do more then two simple resizes....)

guess theres still some work to be done on the linux partitioning tools until they get that polished...

---

### Post by Herman on 2006-06-17
>  guess theres still some work to be done on the linux partitioning tools until they get that polished...No, not at all, Partition Magic is not recommended for Linux partitions and it has been responsible for 'hosing' more then a few partition tables, although I hope you will be one of the lucky ones and get away with it without any damage.
You won't know for some time, because flaws in your partition table can lie dormant for some time and you might not be aware. Then, next time you go to resize you will loose everything that's not backed up. Make sure you back up all your data now while you are still able to!
Good luck with it, Regards, Heman.

---

### Post by mlind on 2006-06-17
[QUOTE=fargoth]wow, i didn't expect it to be that complicated...[/QUOTE]

That's one good reason to consider using LVM. That's what I did when I went through
few partition resize hassles. I can say that task is a lot easier now.

---

### Post by vasimakhtar on 2006-06-17
Hi,
I have similiar kind of situation. I have 80GB, with dual boot. 36GB for winxp and for remain having two partitions for 18GB x 2 each. I am able to access winxp data throuth mount and also able to access one partition of 18GB for ubuntu data. But not able to access remaining 18GB on Ubuntu. I want to reallocate this 18 GB to remaining for Ubuntu. Is it possible? how?
thanks

---

### Post by aysiu on 2006-06-17
So it's probably something like this, right?

/dev/hda1 Windows
/dev/hda2 Ubuntu
/dev/hda5 Empty space

If that's the case, you can use a live CD and GParted to simply extend the Ubuntu partition to include that empty space.

However, if it looks more like this:

/dev/hda1 Windows
/dev/hda2 Empty space
/dev/hda5 Ubuntu

Then the best thing you can do is format the empty space as Ext3 and then follow these directions: [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by vasimakhtar on 2006-06-18
Thanks. I think my situation is little different. Enclosed screen shot of my system. Hopefully your guidance will be helpful.
thanks

---

### Post by aysiu on 2006-06-18
Hm. You have two swap partitions. Is that necessary?

Also, is Ubuntu /dev/hda3 (the primary partition) or /dev/hda6 (in the extended partition)?

---

### Post by fargoth on 2006-06-18
[QUOTE=Herman]No, not at all, Partition Magic is not recommended for Linux partitions and it has been responsible for 'hosing' more then a few partition tables, although I hope you will be one of the lucky ones and get away with it without any damage.
You won't know for some time, because flaws in your partition table can lie dormant for some time and you might not be aware. Then, next time you go to resize you will loose everything that's not backed up. Make sure you back up all your data now while you are still able to!
Good luck with it, Regards, Heman.[/QUOTE]

well, sounds like you had some bad luck with Partition Magic... i used it more then once with ext3, NTFS and fat32... and as long as you scanned for problems first (especially for the fat32) it doesn't do any trouble....

iv'e searched the net to see if anyone alse complained Partition Magic destroyed his data.. haven't found much, there aren't that many complaints and there were more NTFS\FAT32 disks ruined then ext3 (found only 2 other cases who said partition magic was bad luck with linux...)

so i guess you're an unlucky one, and i just hope i won't be too.
anyway, it's always a good idea to backup the important stuff once in a while... thanks for your concern.

(and Gparted could get better if they'd do the process you described automaticall - that is copy and paste to a different partition, delete the original, create a new one and copy and paste again....)

---

### Post by dilidon on 2006-06-19
[QUOTE=Herman]
Good luck with it, if you need more specific help, please post again with the results of ```
sudo fdisk -lu
``` or a screen cap of GParted. 
Regards, Herman[/QUOTE]
Edit: I had a message here that was way too long. Removed it, as I solved my problem, which I had posted in full length. Had messed up my "boot" partition while deleting and moving partitions around. As a relative beginner in linux, I forgot I *had* to have a separate one for that (at least marking a new 50 M partition "boot" solved all my errors and woes). However, I'm posting some some details back here in a shorter format, to give back to the discussion what I took from here. Maybe helps someone in advance.

First, thanks for the tips. I used the Gparted LiveCD and moving stuff was all ok. I encountered a few timeconsuming problems though.
Second, one point of caution for others going for this. When moving the Ubuntu partition OUT of an extended partition, in case it is inside one, it will take another name if there are other vacant names. That happened to me. My Dapper hda5 became hda3. Of course, my machine refused to boot into Dapper after that and I was going for reinstalling Grub. <- problems started.
Third, when I tried to install a new Grub with the Dapper LiveCD, it a) formatted my Windows (even I had told it not to format anything, even the swap, which it still did), and then, b) crashed. I wasn't 100% sure how to use the Grub command line so I failed to use that option as well - grub basically said it couldnt find any of the partitions I was telling it to use, so maybe I simply entered the wrong parameters).
Fourth, my solution so far was to move my Dapper back to an extended partion so it became hda5 again (extended partitions count starts at 5, I think, by default) and creating a small partition flagged "boot".
Fifth, however, prior to doing that, I tried to reinstall Grub with the LiveCD method for the last time, without having to necessarily have my Ubuntu on hda5 as Grub wanted it to be, and Ubuntu LiveCD crashed, again. The error is attached.
My system works right now. Alhtough I don't have windows anymore (that doesn't hurt at all - calculated risk :D) so I will give a try to that VMWare thing to install it under Linux.

What could be the reason for that crash/error indicated on the snapshot that kept me away from successfully reinstalling Grub? Messed up partition table? Damaged CD? (doubt it). A bug?

---

