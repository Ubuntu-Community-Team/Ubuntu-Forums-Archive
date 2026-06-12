---
title: "Installed 7.04 and removed it. Want to try again with 7.10. Questions?"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Flukmo on 2008-01-18
Installed 7.04 and removed it. Want to try again, but am afraid same thing will happen. So, questions!

Installation of 7.04 went well. and I liked it. Reason of removal, it took the booting default of my computer and did not know how to change.

1- How can install so that my computer boots WinXP by default after only a delay of 5 seconds? Dont know how to change MBR. If I want winXP Like to start computer and come back later when all done. If I want Kubuntu, ok to wait 30 secs and select itand come back later.
2- How do I tell Kubuntu to install on my E partition which is empty and has 100 gigs. I tried manual install and then I was asked a series of question I had no idea what to answer, so I cancelled. Very simple, I want the whole thing partition on E, the rest automatic/default.
3- When I installed 7.04, it installed itself all over the place while partition E was there with 100 gigs empty and unused.
4- Finally, a problem for later, 7.04 and the live 7.10 cd does not see my sound card. How do I find out if there are drivers for it and if yes, how do I install. Is it same as adding a software package. I did a lot of software packs installation on 7.04, so have experience in that.
5- Tried the new WUBI installer. It's useless compared to the 7.04 version. Not a real install, it is simply a different Live CD thing with volatile mods. For ex. I installed Firefox which was not there after the next boot. 

Many Thanks

Flukmo

===============
Found answer to 5) above here : [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Also, found that GOOGLE VIDEOS with FOLLOWING SEARCH: UBUNTU DUAL BOOT gives more than 10 results. Will watch, maybe can find answers to all above questions. 

Thanks.

Flukmo

---

### Post by smartboyathome on 2008-01-18
1. You will have to edit GRUB after you install Ubuntu to make it the default (after it installs off the livecd, boot up to Ubuntu and type in a terminal gksu gedit /boot/grub/menu.lst, find the entry for windows, add a like underneith the title with the words makeactive). Now reboot (it should have a timeout of 5 by default).
2. Unfortunately, the Partitioner in the installer isn't very clear right now. I would suggest opening GParted (Applications > System Tools), and note which one has 100GBs (or which one has the closest to 100GBs). Select that same one to be used in the manual installation option to be the / folder, and check the box that says you want to format it. Now it should install.
3. That sounds weird, what do you mean by "installed itself all over the place"?
4. What kind of computer do you have?

---

### Post by Flukmo on 2008-01-18
I admit that comment was not very clear and not very appropriate. 

My computer is new and very powerful. Had it built to specs here in Vancouver. It has 2 gigs mem and a 500 gigs HD partitioned as C, D, E, F. CPU is AMD Athlon(tm) 64 X2 Dual Core Processor 4000+, 2110 MHz. When I installed 7.04, all partitions were NTFS. It installed on D which my most used partition, while E and F were empty, but with NTFS. 

I guess what I mean is that on D, the Ubuntu partition has 2 or 3 additional partitions. Sorry for my ignorance. But it was all on D and not all over the place.

Many thanks for your help.

Flukmo

---

### Post by smartboyathome on 2008-01-18
Ok, you must have selected the D partition by accident when trying to install Ubuntu. Make sure that there isn't any data on the partition you are installing to by running GParted as stated in my answer to 2.

---

### Post by Flukmo on 2008-01-19
OK. Now feel more confident so will definitely try this weekend. Looking forward to know more and experiment with Linux.

Many thanks for your help.

Flukmo

---

