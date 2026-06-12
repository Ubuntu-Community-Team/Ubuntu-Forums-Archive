---
title: "after upgrade to Gutsy, many Administrative tools are gone"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by JMonkeYJ on 2007-11-19
I'll preface this by saying i'm fairly linux ignorant...

so i decided to upgrade feisty to gutsy, which, given my disclaimer above, was perhaps not the best idea. during the upgrade process, some dialogs popped up asking if i wanted config files overwritten. i answered no to all of these so as not to lose my personal info. also, several times it popped up questions about some ldap packages. i didn't know how to answer them, so i hit escape a bunch of times until they went away.

now i have gutsy, and things actually seem pretty OK so far, with one big exception...the add/remove programs program is gone, but more importantly, synaptic is also gone! also, i notice there are many fewer programs in System > Administration now. i didn't really use most of those, so i can't tell you what's gone. what's still there:

Keyring Manager
Network Tools
Printing
System Log
System Monitor
Update Manager

running update manager does nothing. i figured i'd try to get some help before i actually need to install anything...

---

### Post by por100pre1 on 2007-11-21
Some tools now use different launchers, but maybe the upgrade went wrong. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get reinstall ubuntu-desktop
```

BTW, welcome to the forums! Sorry for the delay.

---

### Post by JMonkeYJ on 2007-11-21
thank you, i will certainly try that...one thing i did discover, however, is that i can still access synaptic from the command line, it's just gone from the menu!

as long as i run it with sudo it seems to have all the same functionality as before. it just seems sort of odd that the icons didn't get reinstalled. i'll let you know what happens after i reinstall the desktop.

---

### Post by JMonkeYJ on 2007-11-21
OK, i ran the command:

> sudo apt-get --reinstall install ubuntu-desktop

that's a little different than what you suggested, but i think it's what i was supposed to do. sadly, it didn't put the icons back in the System menu. it's not a big deal since i can run it from the command line, but i'm worried that if i need some other administrative tool, it won't be there and i won't kno what to do.

---

### Post by quonsar on 2007-11-21
use the program alacarte to edit your menu. just type alacarte in a terminal window. if it's not installed, use synaptic to get it.

---

### Post by por100pre1 on 2007-11-22
> **quonsar said:**
> use the program alacarte to edit your menu. just type alacarte in a terminal window. if it's not installed, use synaptic to get it.

This poster got the answer! Actually I edited some entries manually, for example, I removed **Font** that is now part of **Appearance**. It seems that could be the solution for you.

---

### Post by JMonkeYJ on 2007-11-26
haha, oh my, this new problem is just so weird as to be hilarious:

alacarte does look like it's exactly what i want. i go to the System > Administration menu in alacarte, and i see all the tools, most of them without checks next to them. the ones without checks are also italicized. now i check one of them, say Synaptic Package Manager. The check mark stays there for about 5 seconds then disappears!!! if i quickly close alacarte before the checkmark disappears, it still doesn't work.

i feel like i'm in some cartoon here! clicking on things then they disappear right as i'm about to exit. very odd!

so close yet so far... :P

BTW, i noticed that if i log in as root, all the Administrative program icons are still there...

---

