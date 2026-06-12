---
title: "Running upgrade from CMD prompt"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Avenolpey on 2008-09-30
Can someone tell me how to run an upgrade to Hardy Heron from a command prompt. My attempt from Upgrade Manager failed and I can't get the keyboard to respond once the GUI loads. Perhaps if I run it again I will figure out what went wrong.

Thanks

---

### Post by caljohnsmith on 2008-09-30
I don't remember if you have to manually update your sources.list file to make this work, but I think all you have to do in order to upgrade to Hardy is:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Give that a shot and let me know what happens.

---

### Post by Avenolpey on 2008-09-30
sudo apt-get update
sudo apt-get dist-upgrade

Thanks for the suggestion. Not sure it did anything. It ran in 5 seconds and replied it was done. Held back two apps. Upon reboot the mouse and keyboard still do not work and I don't have a normal login screen, just a single bar that says user_____________________

---

### Post by cariboo on 2008-09-30
It sounds like your upgrade process was interupted before it finished, you could try a couple of other things:

```
sudo apt-get -f install
```

If that doesn't complete your upgrade, then try:

```
sudo dpkg-reconfigure -a
```

This should reconfigure any partially installed programs.

Jim

---

### Post by zvacet on 2008-10-01
First look your source list to be sure that all gutsy is replaced by hardy.If that is not a case do it yourself.Then 

```
 sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 
```

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

