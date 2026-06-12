---
title: "Waa It's still crashing whenever I play Runescape!"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by gylti on 2011-06-06
I had a lovely system all working nicely with Ubuntu 10.10 on it and I upgraded to 11.04 and found that I hated Unity because a) couldn't find anything and was in middle of making a new website b) unable to record my desktop. I tried to get rid of things I didn't llike and destroyed my boot so all I got was memory test. Flabbergasted and looking klike the baddy on South Park playing wow vid when they kill him, I managed to save essential files by putting in a 2008 mandriva hd and copying. Then I reinstalled 11.04 from disk and it wouldnt copy my files back. So, used a 3rd old hd to install better mandriva and copied to that then installed on this one 9.04, 9.10, and tried to go through upgrades with latest java enabled in firefox because I Play Runescape and it wouldnt play any more.( On original 11.04 that I broke it played fine. ) Realised I can never use recordmydesktop Ever again I just want my files and Runescape again. I bought a proper 10.10 distro and installed java PERFECTLY and sys crashed when I play game, updated sys, upgraded accelerated graphics, still crashing and screen freezing. Also have now got files onto dvd's from the 2nd hd so thats ok but if I can't play the game I love what use is having a computer at all!!!!!!!! I checked and theres no other java with ln -s in firefox or mozilla, I took the general java one out. Iv got loads disk space and cant fathom it. Disabled x-thingy on keyboard as the layout is wierd even though its uk one. I had it all ok on original before I started all this and had gone through normal upgrades since 9.04, just don't know what else to try. Obviously I'm a nublet but I have a brain and so will be very happy to try anything that anyone will suggest. I don't go out and just really love my game to relax with and im very very miserable

 It just crashed when I was writing this so it isn't only the java applet


SOLVED I put 
sudo apt-get install nvidia-glx-173

in terminal as I had nothing to lose then it crashed again but was slightly better so then i went into synaptic and found all relating packages and installed, then I ran update and it brought in quite a lot of updates, restarted and just had to tweak the settings in the Nvidia xserver settings, also installed recordmydesktop which miraculously is working so im very grateful to everyone who has contrib to other threads about nvidia causing crashes through config and drivers as it was very helpful and pointed me right way. Just have played on Runescape for about an hour without any problem

---

