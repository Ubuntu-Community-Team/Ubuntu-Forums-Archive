---
title: "Beginner needs partioning help"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by bondboy8 on 2008-03-22
I have to little to no idea about partioning.  I am trying to run the alternate installer for 7.10.  I have an 80 gig hard drive and ive cleared out 20 gigs of room for linux.  I am defraging rite now.  Now i need help figuring out what to do next and how to do it.  I need a lot of details cuz i am very afraid to lose windows since i dont no anything about what I am doin.  As far as I can tell this is the hardest part of the install if this isnt true please warn me

---

### Post by tvtech on 2008-03-22
this install goes pretty smooth I was skeptical the first time.  but I've since done it and redone it and redone it.  

swap partition should be = to your total ram, slightly more if you plan on using hibernation <--hibernation doesn't work well imho
/home partition this is where all your configuration is stored. you should allocate at least 5g for it 4 if you want and give the rest to root.  just set up the partition manager on manual or.... use the following live cd to do the partitioning and then manually select the partitions youve created. 
[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

step by step you'll do the following 

1. turn off the following in windows virtual memory paging file, and the restore back up file.  reboot and defrag this should get your system to a reasonable size, and you can turn them back on when your done.   
2. use the live cd to change the size of your windows partition.  leave the new empty partition blank or set it up as a /root /home /swap partition  or just a /root /swap I never use the home partition. 
3. then throw in the ubuntu live cd and doing a manual partition management select what you want to go where.
4. enjoy ubuntu and reinstall in 2 months when hardy comes out!
5. if your still not sure there are A LOT of step by step tutorials out there that can help just search the forums, and of course the internet.

---

### Post by akash238 on 2008-03-22
i dont get anything about partitioning either
i used wubi for 7.04 fiesy fawn
:)

---

### Post by tvtech on 2008-03-22
because the wubi installer doesn't really install it. it's like cheating.

---

### Post by twright on 2008-03-22
wubi installs it enough :)

just run wubi.exe on the cd and it will install ubuntu into a folder within windows, then when you reboot you can choose windows or ubuntu, it is the simples/safest way as you don't need to worry about partitioning and you can remove ubuntu using add and remove programs

you can convert it to a full install later if you want to

---

### Post by Pumalite on 2008-03-22
After you get tired of wubi; here are some links for you:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by bondboy8 on 2008-03-22
with wubi do u still get all the same benefits of using linux over windows

---

