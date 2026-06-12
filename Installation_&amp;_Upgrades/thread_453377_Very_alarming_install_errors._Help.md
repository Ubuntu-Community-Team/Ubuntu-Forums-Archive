---
title: "Very alarming install errors. Help?"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by mastergandalf19 on 2007-05-24
Im installing Ubuntu 7.04 Alternate i386 and its screwing up everytime in the install process when i boot from the cd drive. Error is ISOLINUX: Disk Error 80, AX=4280, drive 9f. Any ideas? Oh and its also saying bad keyword in config file? Im truly stumped as im not an experienced linux user in anyway, and im installing on a recently formatted HDD. however, i think it cud be due to the mismatching md5 sums, ive download 4 times now and theyre all different (the md5 file and the iso itself) from the websites database. Im getting worried that I might not be able to get a reliable torrent download, and the mirror from the UK site is cripplinglyslow. Any ideas?

---

### Post by wpshooter on 2007-05-24
Are you burning the Ubuntu CD at 4X or less ?

Have you checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by mastergandalf19 on 2007-05-24
I burned it at 8x, but tht seems to be a bit too fast. What are those initial verification screens. Ok ill provide some more detailed info on my setup.

2.8ghz p4, 120gb hdd, 128mb Geforcefx5200, 512mb ddr2 ram, running XP Pro on 50gb, and a blank partition of 60gb for Ubuntu Studio (Hopefully). Oh and none of the md5 hashes match the ubuntu hashes...i think that might be a BIG problem aswell.

---

### Post by hardyn on 2007-05-24
if your checksums are mismatching, you are getting bad downloads, its really that simple.

what about a direct download from ubuntu.com?
what about buying a disk?

---

### Post by mastergandalf19 on 2007-05-24
But i want to use ubuntu studio, and ubuntu.com doesnt have it.
Ok some progress, i burnt it at ONE times speed and it got to the install screen, it proceeded to load the kernel and then it crashed, displaying at the very bottom of the screen all kind of numbers and references and garbledegook. Any ideas on that?

---

### Post by mastergandalf19 on 2007-05-24
Oh yeah, and im using the Bittorrent streams like everyone else is. I tried the one and only direct download and its slower than an asmatic ant with some heavy shopping...

---

### Post by wpshooter on 2007-05-24
Sorry did not notice that you are using alternate CD.  The verification function is not on alternate but is on DESKTOP (live CD).

Am I correct that you are NOT using DSL ?

If you are on dialup, I would suggest that you get a friend that has DSL to download both the ALTERNATE & DESKTOP CD version for you.

---

### Post by mastergandalf19 on 2007-05-24
Im on 4mb cable. But im also on wireless, so even if a gnat farts the signal randomly drops out and dies, killing my download. FFS. Whats an alternate cd and a desktop cd? I cant find the desktop cd in any of the ubuntu studio download section. Why couldnt they just release a bog standard version! so i have to download both, then burn them both? Or just one, or the other? HELP!

---

### Post by hessiess on 2007-05-24
try using bit torrent

---

### Post by mastergandalf19 on 2007-05-24
Is that more reliable than Bitlord, or Bitcomet?

---

### Post by Maxtine on 2007-05-24
mastergandalf19 may I suggest you check out the download site  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Choose a location near you and download the ISO.  Then follow the directions at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)   
Make sure that  all  equipment  is turn on. Do a clean install, delete all the partitions and this time create a separate /home and anyothers that you think you may need. Then install Automatix2
Here's more info about alternate CD version, [http://ubuntu-releases.cs.umn.edu/7.04/](http://ubuntu-releases.cs.umn.edu/7.04/).
You can also see screenshots of the partitioning phases here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

