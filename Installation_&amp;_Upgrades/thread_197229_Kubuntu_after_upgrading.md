---
title: "Kubuntu after upgrading"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-06-15
Guys, I do upgrade and dist-upgrade today (june 15 11pm).  however after I restart my computer shows this menu. (there are two the same kernel.)

Ubuntu, Kernel 2.6.15-25-386
Ubuntu, Kernel 2.6.15-25-386 (recovery mode)
Ubuntu, Kernel 2.6.15-25-386
Ubuntu, Kernel 2.6.15-25-386 (recovery mode)
Ubuntu, memtest86+
Other Operating System:
MS Windows XP

I chose the one on the top,  it loads all the devices and drivers etc, then it freeze on loading screen that has the logo of kubuntu without the text shows while its loading. I waited for 10mins, but nothing happens. I tried the 2nd one  on menu (not recovery mode) but it does the same thing.

Is this a known bug? how can I fix this? :)

---

### Post by steph6790 on 2006-06-15
Hi,
I've got exactly the same problem except that my boot menu is the following :

Ubuntu, Kernel 2.6.15-25-386
Ubuntu, Kernel 2.6.15-25-386 (recovery mode)
Ubuntu, Kernel 2.6.15-23-386
Ubuntu, Kernel 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+

and when I choose the 23 one it starts fine as usual
What's the deal with the 2.6.15-25-386 Kernel? I read that other guys installed it and it works fine...

---

### Post by wizzkid on 2006-06-15
I just restart it again, and I got 
Ubuntu, Kernel 2.6.15-25-386
Ubuntu, Kernel 2.6.15-25-386 (recovery mode)
Ubuntu, Kernel 2.6.15-23-386
Ubuntu, Kernel 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+
Other Operating System:
MS Windows XP

I already resolve the hang/ freeze problem, by issuing 
sudo dpkg-reconfigure xserver-xorg

on recovery mode.

:)

---

### Post by icheyne on 2006-06-18
This fixed it for me too. Thanks!

---

