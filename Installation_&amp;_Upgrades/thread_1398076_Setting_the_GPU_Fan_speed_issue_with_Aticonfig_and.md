---
title: "Setting the GPU Fan speed: issue with Aticonfig and Xorg."
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by MaxDemian74 on 2010-02-04
Hello,

first of all: I'm a new user and i installed Ubuntu 9.10 64bit a month ago.

Everything was working fine when I realized that the fan of my ATI 4870 was running too slow, possibly overheating the card.

I read some forum about how to solve the issue and i found this (the description is in italian, but the commands are of course understandable):

[http://guide.debianizzati.org/index.php/Installazione_driver_proprietari_Ati](http://guide.debianizzati.org/index.php/Installazione_driver_proprietari_Ati)

So I installed the ATI drivers, and they seem to work properly.

But when I try to run commands like :

  	 	 	 	 	[I]aticonfig 	--adapter=0 –od-gettemperature
aticonfig --pplib-cmd "set fanspeed 0 40"[/I]

I get this message:    	

	 	 	 	 	  **No layout section was found in the file: '/etc/X11/xorg.conf'. **
 **Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again. **
 **aticonfig: parsing the command-line failed**. 
 

This is clearly related to xorg, so i run the commands:
[I]# cd /etc/X11/
# aticonfig --initial
# aticonfig --overlay-type=Xv[/I]
But i get the message:    	

	 	 	 	 	  **Found fglrx primary device section **
 ** Unable to find any supported Screen section**
 
And here is where I'm stuck now...What else should i Try? Is it too complex for a first time user or there are any chance I could solve this issue? :)

I'd like to keep using linux..but i dont want to damge my card either...

Thanks in advance!

Max








[LIST=1]
[*]
 
[/LIST]

---

