---
title: "[SOLVED] No 3D graphics when tansfering hdd between computers"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by power.supply on 2008-04-14
Hi all,
My old pc has recently passed away:( Damn power supply killed motherboard and CPU. Anyway, because I am cheap and broke I managed to score another pc from a friend, minus hard drive, DVD burner and RAM. So I salvaged these from the recently deceased and installed into the recently acquired. So, since I did not want to loose the mega loads of programs that I have downloaded for my Ubuntu 7.04 release I simply put the hard drive in and, BAM, started to use the pc. This did not seem to be a problem as everything I have come across has worked so far........................... Except one thing. 3D rendering, I cannot run anything that requires 3D rendering, ie games, blender, 3D desktops, etc. So I have downloaded xorg-driver-fglrx and reconfigured xorg and changed the line 
```
Driver "ati" 
```
to 
```
Driver "fglrx" 
```
in xorg.conf. Once I have changed the driver line in xorg.conf I then restart X and get the blue screen of death telling me that xorg isn't configured properly. BAAAAAAA But it is configured properly.
O yeah, my old video card was a GeForce Ti4200 my new one is a ATI Radeon 9200SE.
I know if I formatted my hard drive and reinstalled Ubuntu I could probably get it to work but I don't want to loose my programs and have to do a full back up of my hard drive. So is there anyway of getting this to work or something I am missing (please remember that I am only a Class II Newb in Linux world)
Would doing the upgrade to 7.10 help (I haven't done this yet because I am on a very low broadband plan, Australia you see)[Damn expensive broadband, but I digress]

I have followed numerous tutorials, even this one
[HTML]http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html[/HTML]
But, with no success.
PLEASE HELP

---

### Post by Cannaregio on 2008-04-14
> **power.supply said:**
> O yeah, my old video card was a GeForce Ti4200 my new one is a ATI Radeon 9200SE.

O yeah, this is the problem.
Chances are you'r using your old hard disk nvidia settings on a ATI card.
Even if you manage to change everything for the ATI -as you should-, there's no guarantee, imho, that you'll manage to have your 3D. ATI RAdeons are notorious bitches.

Advice:
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=3RL&q=ubuntu+%22ATI+Radeon+9200SE%22&btnG=Search]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=3RL&q=ubuntu+%22ATI+Radeon+9200SE%22&btnG=Search")

Have a nice good reading.

---

### Post by Peter09 on 2008-04-14
Download envy from here

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

it will help you install the driver for your video card.

PC

---

### Post by power.supply on 2008-04-14
Thanks for your reply,
I tried envy and got this
```
python pulse.py ati 
root@aaron-desktop:/usr/share/envy# python pulse.py ati 
Envy - Version 0.9.10
Ubuntu Feisty 32bit
Your graphic card has been detected as a ATI Radeon 9250/9200 Series
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operating system
root@aaron-desktop:/usr/share/envy# 

```
:(

---

### Post by |{urse on 2008-04-14
Mr. Milone (the guy who wrote ENVY sez
> #
Use the uninstall function in Envy and then set the driver to “radeon” in the Section Device of your /etc/X11/xorg.conf. In this way you’ll use the open source driver.


---

### Post by |{urse on 2008-04-14
i know tht will work btw ^_- i have tht card

---

### Post by power.supply on 2008-04-14
Thanks I tried the uninstall and it worked. Yeah I have 3D.
Thanks again, I have been racking my brain for a good month trying to work this out.
MooooHaha Glest here I come.

---

### Post by |{urse on 2008-04-14
HEY! Wheres my thx? :lolflag: J/K Good to hear things are happy in ur ubuntu again ^^ Game On

---

### Post by power.supply on 2008-04-14
Sorry I am new to this new look forum thing. I can actually play open arena now :guitar:
WWWWWOOOOOOHHHHHOOOOO!!!!!
Thx again.

---

