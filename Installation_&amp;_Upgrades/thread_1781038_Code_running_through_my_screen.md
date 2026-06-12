---
title: "Code running through my screen"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by Hoten96 on 2011-06-12
Hi guys! I'm new to Linux as well as to the forums. My problem is: when I try to run Ubuntu 11.04 (At least I think it is), the menu asking if I want to try it or install comes up. Whichever button I click, it freezes, then goes into a line of code. It says:

[       0.06003]   [<c1******>] ? *******************

the asterisks are flashing miners and letters. Please help, I really want to install Ubuntu. 

Oh yeah, my laptop is a toshiba satellite with 1.86ghz and 512Mb ram. The reason I want ubuntu is because xp doesn't work, I think it crashed on my laptop.

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora.

You could try using the alternate ISO for installing. You can download it from the link in my signature.

---

### Post by Hoten96 on 2011-06-12
Now it says 0.056003, but the rest stay the same. 
 
Would this happen if I had a WINDOWS/system32/config/SYSTEM corruption?
 
Also, if I have 512MB of RAM, would that also impede the download process?

---

### Post by akand074 on 2011-06-12
> **Hoten96 said:**
> Now it says 0.056003, but the rest stay the same. 
 
Would this happen if I had a WINDOWS/system32/config/SYSTEM corruption?
 
Also, if I have 512MB of RAM, would that also impede the download process?

[https://help.ubuntu.com/11.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/11.04/installation-guide/i386/minimum-hardware-reqts.html)

512MB is recommended, so it should be fine. XUbuntu is Ubuntu with a lighter desktop environment and LUbuntu is Ubuntu with an even lighter DE so those are options. But Ubuntu should be fine with that. Nothing in your windows install should matter at all.

Did you download the 32 bit version from [ubuntu.com]("http://www.ubuntu.com/download/ubuntu/download") and burn/verify to make sure the disk is okay?

---

### Post by Hoten96 on 2011-06-12
Well, it works fine on my computer with the same CD, and I have 32-bit, so I'm not sure what's going on. Maybe it's my computer?

---

### Post by mörgæs on 2011-06-13
> **Hoten96 said:**
> Now it says 0.056003, but the rest stay the same. 
 
Would this happen if I had a WINDOWS/system32/config/SYSTEM corruption?
 
Also, if I have 512MB of RAM, would that also impede the download process?

You want to install Ubuntu in stead of the faulty Windows, right? In that case nothing in the old setup matters.

You could try adding boot options as described here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by Hoten96 on 2011-06-13
I tried nomodeset, I have an nVidia graphics card, but it still shows code. I even wiped my disk, just in case.

When I put nomodeset, it shows 0.064003 instead. HELP ME PLEASE.

It only works when I do acpi=off otherwise it shows code again.

---

### Post by mörgæs on 2011-06-14
> **Hoten96 said:**
> 
It only works when I do acpi=off ...

So, does this mean that the problem is solved?


> **Hoten96 said:**
> 
... otherwise it shows code again.

I do not understand. What do you mean exactly by 'code'? Could you post it, please?


By the way, there is no point in yelling HELP ME PLEASE. We will return to the thread, when we are awake.

---

### Post by mastablasta on 2011-06-14
you need to check if all data is well on disk by veryfying the md5sum. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
next the code you are talking about ... similar things happens in windows it's just obscured by some splash screen with windows logo. in ubuntu there should also be a splash screen, however if it can't configure the graphics card or if it needs proprietary drivers to configure it then you might get this what you call "code". actually these are messages that tell you what is going on what is loading etc.
 
now do you get to a point where you see a command prompt? where you can type? if so you can stry typing command 
 
startx
 
this should start the X-window environment. or if not it will give out an error. you could post the error here.
 
anothe roption as it was mentioned is to use alternate cd (which uses text based installer) and then try to configure the card or install drivers before reboot. but you can't do live session with it.
 
you could also try a different ditribution - for example Crunchbang XFCE (based on debian stable) or Linux Mint 11 (based on Ubuntu 11.04). Why would you do this? well because i too have an even older notebook and i can't run the latest ubuntu. it seems they've dropped support for some cards. while the mentioned OS run just fine.
 
though my guess here is that the card is just not recognised. what graphics card (chip) is it?

---

### Post by Hoten96 on 2011-06-15
Hey guys! Thanks for the help. I got it fixed and running. Sorry I couldn't get on a comp fast enough.

---

