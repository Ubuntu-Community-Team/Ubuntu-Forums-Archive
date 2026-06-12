---
title: "Ubuntu 11.04 won't start after installing"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by mitsy on 2011-06-10
Hello,

I have installed Ubuntu 11.04 on my desktop. When prompted to restart after installation, I select Ubuntu (not recovery mode) at the prompt and Ubuntu will not start. All I get is a big bright purple screen which does nothing. :(

I have read some forums that suggested that setting the partition space was wrong and to try to reinstall it. I have tried to reinstall it but I do not get the option to adjust the partition at all. I did the first time I installed it but never saw it again. It just goes right through the installation process and asks me to restart. I again, select Ubuntu and I get another very brightly colored screen. 

I am trying to use it as a dual boot. I have Windows 7 right now and it works just fine. I have no idea what to do now.

I also do not get any error messages. If there are any, they pass way to fast for me to see them. I am also a noob so if there is a very simple solution and I just don't know it because I'm a noob. Forgive me.

HELP!!! I need this for work.

-mitsy

---

### Post by Rubi1200 on 2011-06-10
Hi and welcome to the forums :-)

What graphics card do you have installed?

---

### Post by mitsy on 2011-06-10
Hello and thanks for the quick reply.

I am using an AMD RADEON HD 6450 graphics card.

Thanks a bunch!

---

### Post by Rubi1200 on 2011-06-10
What you described could be a graphics problem.

Try using nomodeset and see if it helps:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

The relevant section for instructions is here:
> [SIZE=4]**How to temporarily set kernel boot options on an installed OS**[/SIZE]

---

### Post by mitsy on 2011-06-10
Oh thank you. I will try this out and let you know how it works out. 

:D

---

### Post by mitsy on 2011-06-10
Hello,

Ok I tried that and now I get a black screen that has checks of things on it. 

As an example the last line says "Battery Check [OK]"

I clicked on the link given before and I was told to enter "nomodeset" after quick splash. There is also something on that line

vt.handoff = 7

I don't know what to do now.

Should I just find an older version and try it out.

Thanks
Mitsy

---

### Post by wildmanne39 on 2011-06-10
> **mitsy said:**
> Hello,

Ok I tried that and now I get a black screen that has checks of things on it. 

As an example the last line says "Battery Check [OK]"

I clicked on the link given before and I was told to enter "nomodeset" after quick splash. There is also something on that line

vt.handoff = 7

I don't know what to do now.

Should I just find an older version and try it out.

Thanks
Mitsy
Hi, here is a link for people that get a purple or black screen.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by MAFoElffen on 2011-06-18
> **mitsy said:**
> Hello and thanks for the quick reply.

I am using an [COLOR=Red]AMD RADEON HD 6450[/COLOR] graphics card.

Thanks a bunch!Sorry I didn't notice your thread until now, but--

Look at the info highligted above.  That chipset has the same problems with 11.04 as it had with 10.10.  It is switched video graphics (Intel and ATI). The new proprietary driver from ATi has less problems with both versions of Ubuntu.  This post on my sticky should get you going again:
[http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)

---

