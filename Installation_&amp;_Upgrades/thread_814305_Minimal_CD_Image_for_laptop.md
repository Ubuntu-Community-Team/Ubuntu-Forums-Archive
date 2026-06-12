---
title: "Minimal CD Image for laptop?"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by FilmAficionado on 2008-05-31
Hi, I want to avoid installing most of the programs I don't need (e.g. Ekiga, certain video and music apps, etc.) and save as much hard-disk space as possible.

I want to install from the minimal CD image ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) but I'm wondering if it will be suitable for a LAPTOP install.

On my current Lenovo T61 with Heron installed I noticed there are specific things installed to work with the laptop that were installed automatically from the FULL live install CD; things like: 

[LIST]
[*]apmd
[*]hotkey-setup
[*]laptop-detect
[*]laptop-mode-tools
[*]libapm1
[*]pcmciautils
[*]radeontool*
[*]toshset*
[/LIST]

*I don't know why these are installed as I don't have a Toshiba laptop and since my laptop is Lenovo T61, it has integrated Intel graphics (so why Radeon?!)

So my question is, will these packages, most of which seem necessary for a proper laptop install, get installed by the minimum install CD? Or will I have to install them manually? (How will I know what exactly I _will_ need?)

Thanks!

---

### Post by theravenproject on 2008-05-31
Like the doucumentation on the Minimal CD Image Download Link page says-it provides the Minimum Requirement for installing Ubuntu onto your CPU and conserves space on the installation media by getting additional packages from online repositories at the time of install...okay I just said what the page did right?  Big Help!  No really though...what you have to do is just lookup what packages your specific laptop needs in order to do what you want it to do...not so hard.  One thing you should know if you already have a copy of Ubuntu/Any Linux Distro...It is highly configurable AFTER INSTALLATION!  If you don't get everything you need at the time of installation package wise; all you have to do once it is installed is go to the package manager and pick out what you need or want.  Make sure that you enable Multi-verse and Universe Repositories...Also, You will find (And this is not always the Gospel Truth as in the case of my Nvidea Graphics Card) that Ubuntu/Linux is very adept at detecting your system specific hardware and installing the Necessary Drivers!  Now sometimes it fails and you have to go looking for a miscellaneous driver the old fashioned way but this is not like Windows where as soon as you install you have to sit there loading driver cd's fot hours!  Linux has a driver (Or two or three or four!) for every piece of Hardware imaginable and if you come across something that isn't covered-inform the community and someone will write one!  Okay-hope this was of some help...Good luck with your laptop install and oh, by the way, there is another place you could try and post your prob,,,hardware/laptops but I don't know-suppose that is a good question for one of the Gurus around here:  Does your prob fall under "Installation/Upgrades or Hardware/Laptops?-that is the question..LOL!!!  Good luck friend-we wish you the best!;)

---

### Post by Rallg on 2008-05-31
If you have enough disk space to start, consider installing the full version, update it, get all your hardware running, then delete applications you don't need.

Some packages are archived for future use. You can get rid of the archived copies from Terminal:

sudo apt-get clean

---

### Post by geo909 on 2008-05-31
I've found out that people who use the minimal installation cd, usually tend to install different window managers and light stuff. If you just want to get rid of the extra applications, that can be easily done by just removing them, like Rallg said.

---

