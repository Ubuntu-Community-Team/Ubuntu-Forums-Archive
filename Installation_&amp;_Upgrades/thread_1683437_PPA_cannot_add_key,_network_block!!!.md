---
title: "PPA cannot add key, network block!!!"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by Enternald on 2011-02-07
I need to get ppa working. Everything works, but when I need to add new ppa repo everything stucks at key from keyserver download. It is the fault of the filtered network connection with p2p ports block (it's academical network). However already added repos are not affected. What can I do about it? It sucks a lot. I can't wait until weekend to get some repos!!!

---

### Post by tommcd on 2011-02-07
What PPA repo are you trying to add? Do you have a link to it? Can you reach your PPA in a web browser 
(e.g., Firefox)?
How are you trying to add the PPA repo? 
Try running in the terminal:
```
sudo add-apt-repository ppa:ppa-name
```
Replace *ppa-name* with the name of your problematic PPA. It should add the GPG key automatically. If you get errors, then post them here.
See this for reference: [http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html](http://www.ubuntugeek.com/ubuntu-tip-simplified-way-to-add-ppa-repositories-in-karmic.html)
Also see this:[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs)

 FYI: You should use 3rd party repositories, including those PPA repos, with caution. The quality of 3rd party repos can vary widely. Also, these PPAs are unsupported by Ubuntu. I have seen many people around here develop all sorts of difficult problems from using rogue 3rd party repositories.
I do not use any PPAs at all.

---

