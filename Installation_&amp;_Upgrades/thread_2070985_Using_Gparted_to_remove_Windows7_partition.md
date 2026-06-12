---
title: "Using Gparted to remove Windows7 partition"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by Exhack on 2012-10-14
Hi Everyone,

I'm running Ubuntu 12.04 in a dual boot set-up, but have finally decided to remove the Windows 7 partition and let rip with Ubuntu. Apart from the fact that 12.04 is a great OS,I'm sick of ruthless, greedy Windows deleting my GRUB.

I've downloaded and had a look at Gparted and it seems perfectly feasible to delete the Windows partition and then enlarge the main Ubuntu partition (I have backed up my Windows stuff so could reinstall if I wanted).

Anyone know of any hidden snags?

---

### Post by darkod on 2012-10-14
No. If you have saved all your windows data, you seem good to go.

Note that if you plan to resize the ubuntu partition later too, it's good to have a backup of ubuntu too. Resize operations sometimes do go bad. :)

---

### Post by oldfred on 2012-10-14
If you have a lot of data in the Ubuntu partition and are moving it left, you are rewriting all the data which may take a while. Any interruption or power failure can destroy data. So as Darko says backups are important.

I prefer just to reformat the NTFS partition as ext4, and create a data partition. To use it easily then you do have to mount in fstab & set ownership & permissions. I have most of my folders from /home in my data partition(s) and link them back into /home.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

Another option is to move /home if larger than what you have as / now.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

---

### Post by Exhack on 2012-10-15
Thanks for that. It's nice and simple and I'll keep you posted.

---

### Post by Exhack on 2012-10-15
Thanks oldfred. There's some reading there so I'll keep you posted.

---

### Post by Exhack on 2012-10-17
I've got the whole file system on a pen drive. I guess that's enough backup, no?

---

### Post by Exhack on 2012-10-25
Thanks again. I've managed to combine two partitions without (so far) any ill effects and am now pausing for breath -:). More news after I've made a Gparted disk so I can unmount and delete the NFTS partition.

---

### Post by darkod on 2012-10-25
You can delete any ntfs partition from ubuntu, because it doesn't run from it. Even if the partition is mounted, you can unmount it yourself.

You don't specifically need Gparted cd.

---

### Post by Slim Odds on 2012-10-25
> **darkod said:**
> You can delete any ntfs partition from ubuntu, because it doesn't run from it. Even if the partition is mounted, you can unmount it yourself.

You don't specifically need Gparted cd.
Although that is all true, I find that the best solution is the Live CD (or DVD), since you can do all of the partition work from there.

---

### Post by Exhack on 2012-11-03
Well, Ive got my Ubuntu computer nd it feels bloody good, if you'll pardon the expression. I made my Gparted disk but, for reasons that I don't understand, the expand/contract button remained greyed out so I couldn't do what I'd planned (see above). So I took the radical root, deleted the Windows partition and set about a clean install of Ubuntu 12.04. This worked reasonably smoothly. But I wasted a few DVDs doing what should have been simple: burning the ISO. 

In case it's of any interest, I'd like to stress that any burn speed greater than 2-4 is liable to fail, also that neither the Windows Installer tool, mentioned in the Canonical how-to nor Ashampoo, the burner bundled in with the Windows 7 installer disk, worked for me. What worked a treat was Imgburn, an open source utility which is simplicity itself to use.I'll never use anything else.

So thanks to everyone who contributed to this thread,Onward and upward!

---

