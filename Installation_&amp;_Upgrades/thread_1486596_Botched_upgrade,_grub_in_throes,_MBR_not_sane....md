---
title: "Botched upgrade, grub in throes, MBR not sane..."
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Silent Warrior on 2010-05-18
*Takes a deep breath*
Right, I only gone and dunnit now... So, here I was, having just applied the last batch of updates for Karmic in preparation for a smoother transition to Lucid - planned using a fresh install, and for a number of reasons. On popping in the installer, it won't list my IDE harddrive in the list of partitions where to install. I have this IDE-drive and two SATA-drives - the latter two are crammed to bursting with Windows-stuff that I'd quite like to keep.
But since GParted recognized the IDE-drive, I thought, hey, no sweat, I'll just format the /-partition and try again. No go. So, there I am, with a mostly EXT4 /home, swap, and clean /-partitions ('upgraded' EXT3 to 4, no reformatting /home...), thought I'd give that a rest and pop into XP for a spell - and Grub throws an Error 17! :(
Well, damn, says I. After poking and prodding in BIOS, attempting to recover/reinstall Grub using other LiveCDs - which didn't work, though Mint 7 (Jaunty?) successfully discovered my IDE-drive through the installer - I thought I'd go and have a look at what XP's repair console had to offer. Brace yourselves...

After running a couple of [fixboot]s, I used fixmbr. On all drives. ](*,) My Linux-drives now insist they're FAT; root, home, and swap all. All isn't disaster-ville, though - I had just realized I was in the market for a fatter harddrive (SATA) - expecting it to arrive today, in fact - so some kind of backup or rescue-operation should have quite enough space, with the /home-partition being only 60 Gb or so.

Now: How do I go about recovering my /home-files? I see in Synaptic this little utility 'ddrescue'/gddrescue which seems to offer the proper functionality.
What about Bacula? ext3grep? friendly-recovery? magicrescue? mondo, even? Are either of them overkill?
I'll have to run this off a LiveCD, but I guess that's the best way regardless. apt-get update FTW.

But what's with the installer not spotting the IDE-drive while GParted does? It's even listed in Places! Even Windows read it with no difficulty (with that EXT-driver for Windows installed). I read some time ago that Fedora planned to drop some form of IDE-support, but can that really be what's bitten me now?
Hm, come to think of it, I just installed sidux Moros on my other, older hardware, IDE up the wazoo... No hitch. Also no SATA-support, possibly a drained battery - the motherboard isn't keeping time, and gave me lip about the last time I mounted a partition - January 2010 - was ten years in the future. Mkay.

---

### Post by oldfred on 2010-05-18
If you have not written to the partitions, testdisk may recover them completely. I have not used it but others have and sometimes it works. You may have to enable universe to download it.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).

---

### Post by Silent Warrior on 2010-05-18
Running the installation (of testdisk) off the LiveCD right now... Thanks for the tip. I don't know if it's because of my... efforts, but during POST, SMART gave me an alarm about "some" IDE-disk showing signs of deteriorating health. Well, I suppose I've had that one since 2003, facing fairly heavy use. Let's see if it changes once the partitions are set straight, though.
So, that's the bad news. The good news is that the new HDD arrived yesterday, and I'm going to pick it up as soon as the shop's open. (As well as a jar o' honey, and a multi-disc player... an' a chassi that won't torch my graphics cards.)

#¤"#¡@$&#8364;¥! It doesn't show up as an available disk anymore! Trying again from Windows...

Phew! There it was! Aaaaaand... Looks good, asks for reboot...

[Breakthrough?]
Okay, after running Testdisk through Windows (#¤%$¥£¥ harddrive-thief you!) my drive is now brought back to visibility in GParted and Disc Utility. GParted reported corrupt EXT2 superblock, though, so I'm taking another pass with Testdisk and this time performing a Deeper Search instead of just restoring the partition-table.
I see a few warnings about incorrect heads, and cylinders per track, otherwise it's looking up.
Oh, and I apparently didn't get the new drive - should arrive later today, in fact, but I wantz it with the chassi so I don't have to run back and forth so much... Too exciting a week, this.

[Update again]
No, still no luck getting the drive to show in Ubuntu. It's recognized by any and all partitioning-utilities, but not the installer. Well, I think I'll have my new drive today - maybe I can gddrescue my stuff then.

---

### Post by Silent Warrior on 2010-05-23
Dude, this deserves a bump! I seem to have succesfully salvaged my data! *Wild party ensues*
Hey, it only took me some 3-4 days, too. And it's a +10 at least for Testdisk. It took me some time to understand what the arrow-keys could do, but with some wizardry, a reboot (or five), I'm now copying some ~93000 files weighing in at just over 46 Gb - would've sucked hard to lose all that.

For reference, the commandline-invocations I used were the following:
```

sudo testdisk # Went with some defaults, then analyzed, analyzed deeper, used arrow-keys to set the Windows-recovery-faked FAT-partitions as D, and my three Linux-partitions set as * and P, then made an image
sudo mkdir /mnt/saf
sudo mount -no loop -t ext4 <path-to/image.dd> /mnt/saf
sudo nautilus # Had to do this as I didn't have permission as a normal user to copy the data. Still, I set permissions on the /home-folder to allow my normal user to read/write and own, and checked that the rest of my stuff reflected this change, then initiated the copy.
```
And some 25+ minutes later with nearly 30 Mb/s transfer-speed, I'm happy! And soon IDE-free!

(Oh, I just had to add that I feel... prrrretty good about myself right now. My first HDD-recovery without hired help! *Sniff* )

---

### Post by oldfred on 2010-05-23
Glad to see teskdisk worked for somebody. 

Some seem to have less good results, not sure if they do not follow details or disk is so bad it cannot be salvaged.

---

