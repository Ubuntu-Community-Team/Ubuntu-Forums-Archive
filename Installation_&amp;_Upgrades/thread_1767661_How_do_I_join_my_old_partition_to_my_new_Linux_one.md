---
title: "How do I join my old partition to my new Linux one?"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by acidincense27 on 2011-05-26
Hi, I have a 200GB hard drive, and today I used Wubi to install Ubuntu on a new 20GB partition. I only allocated 20GB because I was just going to try it out, and needless to say, I fell in love with it. The only problem is that I have all my old files, music, movies, photos, songs I've written, and other stuff on my old Windows 7 partition. I can still access them, but I'd like to get all my old Windows crap off the disk. I want Ubuntu to be my only OS. My question is, is there a way to join both of my partitions and get Windows off, but keep all my music, documents, and other stuff? I want all 200GB to be on the Ubuntu partition. Help is greatly appreciated.

Thanks for reading,
Evan

---

### Post by Hedgehog1 on 2011-05-26
[SIZE="3"]**EDIT:** I missed that you have a WUBI install - Please follow the advice from **mick222** - it is your only real option![/SIZE]

**EDIT: This if for non-wubi**: While it is not possible to 'merge' two partitions together, you can get the same 'net effect' by doing this:

1) Boot into windows and do a defrag on your Windows partition. This will be the last time you ever use Windows.

2) Boot into Ubuntu, and copy as much data as you can from your Windows partition (it may not be all the data).

3) Delete the data you have managed to copy from the Windows partition, and then use Gparted to shrink the Windows partition down.

4) Boot from your Ubuntu LiveCD, and using Gparted from the LiveCD, expand your Ubuntu partition to use the new space.

You may have to repeat these steps until all your data is moved into your Ubuntu partition.

Once all your data has been moved, boot from the LiveCD on last time, and use gparted to delete the Windows partition and expand your Ubuntu partition to fill the disk drive.

Now Boot into Ubuntu, and get rid of the 'Windows' choice in grub be doing this:

```
sudo update-grub
```

***The Hedge***

:KS

---

### Post by mindstorms83 on 2011-05-26
nevermid, The Hedge explained it much better than I did!

---

### Post by mick222 on 2011-05-26
You'd be better to back up your windows files and do a full install of Ubuntu. Wubi is ok to start with but if your windows partition becomes corrupt you will lose everything. Use either g parted ti resize the windows partition or use Windows Disk Management if you use windows make sure you defrag first.Your windows partition can be as small as 30gb leaving plenty of space for Ubuntu.
  You can then install Ubuntu and still have a working windows for things like gaming that don't work well in Linux. I'd also look into creating a separate /home partition.
 See here for basic advice [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
  By the way most people dual boot even though they rarely if ever use Windows

---

### Post by acidincense27 on 2011-05-26
Okay, I'd like to do that, but here's the deal. I have about 65GB of music that's taken a long time to acquire, about 60GB of video data, and about 50GB of other stuff, my work, photos, art, etc. All that I'm trying to really do is have all my entertainment files on the Ubuntu partition. Wouldn't I be unable to perform a backup of it since there wouldn't be enough space?

---

### Post by acidincense27 on 2011-05-26
Or is there no way to expand my Ubuntu partition? My logic (which I'm not sure is possible), is that I could keep cut+pasting the files to my Ubuntu partition, and continue to do so, while after each move, I expand the Ubuntu partition.

---

### Post by mick222 on 2011-05-26
You should be able to access the files from Ubuntu . 
What i was saying is a full install is safer than one under windows with wubi.
    You should really have all that data backed up somewhere a external hard drive would cost a lot less than losing it if your hard drive failed

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]Hi,
I'd **highly recommend moving your music,videos,etc. to an usb hard drive!**  A brand new 350gb hard drive would cost maybe $69.00 or less. Or you  could move them to double layer dvds but that would take a lot of them.  Or you could use a blue ray burner since blu ray discs hold up to 50 gbs  I think But one usb drive would be simpler and you could backup your  linux data and or. partitions to it if you get 350 gb or larger and  partition it into 2 partitions one for the Windows data and one for the  linux data. Next best would be usb thumbdrives. You would need at least 4  of them 64 gb each to copy that much data to. Or a paid cloud plan, I  mean like Mozy, Norton or of Ubuntu One cloud to upload all that data  to  **Anyway, take Mick222's advice in post no. 4!**. These are my suggestions. Also if any of your music or videos were DRM MAKE SURE YOU COPY THE DRM KEYS with them![/SIZE]

---

