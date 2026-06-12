---
title: "Skype not installing on Lubuntu"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by Althusian on 2013-06-28
**Trying to install Skype on Lubuntu (Ubuntu 12.10, LXPanel 0.5.11, on a Toshiba laptop)**

Hi all, would appreciate some advice on this


**1] Tried via Synaptic:**
Menu > System Tools > Synaptic Package Manager
From Synaptic
Settings > Repositories > Other Software - Please check the attached screenshot.
Clicked "Canonical Partners", clicked "Close" then on the main screen of Synaptic, clicked "Reload".


Got this


[FONT=courier new]Mark addition required changes?[/FONT]
[FONT=courier new]The chosen action also affects other packages.[/FONT]
[FONT=courier new]The following changes are required in oder to proceed[/FONT]
[FONT=courier new]To be installed[/FONT]
  [big list of libs etc here]


clicked 'Mark'


Got this:


[FONT=courier new]Could not mark all packages for installation or upgrade[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]The following packages have unresolvable dependencies.[/FONT]
[FONT=courier new]Make sure that all required repositories are added and[/FONT]
[FONT=courier new]enabled in the preferences[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]skype:[/FONT]
[FONT=courier new]  Depends: skyp-bin[/FONT]


Closed it, found skype unmarked for installation.


**2] Tried via Skype website, downloaded version for 12.04, used GDebi Package Installer:**
fairly early on got this:


[FONT=courier new]Error: Cannot install 'libqt4-dbus:i386'[/FONT]


**3] Tried advice from forum, using command line:**


[FONT=courier new]sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"[/FONT]
[FONT=courier new]sudo apt-get update[/FONT]
[FONT=courier new]sudo apt-get install skype[/FONT]


Got this fromt the install command:


[FONT=courier new]The following packages have unmet dependencies.[/FONT]
[FONT=courier new] skype : Depends: skype-bin[/FONT]
[FONT=courier new]E: Unable to correct problems, you have held broken packages.[/FONT]


Any ideas?

---

