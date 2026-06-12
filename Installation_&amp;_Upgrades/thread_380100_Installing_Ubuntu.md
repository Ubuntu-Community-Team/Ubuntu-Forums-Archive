---
title: "Installing Ubuntu"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by teekrul on 2007-03-09
Hello, 

I have been thinking about installing linux for a while just havent gotten around to doing so. Which now i have.

So......

I have now used Gnome partition Editor and currently have 
 /dev/hda1 ---- NTFS ----------7.65gb ----- Boot
 /dev/hda2  --- Ext3  --------- 48.83gb
 /dev/hda3 ---- Linux-swap --2.57gb

Now im figuring that it will install to /dev/hda1 but not sure if i should have it there... or on hda2 (currently not gettig rid of windows) If i install it on hda1 will it mess up my windows installion? or how do i change it to the hda2 drive?

ps i already like the fact that it just labels the drives 1, 2, 3 etc.

---

### Post by teekrul on 2007-03-09
doh! lol... sorry found out.... it was giving me a are you sure you want to proceed thing..... now its not.... so i selected hda2 to be root and hda3 as swap


sooo.... nm

---

### Post by zvacet on 2007-03-09
It is a good thing if you have home directory on it´s own partition,because in that case you can re-install,make fresh install...without losing your files.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

