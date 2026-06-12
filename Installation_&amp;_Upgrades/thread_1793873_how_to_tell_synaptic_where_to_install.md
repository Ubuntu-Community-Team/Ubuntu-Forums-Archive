---
title: "how to tell synaptic where to install?"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by schmendrick on 2011-06-30
Hello Guys,

I am now a proud owner of an SSD on which my new ubuntu resiedes on. 
it is installed and working, and my old HD is mounted on /media/hd, both SSD and hd having ext4.

As space on the SSD is limited, I wonder how i am able to tell synaptic where to install new applications?
I only want to have linux, and everything needed for compiling on the SSD, all the rest of the apps i want to install should go to the hd.

how can i do this?



i searched on the net for this, but it surprised me that no one else seems to have the need for this.

---

### Post by mastablasta on 2011-06-30
when you partition you will have to put system on SSD
 
applications are installed all over the place anyway. and libraries are shared. if you have 10 or 20 GB SSD just stick root on SSD and /home on one of HDD.
 
EDIT: item 3: [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)
 
maybe you could move a few other folder like lib to HDD as well.

---

### Post by Cheesehead on 2011-06-30
Mastablasta's suggestion is much easier than trying to move the install locations of packages.

Install locations are determined by your apt config and by the packages themselves - the system needs to install packages in predictable locations. If you change those, plan on breakage!

---

### Post by schmendrick on 2011-07-04
hm, okay, i understand.

i now put /home onto the HDD and tried to put most of the rest onto the SSD.

and just made a special folder in my home directory mounted on the SSD where i put my build environment. 



thank you guys for your suggestions!

---

