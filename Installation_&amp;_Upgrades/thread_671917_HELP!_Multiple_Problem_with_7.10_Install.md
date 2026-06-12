---
title: "HELP! Multiple Problem with 7.10 Install"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Sega_phreak on 2008-01-19
To start, here is my system specs.

Intel Core 2 Quad Q6600 @ 2.40
EVGA 780i 
4x 1GB Crucial Ballistix PC2 800
2x 150GB Raptor X in Raid 0
1x 400GB Maxtor HD
2x XFX 8800GT 512MB Alpha Dog XXX in SLI
Hanns G 27.5" Widescreen Monitor in 1920x1200

Vista Ultimate 64-bit
Server 2003 Enterprise
XP Professional SP2



I am attempting to install Ubuntu 7.10 64-bit Desktop Edition on a 40GB Partition I set aside on the Raid 0.

Problem #1

Black Screen followed by constant beeping. 

This happens as when I'm using the Ubuntu 7.10 64-bit Desktop Edition LiveCD. I'm able to see the main menu, I select Install and about 5-10 seconds later my screen turns off and about 3-4 mins later the constant beeping starts. 

After some research I decided to use the Ubuntu 7.10 64-bit Desktop Edition Alternate CD. With this cd I am able to start the installation process all the way upto the Partitioning Section. This is where i run into:

Problem #2

Unable to see my NVRaid 0 configuration. 

After some research, I found out that I need to install "dmraid" however every guide I have seen uses the Live Desktop CD, which I cannot get to work on my system. 

Can anyone help me? 

Thanks, 

Sega_phreak

---

### Post by Squiffy on 2008-01-19
I've got pretty much the same config and I'm running into the exact same problems.

As Sega_phreak says, any ideas for a solution would be dandy!

---

### Post by Partyboi2 on 2008-01-19
I have read that the partitioner in the alternate installer lets you create software partitions. From what I understand it comes with mdadm and allows you to configure the Raid if you choose manual partitioning.
Did the system beeping stop when you were using the alternate cd?

---

### Post by Pumalite on 2008-01-19
You better read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

---

### Post by Sega_phreak on 2008-01-19
Squiffy - If you get your install up and running, please let me know, thanks.

Partyboi2 - Yes the beeping did stop once I used the Alternate CD.

Pumalite - I have read both those guides along with the link to the Gutsy Gibbon Raid installation guide. These do not really help as they all use the LiveCD and I am unable to use it. Unless there is a way to slipstream the appropriate video driver, I'm assuming that was the problem, into the LiveCD.

Any more suggestions? Please help. Thank you.

---

### Post by Partyboi2 on 2008-01-19
Have you looked at this [one]("http://ubuntuforums.org/showthread.php?t=408461")? It is done using the alternate cd

---

### Post by Sega_phreak on 2008-01-19
Thanks Partyboi2, that link was very helpful. However, I'm really trying to stay with the onboard raid controller that I have. Also, I would like to install Ubuntu without having to reinstall my other 3 OS's.

---

