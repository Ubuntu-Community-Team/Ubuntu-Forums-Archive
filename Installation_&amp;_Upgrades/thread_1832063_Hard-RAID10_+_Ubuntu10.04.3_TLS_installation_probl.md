---
title: "Hard-RAID10 + Ubuntu10.04.3 TLS installation problem"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by danielfwi on 2011-08-24
Hi all, 

Please help me with this: I got a new server assembled, motherboard is Asus P8Z68 Deluxe, 4x2TB physical hard-drive. trying to configure as RAID10 then install Ubuntu.

Here is what i did: start server- using Ctl+I go to configure RAID, i can see 4 hard-disks(non-raid), then i selected create raid, got an option to use RAID10, then got about 4TB space automatically filled in the size session.
Then selected create volume. After that, i see 4x1.8 TB disk all as "memeber". 

Up to here, am I right? I am wondering, of the 4 disks, which one is playing raid1 which ones are playing raid0?

Then i decide to install OS, booted using alternate installation disk, select language, time zone, keyboard, then detect disk. 
Here is the strange part, the installation disk can detect and ask me whether to activate RAID. i select YES, then i can see 2X2TB volumes are listing there(shouldn't i see 1X 4TB volume???), i got confused here, cus dont know which one should i install os on. 

I tried choosing a random one, but after installation, i could not boot into the system. 
I dont know where the problem is . 
Please help!

---

### Post by YesWeCan on 2011-08-24
Hi and welcome to the forums.

I don't understand exactly what you did. Did you try to set up RAID in your bios first? Is that what you mean by Ctrl-I?

You don't want to use your motherboard RAID for linux. It is meant for Windows. Unless you intend to install Windows on your array you should not use it. So switch it all off in the bios and start again.

The Ubuntu alternate install CD will create the linux RAID 10 for you. You need to create 4 partitions and then add them to a RAID array. You will need two or more boot partitions of about 500MB and add them to a RAID 1 because the version of Grub in 10.04 probably cannot boot a RAID 10 but can boot a RAID 1 (it can be on 2 or more drives; 2 is enough to ensure booting if a drive fails).

---

### Post by danielfwi on 2011-08-25
> **YesWeCan said:**
> Hi and welcome to the forums.

I don't understand exactly what you did. Did you try to set up RAID in your bios first? Is that what you mean by Ctrl-I?

You don't want to use your motherboard RAID for linux. It is meant for Windows. Unless you intend to install Windows on your array you should not use it. So switch it all off in the bios and start again.

The Ubuntu alternate install CD will create the linux RAID 10 for you. You need to create 4 partitions and then add them to a RAID array. You will need two or more boot partitions of about 500MB and add them to a RAID 1 because the version of Grub in 10.04 probably cannot boot a RAID 10 but can boot a RAID 1 (it can be on 2 or more drives; 2 is enough to ensure booting if a drive fails).

I am still a newbie here, just realized the alternate install CD can do RAID10. 
But i still got some confusion:
1.If I want to configure RAID10 during ubuntu installation, do i need to configure RAID(ctrl+i) in bios?
2. how do i set two or more boot partitions of about 500MB and add them to a RAID 1?

Thanks!

---

### Post by YesWeCan on 2011-08-25
No, it is very confusing but bios RAID is different from linux RAID so disable all bios RAID.
This YouTube video (it is in two parts) should help. It is for RAID0 but the same basic method applies, except you need to partition 4 drives and choose RAID10.
[http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)

In the video he starts with blank drives so you will need to delete any existing partitions as the first step.

---

