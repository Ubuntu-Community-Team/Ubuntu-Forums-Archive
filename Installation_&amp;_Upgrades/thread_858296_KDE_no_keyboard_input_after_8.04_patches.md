---
title: "KDE: no keyboard input after 8.04 patches"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by lptr on 2008-07-13
A friends machine does not accept any keyboard input in KDE since last update. He initiated an update via Adept installer last Friday. That installed some 152 packages. Latest kernel and I expect also X. 

Obviously something went wrong, here. He says that machine boots normally. Because automatic log on KDE desktop is active he can use his mouse starting programs and the like. But whatever app he tries to using his keyboard does not work. Ctrl-Alt-F1 does not open normal text console.


[update]
After some research and thinking about what could have been responsible for this strange behaviour I am pretty safe, that it has to do with the following:

This Kubuntu machine has originally been set up in USA with US keyboard connected. This guy came back to Germany using a german Keyboard now and so switched the settings to regional settings.

Anyhow - one of the locales patches we recognized the last weeks probably caused this - I don't need to know my keyboard inputs - on this systems.

Anyone already found a solution for this, too?

rob*

---

