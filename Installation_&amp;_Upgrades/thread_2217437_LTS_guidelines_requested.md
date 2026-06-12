---
title: "LTS guidelines requested"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by pfeiffep on 2014-04-17
I've pretty much familiarized myself with Ubuntu and how to achieve most things with Ubuntu. I'm satisfied after experimentation that I can install and re-install successfully. I'm planning on settling in on 14.04 LTS (gnome flashback / metacity) and have a few questions:[INDENT]1 - with a 40 GB hard drive and 2 GB memory some general partitioning size guidelines?
2 - should /, swap, and home be sufficient?
3 - should I continue using sudo apt-get update, upgrade?
4 - other suggestions / wisdom?[/INDENT]

---

### Post by su:bhatta on 2014-04-17
Hi [**[COLOR=#000000]pfeiffep[/COLOR]**]("http://ubuntuforums.org/member.php?u=1788249"),

The '/' mountpoint creates a Home in itself. So I think you meant Root and Home.
If you dont want to do separate Root and Home partitions then you can select the 40Gb to be your '/' and the Home will be part of that.
This comes in pretty handy if you don't store major data in the Home and use a separate Media partition or HDD. 
Else for a 40Gb partition, you can use 15-20Gb for your Root and rest for your Home.

Root, Home and Swap are sufficient of course. And in case you do not Hibernate the a 2Gb Swap should suffice.

You can always use update & upgrade commands. 
Specially, if you add some PPA first you have to update and then only you can install, otherwise changes in sources.list will not reflect.
Anyways I think that the Updater Software will do automatic updates.

Have a look here: [http://askubuntu.com/questions/21719/how-large-should-i-make-root-home-and-swap-partitions](http://askubuntu.com/questions/21719/how-large-should-i-make-root-home-and-swap-partitions)

---

