---
title: "Nightmare installing on Dell Inspiron 1525"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by sTpny on 2008-11-24
My god, what a hassle it has been. I am well passed the point of giving up and reinstalling windows, but this install screwed up so much that I can't even seem to do that. This particular laptop ran ubuntu 8.04 without many problems for quite some time, only the DRDY errors that others are getting with this and other laptops from dell. Well, I followed instructions to fix this, that is, I changed the mode of the drive to ata in the bios. When I did this, the bios warned that I might need to reinstall my os, which was no biggie. I was planning on a reinstall anyhow, because of how long the computer ran with those drdy errors, and because the new ubuntu is out, but after changing to ata mode in the bios, the hd disappeared. It's just gone! The bios can't see it. 

I thought perhaps the hd had just run with those drdy errors for too long, so I bought another one. The new Ubuntu seemed to install just fine by using the pci=nomsi boot option.  I even installed the updates without trouble and booted and rebooted several times just to make sure everything was working properly, which it seemed to be. So I shut down the computer once more and went to sleep. When I got up in the morning.. The same thing happened again!! no HD!! It's just gone from the bios! I pulled the drive out booted.. shutdown.. reinstalled the drive.. got grub error 16 - inconsistant file system!! What the hell! 

This isn't even my machine.  It's a clients, and he just wants to sell it, so I don't mind putting xp back on it, but how can I do this when the bios can't see the hd!  What the hell is happening here? What can I do to fix this? Please, this will easily cost me $100 which I don't have if it can't  be resolved. (I'll need to buy another hd to install windows to). 

What I would most like is to make the computer a dual boot, with xp and ubuntu. Just because I think it makes the computer worth more as a sellable laptop, but at this point, I'd just be happy to not have to buy another new hd. 

Please, Please, Please, I cannot afford this! How do I get the hd back.  

I'll post any info you need... Just ask. 


Thanks,  

Tony


Penguin Migrations - Smashing Windows and Breaking Gates!

---

### Post by Partyboi2 on 2008-11-24
Have you tried changing back from ata mode in your bios and seeing if your hard drive is being detected by the bios.

---

### Post by sTpny on 2008-11-24
Yep, I've tried that.. Over and over again. I've also tried switching the boot order, removing devices from the boot list, re-seating the memory, and bashing my head repeatedly against a wall. Unfortunately, all I managed to accomplish was a mild headache.  

I don't like giving up, and when re-seating the memory for the second or third time, I noticed that there was a screw missing from where the drive connects to the board, so now I'm thinking its probably a hardware issue. That could explain why this and the original drive have been so troublesome, and this laptop had gone back to dell for servicing when it was still under warranty, so my guess is that they messed it up by not putting it back together properly, or that they just didn't fix all of the problems that were there. The screw is on the connector itself, and it appears to be doing nothing more than holding the connector tightly to the board, so without it, it seems likely that something might have jiggled loose.  Unless someone has a better idea, I might try a complete dismantle, and try re-soldering the connector to the board.

---

### Post by Partyboi2 on 2008-11-24
If its still under warranty maybe you could take it back and get them to check it out, sounds like hardware problem.

---

### Post by sTpny on 2009-06-08
Sorry, I should ended this post a long time ago. This laptop has since been sold, although the issues were never really cleared up. Some laptops, I think, just don't like linux.

---

