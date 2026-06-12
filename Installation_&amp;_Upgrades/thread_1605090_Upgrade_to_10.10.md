---
title: "Upgrade to 10.10?"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by speedracer2010 on 2010-10-24
I am currently running 10.04LTS and saw that a potential newer version 10.10 was out. Following up on the readme I entered update-manager -d in a command box and get the update manager. When I click on UPGRADE it tells me this is a beta version and should NOT be used on a production system. When I go to the upgrade manager from the menu bar and have it scan for any updates there is NO upgrade option offered. So, is the 10.10 officially out or is this a beta/almost ready for prime time version. IF it is the real mccoy then what is the correct way to upgrade with this latest release version without a complete reinstall. THANKS for any answers offered..

---

### Post by DougieFresh4U on 2010-10-24
**[COLOR="Red"]NOT THE APPROVED METHOD[/COLOR]**
The way **_I_** do it, via **terminal**;
```
gksudo gedit /etc/apt/sources.list
```
change all **maverick** to **natty**
save, then:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```
then **_I_** do
```
sudo update-grub2
```

---

### Post by Sef on 2010-10-24
> So, is the 10.10 officially out or is this a beta/almost ready for prime time version.

What do you use your computer for? If you value stability, then stick with Lucid. It will get updates for 3 years. Maverick will get updates for only 18 months.

> The way I do it, via terminal;
Code:
gksudo gedit /etc/apt/sources.list
change all maverick to natty
save, then:
Code:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
then I do
Code:
sudo update-grub2

That is not an approved method any more to update. This is the approved way to [update]("https://help.ubuntu.com/community/MaverickUpgrades").

---

### Post by Yarui on 2010-10-24
> **Sef said:**
> What do you use your computer for? If you value stability, then stick with Lucid. It will get updates for 3 years. Maverick will get updates for only 18 months.
Considering he is using the version that was released just over 6 months ago and is willing to update to a newer version, my guess is that he doesn't mind updating to the newer version every 6 months.  If you are afraid of doing a fresh install, though, from what I have heard the upgrade system is a bit of a gamble.  It may work wonderfully, but it could cause you some issues that make you want to just use a fresh install.  It's your call whether or not this is a risk worth taking.

---

### Post by DougieFresh4U on 2010-10-25
> **Sef said:**
> 


That is not an approved method any more to update. This is the approved way to [update]("https://help.ubuntu.com/community/MaverickUpgrades").
As I stated, that is the way **[SIZE="6"]I[/SIZE][SIZE="4"][/SIZE]** do it

---

