---
title: "Ubuntu and Xp with Raid"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by norman_069 on 2008-04-15
Hello,  I have been reading thru the post but i am still unclear if this is possible.  I have 4 500gb hard drives all sata with my Intel mother board that supports Raid 0,1,5. What i want to do or at least find out if it is possible is to dual boot Ubuntu and Xp on one of the hard drives and set up raid 5 on the other 3.  I want to be able to use the Raid hard drives with ubuntu and linux.  Please let me know if this is possible.

Thanks

---

### Post by norman_069 on 2008-04-16
can anyone help on this please.

---

### Post by Saponsky09 on 2008-04-16
I think there is a mistake in your description or at least I'm not getting something right, I haven't used hardware RAID so maybe I'm getting something wrong but...
Based on your description you want to setup one of your drives to dual boot Windows XP and Linux, but you want to make a RAID 5 array with the other three drives which you left intact???
If nothing's running on those drives what do you want redundancy for? 
Just my opinion bu,t if I had components like yours I would go with one of the following options:
1) An entire RAID 5 array covering the 4 drives with Linux/XP in dual boot.
2) Linux in RAID 5 on two drives and XP aslo in RAID 5 on the others.

---

### Post by norman_069 on 2008-04-17
Let me know if this is wrong but how i understand raid is that if you put 3 drives on a hardware based raid then they will show up as one hard drive.  Then i could take the remaining hard drive and dual boot with it.  when i do i was just wondering if each system would recognize the 3 hard drive raid.  your idea about putting each on there own raid 5 would be good but you need 3 disk min for raid 5 and raid one takes up to much space in my opinion.    

Also if something happens to the computer hardware or the os how hard is it to retrieve the information from the raid,  would it me easier to retrieve if it was raid 1.

thanks

---

