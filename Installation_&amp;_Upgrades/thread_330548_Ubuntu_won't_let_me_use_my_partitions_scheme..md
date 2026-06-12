---
title: "Ubuntu won't let me use my partitions scheme."
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by leobing on 2007-01-03
I sent this query to a ubuntu newsgroup but had no answer so I am trying here.

I downloaded and tried to install Ubuntu 6.10 and after failing I downloaded and tried the same with Kubuntu. My computer is fairly simple. A 200 gig drive, a dvd writer, A router and modem. 512 megs ram and nvidia 64 meg video card. the network card is a bcm4401.
The problem I am having is when I try to install it to my hard drive it wants use other partitions as well as the 2 I have decided on.
I have a 200 gig drive and I have more or less partitioned it into 9 or 10, 18 or 20 gig partitions. I have a 550 meg swap partition and I wanted to install / (root) into hda8. The partitioning thing tried to tell me I had to use and format the hda4 partition which is the extended partition containing all my other partitions not including my 3 primary partitions.
Here is my partition list.

hda1 -dos/win
hda2 -Slackware11
hda3 -Mepis 6
hda4 -extended partition containing my other partitions.
hda5 - swap
hda6 -Kanotix
hda7 -Vlos1.3.0.1
hda8 -which I intended to put Ubuntu 6.10
hda9 -Linux-xp
hda10 Fedora core 5
hda11 Vector 5.1.1
hda12 Vector 5.8

I then thought maybe it wants to be installed only in a primary partition. NOPE that was not any help. It still wanted to format my extended partition.
So far: Ubuntu is the only Linux that has given me problems during my installs.
As you see I do not make other partitions like /home /boot /root /usr etc.
I let all these become subdirectories in the / partitions of each Linux version.
I like to try out every Linux version I can as I have several people asking me about Linux. I push them to try it out but a lot are asking about Ubuntu and I am unable to do much as I can't install it.

---

### Post by logos34 on 2007-01-03
How big is hda8?

---

### Post by dannyboy79 on 2007-01-03
you need to chose the custom option, then proceed from there. You can actually even do an install without even formatting anything, you uncheck the little box that says format if I remember right. it's been over 9 months since I did the install but I had plenty of other partitions and hard drives that I was worried about when I did the install so I chose the custom way and chose where it should install itself etc etc. hope this helps you.

the other thing I remember is something about some files have to be within the first 1024 of the hard drive, would this maybe why ubuntu is telling you it has to install it on hda4? something about the boot files being within the first 1024 of the disk? I forget exactly what this was about.

welll I found this link showing the step that I am talking about, the part where it states, manually edit partition table. then you'll be able to chose. also, if your parititon is already formatted don't forget, you don't even need to format it.'


here, this is what I was talking about regarding the 1024 cylinder limit: [http://www.linuxforums.org/forum/installation/48152-grub-mbr-boot-1024-cylinder-limit.html](http://www.linuxforums.org/forum/installation/48152-grub-mbr-boot-1024-cylinder-limit.html)

---

### Post by logos34 on 2007-01-03
ok, I see what's happening...above poster is right...you're in automatic mode...you need to choose 'manual' partition...and the only format box that should be ticked is hda8.  If hda8 is 9 GB or more as you say that'll work fine.

---

### Post by leobing on 2007-01-03
> **logos34 said:**
> How big is hda8?

19 gigs.

---

### Post by leobing on 2007-01-03
I didn't see any options about non-automatic install but I am going to give it a try now.
Rhanks much.

---

### Post by dannyboy79 on 2007-01-03
> **leobing said:**
> I didn't see any options about non-automatic install but I am going to give it a try now.
Rhanks much.


check out this link before you do it, you should see these screens.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

also, I have attached the 2 pics that are most important. you can pick your drive first (pic labaled partition1) and then when you hit forward you'll want to hit the very last selection, manually edit partition table (pic labeled partition2). good luck

---

### Post by leobing on 2007-01-03
Problem solved!
I am not sure what difference there was but with this attempt to install Kbuntu, I had no problems Everything looked different and I had no trouble installing Kbuntu to hda8 and only formatting hda5 my swap partition and hda8 my Kbuntu root partition.
Thanks for interest and help.

---

