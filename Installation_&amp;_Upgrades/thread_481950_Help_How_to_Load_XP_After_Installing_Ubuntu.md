---
title: "Help: How to Load XP After Installing Ubuntu"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by apolloxi on 2007-06-23
If this has anything to with it (and I suspect that it does), I may have made a mistake when partitioning the HD. I was nervous/confused about all the choices I was offered (since I understood none of them), so I picked "Guided - Whole Drive."

But, when I press ESC when Ubuntu is booting, I don't see "Windows XP" as one of the choices. I see other Ubuntu-related things. I was wondering what I should do to enable me to also boot Windows whenever I want to, and if my partitioning choice has anything to do with this problem.

---

### Post by mikewhatever on 2007-06-23
"Guided - Whole Drive."
Does that mean formatting the whole drive?
In Ubuntu can you open Applications>Accessories>Terminal and post the output of the following command > sudo fdisk -l

---

### Post by IamSoulRider on 2007-06-23
Take a look at this guide, it is very informative on installing with partitioning, even giving you a screenshot at each stage of the process.

According to the guide you have wiped your whole hard drive.  Sorry but windows is no longer on your machine.

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by apolloxi on 2007-06-23
I figured as much. I had a feeling that might've been a mistake.  :(

I still have my Windows XP CD, though, so could I still install it?

And, here's the output, if it'll still be helpful:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7204    57866098+  83  Linux
/dev/sda2            7205        7297      747022+   5  Extended
/dev/sda5            7205        7297      746991   82  Linux swap /

---

### Post by IamSoulRider on 2007-06-25
You'll need to reinstall windows.

Use the windows disk and make 2 partitions, the first one for windows, the second for Linux.  

Install windows on the primary partition, then you will have to install linux again on the second partition.  If you use the manual option when you come to install linux, you will then just be able to select the correct partition and install away with no problems.

I'm afraid you have to install windows before installing Linux if you want to dual boot.

---

### Post by Pumalite on 2007-06-25
Better yet, use Gparted. Decide how much to allocate to each one. Format Ubuntu partition ext3. Windows ntfs. Install Windows first. Install Ubuntu and in 'partitionong':  use 'Guided>Largest available space'. (the Ubuntu partition, formatted ext3.)(Ubuntu will recognize Windblows and load it automatically at boot).

Good Luck!

---

