---
title: "Shrink Windows, Move data over to Ubuntu, and separate home from root"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by Eggby on 2010-06-06
[A picture of my hard drive setup]("http://i.imgur.com/LARFl.jpg")

I'm trying to change my Linux partition to have my "root" and "/home" partitions separate to make upgrading easier.  In addition, I'm trying to move my music/videos/documents out of my large Windows 7 partition onto the /home partition I want to make.  And then shrink the Windows partition again, just to keep it around in case I need Windows for something.  What's the best way to do this?
I was having difficulties shrinking my Windows partition with GParted.

**EDIT:** I just remembered that my Windows partition is currently hibernating.  Fixing that will (hopefully fix this problem)

---

### Post by darkod on 2010-06-06
If you are trying to resize /dev/sda1 mounted like this, it won't work. That's why it has the key symbol, locked.

Otherwise, you will probably have to move the data temporarily on external hdd, shrink /dev/sda1 and create new /home partition separate from /. There was some good website about the procedure but can't remember it right now.

---

### Post by Eggby on 2010-06-06
> **darkod said:**
> If you are trying to resize /dev/sda1 mounted like this, it won't work. That's why it has the key symbol, locked.

Otherwise, you will probably have to move the data temporarily on external hdd, shrink /dev/sda1 and create new /home partition separate from /. There was some good website about the procedure but can't remember it right now.I just had it mounted so you could see the bar showing how much free/empty space was on the partition.

---

### Post by darkod on 2010-06-06
> **Eggby said:**
> I just had it mounted so you could see the bar showing how much free/empty space was on the partition.

No problem, I just wanted to point it out, in case you didn't know. :)

---

### Post by Eggby on 2010-06-06
> **darkod said:**
> No problem, I just wanted to point it out, in case you didn't know. :)I appreciate it.  No offense done.

---

### Post by oldfred on 2010-06-06
Your current configuration does not lend itself to a large /home. I would just shrink the NTFS partition and you probably will have to copy to external in restore. Windows is not happy unless it has 20-30% free space, so depending on how much you move out will determine how much you can shrink windows. 

With win7 it is best to use the windows tools to shrink the windows partition. All other partition editing you can use gparted from the Ubuntu liveCD or download a gparted liveCD. 

I used this to move to a separate /home. But someone had issues and I may have modified her command as I also looked at other sites. Check man cp for explanation of -a.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Her command to copy:
find . -depth -print0 | cpio --null --sparse -pvd /new/
I used cp as other sites discuss but you have to include the -a option
Without -a and copying as sudo root takes ownership, use -a or ownship is not correct.
sudo cp -a source dest

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

