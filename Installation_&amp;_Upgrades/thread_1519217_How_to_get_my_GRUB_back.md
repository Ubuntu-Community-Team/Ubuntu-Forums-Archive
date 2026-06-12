---
title: "How to get my GRUB back?"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by panoet on 2010-06-27
I've just installed BURG on my Ubuntu Lucid and I like it :KS
But the question is if sometime I want to get my "default" GRUB, how can I get it back?

Thx :) ):P

---

### Post by wilee-nilee on 2010-06-27
I assume burg goes into the MBR, or is it just a program that gives you a different screen that is just actually reading grub. Here is link that suggests that it is using a modified grub I guess.
[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg)
Here is the grub2 link, but make sure you know whats up before ever just reloading grub2 as there may be files that hinder this in the grub.cfg or somewhere else.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Section 11 is the reload section for grub2. It may also be that it is still using Grub and you just have toi remove burg to get the regular grub2 gui.

Personally I wouldn't touch burg with a ten foot pole.

---

### Post by panoet on 2010-06-27
> **wilee-nilee said:**
> I assume burg goes into the MBR, or is it just a program that gives you a different screen that is just actually reading grub. Here is link that suggests that it is using a modified grub I guess.
[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg)
Here is the grub2 link, but make sure you know whats up before ever just reloading grub2 as there may be files that hinder this in the grub.cfg or somewhere else.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Section 11 is the reload section for grub2. It may also be that it is still using Grub and you just have toi remove burg to get the regular grub2 gui.

Personally I wouldn't touch burg with a ten foot pole.

Hi, thx for your answer. But I think BURG is not "replacing" the GRUB, just modifying it. So I do not think upgrade the GRUB is the best solution, because it means installing the GRUB whereas GRUB is already installed (not removed by BURG). Remember, just my opinion :popcorn:
By the way, the tutorial to install BURG at your supplied link above was "obsolete". Now we can install BURG on our Lucid just by simple step (I've posted it on [my blog]("http://www.panoet.com") too and now I want to post about getting back the GRUB as related post). And it means we're not replacing the GRUB, just modifying it using BURG. Again, just my opinion...

):P):P

---

### Post by panoet on 2010-06-28
I've got it!!!
```
sudo grub-install /dev/sda
```
:guitar::guitar:

---

### Post by libssd on 2010-06-29
Many people (including me) have had lots of issues installing/configuring burg. However, I have had much better luck with **[Burg-Manager]("http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice")**, which provides a graphical user interface to install burg. Installation instructions for Burg-Manager are in Italian, but are not too difficult to follow, or if you use Chrome, it can translate. Note, however, that the translated page will introduce some spaces around / in directory pathnames. 

Burg-manager itself offers multiple language choices when you start it, and includes a "Remove Burg" choice.

**NOTE:** Burg-Manager is extremely young, so check the site frequently for developments.

---

