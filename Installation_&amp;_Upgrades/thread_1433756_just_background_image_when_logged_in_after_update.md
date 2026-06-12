---
title: "just background image when logged in after update"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by smokin74 on 2010-03-19
as the title says let update manager do its stuff to 9.10 yesterday and now i doint get anything other than the background image after logging in with my user and pw. well, not strictly true as firefox still opens with 'ubuntu one' signin' screen - you cant move the window though - its like theres no gnome??

would like to try to boot an older kernel versio but i never could get the new grub to work when i installed so i use an old grub bootloader from mepis 8 which is also on the system

any suggestions to get my desktop back - could really do without a fresh install right now!!


cheers in advance

chris

---

### Post by smokin74 on 2010-03-19
no one? anyone??

---

### Post by Rodnox on 2010-03-19
ive just got the same problem ..

---

### Post by smokin74 on 2010-03-19
sorry to hear that but im glad im not alone in this- tried looking through the previous posts but nothing as of yet other than possible ownership premission issues of the home folders but im unsure how to look for the permissions via a terminal (i can log in using the xterm option)

heres hoping to a solution

atb

chris

---

### Post by anksush on 2010-03-19
did u try changing the session on the login screen...? I had this 5 days back and it was apparently because the session was going to default and when I selected Gnome it started working fine.

HTH !!!

---

### Post by smokin74 on 2010-03-19
ill give it a go tomorrow when im at the computer in question - thanks

---

### Post by andrewsam on 2010-03-20
Yep me too.. looks like the window decoration had failed. Pressed Alt+T to fire up the terminal and then launch applications from there. The applications launch without title bar and the controversial windows buttons :)

---

### Post by Brandel Valico on 2010-03-20
May have something to do with this issue

[http://ubuntuforums.org/showthread.php?t=1434160](http://ubuntuforums.org/showthread.php?t=1434160)

If this seems to fit your issue

Try this its a workaround provided by Nightwishfan

Workaround for a usable desktop:
Log in and press ctrl+alt+t to get a terminal, type:
Code:


> gnome-panel
Press alt+f2 and type:
Code:


> nautilus
Desktop should be usable, do not close terminal. You may also be able to press alt+f2 again and run:
Code:


> killall gnome-terminal && gnome-terminal
See how it works for you.

---

### Post by sinurge on 2010-03-20
had the same problem got the terminal by ctl+alt+t and then gnome-panel then also tried by sudo apt-get update && sudo apt-get upgrade. A new fix seems to be up and it fixes this

---

### Post by smokin74 on 2010-03-20
> **sinurge said:**
> had the same problem got the terminal by ctl+alt+t and then gnome-panel then also tried by sudo apt-get update && sudo apt-get upgrade. A new fix seems to be up and it fixes this


no upgrade available here 

plus ctrl alt t doesnt work = have to log in using xterm

---

### Post by anksush on 2010-03-21
did you try changing the session from default to Gnome at the login screen? :-s

I tried it again just now and if I select default the desktop environment is just not there and when I select KDE or Gnome I get the correct setup...

---

### Post by smokin74 on 2010-03-22
dont have a default option as im only running gnome so no (kde style) default just gnome and xterm

i just need the relevant updates to make it my way - having no joy so far gnome-panel and nautlus are still versions 1.2.28 rather than 1.2.29 - which versions do you have and what mirrors / repositories are you using

cheers

chris

---

### Post by anksush on 2010-03-22
I will let you know once am back home....I am sorry I can't be of more help...:(

---

### Post by anksush on 2010-03-23
gnome is 2.28 ang nuatilus is 2.28.1...hope this helps...

---

