---
title: "Installing Kubuntu on Acer Aspire 1350 without CD-rom... many methods malfunctioning"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by fizzybrain on 2008-05-24
Evenin' all.
None of your poorly-defined I've-tried-nothing-and-I'm-all-out-of-ideas requests here... this is an epic.
Are you sitting comfortably?
Then I'll begin.

The story so far:
I have come away out of the city (to Felixstowe - beside the seaside, beside the sea) to try to do some video editing on a project to get me employed. I wish to use KDENLIVE, which seems to run *much* faster on a proper KDE installation (it runs on Kubuntu much better than Ubuntu). Annoyingly, I have failed to bring any ubuntu CDs with me. Berk.

What I have with me:
- I have a laptop currently running winXP - acer aspire 1350, 500-ish MB RAM, plenty of space. It has built-in ethernet (VIA Rhine II Fast Ethernet Adapter, according to windows) and wireless (D-link DWL-610), both running under winXP. It has fast USB and firewire (for video capture). I want to install linux to this machine, either on its own partition, or as files (e.g. WUBI) 
- I have another laptop running XP AND ubuntu, but it's slow, has no firewire and slow usb. I can connect the two machines in winXP for file transfer 
- I have a SKY "base" broadband connection which has a stated cap of 2GB - of which I have used 1.5GB (downloading two .ISOs - I'm pretty sure I could download one more 700MB .ISO, but don't know how "hard" the cap is).
- I HAVE NO CD-WRITER!
- I have a 1GB mp3 player from which I have managed to boot.
- I have two USB hard drives, each with plenty of space, but neither of which can be utterly wiped. I can boot to these using the Acer laptop. One of them (the hard drive hastily pulled out of my "home" machine, 5 minutes before my train left) has kubuntu 7.10 on it, which will boot, kind of.

What I have tried (and how it has been less than successful)
- the USB HD with Kubuntu 7.10 will boot (via USB) on the Acer to a command prompt, but I cannot get to a GUI. I have tried reconfiguring xorg, and it goes through the motions, but no joy when I try to startx -  I think this is where I get "fatal error - no screens found". MAYBE I NEED TO DISABLE AND XORG AND USE VESA? ERR... HOW?
- I have managed to install puppy to the mp3 player and it boots (though slowly), but I don't know how to start trying to add KDE and KDENLIVE (just in case there are puppistas reading :-) )
- I have managed to start the minimal Kubuntu 8.04 CD (intending to pull everything through ethernet), but it fails when trying to detect the network hardware - HOW DO I FIND/LOAD A NETWORK MODULE FOR THIS CARD?
- I have managed to load the Kubuntu 8.04 KDE4 desktop CD using WUBI, but again I get to a command prompt and nothing else. After a few minutes the fan starts and "ps aux | less" shows that something is using an increasing (going up to 100%) amount of CPU. All Ctrl-alt-f* screens show command prompt or nothing. I have waited 20mins with no change. If I try to startx I get the same "fatal error - no screens found" error. I can restart cleanly with ctrl-alt-del, but when it tries to stop X it says error, KDM not running. WUBI specifically says it will not work with the alternate cd.
- I have managed to load Kubuntu KDE3.5 ALTERNATE CD using UNetbootin, but fails at the compulsary "find and check CD" stages - not surprising, because it is loading from a file... duh. 

My thoughts:
- while trying to get puppy working I got the definite impression  that VESA will work much better than Xorg. Can I start the installation processes without using Xorg?
- I don't want to download any more wasted data than necessary, just in case the cap becomes real.
- maybe the KDE 3.5 (not 4) desktop edition might work better, but the error is so similar to the erro I get with kubuntu 7.10 (KDE 3.5) that I doubt it
- might an old version work better?
- Anyone live in/near Felixstowe... :-) ?
- while it would be nice to accept the fickle fancies of fate and enjoy this holiday, I *do* need to get this done so that I can get the finished film into schools before the summer holidays so that I can get some feedback to take to prospective employers.

Your mission, should you choose to accept it, is to suggest some way of getting KDENLIVE (or OME, which is also pretty good) running on the Acer laptop. Money very definitely *is* an object (see note about me being unemployed).

Answers to any or all questions greatfully received.
The first ten useful responses will receive the secret of eternal happiness.
ttfn,
fizzybrain

---

