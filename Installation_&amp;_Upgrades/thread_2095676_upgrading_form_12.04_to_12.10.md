---
title: "upgrading form 12.04 to 12.10"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by majorburt on 2012-12-17
how would i go about updating to Ubuntu 12.10? 
i am at Ubuntu 12.04 right now and i can't seem to figure it out.

also, if you think i should stay with 12.04 for whatever reason, than tell me please.


thanks in advance for the help.

---

### Post by darkod on 2012-12-17
If you don't have a specific reason to use 12.10, I would stay with 12.04 LTS.

It's LTS version which means it's supported for 5 years since April 2012.
12.10 is normal release and is supported 18 months since October 2012.

If you do want to upgrade, open Software Centre and find the Software Sources option. On the Updates tab there should be a drop-down box where you select if you want ubuntu to notify you when there is a new LTS available or normal release. If you change it to normal release soon it will show you a message that you can upgrade to 12.10.

Note that upgrades do go wrong sometimes so it's better to have a full backup before you try it.

---

### Post by ibjsb4 on 2012-12-17
How to upgrade

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+upgrade+12.04+to+12.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+upgrade+12.04+to+12.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Debasish Mukherjee on 2012-12-17
If you go to the update manager you will find there is a option of upgrading your system at the top.... 

click it 

it will summerize what new packages to install and what to remove..... it will be done by itself... you just need to click for the next steps....

generally If you have installed a particular software it will be retained in your new version of OS unless new version dosen't support.

):P

---

### Post by snowpine on 2012-12-17
Here are the official upgrade instructions:

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

**Pay particular attention to the "we recommend" statements!!!**

---

### Post by Mark Phelps on 2012-12-17
Couple of things you should know BEFORE you do any upgrade like this ...

First, upgrades are NOT reverseable; that is, if it goes poorly and one of more major problems happen or key things don't work, there is no way to simply "roll back" to your previous version -- the one that worked.

You either have to (1) fix the problems (to get it working, again) or (2) reinstall your prior version from scratch.

Second, AMD dropped support for the HD 1x/2x/3x/4x series video cards this summer such that, the only drivers that will work with them in 12.10 are the open-source Radeon drivers.  So, if you have one of those cards, you will no longer be able to use the restricted video drivers after the upgrade.

Suggest that you try the new version in LiveCD/Live USB mode prior to doing the upgrade.  At least that way, you will see if there are any major driver problems.

---

### Post by majorburt on 2012-12-19
thanks everybody!

the main reason that i want to switch is because i heard something about a very powerful graphics driver coming from Nvidia for Linux. i didn't know which version (12.04/12.10) it was going to be made for and thought i should upgrade.

other than that, is there anything "better" about Ubuntu 12.10 as opposed to Ubuntu 12.04?

---

### Post by snowpine on 2012-12-20
> **majorburt said:**
> 
other than that, is there anything "better" about Ubuntu 12.10 as opposed to Ubuntu 12.04?

The main difference is that all software is 6 months newer; whether or not that is "better" is a matter of opinion. Some users like the newest stuff, while others like older well-tested software.

Furthermore there are many new features, which you can read about in the Release Notes: [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes)

---

### Post by majorburt on 2012-12-20
what is "secure boot" and why is it on Ubuntu if its a windows 8 thing?

---

