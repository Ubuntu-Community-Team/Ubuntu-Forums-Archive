---
title: "Install Ubuntu 8.04 without reformat the partition"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Suhendri on 2008-06-13
Hi,

I have  notebook with Ubuntu 7.04. I make big mistake when installed ubuntu 7.04, i didn't make partition for the installation. I only have 1 partition.

And now i want to upgrade my Ubuntu 7.04 to Ubuntu 8.04. But i don't know what i have to do with my existing data. I don't have backup media to backup all data from my notebook.

Is it OK if i install Ubuntu 8.04 to the existing partition with reformat it ?

---

### Post by logos34 on 2008-06-13
> **Suhendri said:**
> 
Is it OK if i install Ubuntu 8.04 to the existing partition with reformat it ?

No, if you tell it to format, it erases everything and you'll lose your data.


You could upgrade to 7.10, and from there to 8.04 (online or from the alternate install cds).  Your data will not be touched. (that is to say, *should* not be, which is why you should find a way--any--to back up).' 

Either that or shrink your root partition and create a second partition.  Copy all your saved files to it and then do a fresh install over root.

Here's a classic example of where a separate /home partition comes in handy.  If you had created a second partition specifically for home when you originally installed 7.04, then all you'd have to do now to get 8.04 would be to install over root, and specify the other partition as the /home (but tell it not to format it). 

However, you can still create a [separate /home]("http://www.psychocats.net/ubuntu/separatehome") now, if you follow this guide. That way your documents will be safe .

---

### Post by pytheas22 on 2008-06-13
> Is it OK if i install Ubuntu 8.04 to the existing partition with reformat it ?

Maybe I'm wrong but I'm pretty sure that this is impossible.

You have two other options to get to 8.04, however, that I can think of:

1. using a live CD, shrink your partition, and then create a new partition in the freed space.  Install 8.04 in the new partition, copy your files over, and then you can delete the old partition completely.  Keep in mind that it's always a little risky to edit partitions, though, so I would recommend first backing up your really important data if at all possible.

2. upgrade over the Internet to 7.10, and then to 8.04.

---

### Post by deci on 2008-06-13
I just did it myself ...
I got a message that there were updates for my system and I noticed that i could upgrade it to a newer version ...
So I clicked upgrade and it turned out just fine
The only bad thing about it is that you need a huge bandwith and data limit of your ISP ... I did it on an avg of 60 kb/s and I needed 4 hours to upgrade

---

### Post by logos34 on 2008-06-13
> **deci said:**
> I did it on an avg of 60 kb/s and I needed 4 hours to upgrade

I think I have about the same dl speed as you, and the last time I did an online upgrade (feisty) it took ~6 hrs! That's why I always prefer to dl the alt cd first on the fastest mirror and upgrade from that.  All told, it takes about the same amount of time (since you still have to download the latest updates) but a successful upgrade is more likely.

---

### Post by Suhendri on 2008-06-14
> **logos34 said:**
> No, if you tell it to format, it erases everything and you'll lose your data.


But how if i choose not to format the existing partition, the installation will got problem or no ?

> 
Either that or shrink your root partition and create a second partition.  Copy all your saved files to it and then do a fresh install over root.

Here's a classic example of where a separate /home partition comes in handy.  If you had created a second partition specifically for home when you originally installed 7.04, then all you'd have to do now to get 8.04 would be to install over root, and specify the other partition as the /home (but tell it not to format it). 

However, you can still create a [separate /home]("http://www.psychocats.net/ubuntu/separatehome") now, if you follow this guide. That way your documents will be safe .

Maybe this is the good solution for me..:) 

Thanks a lot:guitar:

---

### Post by logos34 on 2008-06-14
> **Suhendri said:**
> But how if i choose not to format the existing partition, the installation will got problem or no ?


What I meant was: whenever you install an OS to a partition, the root partition is (re)formatted, which erases everything.

But if you have, say, a separate /home, or /usr, you can do a fresh install of the new release (in this case 8.04), and tell it to use the above separate partitions, but do not check the 'format' option box.  
> 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
"If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory.

Back-up any important data before following this procedure as data loss is possible, and very well may be likely.

   1.

      Obtain an installation CD for the release of Ubuntu 7.04 you wish to install, and boot from it.
   2.

      Start the installation process. When you reach the Prepare disk space stage of installation, choose the Manual option and press Forward.
   3.

      Identify your current '/' (root) partition. Select '/' as the mount point and ensure that Format is ticked. You will lose all data on this partition and the new version of Ubuntu will be installed there instead.
   4.

      Identify your swap partition and set its mount point as 'swap'.
   5.

      Identify your /home partition. **Set its mount point as '/home' and make sure that Format is not ticked.**
   6.

      Continue installation as normal until you reach the Who are you? stage, enter a username and password which exactly match your current username and password.
   7.

      Complete the installation as normal.

Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact." 

---

