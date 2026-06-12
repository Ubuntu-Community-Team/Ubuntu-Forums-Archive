---
title: "fglrx install on Feisty for ATI Radeon 9200"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-07-04
Do I need to install fglrx driver from Synaptic and then change the video card designation from **ATI** to **FGLRX** in the xorg.conf file for an ATI Radeon 9200 video card installed on a machine that is running Feisty 7.04 ?

The reason I ask is that when I have tried this in the past and then when I rebooted the XSERVER would NOT start.

Thanks.

---

### Post by cursebg on 2007-07-08
I have Absolutely the same problem...if someone can help us pls post here..

Edit:When i change "ati" to "fglrx" the x server can't start but i need it to activate direct rendering....

---

### Post by wpshooter on 2007-07-08
> **cursebg said:**
> I have Absolutely the same problem...if someone can help us pls post here..

Edit:When i change "ati" to "fglrx" the x server can't start but i need it to activate direct rendering....

I don't think we are really going to get any help on this one, because in my opinion this has been screwed up in Feisty on the ATI Radeon 9200 and it appears no one is interested in fixing it !!!

---

### Post by cursebg on 2007-07-08
I think we should try this on some old version of Ubuntu...just to see if it works

---

### Post by wpshooter on 2007-07-08
> **cursebg said:**
> I think we should try this on some old version of Ubuntu...just to see if it works

I already have.  It works fine until you get to Feisty !!!

---

### Post by murdochravlin on 2007-07-11
I see no point in trying to use fglrx as feisty works OK with the open source ati drivers.  EG. for me beryl works just fine. I did have a few problems at start up. My monitor is an LCD 1440x900 , but the monitor ran at   1152x864 until I put 
Modeline "1440x900" 136.75  1440 1536 1688 1936  900 903 909 942 -hsync + vsync
into the  /etc/X11/xorg.conf file. Even now sometimes it slips into the 1152 screen width when switching in and out of console mode.

---

### Post by AR_Kozz on 2007-08-09
I am kind of PO'd about this as well. Judging from the other threads about this, ubuntu's attitude seems to be "not our problem" or "ask ATI about it." But ATI did its job making fglrx a long time ago. If it works thru Ubuntu edgy but not Feisty or Gutsy, then the problem is with Ubuntu. If Ubuntu doesn't fix it, they end up being incompatible with a huge number of PCs. 

The open-source drivers work OK for most normal apps. But I use my PC for games, too. As soon as I upgraded, I was aghast to find Vegastrike and FlightGear crashing as soon as I tried to start them. If it isn't fixed soon, I will have to switch distros. Sorry Ubuntu...

---

### Post by Dubbayoo on 2007-08-09
it is ATI's problem. **ATI** has **CHOSEN** to not support cards older than Radeon 9500 (I believe) in drivers from now on. That is not Ubuntu's problem to fix as it will be the same if you go to Fedora, SLED or anything else. I've been using a Radeon 8500 for near 4 years and I just bought a used Nvidia on Ebay for this very reason. 

Either get a newer card or use the ati drive but DO NOT expect this to change anytime soon. This has been covered ad infinitum in other threads.

---

### Post by A-Sylum on 2007-08-09
is there an older version you can use to support below 9500?
does it work on suse or any other distros?

---

### Post by AR_Kozz on 2007-08-14
There it is again: "It's ATI's problem." Except that ATI not SUPPORTING the 9200 anymore, doesn't mean the compatible driver no longer exists. Older versions of drivers don't just vanish just because their producer stops supporting them.  I still  have it. 

PLus, compared to other types of old hardware, the Radeon 9200 is hardly obsolete. It's handled every game I've run on it, so far. It doesn't need replacing.

Another thing that worked for me in Dapper but not Feisty is direct rendering with the open-source driver. With Dapper I had it working right after install, but in Feisty, with exactly the same hardware, and the dri-module loaded and set to '0666' as it should be in xorg.conf, nothing.  X starts, but rendering stays off.That is not ATI's problem. And I've searched these "ad infinitum" threads for hours in vain for a solution.

---

### Post by murdochravlin on 2007-11-19
WRT fglrx  fglrx_6_8_0-8.10.19-1.i386.tar.gz  worked just fine for me in an old version of gentoo.

---

