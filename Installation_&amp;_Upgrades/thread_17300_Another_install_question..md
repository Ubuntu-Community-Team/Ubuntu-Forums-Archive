---
title: "Another install question."
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by ohman11 on 2005-02-27
I am a linux newbie and I have Ubuntu on a destop and on my laptop now. I am so impressed with it. On my laptop I have a 60 gig drive and I had partitioned it into 2- 30 gig drives. I installed xp and it went fine but when I installed Ubuntu I didnt understand the partition questions it was asking and it wiped out xp. I need to know how to setup the drive to dual boot both systems and the bad thing is I need to get this done tonight so I can get autocad back on my computer. Can anyone help me out here.

---

### Post by can8dnSix on 2005-02-27
When you do the install, install Windows XP first, but only create one(1) 30GB partition. After the install finishes, do the things you need to, then go onto installing Ubuntu. When installing Ubuntu it will automatically detect the "free space" that is available and create its partitions, it should create two, so you will have a total of three. Let Ubuntu do its thing and it will install and configure its bootloader to load Ubuntu by default but give you the option of loading Windows XP. 

When it is over, your 60GB harddrive will have three partitions. 

1 30GB Partition (NTFS) for Windows XP
1 29.5GB Partition (83-Linux Ext3) for Ubuntu
1 512MB Partition (82-Linux SWAP)

Now, another thing you can do... totally up to you is install windows XP using the FAT32 filesystem. This will give your windows install the best performance, because NTFS finds it speed above 36GBs. However, I am sure windows will complain about this. Anyways, hope that helps you out a little. 

Can8dnSix

---

### Post by can8dnSix on 2005-02-27
If my previous post is not an option, let me know, and I can write up a walk through for configuring the partitions manually. 

can8dnSix

aka LunchBox

---

### Post by ohman11 on 2005-02-28
[QUOTE=can8dnSix]When you do the install, install Windows XP first, but only create one(1) 30GB partition. After the install finishes, do the things you need to, then go onto installing Ubuntu. When installing Ubuntu it will automatically detect the "free space" that is available and create its partitions, it should create two, so you will have a total of three. Let Ubuntu do its thing and it will install and configure its bootloader to load Ubuntu by default but give you the option of loading Windows XP. 

When it is over, your 60GB harddrive will have three partitions. 

1 30GB Partition (NTFS) for Windows XP
1 29.5GB Partition (83-Linux Ext3) for Ubuntu
1 512MB Partition (82-Linux SWAP)

Now, another thing you can do... totally up to you is install windows XP using the FAT32 filesystem. This will give your windows install the best performance, because NTFS finds it speed above 36GBs. However, I am sure windows will complain about this. Anyways, hope that helps you out a little.Can8dnSix[/QUOTE] 

It helps alot..........I have a question though. When I create the first partition it seems like I am really creating 2 because it divides it. I tried this and ubuntu didnt like the second partition. Thanks for taking the time to help me out!! I may need a step by step here.

---

### Post by can8dnSix on 2005-02-28
[QUOTE=ohman11]It helps alot..........I have a question though. When I create the first partition it seems like I am really creating 2 because it divides it. I tried this and ubuntu didnt like the second partition. Thanks for taking the time to help me out!! I may need a step by step here.[/QUOTE]
 I dont understand what you are saying lol I'm sorry... can you give me some more details? 

can8dnSix

---

### Post by ohman11 on 2005-02-28
[QUOTE=can8dnSix]I dont understand what you are saying lol I'm sorry... can you give me some more details? 

can8dnSix[/QUOTE]

can8dnsix I am sorry for the confusion. but I did do what you said and it works perfect. This is great I can use my xp for my cad and work related things and all of my internet stuff with ubuntu, if I had my way I would have nothing but linux boxes. I now have ubunto on my laptop and another desktop and I have Lycoris on another desktop. Thanks for your help!!

---

