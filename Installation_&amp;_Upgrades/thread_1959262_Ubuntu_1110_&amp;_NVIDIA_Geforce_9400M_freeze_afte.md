---
title: "Ubuntu 11:10 &amp; NVIDIA Geforce 9400M freeze after last automatic update"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by jpn2 on 2012-04-15
Hello,
 
I've a GIADA N10 running Ubuntu 11:10 and XBMC, and when I rebooted after last automatic update, the PC freezes presenting a message saying "*Checking battery state... [OK].
 
I already have tried all the instructions posted in another threads in this forum without any success.
 
Since I'm a rookie in Ubuntu, could you please inform all the commands that I must do in order to let you have a clear picture of the actual status of my PC.
 
Please note that I already have executed these commands from these threads:
[http://ubuntuforums.org/showthread.php?t=1859820&highlight=checking+battery+state](http://ubuntuforums.org/showthread.php?t=1859820&highlight=checking+battery+state)
**sudo apt-get install --reinstall nvidia-173**
**startx **-received a Fatal server error: no screens foud
 
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Code:
sudo apt-get updatesudo nvidia-installer --uninstallsudo apt-get remove nvidia-*sudo apt-get install linux-headers-'uname -r'sudo apt-get install nvidia-current sudo nvidia-xconfigsudo apt-get update
(Note- This example assumes that you have a GeoForce 6xxx or better card) then try to start the GUI via 
Code:
sudo service gdm start
I got some errors when executing some of these commands...
 
I think that I should start from the scratch, could you please guide me by informing what should I do step by step? 
 
Thank you in advance for your cooperation!

---

