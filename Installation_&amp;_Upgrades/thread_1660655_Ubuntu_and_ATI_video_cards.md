---
title: "Ubuntu and ATI video cards"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Raven2911b on 2011-01-05
Hello all

First, I am a complete newbie to Ubuntu/Linux/non-windows OSes

I am having quite a time to get my installation to work properly.  I have 3 ATI cards in my PC that run very well under Windows.  One AGP Radeon 9200 and two PCI Radeon 9250. They, unfortunately, do  not run under Ubuntu.

I have installed Ubuntu 10.10 assuming that the drivers would work, but no drivers are listed and I can't get any to install at all.  

I have been at this for 2 days trying to install/uninstall drivers to see the cards, so I am going to try a different approach. ... and now the question

Which version of Ubuntu will recognize all 3 video cards? I read that 6.0 will work, but I want  to hear it from expreienced users before I dump 10.10 and try another version.

I had grandiose plans of having Ubuntu and Wine that would run the Windows programs that I needed and see all three screen... just the way I do now under windows.  
Now I just want to see my video cards instead... lol

---

### Post by Raven2911b on 2011-01-07
anyone have any ideas on how i can get ubuntu to at least "see" the other two pci cards?
at this point, i dont even care what the resolution is... tired of staring at one good screen and two black ones.

---

### Post by Raven2911b on 2011-01-08
is there anyone here?

---

### Post by snisarg on 2011-01-08
i am new to ubuntu too, and have a laptop with ATI radeon.
just after installation, ubuntu detected that all drivers were not available, and i had to separately install drivers for ATI Radeon.

so this is what i did...

System>Administration>Additional Drivers

on clicking, it starts a window which searches for additional devices and their drivers. If they are successfully detected, please install the drivers from there and activate them. 
I am not sure what your problem is exactly, but i hope this helps

---

### Post by cascade9 on 2011-01-08
ATI dropped suport for those cards a long time ago. There is no way to get the ATI proprietary drivers working with ubuntu 10.10, or any of the other recent releases of ubuntu. The onyl drivers for those ATI cards that you will find on newer ubuntu releases is the open source drivers. 

8.04 might support the ATI drivers, but its going to have desktop support stop in 3 months, so its not worth trying. 

6.XX ubuntu is not longer supported at all for desktop use, so dont use it.

I dont know anything about 3 video cards with linux distros, so I cant help you there.

---

### Post by Raven2911b on 2011-01-08
Tried to load all kinds of drivers, but none worked.

Looks like I'm out of luck then... 

and I was really looking forward to using Ubuntu. 

Crap... back to windows i guess

:(

---

### Post by cascade9 on 2011-01-08
You should be able to get 2 displays from the 9200. Unless you've got a single output 9200 anyway.....

---

### Post by Raven2911b on 2011-01-08
> **cascade9 said:**
> You should be able to get 2 displays from the 9200. Unless you've got a single output 9200 anyway.....

I wish it did, at least I would have two monitors.

Say, one last ditch attempt here.... can anyone recommend some cards? I still want 3 monitors and I really don't care what type of cards to use (ATI vs nvidia).

My box takes AGP and PCI

Thanks

---

### Post by cchhrriiss121212 on 2011-01-08
> I had grandiose plans of having Ubuntu and Wine that would run the Windows programs that I needed and see all three screen... just the way I do now under windows. 
If you are still expecting Ubuntu to be like this, then I would not spend money on new hardware. Ubuntu is not a free version of Windows. 
If you really want to use WINE for all your Windows programs, research them first using the WINE database:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")
Many programs do not work at all, and even the most compatible ones will require troubleshooting and config work.

---

### Post by cascade9 on 2011-01-08
@ cchhrriiss121212- I agree, but dont forget that almost everything has a linux equivilent. 

> **Raven2911b said:**
> I wish it did, at least I would have two monitors.

Say, one last ditch attempt here.... can anyone recommend some cards? I still want 3 monitors and I really don't care what type of cards to use (ATI vs nvidia).

My box takes AGP and PCI

Thanks

I know that ATI added support for triplehead setups with the newest drivers (Catalyst 10.7) but ATI doesnt have support for 10.7 on AGP cards, so thats out. 
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ0OA](http://www.phoronix.com/scan.php?page=news_item&px=ODQ0OA) 

People have managed to get triplehead setups running in other ways- 

[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

I dont think its going to be at all easy to do, even more so for a beginner.

---

