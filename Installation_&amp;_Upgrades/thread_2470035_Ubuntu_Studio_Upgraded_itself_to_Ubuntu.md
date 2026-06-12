---
title: "Ubuntu Studio Upgraded itself to Ubuntu"
date: 2021-12-17
forum: Installation &amp; Upgrades
---

### Post by newreg on 2021-12-17
It appears that the recent upgrade to my Ubuntu Studio from 21.04 to 21.10 has changed it  to Ubuntu rather than Ubuntu Studio. For one thing, the menu no longer  has the pre-installed Studio apps and also, checking the version shows  only Ubuntu. Is there a way to get Ubuntu Studio back short of a fresh  install?

 In trying to repair, I ran:

> sudo apt install ubuntustudio-installer 

but says it's already the newest version so it made no difference. I also tried to just install the desktop itself along with the various menu entries such as

 > sudo apt-get install ubuntustudio-desktop^
 but nothing seems to happen. I also tried
 > sudo tasksel install ubuntustudio-desktop
 but nothing other than a very brief install progress dialog that  disappears as quickly as it started. I logged out and used the desktop  selector but do not see Ubuntu Studio as one of the choices so I ran
 > ls /usr/share/xsessions
 which shows
 > gnome-classic.desktop gnome-xorg.desktop ubuntu.desktop
xfce.desktop gnome.desktop plasma.desktop 
ubuntu-xorg.desktop xubuntu.desktop
 and there is no Ubuntu Studio to be found. It shows Ubuntu Studio on  the bootup's splash screen but the applications do not show the apps in  the menu although I was able to restore them through a series of commands.

 I also seem to recall that this used to show Ubuntu Studio rather than Ubuntu (I had to add a space as otherwise it kept putting in a smiley face for some reason!)
 > lsb_release -a
LSB Version: core-11.1.0ubuntu3-noarch: printing-11.1.0ubuntu3-noarch:security-11.1.0ubuntu3-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 21.10
Release:    21.10
Codename:   impish

---

### Post by yetimon_64 on 2021-12-17
It sounds as though the upgrade has added another session (ubuntu or gnome) and changed the active session to that. As far as I'm aware ubuntu-studio uses an Xfce session.

I'd suggest you log out and on the log in screen select the session option to boot into. I'd try the xfce and xubuntu sessions to see which one has your previous menus set up. You should only have to select the session for one boot and it should be remembered for all subsequent boot ups.

There may be more to check into but that is where I'd start looking considering the upgrade aspect, hopefully it is as simple as selecting the original desktop session from the log in screen. Your old menus should still be accessible from a different session boot if it is only the default session being changed by the upgrade.

Good luck, yeti.

---

### Post by guiverc on 2021-12-17
Ubuntu Studio last used Xfce in 20.04, and all *release notes* state a re-install was required and not upgrade to avoid issues, as [Ubuntu Studio 20.10]("https://ubuntustudio.org/2020/10/ubuntu-studio-20-10-released/") and later use a KDE Desktop

Prior questions on topic can be found at 
- [https://askubuntu.com/questions/1378120/21-10-upgrade-changed-versions](https://askubuntu.com/questions/1378120/21-10-upgrade-changed-versions)
- [https://askubuntu.com/questions/1374825/xubuntu-splash-showing-when-prior-was-ubuntu-studio-theme](https://askubuntu.com/questions/1374825/xubuntu-splash-showing-when-prior-was-ubuntu-studio-theme)

Yes the Ubuntu infrastructure that Ubuntu Studio uses will allow upgrades; but problems were warned as are encountered into the future.  This only relates if you were using 20.04 or Xfce before your 21.04 upgrade; and won't apply if 21.04 (or 20.10) was a *clean* Ubuntu Studio install (ie. no Xfce or GNOME toolkit was included).

You can re-install Ubuntu Desktops without ending up with a *fresh* install. I **don't** do it often with Ubuntu Studio primarily as the ISO is very large (*compared with others*) but also not enough hours in the day to allocate to QA (*Quality Assurance*) testing. I'll provide a link to a case where I mention it for [Lubuntu testing]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") where it's referred to as "*Install using existing partition*", as Lubuntu use the same `calamares` installer just as Ubuntu Studio does in 20.10-21.10 releases.  I do use the install type ~weekly (*far more often* nearer releases) as it's a QA-test install & I use it to upgrade my *jammy* & LTS (*focal* or 20.04) support boxes instead of doing a `sudo apt update; sudo apt full-upgrade` as it accomplishes both upgrade of packages & a QA-test install; it's a Lubuntu QA checklist item)

---

### Post by ActionParsnip on 2021-12-18
Just log in to the XFCE session on the log in page. Ubuntu Studio uses XFCE as the desktop environment then has some different default apps.

---

### Post by MAFoElffen on 2021-12-19
To all... Just a note.

guiverc and sudodus are both tireless and dedicated Users, that do most of the QA (Quality Assurance) Testing for Ubuntu and Ubuntu's Flavors ISO's before their release. In my honest opinion, they are unsung heroes for all the testing they do. 

I trust guiverc in knowing what is what in different flavors of Ubuntu, what works with different hardware, what should happen & when. He and sudodus work behind the scenes, unrecognized, and are very under-appreciated. Both of them helped to test my Ubuntu Forum's User support script ('system-info') to ensure it was certified safe and worked for various possible hardware combinations, and for all flavors of Ubuntu.

If he says there was "a change"... I trust that is was changed, and that he saw that "personally"...

I would think that the menu's, might still be within the XFCE Desktop and all the app's are still there, but the 'Flavor' has evolved and has changed it's path. To stay on the Ubuntu Studio's current path, look at quiverc's post #3.

---

### Post by DuckHook on 2021-12-19
&#8593; &#128077;
> **MAFoElffen said:**
> To all... Just a note.

guiverc and sudodus are both tireless and dedicated Users, that do most of the QA (Quality Assurance) Testing for Ubuntu and Ubuntu's Flavors ISO's before their release. In my honest opinion, they are unsung heroes for all the testing they do.
This is true of you too, MAFoElffen. =d>

---

### Post by MAFoElffen on 2021-12-21
@DuckHook

You had me in tears of joy and understanding. 

I know how hard it is sometimes. I try and I care about 'Users'. 

I know that in the past, having been a been a Moderator myself, that 'that' is a dedicated job (also), with a lot of things behind the scenes that people just do not see and comprehend. 

I know... and I understand. (To the User's of Ubuntu... And all the people that make that possible!!!)

Thank you.

---

