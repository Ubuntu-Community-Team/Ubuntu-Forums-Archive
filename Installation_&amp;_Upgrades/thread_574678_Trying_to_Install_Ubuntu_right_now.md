---
title: "Trying to Install Ubuntu right now"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by UKCamaroSS on 2007-10-13
Hi,

I have downloaded Ubuntu and wrote the iso to a cd. 
I'm now trying to install ubuntu from the cd.... however I am unable to see the entire desktop screen!

My PC (htpc) is connected to an LCD TV via a VGA cable. I currently have Windows XP MCE  and I am trying to set up a dual boot.

The problem is I can not get Ubuntu to resize the desktop, so am unable all of the install window.

Is there a way I can adjust the screen resolution? I have tried to use Ubuntu to install my Nvidia drivers, but Ubuntu says it has to be restarted, but when I restart, I have the same problem - the driver didn't stick.

Thanks,

---

### Post by bulldog on 2007-10-13
Open a terminal and reconfigure the x-server.
You'll get some choice here,most of them you can apply as they are,but if you get the screen resolution section,just select the resolution you desire [space] .
```
sudo dpkg-reconfigure -phigh  xserver-xorg 
```

---

### Post by UKCamaroSS on 2007-10-13
> **bulldog said:**
> Open a terminal and reconfigure the x-server.
You'll get some choice here,most of them you can apply as they are,but if you get the screen resolution section,just select the resolution you desire [space] .
```
sudo dpkg-reconfigure -phigh  xserver-xorg 
```

Hi,

Thanks for the quick reply.

I did as you said, however I received the following:

xserver -xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20071013102815

So where do I go to from here?

---

### Post by bulldog on 2007-10-13
It will overwrite your existing xorg.conf and make a backup ,no problem.
Just chose the desired resolution and save it to the xorg.conf.

---

### Post by UKCamaroSS on 2007-10-13
> **bulldog said:**
> It will overwrite your existing xorg.conf and make a backup ,no problem.
Just chose the desired resolution and save it to the xorg.conf.

Hi,

Sorry, I'm a complete newbie to linux - where do I choose my desired resolution - I can't see any options. 
I typed exactly what you said, pressed return and received what I wrote in the previous message.... I've seen nothing else.

---

### Post by bulldog on 2007-10-13
Okay,-phigh means it will sorted out most common settings,so it would be the easiest way to do.
Try it this way,you get more options to choose,but most of them are correct,so leave them if you don't know what they are.
```
sudo dpkg-reconfigure xserver-xorg
```
You will get a section which is about the screen resolution,there are a number op pre definied resolutions,you can un select them if you don't use them.
Find here the resolution you want AND which is supported by the graphics you use.
At the end save the file if you're asked to,and reboot.
Now it should be used by default,if not,go to the menu -->system-->preferences and find screen resolution and set the correct value in there.
That should do it.

---

