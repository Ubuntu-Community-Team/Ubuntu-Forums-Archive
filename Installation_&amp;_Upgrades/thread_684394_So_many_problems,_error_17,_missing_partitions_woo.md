---
title: "So many problems, error 17, missing partitions woo...."
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Harryema on 2008-02-01
Where to begin...

I originally had Windows vista, windows XP and ubuntu installed in a triple boot. When i started my computer GRUB starated and I  could select whichever. All fine and dandy... until I decided to get rid of XP since I don't use it any longer. So i go into vista (didn't know about gparted at the time) and i use a paragon partitioner to delete the partition. 

Next boot, Error 17. Oh god. After hours I eventually figured out how to use Super GRUB to restore the GRUB stuff to its happy state and was able to load my original ubuntu, not just from live CD. I then go into my files and I notice that all my partitions were gone. Ew. (Originally I had 5 partiions, 3 for the 3 OS's and 2 extra misc ones) The only one i could see now was, well, the Ubuntu one. Vista, misc, and the  used to be XP one are now gone. 

Anyway, I restarted to try and go to vista to see if that was the same problem, no. Apparently I can't start it anymore. It says error 22: Partition missing. Similar to the the ubuntu fix, I changed the HD(0,1) to HD(0,0) which was the correct one in the startup file that GRUB uses. (menu.lst)

Using super grub again, what happens now is I get a windows 98 loading screen and it goes to DOS saying "Type the name of the Command Interpreter" Holy cow.

Anyway, I try the deleting MBR and fixing it method where I put a windows ME boot disc and and used fdisk /mbr... but I get the same thing, windows 98 loading screen and  "Type the name of the Command Interpreter".

SIgh. I'm aware that reinstalling vista ubuntu would likely fix everything.. but this is just annoying. I've spent hours already. I hope I haven't permanently damaged any sector or whatnot, perhpas you guys have some insight on how to fix this. 

THanks,

---

