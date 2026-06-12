---
title: "psychedelic screen?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by eto_D on 2008-07-05
Sorry for the vague subject but did not know how to describe it better. 

I was reading about Ubuntu in PC User and played around with their UserOS Extreme CD (based on Ubuntu 8.04). After burning the ISO CD, I managed to boot from the live CD and had a short test run. When doing so, I could not boot normally but had to use some function "low graphics" or similar (sorry, I did not write that down) otherwise only a colourful screen would come up. However, when choosing the "reduced version", Ubuntu loaded fine and had no problems checking various functions. As I liked what I saw I then wanted to install Ubuntu and downloaded it via wubi for a dual boot. It installed fine, I get the dual boot option and can choose Ubuntu, it gets to the loading screen and then I only get a psychelic page. It's like looking at a TV screen that has not been tuned yet. Now, I don't see any other option to choose so while the program has installed on my drive, I can't get it to work.

I suppose something in my windows set up is not quite right but I have no clue what to look for. Can anybody please point me into the right direction?

---

### Post by LinuxRocks713 on 2008-07-05
sudo dpkg-reconfigure xserver-xorg

That should solve your problem.

If your problem still persists, please post /etc/X11/xorg.conf.

---

### Post by eto_D on 2008-07-05
LinuxRocks713 - thanks for your help - I appreciate that. 

I tried to work with that but as total noob, I did not get very far. I understand that this would be some command line input and I tried to type this once my psychedelic screen came up. I googled and it appears I have to ctrl+f1 first which I did. 
However, while the psychedelic screen vanished and was replaced by a dos screen, my typing the command did not lead to anything. 
There is probably something totally basic missing in what I do (or don't do) - could you please provide me with more specifc instructions?

As for posting /etc/X11/xorg.conf - the same applies.

---

