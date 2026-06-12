---
title: "[SOLVED] Stuck at installation! need URGENT help!!!"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by majorkonig1337 on 2007-06-22
I am installing Ubuntu 7.04.

At the partitioning place iam stuck at this screen.

[http://i199.photobucket.com/albums/aa203/majorkonig1337/Screenshot.png](http://i199.photobucket.com/albums/aa203/majorkonig1337/Screenshot.png)
[http://i199.photobucket.com/albums/aa203/majorkonig1337/Screenshot1.png](http://i199.photobucket.com/albums/aa203/majorkonig1337/Screenshot1.png)

Iam a noob when it comes to Linux, Can some one Please help me.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by mikewhatever on 2007-06-22
If you are trying to install Ubuntu, you'll need to create two partition, root and swap. Please follow the guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Also,make sure to understand what you are doing. The error message is telling there is no root partition for Ubuntu.

---

### Post by majorkonig1337 on 2007-06-22
ok!

i kinda understood what i have to do.

Right now iam using a Sheep Dip i got off our office, and the stupid tech guy for some reason, made 4 partitions on an 80gb HDD, so i was getting confused.

I made a 18 GB Root partition, and a 2GB swap partition. 

Now while i was installing a got an error about some kinda disk thingy being "in use" and i was taken back to the partitioning page.

I choose the root partition as 'ext3' and named it just "   /    "  

^^^ did i do something wrong here???

---

### Post by mikewhatever on 2007-06-22
> I choose the root partition as 'ext3' and named it just " / "

^^^ did i do something wrong here???
The screenshots you posted show  neither root nor swap partitions. That must be the problem.

---

### Post by majorkonig1337 on 2007-06-22
I did that after wards. I Deleted one of the partitions listed in the screenshot and made 2 new partitions. I went through that link you posted above and kinda understood what i had to doo. I then made 2 new partitions and, 18GB root and 2GB Swap. Made the root partition 'ext3' and named it "  /    ". And just chose swap for the 2GB partition. It went forward. Then at then end when, after i clicked "Install", i got the error that some kind of disk was in use, and i was taken back to the Partitioning scree.

PS- do i have to name the root as "/root" or just "/" cus thats the only place <i>i think</i> i went wrong.

---

### Post by majorkonig1337 on 2007-06-22
anyone !!!

---

### Post by majorkonig1337 on 2007-06-25
I figured out what the problem was. I had to delete the partition in windows and then make new partitions from that free space in Ubuntu. Its working now, and everything is installed. Thanks for the help though!!!


PS- if i wanted to remove ubuntu, since this is an office sheep dip. How do i safely do that, ive heard stuff about GRUB, and all i can think of that is like garbage stuck back on my HDD, and iam gonna have to scrape it out. (lol) 


thanks

---

