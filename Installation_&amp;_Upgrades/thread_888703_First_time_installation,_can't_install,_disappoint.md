---
title: "First time installation, can't install, disappointed"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by ShadowHawk86 on 2008-08-13
Okay so here is the deal. I'm hyped up about trying Ubuntu finally. I've been wanting to do so for a while but haven't gotten the opportunity until now. My employer just gave me an old server and I decided to try Ubuntu Server. I'm sadly disappointed though and here is why.

I have downloaded the 8.04.1 iso from the U Cal servers twice. I even did a checksum to make sure they were all good (they were). I then burned two different brand CDs on two different occassions using Nero 7 (burn completed without errors). I have also tried to install it on 2 different servers. None of them will install which is a little disappointing and frustrating since the checksum and burn were both successful and I know for a fact these servers are in good working condition. 

Here is the setup of the server that I will be installing it on:

Pentium3 1Ghz x2 
4GB DDR2 ECC
4x37GB Serial SCSI (Raid 0)

I'm not sure what you will need beyond that since these seem to be the most important parts of the server for a linux install. 

The server is a Dell PowerEdge 2550 just for the record. 

Any ideas as to why this continues to fail? :confused:

---

### Post by dstew on 2008-08-13
Did you download the Desktop Live CD or another type of CD? Did you check the disk for integrity (opening menu item)? Even if a burn seems successful, if you burn an image CD at more than 4x speed, often there will be some bits that are not readable. The disk integrity check can verify your CD better than the burning software. Also, try to boot the disk in another computer.

---

### Post by ShadowHawk86 on 2008-08-13
> **dstew said:**
> Did you download the Desktop Live CD or another type of CD? Did you check the disk for integrity (opening menu item)? Even if a burn seems successful, if you burn an image CD at more than 4x speed, often there will be some bits that are not readable. The disk integrity check can verify your CD better than the burning software. Also, try to boot the disk in another computer.

Thanks for the reply. I found another thread that is similar to the problem that I (as well as others) are having. 

Here is the steps I've done: 

1)Download from 2 different mirrors (gige and ucal)
2)Burned 2 different CDs (Imatation and Memorex) 
3)md5 check both isos (both valid)
4)Attempt install on two different 2550s (both fail @ same point)

I haven't tried the slower burn yet, but I guess I'll have to do that. I've never gotten a bunk disc out of my burner before and it burned at 24x max on both discs so somehow I doubt this is the entire trouble. 

I was interested to see that the Dell 2550 is not on the "validated hardware" list for Ubuntu Server although it does meet all the requirements for hardware.

---

### Post by suryapraveen on 2008-08-13
the best thing u can do is to mount it form a iso file.

u have lot of mounting softwares and also try burning it slowly with lower speed

that will also help you

---

### Post by ShadowHawk86 on 2008-08-13
> **suryapraveen said:**
> the best thing u can do is to mount it form a iso file.

u have lot of mounting softwares and also try burning it slowly with lower speed

that will also help you

I will have to try burning it slower I guess. The only machine I can mount it on is a Vista based machine (my main machine)which I may move to ubuntu in the future but right now my business needs Windows Apps that aren't supported by WINE as of right now.

---

### Post by ShadowHawk86 on 2008-08-13
Well I just did a CD-Integrity check on my desktop here at work and the CD checked out fine. 

Maybe it is something to do with the CD-ROM in the server box. I will test it out tomorrow.

---

### Post by ShadowHawk86 on 2008-08-15
Well I did a slow burn of the ISO and it still fails at 0%. 

./dists/hardy/main/binary-i386/Packages fails to be exact on both a regular and slow burn. 

Anyone have any ideas?

---

