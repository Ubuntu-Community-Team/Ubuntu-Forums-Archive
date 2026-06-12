---
title: "Typing in  Firefox is extremely slow"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by leuhsam on 2007-10-21
I had to write this post in gedit first as it is just not usable to type in firefox. It takes more than 5secs until a keystroke appears on the screen. 

This behaviour just came up since i upgraded to 7.10 gutsy from 7.04. So i assume it has either something to do with new drivers, libraries or firefox version.

I found a post about the same here:
[http://ubuntuforums.org/showthread.php?t=578668](http://ubuntuforums.org/showthread.php?t=578668)
Unfortunately this post was CLOSED with no reason.

Plattform: AMD64 3GHz
Graphiccard ATI Radeon 9600 which uses RV350

Does anyone has encountered the same issues?

Regards

---

### Post by Steggie on 2007-10-23
O.k. I seem to be suffering the same fate. It is a problem with the restricted driver for the ATI graphics card. I have disabled it with the restricted driver manager and now firefox typing is fine. However I will not have any 3d support till someone can fix it. Hope this helps you with surfing at the very least. 

I am also running gutsy gibbon with an ATI radeon 9600.

---

### Post by RobertLos on 2007-10-23
I have the same problem, but only with one user. It occured both using Feisty as well as Gutsy.
I use four user-accounts, for each member of my family one. IN my own account i had compiz working and firefox responded normally.
compiz did not work in my sons environment, and in this account typing in firefox was extremely slowly (one character per second). I solved the problem by deleting the .mozilla directory and restart firefox again. This worked

After upgrading to gutsy my sons environment experiences the same slow behaviour. Compiz will not start eighter. In my own account everything works fine.

I also have a ATI 9600 card

---

### Post by x-na on 2007-10-24
I have a Radeon 9000 (RV250) card and I have similar problems, altho only page scrolling is sluggish with Compiz. So I had to disable it.

---

### Post by Steggie on 2007-10-24
Yep I had that too however I have unistalled compiz now as I never seem to use it these days. I have found another work around. I installed and tested all the browsers available in the repository. They all work to differing degrees however opera seems to be working with no trouble at all. It is this I am using at the moment.

---

### Post by wisemanleo on 2008-01-12
Has there been no solution for this yet?

---

### Post by LeDechaine on 2008-01-17
Same problem here, no (well, no flagrant) lag when writing, but lag when scrolling and viewing youtube videos.

There's another thread about this here:
[http://ubuntuforums.org/showthread.php?t=665000](http://ubuntuforums.org/showthread.php?t=665000)

**EDIT:** Solved my problem by setting the System -> Preferences -> Appearance -> Visual effects (tab) to None!
Now everything is fluid! Perfect! :D

---

### Post by vkingpele on 2008-03-09
I was having the slow typing problem. It's strange. At first when I install Ubuntu and enabled the restricted drivers everything worked fine typing and such. Under System > Preferences > Appearance I noticed a setting for Visual Effects. I switched to normal, gave it a try and then switched it back to None. That's when typing in Firefox became sluggish. 

I think Xgl has something to do with it. I think it's still trying to reference Compiz, but it's turned off so the system just waits and then passes control back to the restreicted drivers. 

 Right now I'm running in Failsafe mode with the restricted drivers enabled and everything works like a charm.

ATI Graphics Card, Restricted drivers

---

