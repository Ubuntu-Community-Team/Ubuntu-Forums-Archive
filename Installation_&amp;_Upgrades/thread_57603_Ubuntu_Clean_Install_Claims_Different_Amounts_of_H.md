---
title: "Ubuntu Clean Install Claims Different Amounts of Hard Disk Space..."
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by shanghaipi on 2005-08-17
I installed a clean install of Ubuntu onto my 60 GB Hard disk and it took up 1.5 GBs of Swap and 5 Gigs of Ext3.  So I went to install Hoary on my 13 GB Hard Disk (so I could fiddle around with Breezy) and it installed 565 MBs of Swap and ONLY 2.5 GBs of Ext3....What's the deal?

How is it that Ubuntu is a smaller size on my smaller Hard Drive?

ps - I'm using Gparted to find this information.

---

### Post by shanghaipi on 2005-08-17
How big was your Ubuntu's initial Ext3 installation (include how big your hard drive was)?

PS:  Okay, I went on Irc and understand the cluster size part...but why does Ubuntu take up 5 gigs of my 60 gig hard drive!!!!!!!!

---

### Post by az on 2005-08-17
You are refering to the size of the partition, and not the size of the installation, right?

Depending on how much memory you have (and how much hard disk space) the installer will customise the size of your swap space.  If you have a big enough  hard drive, the swap will be twice your ram (as a rule)

Whatever space is free on your disk will be used for the installation.  If you do not hve more than 2.5 gig of free space, ubuntu will not shrink another partition unless you tell it to do so when you install.

Is this what you mean?

---

### Post by shanghaipi on 2005-08-17
Size of the installation actually.  Sorry if I wasn't specific.  Okay, so I installed Ubuntu (again...):

My swap file size is 1.5 gb
        And

I have 5 gigs out of my 58.5 gigs that is used up on my Ext3...

This is after a clean installation.  So how come Ubuntu takes up only 2.5 gigs of my 13 gig hard drive and 5 gigs on my 60 gig hard drive?

---

### Post by az on 2005-08-17
An out-of-the-box install takes up 1.8 gigs of hard drive space.

---

### Post by matthew on 2005-08-17
I saw this thread earlier and I knew there was a reason, but I wanted to do a little research first before responding. I have an idea of why this could be happening. When a file system is created it breaks the space on the hard drive into segments called "blocks." The blocks may be small or large depending on the options chosen during the install. When data is written to a block, the entire block is considered to be used, even if it is only partially written to. In one sense this is good because it gives some space to add to the data without requiring the use of another block. In a large-data storage use this would be really good. Also, wit the increasing size of hard drives this is not a big issue as only rarely is the whole drive needed.

Now, what I think is that when the filesystem was created on the smaller drive, smaller sized blocks were created and when the filesystem was created on the larger drive, larger sized blocks were created.

So...this means that the same amount of data required the "locking up" (probably not the correct technical term) of more space on the larger hard drive due to the larger sized blocks being used.

Okay, that's my thought. Discuss amongst yourselves.

---

### Post by shanghaipi on 2005-08-18
Alright, well, I'm going to delete my 60 gig hard drive in Gparted on my other hard drive Ubuntu system.  Then reinstall.  How would I solve this problem, 3 gigs or hard drive space is a lot of space to missing out on.

Any ideas?

---

### Post by matthew on 2005-08-18
I am not sure you really need to do that. Here's why. 

Even though the blocks are shown as used, there is still some space on them that I believe is available. This minimizes fragmentation as it increases the space between files that are unrelated, so if there is an update or change your hard drive does not need to reallocate new space somewhere else on the hard drive, but just puts the new data next to it in the space of the old data, even if it is a bit larger. So, it's not a bug/problem, it's actually a feature. When a new partition is created on a larger drive the larger block size is chosen to help with disk maintenance later--especially since it is getting more and more likely you won't really need all the space as drives get larger. That is my understanding, and I think it is accurate, but I could be mistaken.

Now to what you want to do. I don't know of any way in gparted (or qparted, or parted) to tell it how large/small to make the blocks when it creates a filesystem for a partition. As far as I have seen it is chosen automatically. I did some exploring again in gparted today and a quick look did not reveal to me any method. You can specify block size from the command line using the "mkfs" command or it's relatives "mk2fs" and others. I have never done this. If you want to pursue it you will have some research ahead of you. You may enjoy that or just decide it isn't worth the trouble since someone who really understands the filesystems well thought doing it this way was good. Your choice. 

If you decide to press on all I can suggest is
1. From a command line in the terminal type "man mkfs" and read it all. Look up the man pages for he related commands it lists at the bottom as well.
2. Do some Google searching for "mkfs" "ext2" "ext3" and related topics as you see fit.

Sorry I can't do anythig more than that for you...I really wish I could.

---

### Post by shanghaipi on 2005-08-18
Your probably right.  I installed all the applications I needed on Ubuntu and referenced the initial install and it went from like 5gigs to 5.8.  I just thought it might have something to with a previous installation of Ubuntu.  I reinstalled Ubuntu twice and the same thing resulted (plus I'm pretty sure that the paritition editor on the Ubuntu install disks erases your previous installation unless dictated otherwise.  I'll put all my mp3s on it and see what I come up with.

But thank you for your attention and explanation.  Much appreciated.

---

