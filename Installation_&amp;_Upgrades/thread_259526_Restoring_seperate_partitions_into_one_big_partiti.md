---
title: "Restoring seperate partitions into one big partition"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by GrootBrak on 2006-09-17
Because of hard drive constraints and running out of space in some partitions, I decided to redo my whole partitioning.

This is what I did.
I used Acronis to back up my partitions on a spare hard disk.
I had the following mount points for my partitions. /usr /var /home /swap and of course the root.
The problem was the spare disk had a lot of data, so I had to shrink the partitions so it can all fit on one drive.

Next I re-installed Kubuntu on the new disk, but with only a large root and a small swap partition. Now I can see me old files and set-up sitting in the back-up partitions on the spare drive, with no apperant data loss.

Now the bit that I don't understand, is how do I get my original set-up working in the new single partition? 

I found this write up.
Quote:
Re: Repairing the ubuntu 

--------------------------------------------------------------------------------

Good news is your data should all be there. The bad news is that it is now hidden. What I would suggest is that you boot up using a live CD. Mount the current / filesystem mkdir /newhome. Then vi or edit the /etc/fstab and point your new partiton to /newhome. Then reboot and you should be back to your starting point. You can then copy (cp /home/* /newhome - Rf) your /home directories to your /newhome. Then umount /newhome and change /etc/fstab to mount /newhome back to /home. Note that doing this will leave your old home folder alone, but hidden so there is some wasted space on your / filesystem. When everything runs OK you can boot up in the live cd again and delete the old stuff (being careful of course to only mount the old / file system and not the new one). Hope that made sense.  


This is not very clear for me, although the general outline is clear, this seems to me that you effectively rename your old partition(s) to whatever the new ones should be. I want the old data in the new one! Simply copying the data from one partition to another seems like a bad idea.

Any suggestions as to the easiest working method?

---

### Post by kidders on 2006-10-01
> **GrootBrak said:**
> Now the bit that I don't understand, is how do I get my original set-up working

What do you mean by "setup" exactly? Copying your personal files is trivial, but re-integrating your original system configuration is a little more involved.

---

### Post by tagra123 on 2006-10-01
If I'm understanding you want to use the var and home etc partition on that disk. Correct.

Backup fstab file.

```
sudo cp /etc/fstab /etc/fstab.bak.01-OCT-06
```

Edit the fstab file.
```
sudo gedit /etc/fstab
```

Make your file look somthing like the one below (your partition may be hda and you may have used a different file system type)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc               proc         defaults                       0       0
/dev/hdc1       /                   ext3         defaults,errors=remount-ro     0       1
/dev/hdc2       none                swap         sw                             0       0
/dev/hdc3       /home               ext3         defaults                       0       2
/dev/hdc4       /var               ext3         defaults                       0       1
/dev/hdc5       /usr               ext3         defaults                       0       1
```

---

### Post by kidders on 2006-10-01
I very much doubt this is what tagra123 is suggesting, but just in case, _**do not**_ blindly mount your original /usr and /var into your new install ... especially not the /var. It would lead to long-term unpredictable behaviour and, depending on the specifics of your configuration, could make a terrible mess.

---

### Post by tagra123 on 2006-10-01
Oh No.

You can do what I suggested if you are also using the same root partition -- which is what I thought is what is going on. I missed the part about new install. Thanks for catching that kidders. I would have felt really bad for causing extra grief to a fellow ubuntu'er.

If you have data, such as a website then mount it as oldvar and copy the data you need.

My personal preference for things like website (apache) data is to store it in another folder or partition and make a symlink in var.

---

