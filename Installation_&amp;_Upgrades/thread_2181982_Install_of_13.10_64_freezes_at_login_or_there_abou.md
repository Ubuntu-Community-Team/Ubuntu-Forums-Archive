---
title: "Install of 13.10 64 freezes at login or there abouts"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by JTPete on 2013-10-19
Many kind thanks in advance!

I am optimistic as I am getting close to having ubuntu back again. A short history: I have been using ubuntu since 2008 on a home built computer, first as a dual boot but for the last few years as my only operating system. I always used the newest releases and never had a problem running any of them. I built a new computer around the end of July consisting of: Gigabyte Z87X-D3H main board, i7-4770K processor, Asus GeForce GTX 650 Ti, 32 GB GSkill 2133 (pc3 17000) Ripjaws X series 4x8 modules. My attempts at installing 13.04 ended in complete frustration (after an apparent successful install, I could not even get to grub only black screen of death on every boot,). Regretfully I purchased a copy of win 7 pro and that runs fine (this is where I am typing now).  

But not to be shut down forever, I tried again with the 13.10 release. First I went into windows disk manager and made sure there was a partition for ubuntu. I proceeded to go through a successful installation of grub and ubuntu on it own partition and a swap space. I rebooted at the point when told to do so and now I get to grub choices cleanly, I can go to windows loader from there or I can go to ubuntu. After loading ubuntu the freezing starts. Sometimes the screen freezes before I can enter my password, sometimes I can enter the password and then it immediately freezes, and sometimes I can get to the desktop and then as soon as I do anything (open terminal, software center, etc.), it freezes. 

But I am hopeful. 13.10 is getting me much closer to a working desktop and perhaps someone knows what I can do from here? besides waiting for 14.4...  
I will be forever grateful to be back with my beloved ubuntu  :-)

---

### Post by JTPete on 2013-10-23
So I have been trying to think of any additional information that might be helpful. I did install under UEFI. My install media was a fresh burned dvd, after hitting F12 at the post I am presented with 5 choices: internal hd with UEFI and without, dvd drive with UEFI and without, and an external storage hd. I choose the dvd with UEFI and the installation proceeded normally.

One other thought. While installing the computer was not networked as I have been using a netgear 4100 wireless adapter and I need to rebuild the driver after each install. I do have access to a 50 foot cable and could try installing while networked using that?... I guess I am wondering if drivers have already been updated and thus warrant the connection...

---

### Post by JTPete on 2013-11-01
Well, I am back on my beloved Ubuntu as we speak, or should it be with... Either way I am happy, here is all I know. I continued to occasionally (once a day or two) try to boot up 13.10, this morning I was able to get to the desktop but the software updater froze as did the notification for language update. This was while using my wireless connection a netgear WNDA 4100 which is not supported but another thread tells how to build the driver for it (many thanks Chili555, et al ) here [http://askubuntu.com/questions/219575/how-would-i-install-drivers-for-n900-wnda4100-wireless-adapter](http://askubuntu.com/questions/219575/how-would-i-install-drivers-for-n900-wnda4100-wireless-adapter)  

So, I pulled the wireless rebooted with a wired connection and was then able to update my software and since I have been fine. I am still on the wired connection, but it should be no problem to go back to the wireless, I had it working with 13.04 just fine. I will test that now.

---

### Post by JTPete on 2013-11-01
Oops, lost the drop down menu up at the top right. You know the one with shut down and restart, nothing there...

---

### Post by JTPete on 2013-11-01
Okay, the problem with freezing is back as soon as I go to the netgear WNDA 4100, and the problem never occurs when cabled to network, tried several times (with reboots) to be sure. What seems funny is this adapter and the solution above from Chili555 worked great on 13.04, * edit *,  it worked on 13.04 on my 'old' hardware, not the new build.

---

### Post by JTPete on 2013-11-01
The freezing problem continues but it is not a problem with the installation. System works great on wired connection, problem is with wireless adapter, netgear WNDA 4100.

---

### Post by JTPete on 2013-11-04
Just to update. There remain issues or conflicts in my system: printer driver will not install, sound problem in my favorite game Eufloria HD only one tested so far, web pages not entirely functional RideWithGPS for cycling log, once on waking from sleep state by mouse movement I got complete screen flicker on/off continuously.  All these things I assume are attributed to my build using new hardware, where as my previous build back in 2008 I used hardware that had been out for a while. Unfortunately I forgot that piece of advice.

---

