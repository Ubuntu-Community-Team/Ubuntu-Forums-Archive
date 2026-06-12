---
title: "Trying to install 6.06 LTS"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by bjk03 on 2007-07-18
I'm trying to install with the Alternate install CD. My system specs are as follows: Gateway E-9425, two 1.6 Ghz Xeon processors, 4GB 667MHz DDR2 Fully Buffered, Registered ECC RAM, RAID 1 (2 500 GB SATA drives) Gateway LSI1068E 8-port (4i+4e) SAS HBA MzBoard controller, Matrox G200 Graphics with 2.25MB Video Memory.

Here's my issue, I chose text mode to install from, things started out OK. Then I got to where it said starting up partioner and the progress bar seem to get to 100 % and then I was left with just a blue screen with a grey bar at the bottom (no text on the screen).  The server just sits there, I left it alone for an hour and came back and its still sitting at the blue screen. :confused::confused:

---

### Post by wpshooter on 2007-07-18
Hmmmmmmmm, quite a machine.

Did you check the integrity of the CD by running the verification function that is found on the initial boot screen menu ?

---

### Post by bjk03 on 2007-07-18
Yes I did, I had burned the disk at 48X and at 24X, I ran into this same problem with the CD burned at 48X so I burned one at 24X, had the same problem and then tested that CD, which tested OK.

---

### Post by bjk03 on 2007-07-18
Just for the heck of it I try booting off a 7.04 live CD and it worked. I'm also downloading 7.04 alternate install to see if I can get it to install.

---

### Post by tgalati4 on 2007-07-18
For data integrity, you should be burning at 10X or 12X.  Most fast media can handle the higher burn speeds for WAV files (i.e. music) that has built-in viterbi/reed-solomon error correction.  Data disks are more prone to error bits so I would use the slower burn speeds.

Always check the MD5 sum after the burn and compare it to the repository's value.  A little time spent here will spare you some headaches.

---

### Post by bjk03 on 2007-07-18
The slowest I can burn at is 16X. The MD5 sum was the same as the repository's value.

---

