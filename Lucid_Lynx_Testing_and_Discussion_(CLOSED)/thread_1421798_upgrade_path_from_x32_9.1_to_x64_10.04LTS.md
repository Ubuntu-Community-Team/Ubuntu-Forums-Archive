---
title: "upgrade path from x32_9.1 to x64_10.04LTS"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nss0000 on 2010-03-04
Gents:

The newer ( AMD-965/MSI-gd70 ) of my three Ubuntu kits currently runs x32_KK_9.1. I intend ram/HDD 'freshening' to that new system and installing LL_10.04 LTS as its OS. 

What is the most prudent OS upgrade path for me to chose ?  

**BTW** my "2nd" system (AMD_5600+/asus-M2N) has run x64_8.04.1 practically without issue since its release & I see no reason to touch it!

---

### Post by dabl on 2010-03-04
There is no upgrade path between architectures -- it's a "differentgrade", not an "upgrade".  :D

New installation for you, if you go with the 64-bit.

---

### Post by nss0000 on 2010-03-04
> **dabl said:**
> There is no upgrade path between architectures -- it's a "differentgrade", not an "upgrade".  :D

New installation for you, if you go with the 64-bit.

It would be better, then for me to install x64_KK-9.1 in anticipation of moving_over to x64_LL-10.04 ?

---

### Post by oldfred on 2010-03-04
After upgrading for 3 years and having issues every time, and a clean install of Karmic without any issues I have become a fan of clean installs. In fact I now have 3 root partitions since they do not have to be large (about 10-20GB), old install, newinstall, and beta for testing new just before it comes out. I have a separate /data so it is easy to link in all my data.

---

### Post by nss0000 on 2010-03-06
> **oldfred said:**
> After upgrading for 3 years and having issues every time, and a clean install of Karmic without any issues I have become a fan of clean installs. In fact I now have 3 root partitions since they do not have to be large (about 10-20GB), old install, newinstall, and beta for testing new just before it comes out. I have a separate /data so it is easy to link in all my data.

Perhaps I have been lucky.

My "upgraded" U_8.04.1LTS has always worked without issue. On newer kit I upgraded from a flakey U_9.04 to U_9.1 ... considering I been reduced to text_mode in U_9.04, almost everything **just-worked** in the upgrade. 

But, yes ... I COULD wait for the x64U_10.04LTS "factory-CD". I have been cautious NOT to put anything on the new-kit that cannot be blown-off. Since I expect to have that kit around for years ( AMD-965/MSI_gd70/9800gtx+/ Hanns 28"/ 8-G Crucial/500+640 Satas ) spending an extra  bit of start-up time is no-big-deal.

---

### Post by dabl on 2010-03-06
I installed the Kubuntu 10.04 64-bit "daily build" of 5 March, from here:

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

Seems pretty solid.  Takes awhile to configure everything to my personal taste, but it's not crashing and supports VMware, the proprietary Nvidia driver, Firefox with flash and java plugins, etc. etc.

---

### Post by markbuntu on 2010-03-06
If you are going from 32bit to 64bit you really need a clean install, there are way too many conflicting libs etc that make it very hard to make the switch with any grace. 

FYI if you are considering upgrading from 8.04LTS to 10.4LTS for your other machine
10.04 being an LTS will provide a direct upgrade path from 8.04. This is being tested right now by a few intrepid souls with varying success. There is a thread in Development and Testing/Lucid Lynx if you want to find out what's going on with that

---

### Post by nss0000 on 2010-03-07
> **dabl said:**
> I installed the Kubuntu 10.04 64-bit "daily build" of 5 March, from here:

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

Seems pretty solid.  Takes awhile to configure everything to my personal taste, but it's not crashing and supports VMware, the proprietary Nvidia driver, Firefox with flash and java plugins, etc. etc.

Yes ... I did DLoad and burn that x64.U.iso ... only to discover horror-of-horror it is KUBUNTU ... as you said not UBUNTU running **Gnome**. I have NEVER run a K* GUI and think it's a bad time to experiment just now.

Thanks anyway I had a good practice time ... soon as I find the equivalent GNOME version I will blast away. I feel lots-more confident with the CD_burning process.  

Now ... if ONLY <flashrom> worked for the MSI_790-gd70 ....

---

### Post by nss0000 on 2010-03-07
> **markbuntu said:**
> If you are going from 32bit to 64bit you really need a clean install, there are way too many conflicting libs etc that make it very hard to make the switch with any grace. 

FYI if you are considering upgrading from 8.04LTS to 10.4LTS for your other machine
10.04 being an LTS will provide a direct upgrade path from 8.04. This is being tested right now by a few intrepid souls with varying success. There is a thread in Development and Testing/Lucid Lynx if you want to find out what's going on with that

Thanks for the info. The issue is bullet-proof reliability. I really count-on the x64-U_8.04.1 system; daily. Almost all bugs are shook-out ( CHEEZE has recently failed after an update ). What I expect to happen does happen. 


Sure I can see room for LOTS of improvement and tuning; nobody said U_8.04.1 is perfect.  But, I imagine U_10.04 will take-one-year to become robust.

---

