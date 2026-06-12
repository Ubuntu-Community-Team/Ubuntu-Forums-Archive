---
title: "installation- total noob Plz help"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by azndreamer781 on 2007-05-25
Ok i just downloaded ubintu live cd and i want to install ubuntu. I only have 1 hd but i make them into 3 part( all 3 is ntfs format) and by the way i got window xp.

The first part is my window xp and i dont want to install on that one and the second part is just data ( my personal stuff)  and i also dont want to install it on that one. but the third part is empty. is there anyway for me to install it on the third partition?

here my hd space.
partition 1 = 61.8 gb
partition 2 = 59 gb
partition 3 = 69 gb

I try installin it like wut you guys said on a other tread. create two more partition with my partition 3
1 for swap and 1 for "/" ( both partition is ntfs) and when i install it it will stop  in the middle of the installation and it will close the instation bar by it self. i dont kno is my disc is mess up or i am doin this wrong.
and what size should i make my swap and my "/" to ( who get more space)

---

### Post by Big Ed on 2007-05-25
> **azndreamer781 said:**
> 
here my hd space.
partition 1 = 61.8 gb
partition 2 = 59 gb
partition 3 = 69 gb

I try installin it like wut you guys said on a other tread. create two more partition with my partition 3
1 for swap and 1 for "/" ( both partition is ntfs) and when i install it it will stop  in the middle of the installation and it will close the instation bar by it self. i dont kno is my disc is mess up or i am doin this wrong.
and what size should i make my swap and my "/" to ( who get more space)

If I'm reading this correctly, you split your third partition in to smaller ones for /swap and root (/). and made them both ntfs?  If so, this is the problem.  Delete these extra partitions (leaving your first two for XP and data).  Then run the install and let Ubuntu load itself into the unpartitioned space.  It will set up /swap and root for you.

Normally your /swap partition is twice the size of the computer RAM.  So if your box has 1 gig of memory, then your /swap should be two gigs.  This isn't always best, but it will do to get you started.  Root will take up the rest.  Later on, you may find that you want separate /home, /var and /usr partitions also.  Don't worry about those now, just get your system running and see how you like it.

HTH,
Ed

---

### Post by azndreamer781 on 2007-05-25
what format should i use to install ubuntu ( ntfs , ext , fat32) and wut about the logical , primay crap which one should i choose.

and do you mean when i get to the place to choose "/" , /home , etc i should just choose "/" for the 3 partition first and install it. i have try this method and the the installer just close it self without any waring or notice( durin the actual installation, i think my disc is corrupt or sumthin)

i dont really kno wut you mean. is it like this?? first i delete my third partition with the editor and leave it there and ubuntu will automatic install it there?

---

### Post by tommcd on 2007-05-26
Choose "manually edit partition table" when you get to partitioning. Delete the 3rd partition. This will create "unpartitioned space" where the 3rd partition was. For simplicty, create 2 logical partitions. The 1st one will be 1GB in size, mount point swap, and file system swap. The 2nd partition will be the rest of the space, mount point / (root) and file system ext3. Alternatively, you could make / around 10GB, and create a 3rd logical partition using what is left as ext3 and mount it as /home.
See this site for good beginner friendly help:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Work your way down the menu on the left of the page.

---

