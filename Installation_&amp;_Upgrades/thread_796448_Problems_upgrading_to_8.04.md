---
title: "Problems upgrading to 8.04"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by skurpi on 2008-05-16
I am having a wierd problem. I cant upgrade my 7.10 to 8.04. When I run update manager, and update everything to the lastest, I still dont get the button to "Upgrade to 8.04".

Anyone know how to fix this bug, or just a command-line to "manually" upgrade to latest version?

---

### Post by dstew on 2008-05-16
When you open the Update Manager window, what does it say at the top?

---

### Post by skurpi on 2008-05-16
"Your system is up-to-date"

---

### Post by linux phreak on 2008-05-16
Try changing to "main server" in the software sources then update the list.

---

### Post by jpietari on 2008-05-16
Option 1 - From the commandline:
sudo apt-get update && sudo apt-get dist-upgrade

Option 2 - Download CD

---

### Post by skurpi on 2008-05-16
It was already set to main server. I tryed switching it to swedish server, didnt work, then back to main server... didnt work

the apt-get commands did not work either, the output after the last command is 
```
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Beräknar uppgradering... Färdig
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.

```
Which translated means: 0 upgraded, 0 new installs, 0 to remove and 0 not upgraded

Anything else? I would prefer to install it via network instead of CD

---

### Post by housam on 2008-05-16
Try this guide :[[COLOR="Red"]_http://www.ubuntu.com/getubuntu/upgrading_[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by lswest on 2008-05-16
hit <alt>+F2 and then type in "update-manager -d" (without the quotes) and it should prompt you for a new version of Ubuntu.

---

### Post by skurpi on 2008-05-16
> **housam said:**
> Try this guide :[[COLOR="Red"]_http://www.ubuntu.com/getubuntu/upgrading_[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading")

Doesnt say anything new. Already tried that

---

### Post by skurpi on 2008-05-16
> **lswest said:**
> hit <alt>+F2 and then type in "update-manager -d" (without the quotes) and it should prompt you for a new version of Ubuntu.

Very strange, but that did not work either. It starts the update manager, but the button to upgrade to 8.04 still doesnt show

---

### Post by az on 2008-05-16
Do you have the security and updates repositories enabled?

---

### Post by skurpi on 2008-05-17
I started my computer today (the next day) and it is now working, the button to upgrade is showing. Dont know what the problem was but it is resolved now. Thanks for the help

---

