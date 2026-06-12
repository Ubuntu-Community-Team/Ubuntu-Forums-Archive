---
title: "Installing 64 bit Ubuntu over 32 bit"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by irh1991 on 2010-11-04
Hey guys

I just downloaded Ubuntu remix Netbook edition 10.10. during the installation i wasnt paying attention and I downloaded the 32 bit version... The thing is the Unity interface is not showing up, and perhaps its becuase of this 32 bit thing.
Anyway I would like to install the 64 bit version. Ive read around that the best way is to uninstall everything from windows (its dual boot) and re install. The problem is I dont have a windows xp start up cd, so that wouldnt work, or would be complicated. However somewhere I read I could install over it, and I would like your thoughts. First off how would that work?? Ive learned my lesson not to play with the OS...

---

### Post by P4man on 2010-11-05
Slow down. A few things:
First, 64 bit isnt going to solve your problem. If anything its probably more error prone.

Secondly, unity is very much a prelease IMO. It just doesnt work with a lot of hardware configuration (like many ATI cards). I would give the regular ubuntu desktop edition a try first. If that works, you can always install the unity interface on it to try that. 

Last, you dont need windows cd to install or uninstall ubuntu. I assume you did a wubi install? Avoid wubi if you can. Just make a bootable cd (or USB stick) and boot from that. If it works in live session, then install it "side by side" with windows.

---

### Post by irh1991 on 2010-11-05
Ok thanks. No I didnt install it through wubi, I did it with a pendrive. Ok I was just freaking out, thinking I permanently screwed my computer. 

However I installed Ubuntu Netbook, precisely because I have a netbook! And I want the Unity interface, becuase well, I do. However I would like to ask something regarding this specific topic. 

My harddrive is currently partitioned in 2. I talked to a computer friend, and he told me I could install the 64 bit version on top of the 32 bit version, using the same partition ubuntu currently uses. OF course it would delete evverything inside ubuntu but thats ok, he told me. Could this be done? And I am running a small netbook with 1G ram, so is it even worth it (to install the 64 bit). 

This was a freaking out post, I will admit, and I am sorry for the haziness. Ill start a different thread with the unity problem.

---

### Post by P4man on 2010-11-05
Yeah you can install 64 bit ubuntu on those same partitions (just manually select the partitions in the "advanced" portion of the setup) but it will indeed wipe everything, including your files in /home unless you made a separate partition for that. Will it solve your problem or provide any benefits? not likely, especially not with just 1 GB ram.

As for unity, id still suggest a regular gnome installation first. if you install ubuntu-netbook later it will be exactly like UNR. If gnome/ubuntu desktop works fine then you know where the problem is and at least you have a desktop environment to fall back to in case of trouble with unity. 

Alternatively, stick to ubuntu 10.04 NBR for a while, though its not unity but a different netbook interface.

---

