---
title: "install desktop on top of server?"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by nathasar on 2011-02-15
I'm new to ubuntu.
 
for some reason my disc I burned for ubuntu desktop 10.10 freezes when I get to the ubuntu logo with the 5 dots. I am able to install ubuntu server just fine.
 
I tried to install desktop on top of server using sudo aptitude install ubuntu-desktop and then whenever I reboot it freezes during startup.
 
I think it might be my swap partition. I recall seeing a blip of an error talking about "press C to skip or M to start maintenence" or something like that. It never stayed on the screen long enough for me to read it.
 
Am I doing something wrong?

---

### Post by mikewhatever on 2011-02-15
What are the computer specs? Some older machines wouldn't be able to load the latest Ubuntu desktops, mostly because of the RAM constrains.
To see what happens during the boot process, boot from a live media (System Rescue CD), mount the Ubuntu partition and look at /var/log/dmesg.

---

### Post by nathasar on 2011-02-17
I figured it out. the nvidia drivers on the live CDs, both server and install, were causing my GPU to hang.

updated nvidia drivers and BANG here I am running desktop on server, just like that.

---

