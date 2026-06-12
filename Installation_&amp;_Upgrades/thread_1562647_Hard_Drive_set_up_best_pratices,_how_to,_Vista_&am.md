---
title: "Hard Drive set up best pratices, how to, Vista &amp; Ubuntu 9.10"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by rweddy1 on 2010-08-27
Hello all, 

I have been running ubunto 9.10 and love it. 
Orginally I was planning on using it from time to time but now with vmplayer and xp I am not sure if I will need my dual boot very much at all.

I have a 400 GB hard drive I want to give more HD space to Ubuntu but after doing some searching read that linux should not be huge. I was going to resize using GParted, put vista to say 50GB, leave Ubuntu along at 67 GB. Then how can I make the left over 275GB for both to used for Data? 


I have my HD set up as dual boot details below:

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a2e9344

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         605     4853760   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         605       40125   317443136    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           40125       48641    68410440    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           40125       48288    65575408+  83  Linux
/dev/sda6           48289       48641     2834968+  82  Linux swap / Solaris


TIA. 

-R

---

### Post by mikewhatever on 2010-08-28
You won't have to do anything other then creating a 275GB NTFS partition. It should be accessible and writable from both Ubuntu and Windows by default.

---

### Post by oldfred on 2010-08-28
If you have Vista use Vista's tools to shrink the Vista partition. It will still want to  run chkdsk after a resize, but if you use gparted and do not uncheck the round to partitions flag it will require repairs.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I used to directly mount my NTFS into /home but now I mount it elsewhere and link it in.
Some alternatives:
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

