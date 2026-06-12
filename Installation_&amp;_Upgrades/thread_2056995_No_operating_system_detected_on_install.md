---
title: "No operating system detected on install?"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by ac529762 on 2012-09-12
This may in fact be something I've mucked up on the Windows side, and if so I hope someone can help me fix. Anyhoo...

Having installed 12.04 on my netbook with no issues whatsoever and being very happy with it I decided to set up a dual boot on my Windows 7 PC. This has a SATA Hard Drive (C) and two external drives, one fairly full (H) the other with plenty of space. (I)

When I first booted from the CD I got to the stage where I was given three options - install alongside W7, delete everything and install Ubuntu only, or do something different. I chose the first, but when it came to the bit where it asked me where I wanted to install I was only offered the chance to create a partition on (I). I didn't want this, so I went back and tried the 'something else' option, but when I got the list of possibles it wasn't clear where it was safe to install, and I didn't want to take the risk of selecting where it said Windows 7 in case I deleted the OS there (though on reflection this may be what I should have selected).

Anyhow, I figured that if I shrank my C: drive and created a new partition maybe that would do the trick. So I did so in Windows. When I reran the installer I went for the 'something else' option again to try and specify where to install. However, the partition (which I'd left unallocated) was listed as unusable. So, I tried giving it a label and assigning a drive letter in Windows. I got a message at this point saying something to do with not being able to boot anymore except for the partition already allocated to boot so I continued (after all I was working on a partition which didn't contain boot data). To reassure myself, after all this I rebooted and Windows 7 loaded fine.

Once more I restarted my PC to boot from the CD but now I get told that there appears to be no operating system and therefore only have a choice to install deleting everything or the 'something else' option (which of course no longer lists anything as having Windows 7 on it).

The partitioning caused me to lose all my System Restore points so I cant wind Windows back.

Haw can I (a) get W7 back to the correct config so that the Ubuntu install recognises that it's there, and (b) what do I do to get the installer to allow me to partition the (C) drive and install 12.04 there so that i'm using that physical drive whichever OS I decide to boot into?

---

### Post by darkod on 2012-09-12
From what you described, my assumption is that you had all 4 primary partitions used up on the primary disk, that's why it said the empty space was unusable. You can't have more than 4 primary partitions on a disk with msdos partition table.

But when you created the fifth partition in windows, it automatically (without asking your permission) switch the disk from Basic to Dynamic.

Boot windows, open Disk Management and check whether the disk is Basic or Dynamic. I guess the latter.

Dynamic disks is MS format and ubuntu doesn't fully understand it, so now it can't even detect win7 is there.

First, delete the new partition you created and leave it as unallocated space again.

After that, you should be able to switch the disk back to Basic with something like EASEUS Partition Manager (or Wizard, etc). I haven't used it, but people have reported that it does the job without loss of data on the disk. It's best to have a full backup before you try this anyway.

If that get done without problems, you still need to think which partition to delete so that you have only 3 primary partitions on the disk. In that case the ubuntu installer will offer to install, either by the auto method or the manual (I always recommend the manual).

---

### Post by opensshd on 2012-09-12
Try running the windows installer from disk/usb. You should see a screen that says "repair", you're looking for an option that restored MBR/bootloader.

That should find your windows install again, providing you did not nuke it with partitioning. If you just shrank the c: and did not format it you should be ok, I think you've just mucked up the bootloader.

Once you have windows running again, boot again from the linux disk. Click try Ubuntu, not install, and run gparted. Identify the partition you want to place linux on and format it to ext4. That should make it easier to get through your installer.

---

### Post by opensshd on 2012-09-12
Ubuntu will run on either a primary or logical partition will it not? But yeah, better to install to primary partition I think. And use a swap file instead of a swap partition. Will save you one of those slices. ;)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by varunendra on 2012-09-13
Welcome to the forums ac529762 !

Do exactly what darkod suggested.
In order to let us help you decide which partition to delete to allocate space for Ubuntu, post the outputs of:
```
sudo fdisk -l
sudo blkid
```
(or simply run gparted from the live cd and post its screensho)


> **opensshd said:**
> I think you've just mucked up the bootloader.
^^ Wrong assumption, and no need to repair MBR.

The OP said Win7 is loading fine which means the case is quit certainly what darkod described.

---

### Post by opensshd on 2012-09-13
> **varunendra said:**
> 
^^ Wrong assumption, and no need to repair MBR.

The OP said Win7 is loading fine which means the case is quit certainly what darkod described.

Perhaps! I didn't know windows did that. Never heard of a dynamic disk before :P

Also, I guessed OP post: "The partitioning caused me to lose all my System Restore points so I cant wind Windows back." meant he couldn't boot windows anymore either... what would have caused his restore points to get lost in that process?

---

### Post by varunendra on 2012-09-13
Just two lines above that: > **ac529762 said:**
> To reassure myself, after all this I rebooted and Windows 7 loaded fine.


> **opensshd said:**
> Never heard of a dynamic disk before :P Ah, God forbid those.. we're rather good with lvm's :)

> **opensshd said:**
> Also, I guessed OP post: "The partitioning caused me to lose all my System Restore points so I cant wind Windows back." meant he couldn't boot windows anymore either... what would have caused his restore points to get lost in that process?
I'm not sure, I don't have experience with dynamic disks. Maybe the OP intentionally purged the restore points to recover some space, or maybe windows did it to avoid possible errors in old static disk configurations stored in those restore points.. just my guess. :/

---

### Post by opensshd on 2012-09-13
Hmmm.. cool, thanks for pointing that out =]

---

### Post by ac529762 on 2012-09-14
Just wanted to say thanks for the above help.

The disk was dynamic, so changed it to Basic. Also fixed the master boot record (I think).

A couple of the partitions were redundant and so with a bit of help from EaseUS I deleted them, rejigged and expanded partitions till I had just two.

Reran the installer with my external drives unplugged and lo and behold got presented with the dual boot option, so I now have 200GB for W7 and 50GB for Ubuntu.

I'm in Ubuntu as I type this and look forward to playing with it and learning more.

Thanks again for making a newbie very happy!!

---

### Post by varunendra on 2012-09-16
Pleasant news, congratulations!!

You should mark this thread as [solved] now (follow my signature to see how), as it helps others having similar problems.

Hope you'll have a good time with Ubuntu and ubuntuforums.

---

