---
title: "Partitioning studio"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by ledwardz on 2011-08-23
Hey i'm after installing ubuntu studio alongside my windows. So i have my disk i loaded up the boot menu and ran from cd which works great till i get to the partitioning bit. Normal ubuntu gave the option to partition and it was very easy to do so but im struggling with this. I have had a look at a few threads but no one seems to give any actual answers i figure that i need to make 2 partitions.

1 for the swap and 1 for the root destination. Would someone be able to run me through this or maybe provide a tutorial? I don't know why there isn't a help section about doing this???? maybe i just havn't looked hard enough? anyways any help is much appreciated. Thanks, Lee.

---

### Post by Quackers on 2011-08-23
Please post the output of ```
sudo fdisk -lu
```

---

### Post by Quackers on 2011-08-23
oops, sorry, it's not a live cd is it?
If you post a screenshot of your Windows Disk Management screen it will give an idea of your current partition layout.

---

### Post by ledwardz on 2011-08-23
> **Quackers said:**
> oops, sorry, it's not a live cd is it?
If you post a screenshot of your Windows Disk Management screen it will give an idea of your current partition layout.

hi. first off thanks for the reply. It is a live cd i burned using image burn, by live cd you do mean the operating system is on a cd right??? or at least thats what i did.

 I have 1 500GB hard drive that isn't partitioned as i only have windows on it currently. I was hoping that on the ubuntu studio installation i could partition it. when in the installation i am given the  option to do it manually i just don't know what to do form there? does that help at all? sorry, i'm new to this.

---

### Post by Quackers on 2011-08-23
I believed that the Ubuntu Studio was on a dvd and no live file system was included. When you boot from the cd/dvd do you get an option to try the system first, thereby loading a normal desktop?
If you have Windows on there already then the hard drive is already partitioned. There may be anything from 1 to 4 partitions already in use. It depends on the version of Windows and the manufacturer's preference.
If you choose the manual partitioning what do you see?

---

### Post by ledwardz on 2011-08-23
erm okay no it's not a live cd it does not give me the option to try it. Here is an attachement of my partitions and i will find out exactly what is says about partioning and post it in a minute.

---

### Post by ledwardz on 2011-08-23
> **Quackers said:**
> I believed that the Ubuntu Studio was on a dvd and no live file system was included. When you boot from the cd/dvd do you get an option to try the system first, thereby loading a normal desktop?
If you have Windows on there already then the hard drive is already partitioned. There may be anything from 1 to 4 partitions already in use. It depends on the version of Windows and the manufacturer's preference.
If you choose the manual partitioning what do you see?



Okay so it asks me to select language keyboard additional components CD Rom and Network autoconfig which fails for some reason???? says something about DHCP may not be used.  so i go ahead and enter my ip the net mask and the gateway it then trys to configure the clock which fails because it obviously doesn't have a network connection.  nm tho im sure i can get that working when i have the system up and running.

I then am asked which partition i want to install it on to or make a partition my options are
1. Guided - Resise SCSI3 partition #1 sda and use freed space
2. guided use entire disk
3. guided- use entire disk and set up LVM
4. guided - use entire disk and set up encrypted LVM
5. manual


my manual options are:
1. guided partioning
2.configure software raid
3.configure the logical volume manager
4.configure encrypted volumes

.......

---

### Post by Quackers on 2011-08-23
I'm not clear about what drive E: is. A FAT32 14.84GB partition. Could you elaborate please?
Your main drive is a 500GB drive, which when partitioned for Windows becomes a single partition of type NTFS, size 465.76GB
That's your whole hard drive used by Windows.
If your Windows system is Vista or Windows 7 I would suggest that you first defragment the C: partition at least once.
Then you should go to Windows Disk Management console and right-click on the C: drive (as Windows calls it) and select "shrink". A pop up box will appear telling you by how much you can shrink the C: partition. You can change the numbers yourself to an amount less than those quoted, if you want to, but not more.
In other words you can shrink C: by the amount shown, or less than that amount, but not more.
Once that is done you can boot from the Ubuntu Studio dvd and try again. This time there will be unallocated space for Ubuntu to install into.

---

### Post by ledwardz on 2011-08-23
ha ha ha i was on ages trying to figure out what the fat memory was. I put my phone memory in the memory reader and forgot to take it out...... im such a tool. Okay al give it a go, cheers.

---

### Post by ledwardz on 2011-08-23
> **Quackers said:**
> I'm not clear about what drive E: is. A FAT32 14.84GB partition. Could you elaborate please?
Your main drive is a 500GB drive, which when partitioned for Windows becomes a single partition of type NTFS, size 465.76GB
That's your whole hard drive used by Windows.
If your Windows system is Vista or Windows 7 I would suggest that you first defragment the C: partition at least once.
Then you should go to Windows Disk Management console and right-click on the C: drive (as Windows calls it) and select "shrink". A pop up box will appear telling you by how much you can shrink the C: partition. You can change the numbers yourself to an amount less than those quoted, if you want to, but not more.
In other words you can shrink C: by the amount shown, or less than that amount, but not more.
Once that is done you can boot from the Ubuntu Studio dvd and try again. This time there will be unallocated space for Ubuntu to install into.



yes!!! that worked! it actually worked. Although i still have one more question how do i find my threads? lol..... i know, I'm a noob. can i give u like a thumbs up or something for the help?

---

### Post by mongotk on 2011-08-24
How do you do the same thing for an XP professional computer? I have  tried using an older Ubuntu 9.04 disk, but it does not give the option  to install with Windows? I have one 160 gig disk that is formated with  NFTS. I would like to be able to run both operating systems. I have gone  through the Ubuntu partition portion, but do not know what type of file  the partitions should be or the mounting point so that it will set up  windows on one partition, a swap area, and be able to install Ubuntu on  the last partition. Any help is appreciated.

---

### Post by Quackers on 2011-08-24
> **ledwardz said:**
> yes!!! that worked! it actually worked. Although i still have one more question how do i find my threads? lol..... i know, I'm a noob. can i give u like a thumbs up or something for the help?

No need, but thanks for the tought :-)
You're welcome!

mongotk, you can use partition managers (like gparted) to reduce the size of your current Windows XP partition. You should defragment it first though.
You should also make sure that all your important data is backed up first, and als make sure that you can recover XP if things go badly (ie have recovery discs or installation disc).
Once the partition is resized Ubuntu will offer the "install alongside" option. Or you can set the partitions up manually if you choose.

---

