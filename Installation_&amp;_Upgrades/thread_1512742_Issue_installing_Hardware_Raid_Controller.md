---
title: "Issue installing Hardware Raid Controller"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by louis802 on 2010-06-18
Hi everyone, I want to apologize in advance, I'm new to the Linux world. I spent a lot of time last week on the net trying to see if anyone else had the same problem. Hence why I'm writing here. 

Here's my goal: I want to create a file-server with Ubuntu and have two additional hard drives in a RAID 1 setup.

Current Hardware: 
I purchased a RAID controller from newegg.com (Rosewill RC-201). 
I took an old machine with a 750GB hard drive (installed Ubuntu on this drive). I installed the Rosewill RAID card via PCI port. Connected two 1TB hard drives to the Rosewill raid card. Went into the RAID bios and configured it to RAID 1.

My Problem:
When I boot into Ubuntu and go to the hard drive utility (I think that's what its called). I see the RAID controller present with two hard drives configured separately. I format and tried varies partition combination and at the end of the day I see two separate hard drives. Just for giggles, I also tried RAID 0 to see if they would combine the drives. Still nothing. 

I wanted to see if anyone could help me with this or maybe lead me in the right direction. Thanks again and sorry for the troubles.

---

### Post by bpb_21 on 2010-08-01
I don't know about the RC-201, but I don't think the RC-215 works all that well with Linux (Ubuntu 10.04).  I don't know all the differences between the models, and I'm just basing this off of a review on Newegg.com of the RC-215 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16816132012](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132012)).

However, when I try to do the same setup you describe with the RC-215 I get the same result.  All the drives are recognized - as separate drives.

---

### Post by igorgatis on 2010-12-10
same with RC-212

---

### Post by ronparent on 2010-12-10
At the price I doubt this is a true raid controller. If it were it would be completely useless with any Linux OS without a Linux driver. I think it is comparable with the raid found in most current MB's which is what the community refers to as 'fakeraid'. If so, the good news is that the Linux dmraid software would probably serve the same purpose as the Windows drivers to to run it in your system.

Looking at the Newegg site and following the link to the manufactures website indicates that the card uses a via chip set. If you have one of the card referenced and are willing to experiment, you could set up two drives in a raid configuration ans see if you could access it in Ubuntu.

Dmraid comes packaged with Ubuntu 9.04 and later distro's. It can be installed on any recent distro of Ubuntu with the 'sudo apt-get install dmraid' command. The command 'sudo dmraid -ay' would tell you if the raid can be activated with Ubuntu. 

I figured I would tell you that before one of the Ubuntu self appointed guru's came along to tell you it is Windows garbage and not a true raid and not worth bothering with. Not true. Fakeraid has most of the advantages and disadvantages of software raid is is usable in a dual boot with windows. Linux software raid would be a better choice if you are booting only linux. Fakeraid is the only choice if you want to share data on the drives between linux and windows. If you are not interested in studying the intricacies of various of raid systems, I would recommend that you simply use these cards to simply increase the number of SATA ports in your system.

---

