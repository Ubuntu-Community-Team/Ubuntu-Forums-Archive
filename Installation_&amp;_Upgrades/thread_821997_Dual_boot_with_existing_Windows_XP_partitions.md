---
title: "Dual boot with existing Windows XP partitions"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by GZ Expat on 2008-06-07
I'm wondering if I could install Ubuntu on one of the existing partitions I have on my HD already, and if it would not effect any of the other partitions.  Example...I have 48G partitions from C through G.  I'd like to take just one of those and dedicate it to Ubuntu.  Can I do that without effecting the other drives?

---

### Post by Partyboi2 on 2008-06-07
Yes you can use one of those partitions for Ubuntu. But all data on that one partition will be lost.  When you get to the partitioning stage of the install I would suggest choosing to manually partition and create a 
/ (root) partition
/home partition (optional)
/swap (About x2 amount of onboard ram but prob no more then 2gig)
partition, which means you will need to divide the partition you are allocating to ubuntu into 2 or 3 smaller partitions. You can create these partitions if you like before you start the install by booting the ubuntu live cd and when you get to the desktop go to Partition Editor (System>Admin>Partition Editor) This will open up gparted where you can delete one of your current partitions (one going to be used for ubuntu) and with the unalocated space create from that  your ubuntu partitions. Then after that start the installer and use the partitions you created for ubuntu.

---

### Post by avtolle on 2008-06-07
Be sure you know the device/partition identifier under linux for the partition you are reformatting and installing Ubuntu on.

---

### Post by GZ Expat on 2008-06-07
Partyboi2 - Thanks for the advice.  I'll poke around a bit for a step by step to doing this...like I said, I am completely new to this and haven't the complete computer skills that make me feel fully confident in doing this.  Any additional links you can point me to would be helpful.

---

### Post by Partyboi2 on 2008-06-07
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.pcmech.com/article/installing-ubuntu-linux/](http://www.pcmech.com/article/installing-ubuntu-linux/)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
If you are unsure about anything just post the question and somebody should be able to help you.

---

### Post by GZ Expat on 2008-06-14
Thank you all for the assistance.  I've taken your advice and run the install and re-partitioned my HD accordingly.  I'm back with Ubuntu and waiting for it to update as I type.  Woot.  

I'll be back for more advice, that's for sure.

---

