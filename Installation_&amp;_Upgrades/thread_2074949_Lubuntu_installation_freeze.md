---
title: "Lubuntu installation freeze?"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by JackDooner on 2012-10-22
hi all, i'm new to the whole Ubuntu/ Lubuntu OS. 

I have an old dell laptop so i decided to install ubuntu on it. I then ran in to graphics card problems and it would boot to the desktop sometimes but overall didn't work well. So i decided to go for Libuntu. But when I am installing, and it reaches the point where it has the small check-list (Wireless connection, 4.4gb free etc etc...), the installation never seems to progress.

It is staying on the screen PREPARING TO INSTALL LUBUNTU with the little check list and nothing happens. The CD drive comes to a hault and the cursor becomes a spinning circle. 

It's been like that for around 45-50 mins. I've tried restarting the installation but same problem over and over.

Please, any help is really appreciated :)

Thank you.
Jack

---

### Post by Rex Bouwense on 2012-10-22
Two things right off the bat.  First did you do an md5sum on your download?  Second did you burn the ISO at the slowest possible speed?  I have found that most installation problems can be traced to one of those.
The next question I would ask is how much RAM do you have installed?  While Lubuntu is very light, it still requires in excess of 256 Mbs to install.  I have installed Lubuntu 12.04 on an old Dell Inspiron 1000.  I did add 256 more Mbs so it has 512 and it runs Lubuntu very smoothly.  The only thing I had to do was install the broadcom driver for the WIFI.

---

### Post by ~jx on 2012-10-25
I had a similar problem when I tried to install Lubuntu yesterday but when I deleted two old ext4 partitions (by using gparted), I was able to continue through the following steps. Hope it helps

Excuse my poor English.

---

### Post by akshatk on 2012-12-23
hi,

m facing same issue while trying to install lubuntu 12.10.

m using a cd, i checked its mdsum, burnt it with lowest rate, also checked the cd via "check disc for errors".

no error came in above mentioned tests.

please help ??

---

### Post by Rex Bouwense on 2012-12-23
How much RAM have you got installed?  How big is the hard drive that you are trying to install Lubuntu?

---

### Post by akshatk on 2012-12-23
I am having 1 gb ram and drive has 10 gb of free space.

---

### Post by Rex Bouwense on 2012-12-24
Are you installing Lubuntu onto your entire hard drive or are you trying to dual boot.  The RAM is sufficient to install and run Lubuntu quite quickly.

---

### Post by Dennis N on 2012-12-24
When we installed Lubuntu 12.10 on five computers, this same event happened on one of the five machines. 

If you google "stuck at preparing to install Ubuntu" you will find many cases of the same problem.

The solution that worked for us was to download and use the alternate ISO:

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

The difference is this installer is controlled by the keyboard, but produces the same (well, almost the same) Lubuntu installation that the standard installer provides. 

There are a couple of differences, for example the alternate ISO installs Firefox by default along with Chromium.

---

### Post by joy_deep on 2013-01-28
I am having the same problem. Downloaded Lubundu, matched checksum, burnt at 4x speed. I am having Compaq Presario with 512 Mb RAM and 160 GB HD. Still it freezes just after the "Who are you?" screen.
Is there way to use the graphical installer or is this a bug and there is no other way to install except downloading alternate ISO?

Thanks!

---

### Post by sunkwoun on 2013-01-28
I had similar problem with my Dell Latitude C610 machine when I tried to install Lubuntu 12.10 recently. Installation was stuck right after putting my name, ID, Password. So I googled and found that there has been an issue with slideshow during the installation for the Dell machine (I don't know whether it is only for Dell or not). Anyway I found a tip saying that as following.

1. Boot with LiveCD
2. Open Terminal and remove slideshow by typing as below
  sudo apt-get remove ubiquity-slideshow-ubuntu
3. Start install by clicking on icon on the screen

However when I tried 2 above somehow I couldn't remove slideshow. So I used synaptic to remove ubiquity-slideshow-ubuntu. Then I was able to install Lubuntu 12.10 without further problem.
You can find more details on following address.

[https://plus.google.com/112011951601268696219/posts/PjVFwGQdKiX](https://plus.google.com/112011951601268696219/posts/PjVFwGQdKiX)

If you succeed, please thank him not me  :)

Goodluck

---

### Post by adreask on 2013-03-22
This worked for me too!
Thank you ;-)

> **~jx said:**
> I had a similar problem when I tried to install Lubuntu yesterday but when I deleted two old ext4 partitions (by using gparted), I was able to continue through the following steps. Hope it helps

Excuse my poor English.

---

### Post by pulsarunlimited on 2013-10-28
I couldn't get passed the preparing installation screen either, until I deselected the 'install mp3 fraunhofer and such non free libs'-option... Weird, but that seemed to do it.

---

