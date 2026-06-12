---
title: "The works boot . . ."
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Christie_k22 on 2010-11-11
I hope this is the right place for this. I searched the forums and got little bits and pieces here and there. It really is a mess. . . though oddly enough MOST things work. 

The computer (Dell if it matters) came with Vista (wish I had another choice but I didn't). I installed Ubuntu as well but was still using the windows loader. I eventually installed Ubuntu Studio when I got another HDD (which is where I installed it). Don't ask me how I did it. . . I am completely unsure what happened. . . As of now no loader automatically pops up. It acts as if there is nothing to boot from. However I can hit f12 and chose which HDD to boot to. On one it comes up with the Windows loader w/ Vista and Ubuntu. I can chose Vista and it works just fine. However if I chose Ubuntu it starts going a lil nuts and restarts. If I chose the other HDD it boots up Grub w/ options of Ubuntu and Ubuntu Studio. Studio works (which I'm currently on) and pretty much the same thing happens as before when I chose Ubuntu. 

So if the 2 OS's that I need work (Only really use windows for games) then what is the problem? I know its a little bit annoying trying to remember to hit f12 and having to chose your OS again after that (and of course the extremely annoying vista startup times). Some other things in both Studio and Vista don't want to work like they should. This is about the only thing left that I could think of that may have something to do with it. 

My wireless card+an old wireless card I found won't work w/ either. Yet they both work on other computers running Vista and/or Ubuntu (not studio). I seem to always keep having display problems on both as well (dual monitors and graphics both). Even on studio I have to restart it sometimes to even get it to let me go fix it. My wireless controller receiver (for games)  will stop working randomly and need to be unplugged and plugged back in. I also have problems with Studio recognizing SD cards and DVD/CD's.

I am not sure much of anything can be done aside from wipe and fresh install on both. Bad thing is I don't have my other computer with me and can't afford to buy a 1TB HDD right now. Anyone have and suggestions? I appreciate it much! :P
I would appreciate any help very much.

---

### Post by cchhrriiss121212 on 2010-11-12
First thing you should do is to decide what it is you want to end up with, the slowly work towards it (separate threads for separate issues). From you post it seems you only want 2 distros installed, Vista and Ubuntu, and currently you have 4.
Here is what I would recommend:
Drive one with Vista should be left as Vista only, remove Ubuntu from it if you like and restore the Windows partition to 100% usage. You can do this with a live cd and gparted.
Drive two can be for Ubuntu, go for a regular install of 10.04 (studio has no network manager which is why you have wireless issues).

---

