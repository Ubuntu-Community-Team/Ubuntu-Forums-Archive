---
title: "Recommended install for Toshiba NB505..."
date: 2022-05-23
forum: Installation &amp; Upgrades
---

### Post by ae4ja on 2022-05-23
A friend gave me a Toshiba NB505 Netbook and I was wondering what version of Ubuntu to install on it. It's a 1.6ghz Atom with 2 gigs of RAM and a 120Gb Intel SSD. Looks like the hardware requirements for the latest version are >WAY< above this machine...   Thanks in advance and 73 to those who know what that means...   =)

---

### Post by tea for one on 2022-05-23
Is this Netbook 32-bit or 64-bit?

---

### Post by ae4ja on 2022-05-23
It'll do either, I'd prefer to use 64bit unless someone can give me a real good reason not to...

---

### Post by tea for one on 2022-05-23
Have a look at Lubuntu
[https://lubuntu.me/](https://lubuntu.me/)

---

### Post by GhX6GZMB on 2022-05-23
> **tea for one said:**
> Have a look at Lubuntu
[https://lubuntu.me/](https://lubuntu.me/)

Seconded.

---

### Post by grahammechanical on 2022-05-23
> It'll do either, I'd prefer to use 64bit unless someone can give me a real good reason not to...

Then the CPU must be 64 bit as a 32 bit CPU will only run a 32 bit operating system. When the 64 bit CPU was invented there weren't any 64 bit operating systems to run on the CPU. So, the designers made 64 bit CPU's backwards compatible. Ubuntu does not provide a 32 bit OS any more. Debian still does, I think.

My advice would be to try the operating system as a live session first.

Regards

---

### Post by ae4ja on 2022-05-23
Downloading it now, will advise upon installation. Looks good so far...   =)

---

### Post by GhX6GZMB on 2022-05-23
Lubuntu will run fine on 2 GB and 1.6 GHz, you'll have boot times of around 80 seconds. If you're in a position to replace the HDD with an SSD, this will be around 4...5 times faster.

---

### Post by ae4ja on 2022-05-23
> **ml9104 said:**
> Lubuntu will run fine on 2 GB and 1.6 GHz, you'll have boot times of around 80 seconds. If you're in a position to replace the HDD with an SSD, this will be around 4...5 times faster.

Already has a 120 gig Intel SSD, so I'm good there...

---

### Post by guiverc on 2022-05-23
I don't know your box, nor your tastes, nor importantly what you'll use the machine for and thus the apps you'll be using, which would go into making my choice.

Many bloggers state Lubuntu is the *lightest* out of the box, and I'm using it now on my old 2009 dell desktop, but its **not** all I'd consider.

Lubuntu uses the LXQt desktop, which uses Qt5 *libraries/toolkits*, thus will be most efficient (*esp. as RAM is limited*) when Qt5 apps are used, otherwise you'll be wasting resource by needing *libs* required by the desktop, and others that do the same thing but are used by your apps.

If you're wanting to use GTK3 apps, Xubuntu whilst not as light as Lubuntu, being a GTK3 desktop, when running GTK3 apps won't suffer that HIT and ***can*** outperform Lubuntu with GTK3 apps. Xubuntu likewise will do very badly if Qt5 apps are used.  My point is the use/apps you'll use should be considered.

My lowest-spec box I use in QA (*Quality Assurance*) currently is
- lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)
Both Lubuntu & Xubuntu run on it.  If it was me I'd likely select mostly by what apps you'll use, then consider your tastes (LXQt vs. Xfce) as you want to use something you're happy with.

For a release I'd use a LTS release; so consider 22.04 as it has most of its three years of life remaining, or maybe 20.04 LTS (a little under a year of support remains for *flavors* like Lubuntu/Xubuntu).  The better choice normally is 22.04 LTS or the *latest *LTS, however if you plan on using `firefox` as a browser; it's now a *snap* package and I've had both good & bad experiences on devices with 2GB of RAM; thus my mention of 20.04 LTS   (*if it weren't for firefox/snap I'd not mention 20.04*).  *When RAM is tight `systemd-oomd` can shutdown snap packages which means firefox keeps getting closed... Sure it can be disabled but not newbie friendly stuff. The snap package can also replaced with another package type.. but again not newbie stuff.  Ensure you have swap enabled.*

Flavors of Ubuntu (Lubuntu, Xubuntu etc) come with 3 years of supported life for a LTS; where main Ubuntu comes with 5 years - but on your device I'd use a *lighter* flavor. 

My 2c.   (*and I'll second trying them out in live first too*)

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)   (*applies to all flavors of Ubuntu too*)

---

### Post by ActionParsnip on 2022-05-24
You may want to expand the RAM. Otherwise Lubuntu will run fine. The low RAM will mean that you will be able to run fewer application smoothly

---

### Post by GhX6GZMB on 2022-05-24
> **ActionParsnip said:**
> You may want to expand the RAM. Otherwise Lubuntu will run fine. The low RAM will mean that you will be able to run fewer application smoothly

Just to put a few facts on that one (Lubuntu 20.04 LTS):
RAM usage after boot: around 320 MB total.
Adding Brave browser with five tabs: around 900 MB total.

Unless you're doing LTSpice simulations or things like that, you'll get along OK with 2 GB.

---

### Post by him610 on 2022-05-24
FWIW: I have similar device with a Intel Atom N270 1.6 GHz processor. It is a x86 (32 bit) machine. Upgraded RAM from 512KB to 1.5GB. SSD upgraded from 8GB to 16GB. BIOS date is May 9, 2008.
Used to have Xubuntu installed on it, but when Ubuntu discontinued 32 bits I switched to Rasbian (Debian) Stretch x86.
It works fine; although, one needs to be patient, it is not as fast as a modern computer. It's Atom powered!

---

### Post by ae4ja on 2022-05-25
> **ActionParsnip said:**
> You may want to expand the RAM. Otherwise Lubuntu will run fine. The low RAM will mean that you will be able to run fewer application smoothly


More RAM would suit me just fine, but it's already maxxed out with 2gb. I even tried sticking a 4gb in it and it wouldn't even boot...

---

### Post by ActionParsnip on 2022-05-26
Seems the max is 2Gb for that model
[https://www.memorystock.com/memory/ToshibaMiniNotebookNB505N500BL.html](https://www.memorystock.com/memory/ToshibaMiniNotebookNB505N500BL.html)

---

