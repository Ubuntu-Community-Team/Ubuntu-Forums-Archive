---
title: "problem monitoring multiple devices with mrtg"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by babyboi on 2010-07-22
Hello people 

i have set up mrtg with the following guide 
--> Red Hat Linux MRTG Configuration HOW-TO (found on cyberciti site)

It work well for 1 device, however when i run the config maker for the second device it overwrites the current one and I can only see graphs for the new device. I am not sure how this works but I want to have only one html file and not have to create multiple folders or multiple html files for every device.

to create the cfg file i run 
--> cfgmaker --global 'WorkDir: \var\www\html\mymrtg --output \etc\mrtg\mymrtg.cfg public@10.1.1.1
--> indexmaker --output=\var\www\html\mymrtg\index.html \etc\mrtg\mymrtg.cfg

When I wan to create the cfg for the second file I run the same thing and change the IP to match the device (not sure if this is the correct thing to do)
--> cfgmaker --global 'WorkDir: \var\www\html\mymrtg --output \etc\mrtg\mymrtg.cfg public@10.1.1.2
--> indexmaker --output=\var\www\html\mymrtg\index.html \etc\mrtg\mymrtg.cfg

Right now I just need help going about creating graphs for a new device

Any help will be appreciated. 

Cheers

---

