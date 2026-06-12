---
title: "[SOLVED] How to RE-INSTALL or CLEAN INSTALL Ubuntu with Dual Boot Vista"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by anuban on 2008-03-26
I have been using Ubuntu extensively for the last 6 months.  And I am very happy to say that I am really a great fan of Ubuntu.:guitar:
Now I want to start over again so as to do a clean install of Hardy.
How do I do that? I did a upgrade to Beta but I want to do a clean install. I know I will get Hardy automatically as it is released.
The only thing which I don't get is how do I create/delete/re-create my dual booted with Vista laptop.
When I try to install Hardy from LiveCD, I am held up at the partition manager.
At present I have following partitions:[LIST=1]
[*]EISA Configuration - 55MB
[*]OS (Vista) - 80GB
[*]Recovery (Vista) - 10GB
[*]Ubuntu (ext3) - 13 GB
[*]Swap - 600MB
[*]Media Direct - 2GB[/LIST]It is a Dell Inspiron 1505 Laptop with 2 GB RAM and 120GB HDD preinstalled with Vista Home Premium.

When I try to format Ubuntu (ext3) partition keeping swap the same and without touching anything else, Partition manager gives me an error message talking about some Clusters and all which Windows won't like and should be something else :confused:

Is there a way to completely get rid of Ubuntu so that I can START OVER.

Any help will be appreciated.:sad:

And I would suggest to have such kind of How-to in the Ubuntu Wiki itself.  Ubuntu wiki talks about installing everything but nothing about uninstalling it.
Just a thought....:)

---

### Post by Pumalite on 2008-03-26
Go 'Manual and install Hardy on top of Ubuntu using the same partitions.

---

### Post by anuban on 2008-03-26
> **Pumalite said:**
> Go 'Manual and install Hardy on top of Ubuntu using the same partitions.

It doesn't let me do that.  Throws up error.  Below is a grab of my sudo fdisk -lu[INDENT]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112640    21084159    10485760    7  HPFS/NTFS
/dev/sda3   *    21084160   202981375    90948608    7  HPFS/NTFS
/dev/sda4       202981462   234438655    15728597    f  W95 Ext'd (LBA)
/dev/sda5       230246400   234438655     2096128   dd  Unknown
/dev/sda6   *   202981464   229006574    13012555+  83  Linux
/dev/sda7       229006638   230243579      618471   82  Linux swap / Solaris

Partition table entries are not in disk order
[/INDENT]I am not sure what I need to do to save my Vista partition and clean install Ubuntu Hardy on the existing Linux partition.

Attached is the grab of the error I am getting...

Thanks

---

### Post by anuban on 2008-03-27
Anyone for help...

---

### Post by Pumalite on 2008-03-27
No error there; click on sda6, Delete and make new partition of the same size and mountpoint. You can leave /swap alone, press 'Forward'

---

### Post by anuban on 2008-03-27
So basically just ignore the error and delete the existing partition, create a similar partition again with same details, BUT IT WILL BE MOUNTED AS '/' ..RIGHT.
I will try that today...

---

### Post by WoosterB on 2008-03-27
Can I get a procedure for "go manual" with only a command line interface?  The GUI is down and I have to start in safe mode.  

or, now that I think about it is "manual" the option in the disk install?


-W

---

### Post by WoosterB on 2008-03-27
Ok, I brain farted in the above post.  I went to the manual selection and saw my partition.  I then checked it off and hit "forward".  It gave me an error that I have to define a root file which can be done in the partition window.  I'm not sure how to proceed here as the "edit" and "delete" partition do not have anything that suggests they will fix this error.  

I'm not being very courageous in my clicks because the last time I tried something like this I managed to obliterate pieces of my windows partition.  Hence, I'm sorta trying to get some "do this and then do thats"

:)

-W

---

### Post by anuban on 2008-03-28
Actually Deleting the sd6 did the trick, though I had to Ignore the warning as mentioned above.  I still don't understand what it means.](*,)
But fortunately I was able to Clean Install Hardy on top of my Gutsy partition without any problem from the Live CD.
It dual booted properly without any GRUB modification.:)

I would definitely say that "Clean install is better than Upgrade option" because now I have all the things for Hardy and there is nothing which will conflict with Gutsy.  And I don't mind spending some extra time installing some extra software I need.  :popcorn:

I love Ubuntu...:guitar: and I like to be a part of this extremely helpful forum.
Thanks for helping me out 'Pumalite'.

---

### Post by Pumalite on 2008-03-28
You are welcome. Good luck.

[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by frogotronic on 2008-03-30
> **Pumalite said:**
> You are welcome. Good luck.

[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)


Okay, I've got a variation on this original question: I installed HH 64-bit beta as a dual boot with my existing 32-bit Gutsy install to check out the 32-bit vs the 64-bit performance.

I managed to hose my HH install, but no problem - that's why I did the dual boot!

Now I want to reinstall HH over top of (on) the "existing" HH partion and start again with a fresh HH 64-bit Beta (I figured out what I did wrong).

Using the LIVE CD, the Guided partioner wants to resize Gutsy (again) and install another (a third) Ubuntu (HH).  I don't want to do this - I'd like to force it to reinstall on top of the existing HH thereby erasing it and giving me a fresh install of the HH without touching my Gutsy install.

Q:  Do I use the manual option and delete the current HH install (leave the swap alone); then install HH (again) on the partition I just deleted?

Thanks,
CH

---

### Post by Pumalite on 2008-03-30
Use Gparted Live CD and use the method I outlined in this thread.

---

### Post by anuban on 2008-04-01
> **cement_head said:**
> Okay, I've got a variation on this original question: I installed HH 64-bit beta as a dual boot with my existing 32-bit Gutsy install to check out the 32-bit vs the 64-bit performance.

I managed to hose my HH install, but no problem - that's why I did the dual boot!

Now I want to reinstall HH over top of (on) the "existing" HH partion and start again with a fresh HH 64-bit Beta (I figured out what I did wrong).

Using the LIVE CD, the Guided partioner wants to resize Gutsy (again) and install another (a third) Ubuntu (HH).  I don't want to do this - I'd like to force it to reinstall on top of the existing HH thereby erasing it and giving me a fresh install of the HH without touching my Gutsy install.

Q:  Do I use the manual option and delete the current HH install (leave the swap alone); then install HH (again) on the partition I just deleted?

Thanks,
CH

Yes, just select the Manual option...Select the partition you wanted to reinstall.
Delete this partition and then again select it to create a new partition with mount as '/'.
You are all set.:)

---

