---
title: "Update Question"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by Usbman on 2007-03-04
Hi all,

I'm new to ubuntu.

In past 7 days I've installed ubuntu twice on a spare system. Tonight is 3rd time(right now). 

1st time... it played well for 4-5 days and I was slowly learning about it... I installed automatix to save time... which gave a few errors (won't go there again). but overall it played nice... before desktop wouldn't load one morning... so during boot-up all I would have command line. 

2nd time.. I installed on system yesterday... and opted to update it straight away which came in at 238mb... during the installation of these packages.. it hanged or appeared to hang as it stayed in same place for about 2 hours.. i reset.. system was corrupt.

 
These updates... are they absolutely necessary... does it affect security? has anyone else had updates freeze on them...? any tips..

---

### Post by nyinge on 2007-03-05
Does it spit out any errors or it made the whole system hang?  I've never seen anything like it.  At worst cases, it would just complain about dependency issues and exit with errors.  Were you using the apt-get in the Terminal or the little update icon in the task bar?

---

### Post by Usbman on 2007-03-05
I used the update icon in task bar...

On first installation it was fine. on second one It didn't return an error.. it just hung.. 2/3 way through.

---

### Post by zvacet on 2007-03-05
if you installed one time there is no reason not do it again.Maybe during download your internet connection  didn´t work.If you get in same trouble with desktop in the future try
```
sudo dpkg-reconfigure xserver-xorg
```

---

