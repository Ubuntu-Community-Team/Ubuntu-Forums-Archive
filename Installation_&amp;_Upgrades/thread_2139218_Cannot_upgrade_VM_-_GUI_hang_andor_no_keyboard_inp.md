---
title: "Cannot upgrade VM - GUI hang and/or no keyboard input"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by thany on 2013-04-26
I'm running (regular) Ubuntu 12.10 x64 in a VM inside Virtualbox 4.2. VB Additions are running, video driver is working properly and everything. It's fully updated.

When I do the upgrade from the software updates tool, the GUI just hangs at some and the whole upgrade process doesn't do anything. The whole machine is not hanging though, the mouse cursor moves as normally. There's no CPU or HDD activity during the hang.

I also tried to do the upgrade from the commandline. At some point it's asking me a question about something-something virtualbox module, but the thing is, I cannot type anything. Mouse input appears to work normally, I can select text at the terminal and even open a new one. The fact that the terminal has lost all of it chrome is probably because the GUI is in the process of being upgraded too. At any rate, I cannot answer the question being asked, because the terminal doesn't accept any keyboard input at all. In fact, NOTHING I do on the keyboard does anything. I can inject Ctrl+Alt+Del as much as I want and not even that has any effect. NOTHING goes in, so it seems.

So how do I answer any questions during the upgrade??

/edit
Small update: it appears to ONLY work when I turn over to a real textmode terminal, such as the one you get after Ctrl+Alt+F2.

@Developers: please look into this. VirtualBox is not too uncommon, is it?

---

