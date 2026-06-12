---
title: "wine: Depends: libaudio2 but it is not installable"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by stalefist on 2007-10-20
im getting this error when i try to install wine.

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages

im getting the same error but with different packages when i try to install other things too, like VLC and gstream...

does anyone know how to fix this or whats causing the problem?

---

### Post by cozadaman on 2007-10-21
Righty'o. i had the same probem... scanned hundreds of different forums til i stubled accros a site that had libaudio2.deb on it, gave it a shot and it worked. fixes your libaudio2 problem and all is good and dandy. 

Im using ubuntu 7.10. if your using something different, try looking for other files.

Here's the link for the *.deb file:

[http://packages.debian.org/unstable/libs/libaudio2](http://packages.debian.org/unstable/libs/libaudio2)

Best of luck.

---

### Post by Soujiro Seta on 2007-10-21
WOW! this helped me a lot! thanks! I was already gonna make a new post >_< XD

---

### Post by cozadaman on 2007-10-26
Whilest where on the topic of WINE, and such, What version of Ubuntu do you have? and does your system take ages to boot and load files after the installation of WINE?

Cheers!

---

### Post by AuroraManson on 2007-11-03
Hey sorry to jump in but I have the same issue while trying to install Wine.  My question is I downloaded nas-1.9a is that the correct file? If so what directory do I place it in?  

Also I have gutsy gibbon 7.10 same exact issue with wine from what Ive seen a lot of people have this problem with gutsy.

---

### Post by AuroraManson on 2007-11-04
Never mind I got it to work you don't actually need to download that file.

What I did was make sure that all the software sources were enabled (universe, multiverse) updated them, added specific wine repository made sure my system was updated then installed wine no problem.

---

### Post by cozadaman on 2007-11-11
Ah. I figureed out WINE wasnt acctually making my system slow, its something ive added from the add/remove programs. i havent pinned it to anything yet, but i think it might be Ubuntu Restricted Drivers. my system takes about 2 or 3 mins to boot fully. the live CD is quicker than that. eh. ill figure it out when im not screaming and crying. lol.

---

### Post by darvasi on 2008-02-28
I have had the same problem.
Your treat (cozadaman) is worked well.
Thank You!

---

### Post by zvacet on 2008-02-28
**system<admin<software sources**>check all boxes under Ubuntu software and under updates tab.Reload.Now you can install all packages from repos via synaptic.No need to go to the debian repos.Ubuntu have it´s own and you can see them [here.](http://packages.ubuntu.com/)

---

### Post by luke1026 on 2008-03-01
> **AuroraManson said:**
> 
What I did was make sure that all the software sources were enabled (universe, multiverse) updated them, added specific wine repository made sure my system was updated then installed wine no problem.

You have just saved me 1/2 hour of screaming!!

---

### Post by cozadaman on 2008-03-21
wow, people still read this post lol, i think the problem was fixed maybe 3 weeks after i got it working. :lolflag:

---

### Post by luke1026 on 2008-03-26
well, I like to do alot of searching before asking anything... so I tend to dig up old posts quite alot!! sorry!

---

