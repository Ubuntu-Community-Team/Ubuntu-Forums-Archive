---
title: "Feisty install problem"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by TronDiz on 2007-04-20
I am trying to install feisty. But when i come to the installation i get. The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed.

I made ubuntu erase the whole HD and ubuntu made the partition table.

Whats wrong?!

Its a 200gb S-ATA disk so wht does it say SCSI?! :S

---

### Post by saqz on 2007-04-20
i have a same problem...cannot install Feisty.....error  W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb)



what that problem...:confused:

---

### Post by TronDiz on 2007-04-20
Could it be that my Harddrive has ****** up a bit?!

---

### Post by Immolatus on 2007-04-20
You should try manually allocating the partition table. I'm assuming win is on the first part of the drive so the very next should be the swap because the closer to the beginning of the drive the faster it'll run. and . most distro's don't do the by default. Also try installing "Speedfan" in windows and check the drive health you can find it on cnet.com for free.

---

### Post by JackOfAllGames on 2007-04-20
I'm having the same problem as the topic creator:

------------------------------------------------------------------
The creation of swap space in partition #5 of
SCSI3 (0,0,0) (sda) failed.

                                                 [ <-' OK ]
------------------------------------------------------------------

I thought it must be my hard drive, but no, I just purchased SpinRite (I've been meaning to for a while) and ran a full scan of my drive. No problems. None. I tried reinstalling Windows and that installed just fine. ...so I'm back to square one. I have a Dell XPS 400 with the default Maxtor 80GB SATA hard drive. I tried going back, installing Ubuntu 6.10 (to upgrade from there), but the Ubuntu 6.10 GUI won't run. XP I'm just not having any luck so far. =/

EDIT: Well, about 24 hours after starting, I seem to have it working! One of the times after trying a full format on my drive, I tried the partition editor again. I told it to format the unallocated space as ext3 (as I'm sure I tried at least once before). Once it was done, I told the install to repartition that ext3 partition (using 100% of it) and the install seems to have worked. I've just been told to reset to start Ubuntu. Looks like I may finally have it. =P

---

