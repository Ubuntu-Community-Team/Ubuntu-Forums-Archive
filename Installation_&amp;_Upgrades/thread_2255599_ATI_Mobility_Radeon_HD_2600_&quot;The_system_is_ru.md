---
title: "ATI Mobility Radeon HD 2600: &quot;The system is running in low graphics mode&quot;"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by dontstopmenow on 2014-12-06
Hi eveybody, it's my first post!
I'm sorry for my english, i'm italian so please forgive my mistakes...
my notebook is toshiba satellite a200-289 and i've just upgraded ubuntu to version 14.10, but when it reboot it starts when ...the system is running in low graphics mode and i do not know hoe to fix it. please consider that i'm an absolute beginner so &#8203;answer me in the most simple way. thanks in advance

[LIST]
[*][B]
[/B]ATI Mobility Radeon HD 2600, 128MB dedicati
[/LIST]
[COLOR=#101010][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by Mark Phelps on 2014-12-06
Some folks might tell you to install the AMD drivers, but AMD dropped driver support for your card last summer; so, forcing an install of AMD drivers now is only going to corrupt your display.

What might work is adding either xforcevesa or nomodeset to your kernel boot parameters: [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by dontstopmenow on 2014-12-16
mmh sorry i do not know how to do, i need to be follow step by step, im a very beginner.
i also have a message from terminal NAK bailout for several times, i've read somewhere that it's a problem of the version of ubuntu during installation

---

### Post by Mark Phelps on 2014-12-16
>  i need to be follow step by step, im a very beginner.

Right ... and the step-by-step actions are listed in the link.  

You need to read through them, especially the part about setting the options temporarily in an already installed OS.

---

