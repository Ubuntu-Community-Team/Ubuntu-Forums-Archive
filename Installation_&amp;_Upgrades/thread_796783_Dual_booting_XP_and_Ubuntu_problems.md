---
title: "Dual booting XP and Ubuntu problems"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by sizzlefire on 2008-05-16
Alright, I am pretty new to ubuntu, so I dont know too much about sudo because I'm used to windows. Anyway, what I am trying to do is dual boot ubuntu and windows. I have already tried using unetbootin  (because I dont have access to any ubuntu cds), I used the iso, rebooted, booted up using unetbootin to display the livecd, and tried to install from there. Unfortunetly, when I tried to run the installer on the live cd, it wouldnt let me partition manually, or any other way, even though my hard drive is over 1/2 full, which leaves about 20 gigs, so there should be no space problems. So basically, my question is, is there a way to somehow get it to partition, or does anybody have any idea on why it wont? Thanks in advance.

---

### Post by Rytron on 2008-05-16
Welcome to Ubuntu.
Firstly derangement your Windows partition if it is not already done. Then load the Ubuntu Live Cd. If you have trouble installing with the Live Cd you could also try the Alternate cd. To get the Alternate cd check the box at the end of this page: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
Hope this helps.

---

### Post by kk0sse54 on 2008-05-16
> Alright, I am pretty new to ubuntu, so I dont know too much about sudo because I'm used to windows. Anyway, what I am trying to do is dual boot ubuntu and windows. I have already tried using unetbootin (because I dont have access to any ubuntu cds), I used the iso, rebooted, booted up using unetbootin to display the livecd, and tried to install from there. Unfortunetly, when I tried to run the installer on the live cd, it wouldnt let me partition manually, or any other way, even though my hard drive is over 1/2 full, which leaves about 20 gigs, so there should be no space problems. So basically, my question is, is there a way to somehow get it to partition, or does anybody have any idea on why it wont? Thanks in advance.

unetbootin? I have never heard of it before.
 
> use I dont have access to any ubuntu cds

 are you saying that you don't have internet access or just a slow internet? Because other wise just go to ubuntu.com and downlaod the iso from there. Like Rytron said make sure you defragment your windows partition before hand otherwise it won't work. About manually wanting to make the partitions instead of going through the install try out the liveCD and in the programs available there should be a program called Qparted which will let you mess around with your partitions and have them ready before hand going into the installation process.

---

### Post by sizzlefire on 2008-05-16
> **C!oud said:**
> unetbootin? I have never heard of it before.
 


 are you saying that you don't have internet access or just a slow internet? Because other wise just go to ubuntu.com and downlaod the iso from there. Like Rytron said make sure you defragment your windows partition before hand otherwise it won't work. About manually wanting to make the partitions instead of going through the install try out the liveCD and in the programs available there should be a program called Qparted which will let you mess around with your partitions and have them ready before hand going into the installation process.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) That is unetbootin, it basically does the job of a CD, only without a CD, what I was saying was that in my house, I have no blank CD's.

@Rytron - I am downloading the alternate CD now, and I hope it works, but for some reason I have never been able to get my hard drive to partition before either.

---

### Post by kk0sse54 on 2008-05-16
ahh okay I understand now.

---

### Post by sizzlefire on 2008-05-16
> **C!oud said:**
> ahh okay I understand now.

I just re-read what you said before, and noticed you mentioned gparted. I tried booting up from live cd, and when I tried to use gparted, it wouldnt let me change anything with my main partition. Could this be caused by the fact that my windows partition wont defrag fully? And if so, is there a way to get it to defrag fully?

---

### Post by sizzlefire on 2008-05-17
> **Rytron said:**
> Welcome to Ubuntu.
Firstly derangement your Windows partition if it is not already done. Then load the Ubuntu Live Cd. If you have trouble installing with the Live Cd you could also try the Alternate cd. To get the Alternate cd check the box at the end of this page: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
Hope this helps.

Alright, I tried that, and it couldnt mount the CD, because since Im using unetbootin, there's no CD. Does anybody know how to force my computer to partition, or have any idea on why it refuses to? Or know of any other way to get a dual boot? I also defragged, and it didnt help any. :confused:

---

### Post by undecidable on 2008-05-17
I had a brief look at unetbootin, and it appears to run from the disk,
which means it is running from the Windows partition on your disk.
In general, you cannot repartition a mounted partition.
This may cause gparted confusion as it likely thinks you are trying to repartition a mounted partition - nok.

The possible solutions might be:
1.  unetbootin offeres an option to install to usb - this might work.
2.  Do your partitioning from Wz, eg  with Partitionmagic,
so that all your partitions are setup before you try to install.
3.  Buy a CD - really might be easiest, as you can then also run things like the gparted live CD.

Hope this helps.
MC

---

### Post by sizzlefire on 2008-05-18
Okay, I got it to finally work, I partitioned, and then installed it on the partition, however y some mistake I managed to uninstall my wireless driver, so I cannot get wireless now >.<

---

