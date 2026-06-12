---
title: "After install issues"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by JeremyJTerrazas on 2011-05-19
I have recently installed 11.04, but after install when booting I get the grub loader and it stays there on the grub till I pick something, No other OS installed yet. then when I pick 11.04 it loads a terminal screen where I have to type exit just to get the GUI to load. anyone have this issue and know how to fix it. I have reinstalled 3 times so far and all with the same effect. going to try a new hdd tomorrow. I think it might be the way I am installing it, but not sure. 
 
I downloaded Ubuntu 11.04 64-bit. burned to cd from my Windows 7 notebook to install on my desktop. The live cd part of the image works fine install seems to go fine, I reformat the drive, and repartition it so I can dual boot with Windows 7 eventually Put in a 1 gb swap partition, with a 245 Gig partition for Ubuntu and a 245 Gig partion as storage for linux stuff only, then 2 new partitions of 250 each for Windows 7 and stuff. I put the Ubuntu root as "/" only no "/home" that could be where I am going wrong, I just dont know, any help would be greatly thanked. also if I put this in the wrong section of the forum I am sorry new to this forum. I tried to do a search for this issue but did not find any so if this is a double post again I am sorry.

---

### Post by Quackers on 2011-05-19
Welcome to UF :-)
A separate /home partition is not required, it's just an option.
What does the terminal type screen say? Is there a BusyBox message ending with a initramfs prompt?
At the moment you are typing in "exit" and the system then boots, is that correct?

---

### Post by JeremyJTerrazas on 2011-05-19
thats exactly what I am getting the initramfs prompt. then I type exit and it then starts to load the GUI, after that.

---

### Post by JeremyJTerrazas on 2011-05-23
Update, I have tried an almost new system. I got a new proc and motherboard memory and Hard drive, the only things I have kept are my 1 dvd drive, my 1 blu ray drive, and my 2 6870 video cards.yet I still get that damned busybox initramfs prompt. I have tried several different things. I even tried loading an older version of Ubuntu and then upgrading. went from 7.04 to 11.04 Feisty to Natty on Feisty it works fine then I upgrade and that prompt returned. I am at the point where I am just going to just install windows and forget about using Linux anymore.

---

