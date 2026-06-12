---
title: "Old laptop shutdowns during Live CD start up (preinstall). Can boot options help?"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by frogo on 2011-06-02
Hello,

I'm wondering which, if any, are the important boot options in the live CD to address the sort of problem I meet with my failed installation. Are there any of these options I could/should tweak in order to load as safely and minimally as possible or in order to accommodate the crappiness of my machine? 

I'm quite useless so I probably look for a magical answer here. Pointers to documentation relevant to the problem is most welcome (I couldn't find any that seemed specifically and immediately applicable or if I did, I didn't realize or understand). I'm happy to provide any information I can gather although I'll probably need guidance in order to obtain them.


Problem: 

when trying to run, without installing, Ubuntu from a Live CD, the machine turns off after 5 to 30 secs of displaying the screen with the ubuntu logo --- it never goes beyond that screen (I'm talking about the screen that is *after* the boot menu screen, I don't know if it has a name). 


Versions I tried to install: 

- Ubuntu 10.04: In addition to the systematic shutdown, the screen is very badly scambled, all lines are elongated, thick and diagonal (looks like children drawing). If I press keys, the screen seems to change to a page of zeros (it's unreadable but it looks like a blurred HEX editor screen)

- Ubuntu 11.04: Here I can see more or less normally, although the resolution gives a bit of a late 80's impression.

- Xubuntu 11.04: Same as 11.04, although in the few runs I tried it seemed to shutdown faster. 

- I've tried burning a Lubuntu CDs but they all seem bad. 


Background:

I am trying to install Ubuntu (any ubuntu that will work really) on the following machine:

Acer Aspire 1350 (ca. 2003)
AMD Mobile Athlon XP 2600+
512MB RAM (the BIOS says 447MB if that changes anything)
The hard drive is new: Samsung IDE HD 120Gb

The use of the live CD is slightly complicated by the fact that the internal CD drive is not reliable, although it works 2/3 of the time. The machine can't boot from USB and it doesn't boot well from an external CD drive (at the moment, less reliably than with the crappy internal one).

The machine is not broken, as I could install Windows 98 (if that proves anything...). 


Apologies:
This question follows from a thread on the range of available means for installing ubuntu on an old laptop: [http://ubuntuforums.org/showthread.php?t=1772583](http://ubuntuforums.org/showthread.php?t=1772583) and I am in the process of exploring suggestions. I know it is bad forum practice to have closely related threads, but i find the question asked here to be distinct enough from the more general one I asked in the previous thread. 


many thanks in advance for any input/pointer/suggestion or clarification question

---

### Post by zvacet on 2011-06-02
With your ram I think Lubuntu is a best option.Read [this]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall")  and see if it is of any help.

---

### Post by frogo on 2011-06-02
> **zvacet said:**
> With your ram I think Lubuntu is a best option.Read [this]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall")  and see if it is of any help.


Very useful link! I downloaded the alternate iso for lubuntu and that was burnt very well by xfburn. However...

I went as far as stage 4 completed in the alternate install instructions. It broke with:

* 5. The  installer will then detecting the hardware required to complete the  installation, scan the CD ISO, load any additional components required  for the installation and some other network items. *

The last thing I saw, I think, in a blink of an eye was something like 
"detecting internal hardware; 
 detecting internal CD drive"

(I'm not sure exactly, I'm afraid. I'll wait a bit and try again to see if it breaks at the same point and try to catch what it's doing precisely if I can.)

At that point the machine suddenly turned off.

---

### Post by frogo on 2011-06-02
> **frogo said:**
> It broke with:

* 5. The  installer will then detecting the hardware required to complete the  installation, scan the CD ISO, load any additional components required  for the installation and some other network items. *

The last thing I saw, I think, in a blink of an eye was something like 
"detecting internal hardware; 
 detecting internal CD drive"


Tried again. The first time, it detected hardware and then broke while 'scanning' the ISO CD (I had just seen 'CD' before I guess). It went just a bit further this time. Hardware detection, then ISO scanning but it did shutdown some way through the next step (installing components -- could see .deb packages big picked)

I'll do the same a few times: wait, reboot, and possibly cycle through this for a while until I see no more progress... 

Not there yet, but still much more encouraging than what was happening with the other variants and versions! Thanks!

Update:

well... /pout/ it was not progress when it went further the second time, it was just luck. The machine just turns off more or less randomly once it's started the install process, although it seems it can hardly handle a minute under the lubuntu install. I guess the same was happening with the other systems, only I wasn't trying to install but to run (x)ubuntu, so I didn't have the impression something was happening...

I'll never stop being naive and hopeful about ubuntu.

---

### Post by frogo on 2011-06-03
Still stubbornly trying to install Lubuntu. But it's now worse than the previous random shutting down during installation. 

On trying to install from internal drive, it idles at the Lubuntu boot menu. I let it for a good hour and  the internal CD/DVD drive seemed to choke. When I got back, it was doing a regular reading notch noise and the screen was slowly promising to fill with lines such as: EDD: Error AAAA reading sector 334324 (barely readable because the font looked like a 70's video game's).

Upon forcibly removing the disc I get: 
```

EDD: Error 3100 reading sector 33424

Invalid or corrupt kernel image
boot: <cursor>
```Booting from an external drive has become even more unsuccessful. It doesn't even get to the Lubuntu menu and shuts down  during the BIOS screen. 

I've read that there's a known issue with installing Lubuntu from external drives, although I don't know what this issue is... Is it my LiveCD (burnt at 10x, I couldn't go lower) that's rotten or is it my internal drive?

I still haven't tried installing on the HD using another machine. I'm wondering whether I shouldn't go to yet another linux for the ACER. I came across positive reports for OpenSuse and Mint, but I have yet to find one for Ubuntu I'm afraid.


Update:

well I'm desperate now. Seems the previous errors must have been related to the internal drive being junk. Then perhaps my reboot weren't cold enough... I don't know. From external I could again engage the install process and then it shut down again during it... despondent about this

---

