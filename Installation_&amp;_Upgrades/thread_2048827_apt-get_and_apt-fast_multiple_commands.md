---
title: "apt-get and apt-fast multiple commands"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by equatorlounge on 2012-08-27
hi
im fairly new, a few months, to the world of ubuntu linux; ive installed like 20 times linux ubuntu 12.04 just to get to know the system better and to find ways to improve on what i have installed before.

now i still have loads of issues but i wanted to start with one: something like creating a file and then executing it from the command line.  

i tried it once using sudo nano /home/mypcname/_harmless.sh, chmod+x'ed it and afterwards typed down sudo /home/mypcname/_harmless.sh and it's not working

ive added 
> 
#bin/bash
sudo apt-fast clean
sudo apt-fast remove
sudo apt-fast autoremove
sudo apt-fast purge


i wanted to do this because after many installations and upgrades, im being asked to do this from the terminal, so my idea was "why not doing it all in one go?"

thanks anyone

---

### Post by wojox on 2012-08-27
```
#!/bin/bash
```
Should fix it.

---

### Post by equatorlounge on 2012-08-27
it works on my laptop but not on my pc, should be a hiccup somewhere !

thanks a bunch !

---

