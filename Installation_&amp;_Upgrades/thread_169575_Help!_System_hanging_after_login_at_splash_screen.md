---
title: "Help! System hanging after login at splash screen"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by aps245 on 2006-05-02
Hello everyone. I'm not an expert with linux or the command prompt, so I'm looking for your help. I've looked around the forum for an hour and seen a few threads similar to this problem, but none with a good solution.

For some reason, when I try to log in to Ubuntu on my system, it hangs at the splash screen (not the boot splash, but the one immediately after entering your password). I initially figured it was just a Dapper problem and I tried to install the x86 version of Breezy, but the problem repeated. The graphics seem to become, for lack of a better word, "disjointed" and there are lines through the text/graphic in the center of the screen. I initially was going to dual boot with XP pro, but then wiped my hard drive and did a clean install to see if that might fix it (don't worry, I have a ghost image of XP and all my data elsewhere). Nothing has worked so far.

It's a custom machine. Here are the specs:

Athlon X2 4600
ASUS A8N-SLI MB
nVidia GeForce 7800
Creative Labs X-Fi Sound Card
2GB Corsair RAM
2 x WD 250GB SATA HD

I suspect the problem has to do with the graphics card/drivers, or maybe and irq conflict with the sound card? Like I said, I'm no expert at the linux command prompt. I need your help! I would love to try Dapper, and it would be greatly appreciated.

---

### Post by Kapre on 2006-05-03
[QUOTE=aps245]For some reason, when I try to log in to Ubuntu on my system, it hangs at the splash screen (not the boot splash, but the one immediately after entering your password). I initially figured it was just a Dapper problem and I tried to install the x86 version of Breezy, but the problem repeated. The graphics seem to become, for lack of a better word, "disjointed" and there are lines through the text/graphic in the center of the screen. I initially was going to dual boot with XP pro, but then wiped my hard drive and did a clean install to see if that might fix it (don't worry, I have a ghost image of XP and all my data elsewhere). Nothing has worked so far.

It's a custom machine. Here are the specs:

Athlon X2 4600
ASUS A8N-SLI MB
nVidia GeForce 7800
Creative Labs X-Fi Sound Card
2GB Corsair RAM
2 x WD 250GB SATA HD

I suspect the problem has to do with the graphics card/drivers, or maybe and irq conflict with the sound card? Like I said, I'm no expert at the linux command prompt. I need your help! I would love to try Dapper, and it would be greatly appreciated.[/QUOTE]

aps245 - when you are on the log-in screen press CTRL+ALT+F1 to put you on the text mode. Then on the screen type "sudo dpkg-reconfigure xserver-xorg" (this will try to reconfigure your grafx card - in which you will try to choose which is best to use for your grfx card).

Hope this can help.

K

---

### Post by aps245 on 2006-05-04
Thank you so much! That did it.

---

