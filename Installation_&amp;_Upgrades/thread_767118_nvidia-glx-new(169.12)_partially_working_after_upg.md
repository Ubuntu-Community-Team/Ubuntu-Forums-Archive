---
title: "nvidia-glx-new(169.12) partially working after upgrade."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by DarkSim on 2008-04-25
I was wondering if anybody can help me out with this one. I am stumped on it. When I upgraded to 8.04 I thought the video drivers went through without a hitch. I ran a couple of games to discover that the 169.12 drivers doesn't seem to gel with my FX5500. 

In native games certain textures get messed up. For instance UT2004's Lightning gun shoots white checkerboard squares and other artifacts are happening. Most of the NPC's in NWN have a similar thing happening to their skins.

I also uninstalled the ones through restricted manager and then set it up in EnvyNG but the same thing happened. I installed the same drivers about a month back through Envy on 7.10. I had the same exact thing happen so I think its the 169.12 drivers not liking my card.

What I'm wondering is I have the nvidia-glx-new setup in restricted driver management. How do I switch over to nvidia-glx? I tried to install nvidia-glx and then enable it through driver management but it just gets rid of glx and reinstalls glx-new. 

I know its probably something simple but I'm burnt out from spending over four hours on sound. Turns out that was because i typed ca0106 instead of CA0106 in my .asound file. :lolflag:

Thanks for any help you can give.

---

### Post by TRILEY83 on 2008-04-25
***WE are both in the same boat the truth to the matter is ubuntu will not tell you this but until nvida tell the chipset there is nothing they can do because they will not share there'e trade secret with linux because they are making too much money. you and I are caught in the middle between linux and nvida the best thing I can tell you may want to consider to save up and buy and new video card that works well with linux since u are a gammer this really sucks huh.***

---

### Post by DarkSim on 2008-04-25
I don't know about all the legalities and what not. I haven't had the chance to try the others yet. I do know the gutsy glx-new (100.14.19 I think it was) worked without a hitch. 

So hopefully once I get my head out of my rump and figure how to switch to nvidia-glx it should all be gravy. Mmm gravy! Where was I? Oh yes. Heres a pic from NWN to show whats going on.I took a couple in UT2k4 but I don't know where they are.It's big so I'll just use a link.

[http://www.imagehostingsite.com/gallery.php?entry=images/3yjmiymdtknmyzuenjmo.jpg](http://www.imagehostingsite.com/gallery.php?entry=images/3yjmiymdtknmyzuenjmo.jpg)

---

### Post by DarkSim on 2008-04-25
I think I have my problem cleared up for now. I had to use EnvyNG to install version 96.43.05 (nvidia-glx). No more checkerboard skins and rockets for me. :guitar: Thanks to the guy who made that nifty little tool. You're a real life saver.

I would still like to know why the restricted driver manager wouldn't let me switch back to nvidia-glx from nvidia-glx-new.

Now to the easy part of getting my side buttons on my five-button mouse to work.

---

