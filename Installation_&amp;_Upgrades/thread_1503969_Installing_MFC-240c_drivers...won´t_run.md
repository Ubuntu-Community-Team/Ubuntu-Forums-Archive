---
title: "Installing MFC-240c drivers...won´t run"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Dishuman on 2010-06-07
[LEFT][FONT=Century Gothic][SIZE=4]I run a [COLOR=Red]Lenovo Ideapad Y530[/COLOR] with [COLOR=Red]Ubuntu 10.04[/COLOR]. I love this OS so far, but because my knowledge in coding is limited there are times when my patience runs thin and I fall into deep despair and frustration.[/SIZE][/FONT]

[FONT=Century Gothic][SIZE=4]My dilemma right now circles around the fact that I cannot print via my Brother [COLOR=Red]MFC-240c[/COLOR] printer. The friend who installed Ubuntu for me is away in New York and cant explain on the phone. He says the driver should come up automatically but this does not happen for the [COLOR=Red]MFC-240c[/COLOR]. [/SIZE][/FONT]

[FONT=Century Gothic][SIZE=4]I downloaded the drivers from the brother website. They were .deb files so I opened them up using the GDebi Package installer. First the [COLOR=Red]LPR[/COLOR] then the [COLOR=Red]CUPS[/COLOR]. The printer is visible in the system but it just doesnt print and freezes when ¨Receiving Data¨. [/SIZE][/FONT]

[SIZE=4][FONT=Century Gothic]I tried installing through the terminal and I kept getting errors of directories and files that weren´t found. Should I extract the package even when its on a .deb? I would think this true, but *shrugs* I am not sure. [/FONT][/SIZE]


[FONT=Century Gothic][SIZE=4]Please, I am in desperate need of help.[/SIZE][/FONT]

[FONT=Century Gothic][SIZE=4]PS: I am 90% sure I run [COLOR=Red]64bits[/COLOR]. [/SIZE][/FONT]

[/LEFT]

---

### Post by dino99 on 2010-06-07
with ubuntu, the packages are already compiled and ready to install: 

open synaptic (system admin synaptic) and install:  brother-lp-drivers-bh7

this package deal with your printer (search: "mfc" into synaptic)

---

### Post by timfinley on 2010-07-04
Thanks for the fix dino!!! same problem same printer. now to get the scanner key working....

---

