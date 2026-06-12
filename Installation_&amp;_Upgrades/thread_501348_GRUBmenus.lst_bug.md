---
title: "GRUB/menus.lst bug"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2007-07-15
This has been annoying me for a while. Actually, it's got to the stage where I just accept it, make the necessary change and move on, but I think it's about time this was fixed. I don't know if it's a GRUB bug or (K)ubuntu problem or if it's already been logged, but:

Every single time I reinstall or upgrade my system, my menus.lst gets broken. For some unfathomable reason the whatever-is-busted goes and changes the root from (hd0,0) to (hd2,0) and removes the necessary noapic switches. It's OK when you know to expect it and know how to fix it from the command line, but I'm thinking of the people who, bless 'em, just want to update KDE or the new kernel or whatever it is Adept is prompting them to install ("It's got a big danger sign on it, I'd better install it or bad stuff might happen, even though I don't know exactly what it means, I'll trust Ubuntu...."). Whoops! Not only is your GRUB menu list destroyed ("the what now? Does this mean no dinner?") but your graphics driver no longer works ("there's something wrong with my car too??") and to all intents and purposes you have no more computer until you can persuade your nephew to come round and fix it. 

There must be some reasonable way to allow people to upgrade their system (or at least warn them *not* to if they're not nerded up rather than warn them they *have* to) and subsequently fix their graphics drivers and not fsck up their boot loader.

Currently, it's like giving kids chocolate full of powdered glass.

---

### Post by mikewhatever on 2007-07-15
You frustration is understandable. Yes, grub should work better, especially with multiple hdds, updates should not break the system, all hardware should be recognized, etc. I too wish that would be the case, but do we live in the perfect world?
You may help to fix some of those problems and benefit yourself and the community in the long run, by filing a bug report at launchpad.net.

Regards.

---

### Post by Pumalite on 2007-07-15
Do not fix your system if it's not broken. Every kernel update implies you'll have to recompile your graphics driver modules, As for distribution updates; I'll wait until October. You should always backup your menu,lst and fstab before updates. As a matter of fact you should have backups of those files, period.

---

### Post by mikewhatever on 2007-07-15
> Every kernel update implies you'll have to recompile your graphics driver modules,
Not in my case. The latest kernel update was totally painless.

---

### Post by Pumalite on 2007-07-15
I use propietary drivers.

---

### Post by pickarooney on 2007-07-15
> **Pumalite said:**
> Do not fix your system if it's not broken. 


A rather trite statement surely, when the OS itself is goading you to update (flashy warning sign).

> 
Every kernel update implies you'll have to recompile your graphics driver modules, As for distribution updates; I'll wait until October. You should always backup your menu,lst and fstab before updates. As a matter of fact you should have backups of those files, period.

But, even supposing Joe Q. Ubuntunewbie knew that, it wouldn't be enough, as the old menus.lst would reference the previous kernel and therefore not boot.

> You may help to fix some of those problems and benefit yourself and the community in the long run, by filing a bug report at launchpad.net.

I'd like to, but does it go under Ubuntu or GRUB, does anyone know?

---

