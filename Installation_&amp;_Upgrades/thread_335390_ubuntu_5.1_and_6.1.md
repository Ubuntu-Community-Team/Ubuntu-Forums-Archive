---
title: "ubuntu 5.1 and 6.1"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by pichoscosama on 2007-01-10
I have both Ubuntu 5.1 and Ubuntu 6.1. Both of them are live. My question is version 5.1 works perfectly at my laptop but at version 6.1 there is sound but there is a black screen. I read that Ati x700 has some problemas but why is version 5.1 is working perfectly?

---

### Post by Sidster on 2007-01-10
You have the wrong version numbers. Ubuntu was never released as version 5.1 it was 5.04 and it wasn't a live cd. Refer to the installation manual if you get stuck. There should be a list of compatible hardware on the forum somewhere. Try google if you can't find it. The only version of Ubuntu you need to have at the moment is 6.10 codenamed Edgy Eft (This is the latest version) unless you need long term support in which case you need 6.06 codenamed Dapper Drake. To read about long term support go [here]("http://www.ubuntu.com/products/GetUbuntu/download#lts")

---

### Post by pichoscosama on 2007-01-10
maybe it wasnt 5.1 but it was live ubuntu and working on my laptop. Why that latest version 6.10 doesnt run on my laptop?

---

### Post by pichoscosama on 2007-01-10
I controlled it. It is 5.1

---

### Post by pichoscosama on 2007-01-10
I'm writing these words from my Ubuntu Live 5.1 64 BIT on my laptop MSI M635 which has a ATI Redeon x700. It works perfectly. When I try Ubuntu live 6.10 32 BIT on my laptop MSI M635 which has a ATI Redeon x700 only sound works. There is no image on my lcd. I hope new version must be better but It wasn't.

---

### Post by Sidster on 2007-01-11
Sorry, my fault I forgot about Breezy Badger which is version 5.10 :-) The version numbers are only a reflection of the date it was released. Breezy Badger was released in 2005 in the 10th month therefore it is version 5.10.

The main difference between the two (5.10 & 6.10) is that 5.10 is not a live-install cd, meaning you can boot into a "Demo" os but you can't install it on your hard drive. 6.10 will let you "demo" the os and let you install to your hard drive.

Most likely your problem has something to do with your xorg.conf file. There's a value that might need to be changed in that file. It's a bit tricky with the live CD but it can be done. I'm sure there's a how-to somewhere on the forums, otherwise try google.

My advise long-term is to go for a full install. The live cd is great for demo-ing and testing compatibility but the advantages of a full install are many. For example, you can install Ubuntu in non-graphical mode and run updates via Apt. That way you know you've got the latest packages and there's a better chance your issues will be fixed. I'm pretty sure that your graphics card is supported, it's just a question of setting it up correctly.

I know you're expecting the live CD to just work but your situation is an exception rather than a norm. You can also try 6.06. It's not very different from 6.10. The most obvious differences can be installed on 6.06 afterwards. Keep looking, I know the solution is out there somewhere.

---

### Post by Sidster on 2007-01-11
Check out the guide located at [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

There's a good chance you find a version of the guide in your own language.

---

### Post by pichoscosama on 2007-01-11
> **Sidster said:**
> Sorry, my fault I forgot about Breezy Badger which is version 5.10 :-) The version numbers are only a reflection of the date it was released. Breezy Badger was released in 2005 in the 10th month therefore it is version 5.10.

The main difference between the two (5.10 & 6.10) is that 5.10 is not a live-install cd, meaning you can boot into a "Demo" os but you can't install it on your hard drive. 6.10 will let you "demo" the os and let you install to your hard drive.

Most likely your problem has something to do with your xorg.conf file. There's a value that might need to be changed in that file. It's a bit tricky with the live CD but it can be done. I'm sure there's a how-to somewhere on the forums, otherwise try google.

My advise long-term is to go for a full install. The live cd is great for demo-ing and testing compatibility but the advantages of a full install are many. For example, you can install Ubuntu in non-graphical mode and run updates via Apt. That way you know you've got the latest packages and there's a better chance your issues will be fixed. I'm pretty sure that your graphics card is supported, it's just a question of setting it up correctly.

I know you're expecting the live CD to just work but your situation is an exception rather than a norm. You can also try 6.06. It's not very different from 6.10. The most obvious differences can be installed on 6.06 afterwards. Keep looking, I know the solution is out there somewhere.

Actually I am using Mandrake 2006 (mandriva). I am searching a better one. I used for my server freebsd and liked port system. I heard that Debian has a port system like freebsd After a quick search I saw that Ubuntu was clone of Debian which was user friend Linux. Because of this I downloaded Ubuntu but when I wanted to install on my PC to the Mandrake partition I saw that it couldn't recognize the partition table that created with Mandriva. Also when I tried Ubuntu 6.10 on my laptop it couldnt start. 

Their slogan is "Linux for human beings" but I used Redhat, Mandrake, FreeBSD and they were easier from this crap.

---

### Post by Sidster on 2007-01-11
What file system/s are you using. I would suggest backing up your data to cd's or dvd's or perhaps a removable disk and then allowing Ubuntu to use the entire disk and create new partitions.

I've tried Mandriva. I liked it alot. If Mandriva had a good package manager like Synaptic I'd stick with it. At the end of the day you have to weigh up the pro's and con's for your situation.

However, if Mandriva 2006 works then Ubuntu 6.10 should work aswell. Have you checked the cd for defects?

I have never had problems with Ubuntu that I couldn't find a solution to on the forums. What spec is your server and what spec is your laptop? Maybe I can find a solution.

---

### Post by pichoscosama on 2007-01-11
> **Sidster said:**
> What file system/s are you using. I would suggest backing up your data to cd's or dvd's or perhaps a removable disk and then allowing Ubuntu to use the entire disk and create new partitions.

I've tried Mandriva. I liked it alot. If Mandriva had a good package manager like Synaptic I'd stick with it. At the end of the day you have to weigh up the pro's and con's for your situation.

However, if Mandriva 2006 works then Ubuntu 6.10 should work aswell. Have you checked the cd for defects?

I have never had problems with Ubuntu that I couldn't find a solution to on the forums. What spec is your server and what spec is your laptop? Maybe I can find a solution.

:) I think you misunderstood some of the thing I said. (maybe because of my lack of english :mrgreen: )
[LIST=1]
[*]Mandriva is _installed_ at my _PC_.
[*]Ubuntu Live 6.10 32 BIT working by _CD_ on my _PC_ perfectly. Video card is Nvidia FX5200
[*]Ubuntu Live 5.1 64 BIT works by _CD_ on my _Laptop_ perfectly. Video card is Ati Redeon x700
[*]Ubuntu Live 6.10 32 BIT working by _CD_ on my _Laptop_. There is sound but no image. Video card is Ati Redeon x700
[*]Ubuntu Live 6.10 32 BIT can not see the harddrive parts partitioned by Mandriva at my PC. That harddrive has 1 ext3 part and 2 NTFS part. 
[/LIST]

---

### Post by Sidster on 2007-01-11
Ubuntu 6.10 does not mount your disks automatically. Are you checking in "Places > Computer" or do you mean it doesn't appear in the partition manager during the install?

If you mean your disk's partitions are not appearing in "Places > Computer" then you can follow [this]("http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive") guide on how to manually mount partitions.

If you mean it's not appearing in the partition manager during the install then it probably means the device is not recognised or something. I'm afraid I'm out of my depth in that department so I can't help you there.

---

### Post by pichoscosama on 2007-01-11
> **Sidster said:**
> Ubuntu 6.10 does not mount your disks automatically. Are you checking in "Places > Computer" or do you mean it doesn't appear in the partition manager during the install?

If you mean your disk's partitions are not appearing in "Places > Computer" then you can follow [this]("http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive") guide on how to manually mount partitions.

If you mean it's not appearing in the partition manager during the install then it probably means the device is not recognised or something. I'm afraid I'm out of my depth in that department so I can't help you there.
:) I know how to mount. I looked with partition manager. The harddrive that was installed Mandriva is seen in Ubuntu's partition manager unpartitioned. My second harddrive which partitioned by XP seen normal.

---

