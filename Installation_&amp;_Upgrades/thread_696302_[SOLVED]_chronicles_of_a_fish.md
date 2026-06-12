---
title: "[SOLVED] chronicles of a fish"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by powderhound99 on 2008-02-13
I'm about four hours into testing the newest Ubuntu and no real problems not only that i see improvement. My CPU has ran hot under Gutsy and was shutting down; not to say it hasn't happened but it has gotten better already and while running with extra desktop effects turned on unlike before. My temp seems to run about 20 degrease cooler and drops down faster. I've been using Ubuntu for about a year and a half now and am very happy but was disappointment in Gutsy I'm stoked for the new release and what it will bring; and I plan on reporting back as much as possible. I've even installed new themes electricsheep and others.  Tonight when I'm away from the free wifi connection I'll install config files, .vimrc, etc. Talk at you soon

---

### Post by powderhound99 on 2008-02-14
So I've spent the day setting up themes; Firefox preferences, loading my music. Rhythmbox crashed while installing codecs, but runs fine now; I haven't tried managing my Ipod yet. No problems W/ Nautilus. No major crashes due to NVIDIA Card. Audacious wont run at all. CPU temp is a bit higher but still MUCH better. just for the fun of it here's a screenshot

---

### Post by tgalati4 on 2008-02-14
When you run audacious in a terminal, what is the output?

---

### Post by powderhound99 on 2008-02-16
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault (core dumped)
I reported ths bug and it's seems common.


I lied about no NVDIA trouble once in a while my desktop effects will crash and (i assume it's...) metacty runs in it's place. Streaming seems to be a bit of a pain most players won't play the stream. The solution I've used is open t wth audacious; then after it crashes click open on the Firefox  d.l window and it will play in movieplayer. 

I can't think of any other problems and to give an idea of what I'm working against........ er I mean with my hardware is



 1  	 Sager NP2080 SUPRA
Invoice #: 539318 Ship Date: 03/29/07 Serial #: 8703SC866484
15.4" WSXGA+ (1680 x 1050) "Matte" LCD w/PCI-e nVIDIA GeForce Go 7600 w/256MB
Intel® Core™2 Duo T5500 1.66GHz Processor w/2M L2 Ondie cache - 667MHz FSB
2,048MB (2 SODIMMS) DDR2/667 Dual Channel Memory
80GB SATA/150 Hard Drive at 7,200 RPM
Combo Dual Layer DVD +/-R/RW CD-R/RW Drive w/Softwares
4-in-1 Memory Card Reader (MS/MSPRO/SD/MMC)
Built-in Intel® PRO/Wireless 3945 802.11a/b/g
9-cell Smart Li-ion Battery
Full Range Auto Switching AC Adapter
Built-in Bluetooth Wireless

After I get a few important things done I'll try compiz-fussion and so on. maybe a couple of games just to push the issue.

---

### Post by powderhound99 on 2008-02-22
Ok so It's been a little over a week now and all together I'm mostly happy with this install. I'm running hot but still not hot enough to cause a shutdown. I've installed a few games and they all run a little shaky at first but then they ran fine. The latest round of updates on the Linux-headers and gnome files were interesting they caused my mouse pad to be.... when I first log on and on occasion my mouse pointer jumps all over the screen then when I do regain control it's VERY sensitive for a few seconds then it calms down and acts as normal for a while {hour or two). My top pannel gets moved to the bottom. Firefox 3 doesn't like most of my plugins; but configuration mania and better gmail2 work so I'm pretty happy there. Running games through wine has given me a result I've seen a few times in this install; memory issues more specific core dumps. Now I've yet to put much effort behind the wine issue so lets leave that one be until I look at it a little better. The new improved search tool seems much better but I use locate ..... in my terminal to find what I'm looking for typically..... er I mean allways so I'm not really one to judge that. As far as audacious goes I didn't use it until this distro I was using old school xmms. And have gone back and it works just as I need and want it too. As far as the rest of my Multimedia needs go I've been satisfied so far.

---

### Post by powderhound99 on 2008-02-22
well that was fun I had my monitor just blank out. I started to play flight gear and my system shut down I had to use an external monitor to see any thing i didn't even get to check my mods or anything  had to leave for about an hour or too and when i restarted it worked fine now my external monitor won't work but better the one that is screwed on to my machine. I couldn't even go into a V.T.

---

### Post by powderhound99 on 2008-02-26
Ok so I've been dealing with the trackpad issue by using hot keys as much as possible (ok with me but still a little annoying) But today with out any updates mods to xorg.conf it seems to be working better kinda weird. Also I forgot to explain my joke the fish is a reference to my machine because I thought It might get gobbled up by the heron. I'm unemployed and have no current working projects so Ive made biking and testing my current projects I have no other distro installed at the moment and....... well you can read. I'd say the fish is getting away just fine maybe a couple of nips at it's tail but ok. I'm going to install a big round of upgrades to gnome, nautilus, and Linux headers, last time I had no issues; It's always interesting; and..... well gut churning before i hit that install button, especially when I don't see any posts about successes or failures. This is the point were I'm going to encourage questions if anyone wants to know about a feature I haven't covered or want screen shots and such let me know and I'll try and post them. Also it seems most of my Firefox addons are catching up to the current version.

---

### Post by powderhound99 on 2008-02-27
Results of yesterday's upgrades weren't very good. My machine shut off during upgrades when I logged on I saw the tale tale big fuzzy ugly x as a cursor, I of course had to boot into low resi mode. I rand sudo apt-get update didn't work then ran sudo dpkg --configure -a then apt-get update then ran upgrades through the gut. still didn't get desirable results so I booted into recovery mode ran xfix, then was able to boot normally. I then realized my desktop effects weren't turned on went to turn them on my NV driver wasn't enabled so I opened the restricted drivers manager were it said I didn't have any proprietary drivers on my machine. Like the greedy masachistic S.O.G I am I apt-got an Nvidia driver updated xorg.conf and then lost my screen like before. I updated and found no upgrades except a Linux-header that couldn't be installed after a few more tries of updating things and changing xorg around I hadn't had any luck and was tired. I woke up this morning ran updates found a few new upgrades and nothing better yet. I then went into the last kernel still no better but I enabled the NV driver and restarted and it worked I can boot into the new kernel w/ out the NV driver but am able to see my screen or I can boot into the older and use my eyecandy. The trackpad issue seems to be less often and less dramatic in the new kernel though. 

At this point I'm wondering about giving Gen 2 a try..... not that I think I'll manage to pull it off (meaning having stability let alone a working GUI), but maybe I can learn something from it. We'll see. I hope this journal isn't falling on def ears even with all the less than intelligent things I try I still have enough that I hope it can help someone or better yet everyone (developers?)

---

