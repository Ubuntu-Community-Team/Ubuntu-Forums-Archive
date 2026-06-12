---
title: "Property drivers/steam issue"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by lukash-pierz on 2015-05-18
Hello,
I was not sure is it right forum section so I hope i didn't make mistake by posting here.
I have following issue. i freshly installed ubuntu gnome 15,04 and i wanted to install steam but for some reason i can run it from soft centre. i used apt-get to install it but it don't show up (it show up in system monitor as running proc). I didn&#8217;t had this problem with Ubuntu 14,10 but i was thinking it is a driver issue (in 14,10 i could install it anyway but on start it has alert me about drivers), but it appears that i can't even install correctly amd drivers... I used property drivers from system, from amd web page (both dedicated to ubuntu and generated). After installation of drivers (in any mentioned way) my os can't boot. I can't be sure is this a reason of steam not working since I can't run system after installing drivers... Again I had no problem with installing a property drivers in 14,10 ubuntu.
I would appreciate help since I would like to use 15,04 gnome but fact that i can't use property drivers and steam is making this transition impossible.

p.s. Ubuntu is really disappoint lately since i got crashes of soft centre in 1 min after fresh installation... And random crash in middle of installation.
p.s.II how it is possible that things that worked great in 12.10 are not working now? how bad ubuntu is becoming :(.

My spec Ubuntu Gnome 15.04 (both gnome 3.14 and 3.16), GPU AMD radeon 5650, CPU intel i3,

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

Honestly, for me it's working better than ever. Proprietary nvidia drivers + Steam and 20 or so games all running amazingly good. So, no... Ubuntu hasn't become "bad". And neither Ubuntu nor Cananical has something to do with the manufacturer (AMD) decision to relegate your hardware to LEGACY, hence not providing drivers compatible with newer LINUX kernels. Again, nothing to do with Ubuntu, directly or indirectly.

The open source driver you're using now is the best you'll ever get. If you can't run games properly with those then I'm sorry but it might well be GAME OVER for that machine (not really, you can always install some recent Windows and play games there).

---

### Post by lukash-pierz on 2015-05-19
Hello,
it is not problem of drivers since i used this same with Ubuntu for over 1 year and they worked even after upgrading kernel.
In internet I found information that this is confirmed kernel bug... so it is linux fault (even if not Ubuntu directly) and users both nvidia and amd have this problem.
Any way thank you for your response I will await for official fix for this problem :(.

---

### Post by Vladlenin5000 on 2015-05-19
> **lukash-pierz said:**
> Hello,
it is not problem of drivers since i used this same with Ubuntu for over 1 year and they worked even after upgrading kernel.
In internet I found information that this is confirmed kernel bug...

Would you be so kind as to share your findings?

---

### Post by mastablasta on 2015-05-20
the 5xxx series shouldn't be legacy.
nVidia brand doesn't mean flawless experience as I recently found out when even NVidia techsupport had no clue as to why it doesn't work on my PC. had to return the card and I am now back on the old ATI I was hoping to replace. which also by the way worked reasonably well but lately for some reason drivers don't start up the fan which causes it to over heat. radeon driver & ubuntu combo fault that is...

to the OP in case you didn't know Ubuntu is changed to new policy - LTS for use, other release more for testing new things. well it was like that before but intermittent releases are now even more a testbed for new features. also new change is planned - to keep kernel same and update only apps. or to update both. kind of rolling model and rolling with stable core it seems.

anyway I see no reason to update to 15.04 when 14.04 works kind of well.

---

