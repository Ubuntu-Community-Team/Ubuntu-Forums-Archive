---
title: "Complete Ubuntu Noob!"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Rkilbane on 2007-03-28
I am trying to install wine.  I just switched from XP to Ubuntu and I can not figure out how to install anything.  I have tried every tutorial on how to install wine and non of the seem clear enough and expect me to know something that I do not no.  If somebody can tell me how to install wine clearly and which version to get that would be so awesome.

---

### Post by esodin on 2007-03-28
I am very much an Ubuntu noobie like your self. I found out that the simple way to install anything in Ubuntu is to use the tools built into Ubuntu. Unfortunately, I am now at work (no Ubuntu available here), so I cant tell you the exact names of the programs to use. You first need to set up your repositories (where Ubuntu finds all the programs it can install directly) to also include more than the basics. It's under the administration menu. You then need to go to the Synopic (?) package manager (not totally sure about the name) and search for wine. Select it when it fines it and say yes to any additional packages Ubuntu wants to install. once installed there are two important commands: ***winecfg ***(this allows you to set up Wine) it lookes like a window from XP; and ***wine ***. wine needs to be run from the terminal. you put it in front of the program you want to run.

I am not on an ubuntu machine right now, but I'll check back when I get home and see if you have got it working.

My message is: don't give up. I now have all sorts of Windows programs working great under Ubuntu, including CS:S and Movie Collector. Both very important to me. :)

---

### Post by LCC on 2007-03-28
Wich version are you running? 6.10? if so

Go to the terminal (APPLICATIONS, ACCESSORIES,TERMINAL)  and copy and paste the following

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

press enter then type

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

What the above commands done was tell the [COLOR="Red"]synaptic package manager  [/COLOR] where to look for wine
Synaptic Package manager (SYSTEM, ADMINISTRATION, SYNAPTIC PACKAGE MANAGER) now the next time you type  wine it will now where to find it, but be sure to do the following on the synaptic:  go to SETTINGS, REPOSITORIES and enable MULTIVERSE and UNIVERSE  sources of repositories.Now on synaptic you click on search and type [COLOR="Red"]wine[/COLOR]  then you select and click on install. After installed close synaptic 

Then on the terminal (APPLICATIONS,ACCESSORIES.TERMINAL) you type winecfg and just ok the options it shows, close it and then when you have a[COLOR="Red"] .exe[/COLOR] you
right click the file and choose  OPEN WITH ANOTHER APLICATTION, there will be a little arrow saying USE A CUSTOM COMMAND on that you type wine

---

### Post by Rkilbane on 2007-03-28
Alright thanks to the both of you I finally got it working.  Not only wine but I got to play Counter-Strike also.  All I have to do is put in the fonts and I will be able to read what people say and other things but its still playable.  It runs better on Ubuntu then my Windows.

---

