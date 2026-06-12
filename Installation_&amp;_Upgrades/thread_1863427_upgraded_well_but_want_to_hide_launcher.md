---
title: "upgraded well but want to hide launcher"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by jonthiele on 2011-10-17
The upgrade went smoothly and the computer works.  

I would like to hide the launcher forever.  In help I saw that one can change icon size via Compiz Config Settings Manager and thought maybe that will tell me how to kill it too.  So I went to the software center to get it, and it said it was already installed. I hit the gear, system settings, personal, and Compiz is not there as it is supposed to be.

So please help: how do I get rid of the launcher?

Second request:  How do I add icons to the top panel?  Next to the battery level indicator and wireless signal thing, I'd like to add the system monitor, force quit, and a couple others lost in the upgrade.

Thank you for your attention and, yes, you may correctly infer from phrases like "the computer works" that I am not a technical guy so simple instructions will be appreciated.

---

### Post by jonthiele on 2011-10-19
When I put the cursor on an icon in the launcher and reveal a menu such as 'safely eject' a USB, the menu does not work.  Salections do not highlight and clicking on them does nothing.

---

### Post by jonthiele on 2011-10-29
So is it possible to hide the launcher?

---

### Post by dFlyer on 2011-10-29
If you install compizconfig-setting-manager (ccsm) you will be able to hide the launcher.

From a terminal enter the following command:

sudo apt-get update
sudo apt-get install compizconfig-setting-manager

After the program is installed press alt-F2 and enter about:config in the pop up windows.

you will find the setting under experimental

---

### Post by Hakunka-Matata on 2011-10-29
> **jonthiele said:**
> The upgrade went smoothly and the computer works.  

I would like to hide the launcher forever.  In help I saw that one can change icon size via Compiz Config Settings Manager and thought maybe that will tell me how to kill it too.  So I went to the software center to get it, and it said it was already installed. I hit the gear, system settings, personal, and Compiz is not there as it is supposed to be.

So please help: how do I get rid of the launcher?

Second request:  [COLOR=Red]How do I add icons to the top panel?[/COLOR]  Next to the battery level indicator and wireless signal thing, I'd like to add the system monitor, force quit, and a couple others lost in the upgrade.

Thank you for your attention and, yes, you may correctly infer from phrases like "the computer works" that I am not a technical guy so simple instructions will be appreciated.
[COLOR=Red]How do I add icons to the top panel?[COLOR=Black]
left mouse button on an Icon you want, hold the left button down and drag the Icon to the top panel, then release.  That copies the Icon to the panel.[/COLOR]
[/COLOR]

---

### Post by jonthiele on 2011-10-30
Thank you for your replies, but the reco'd fixes do not seem to be working.

For moving icons to the top panel, it simply doesn't happen.  The icon moves off the launcher, but it does not stay where I put it whether it is the top panel or the desktop.  It returns to the launcher.  And I cannot find "force quit" or "system monitor" in the first place (these are what I want up there).

For the compfig, it is installed already.  It does not appear in the perosnal menu of system settings as the help guide says it should, and at the software center there are comments that say using it with 11.10 can be deadly.  

There is on improvement since my comments, though.  If I right click and hold on an icon on the lauch bar, the menus work now.

---

