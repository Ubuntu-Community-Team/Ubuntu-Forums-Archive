---
title: "Need help installing ubuntu on first partition"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by Predtech on 2008-10-03
Hi guys. I am building a small server with 2 twin 120GB 8MB cache WD drives. I used the new GParted cd to delete any existing partitions and created a 5GB partition at the start of each drive and the rest of it would be the second partition. All partitions are EXT3.

Here's where my problem is, i want to install Ubuntu 8.04 on the first 5GB partition pc the first drive (sda1) and leave sda2 untouched so when it's installed i can have the second partition on both drives exactly the same so i can set up a RAID 0 partition, and then just the sdb1 partition for backing up my server installation.

I am using Ubuntu 8.04 desktop edition because i want to be able to ftp and vnc into it, and also it's what i'm used to on my main pc.

Can someone please tell me how to manually install ubuntu from the live cd instead of using the guided method which either let's me use the entire drive which i don't wanna do or resize my sda2 partition which i also don't wanna do.

Thanks

---

### Post by axionet on 2008-10-03
You will need to download the alternate cd in order to manually install ubuntu.

---

### Post by Predtech on 2008-10-03
good idea, i didn't think of that.

Thanks man

---

### Post by Idefix82 on 2008-10-03
You just select "Manual installation" or something similar in this menu where the different installation options are offered.
Then you tell Ubuntu to mount the existing partition as / but uncheck the "format" box since you have already formatted it.

However, if you want to have a reasonably stable and secure server then your setup is not ideal since you should have a separate /boot partition. This can theoretically go anywhere on modern machines but it is generally recommended to have it as the first partition on the disk. So you might want to split the 5gig partition into a small one, like 100 MB, and the rest then do as I just described but mount the first partition as /boot and the second partition as /.

Apart from that you can decide which other partitions you want to create in the unallocated space (eg. SWAP, /home, /var, tmp, etc).

---

### Post by Predtech on 2008-10-03
sweet, i think that's what i needed to hear. I have never manually installed ubuntu befrore so i was nervous, but hopefully you have solved it for me. I'll do that and report back with my results.

thanks

---

### Post by Idefix82 on 2008-10-03
> **Predtech said:**
> I'll do that and report back with my results.

thanks

Please do!

---

### Post by axionet on 2008-10-03
Seperating the partitions I never liked it just reminds of the old red hat days. 100 mb for a /boot is just a waste of space. 

I only seperate / and /home in case i ever need to reinstall my data is secure on the /home drive.

---

### Post by Predtech on 2008-10-05
ok, sorry for the delay, i had a few busy days. 
Anyways, what i did (after a few different times) i eventually booted into the new Gparted live cd and created an extended partition of exactly 10GB at the start of each drive and in the first one i made a 120MB partition, a <5GB partition and a 5GB partition, and then i made the rest of the drive a primary partition and using the Ubuntu server edition went through the steps you guys told me. I put the /boot on the 120MB drive then the root on the next biggest one then the swap on the 5GB partition, and then  set up the large partition for RAID 0 prior to install by configuring ubuntu to do it. Then the second drive i just have a 10GB partition which will act as a daily backup of my primary install and the second which is a twin of the large partition on the first drive, and made them into a RAID 0.

In case anyone's interested, i know that making a raid drive with both drives on the same IDE channel is not good for performance but i didn't necessarily do it for performance, i did it just so could have a single drive available instead of splitting files when one get's full.

Yes i know it's alot of work to do something like this just so i can be lazy and not have to split files at a certain point, but..... that's how i work, lol.

---

### Post by Idefix82 on 2008-10-06
Edit: obsolete

---

