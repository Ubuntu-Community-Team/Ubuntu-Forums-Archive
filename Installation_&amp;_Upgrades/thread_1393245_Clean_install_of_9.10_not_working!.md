---
title: "Clean install of 9.10 not working!"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by gurudev1000 on 2010-01-29
Hi,
I was running windows xp for sometime until I found so many troubles in there that i decided to do away with it. My internet wasn't working at all due to some driver problems.

Now, I have an old (failing) IDE 250 GB HDD. 200 GB of it is a partition for my media files which I want to keep safe (NTFS). So yesterday, I installed 8.10 because I need to get online somehow to download and burn 9.10. 8.10 was installed after deleting the windows partition and dividing it to 1GB swap, and the rest of 39 GB ext3 on / for linux. then i downoaded and burned 9.10. Today morning, I decided to do a direct clean install of 9.10 and booted in the CD.
At the partition screen during installation, I clicked on 'change' for the partition housing 8.10 and clicked on the 'forma't option and then NEXT. Everything finished installing and I pressed 'skip' twice at the end to save time and do those updates later on.
Now after that, the system wouldn't load and the error 15 would happen. I have spent around 3 hours this morning on the IRC channels and booted around 5 times into 8.10 and 9.10 CD live taking in various suggestions.
Based on one suggestion, I folllowed some commands for grub update and now the error 15 doesn't happen. But I enter straight into the command mode. Then the STARTX error also doesn't happen there. Someone said this could be something bad missing and I have to do a clean install.
I don't wnat to put my old harddisk through a lot of formatting and not even sure what is the foolproof way of arranging partitions so as to keep my media files safe.

Please help me as to what i can do right now through the terminal or something. I am online through the 9.10 live CD.

Thank you.

---

### Post by llawwehttam on 2010-01-29
It sounds like your hard drive is dying. If it is a fresh install Grub error 15 means it can't find some files so your HDD may be corrupted. You caould always try FCSK in the terminal ( a bit like chkdsk  in windows) but I would get a new HDD if I were you.
 
I had the exact oppasite problem a while ago. The MBR sector of the HDD was the first to go so I lost grub but nothing else.

---

### Post by gurudev1000 on 2010-01-29
I will get one as soon as posible. but for the moment what do you suggest? I need to be up and running soon. I can't get a new hdd immediately. If a clean install could sort things out, can you suggest a proper partition format? I just want to keep the 200 GB of NTFS files at hte end of my HDD.

---

### Post by llawwehttam on 2010-01-29
If I were you I would back the NTFS partition up as soon as possible and use that computer as least as possible as it may not have that much time left.
 
Opensuse is very good with dying HDD's as it runs FCSK on startup. If this works when you get a new HDD I reccommend coming back to ubuntu as OpenSUSE is a bit weird with hardware compatability.

---

### Post by kansasnoob on 2010-01-29
> I pressed 'skip' twice at the end to save time and do those updates later on.

I'll bet that kept grub2 from installing properly. Do a clean install and don't "skip" anything.

---

### Post by gurudev1000 on 2010-01-29
But why do they give the 'skip' option for something important like grub? I thought was just to do with the languge pack and stuf like that in the previous versions! So, if I have to do a clean install, can you pls lay down a clear way of stallation that a noob would understand? I want to keep safe the 200 GB NTFS partition with my media files and want to keep 9.10 as my only OS.

thank you.

---

### Post by gurudev1000 on 2010-01-29
OK guys, Thank you. I did a reinstall without 'skipping' anything. Just that during the APT configuring it was taking too long, and I realised the internet activity was high. So disconncected the net and then the install was a breeze.

Thanks again.

---

