---
title: "Shrink partition"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2013-12-08
I have installed Xubuntu 13.10 three times now. The first one got messed up because I was trying to clone Xubuntu from my old laptop and I copied over a lot of configuration files - stuff like .libreoffice, .vlc, .mozilla, etc. At least one of them was a mistake because Xubuntu wouldn't boot. I tried using the Live DVD to do a reinstall, but that came out almost as bad. At least it would boot, but it was really messed up. 

So finally I bit the bullet and told the Live DVD to reinstall the existing installation instead of a fresh install. It proceeded and when it finished I was back to where I started from - a fresh install. The "reinstall" option said it would try to save my applications and settings, but it saved nothing. OK, I'm no worse off than if I had done a fresh install, but now I have spent all day reinstalling my applications and getting everything back again only to discover that the "reinstall" did not honor my existing partitions. For my original installation I set up a 50 GB partition for /, 6 GB for swap, and the reimainder of the 1 TB disk for /home. After the reinstall I find that I now have 983 GB for /, 17 GB for swap, and another 17 GB partition that is just labeled Partition 2. I have no idea what the installer was thinking. I certainly was never asked to approve a new partition scheme.

Rather than spend another full day reinstalling a fourth time (I have a lot of custom applications), I would prefer to shrink the 983 GB down to 50 GB, shrink the swap down to 60 GB, and then take the free space and make it /home. The installer may have used 983 GB for /, but all that has been installed so far is Xubuntu and some applications - no data files yet. It will easily fit into 20 GB or so.

Someone please tell me this can be done. Oh, and there are no logical volume things to deal with; just plain partitions.

---

### Post by james2b on 2013-12-08
You can try the Gnome partition editor called GParted, found here; [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) , then you boot to that on a CD and can then edit your partitions.

---

### Post by heir4c on 2013-12-08
You don't have to download gParted separately, you can boot up with the Ubuntu live-DVD and there you open gParted (PartitionManager).
There you can edit your partitions. 
FIRST resize the swap partition to 6GB. IMPORTANT!: resize it from the left to the right so the end of the swap is the end of the diskspace.
Then resize the / partition to the left so you have free space between the / partition and the swap.
Use 30GB for / (give the system a little bit space to work)

Success!!!

Greetings
Gerolf

---

### Post by fantab on 2013-12-08
Post the output of the following:
```
sudo parted -l
sudo fdisk -l
```

So that we can clearly see how those partitions on your HDD are laid out.
"Code speaks louder than words". ;-)

---

### Post by John Jason Jordan on 2013-12-08
> **fantab said:**
> Post the output of the following:
```
sudo parted -l
sudo fdisk -l
```

After posting my original query last night I used Palimpsest (why is that not included in Xubuntu, and why is it so hard to find in Synaptic?) to delete Partition 2, leaving it as free space. Then I went to bed, hoping that this morning I would not feel so annoyed and frustrated. Here is the output:

```
Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  983GB  983GB  primary  ext4         boot

jjj@Devil-Bonobo:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004394d
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1920057343   960027648   83  Linux
```

Also, I made a typo last night, the swap is 17 GB after the reinstall, when I wanted it to be 6 GB as I had done in the first install. Actually, I'm not sure I even need a swap, as the computer has 16 GB of RAM, but what the heck. 

Thanks to those who suggested gparted. I have a number of live "rescue CDs," one of which is gparted-live. I'll burn it and boot to it, and see how it goes. 

Oh, and I also failed to mention last night that the drive is a Seagate hybrid with 8 GB SSD. Naturally I want / to be on the SSD, but I suspect (not sure) that the drive itself automatically moves frequently used stuff to the SSD part, so maybe that doesn't matter.

---

### Post by John Jason Jordan on 2013-12-08
> **heir4c said:**
> You don't have to download gParted separately, you can boot up with the Ubuntu live-DVD and there you open gParted (PartitionManager).
There you can edit your partitions. 
FIRST resize the swap partition to 6GB. IMPORTANT!: resize it from the left to the right so the end of the swap is the end of the diskspace.
Then resize the / partition to the left so you have free space between the / partition and the swap.
Use 30GB for / (give the system a little bit space to work)Gerolf

Since I already had the ISO image of GParted Live I just went ahead and burned it to a CD and booted to it. 

But then things got kind of confusing. Palimpsest had told me that partition 1 was 983 GB and was the boot partition, with a partition 2 of 17 GB (which I deleted with Palimpsest last night) and a 17 GB swap partition. What I saw in the GParted GUI was 17 GB of free space on the right, and one partition of 983 GB. The swap partition that Palimpsest saw was not there. The 983 GB partition had a yellow area on the left, which GParted said was 52+ GB; that is, I assumed it was 52+ GB because that is what GParted said was the smallest I could resize the partition to. 

Since GParted did not see a separate swap partition I assumed that the 17 GB that Palimpsest had seen was within the 983 GB partition - some kind of LVM? If it's an LVM I want to wipe it all out and start over, even if it costs me another day of work. LVMs have their uses, but I totally hate LVMs on my personal computers. I want a separate single partition each for swap, root and home.

Anyway, I resized the 983 GB partition to 98 GB leaving 895 GB of free space, on which I created one partition of the whole thing and formatted it to ext4 to use for /. Unfortunately, / is on the 98 GB partition. Somehow I need to tell Xubuntu to move / to the new partition, and I have no clue how to do that. Hopefully my friend Mr. Google will know.

---

### Post by John Jason Jordan on 2013-12-08
Success!

I found instructions for moving ~/ to a new partition here:

[http://www.maketecheasier.com/move-home-folder-ubuntu/]("http://www.maketecheasier.com/move-home-folder-ubuntu/")

And it went perfectly. I now have a bootable / of 100 GB, of which about 8 GB is used, and a ~/ of 885 GB, of which 17 GB is used. However, swap seems to have disappeared. Not sure why, but I'm just as happy without it. 

The only remaining problem is that upon booting I get an error message just before the login screen comes up. It disappears too fast to read it, but I think it says that something was not found. Bet it's the missing swap.

---

### Post by fantab on 2013-12-08
Though SWAP may not be used with good RAM quantity on board, yet is highly recommended that you have one. And that error probably relates to missing SWAP.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Also 100Gb for '/' partition is not a good idea. You must keep your Data separated from 'system files'. If something were to give in and you had to re-install Ubuntu then it might be a problem with data on the same partition.
If I were you:
20-25Gb '/'
2-6Gb SWAP (If you have enough space then, keep the SWAP size about 1Gb more than your RAM quantity). 
???Gb Data Partition (You can either keep it a simple linux data partition (ie, you don't use any mountpoint at the time of install) or use '/home').

To minimize the SWAP usage you can reduce the [swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") from Ubuntu install.

---

### Post by John Jason Jordan on 2013-12-08
> **fantab said:**
> Though SWAP may not be used with good RAM quantity on board, yet is highly recommended that you have one. And that error probably relates to missing SWAP.
Also 100Gb for '/' partition is not a good idea. You must keep your Data separated from 'system files'. If something were to give in and you had to re-install Ubuntu then it might be a problem with data on the same partition.
If I were you:
20-25Gb '/'
2-6Gb SWAP (If you have enough space then, keep the SWAP size about 1Gb more than your RAM quantity). 
???Gb Data Partition (You can either keep it a simple linux data partition (ie, you don't use any mountpoint at the time of install) or use '/home').

To minimize the SWAP usage you can reduce the [swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") from Ubuntu install.

First, I guessed that the error message related to the missing swap, even though it disappeared too fast to read it. There was a line in /etc/fstab relating to the swap and its UUID, so I commented it out, saved the file, and rebooted. No more error message, so your guess and mine were undoubtedly correct.

As for the amount I set for /, I can always shrink it later, but for now I will keep it at 100 GB. It is a 17" laptop with two hard drive bays and two mSATA slots. Right now I have just one 1 TB hyrbid drive, but I have a 480 GB mSATA SSD on the way. When it arrives I will use clonezilla to put / on it in a 100 GB partition. I changed my mind about ~/ and decided to make it only 300 GB, mostly so I can use clonezilla to put it on the mSATA as well. Then I can use the entire 1 TB hybrid drive for random data. Some day there will be laptop drives larger than 1 TB, and I can always add even more storage later. In short, I am probably wasing some space by giving / 100 GB, but I don't care.

As for the swap, I suppose I could add one but, again, I don't see the need for it now. The computer has two 8 GB sticks and two empty slots for more. My old computer had 4 GB of RAM and I never used the swap. Now that I have 16 GB of RAM I doubt that a swap partition would make any difference at all. But if it ever does, I have lots of free space to create one.

---

