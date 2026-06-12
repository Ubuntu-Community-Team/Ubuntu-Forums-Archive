---
title: "install the full Ununtu"
date: 2021-06-08
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-08
I fell for the option "install only basic" , hoping it would be faster. It was not. 
Now I am missing "stuff" likes LibreOffice etc. 
**Is there  a way to reinstall ALL on RUNNING OS?**
I do not fancy to go back to ISO and do it again.

---

### Post by TheFu on 2021-06-08
sudo apt install ubuntu-desktop ?

```
$ apt search ubuntu-desktop
Sorting... Done
Full Text Search... Done
edubuntu-desktop/bionic 15.12.9 amd64
  educational desktop for Ubuntu

kubuntu-desktop/bionic 1.370 amd64
  Kubuntu Plasma Desktop/Netbook system

lubuntu-desktop/bionic-updates 0.94.1 amd64
  Lubuntu Desktop environment

qtubuntu-desktop/bionic 0.64+17.10.20170707-0ubuntu7 amd64
  Qt plugins for Mir support on Ubuntu (desktop)

**ubuntu-desktop**/bionic-updates 1.417.5 amd64
  The Ubuntu desktop system

xubuntu-desktop/bionic 2.225 amd64
  Xubuntu desktop system
```

---

### Post by anneranch on 2021-06-08
> **TheFu said:**
> sudo apt install ubuntu-desktop ?

```
$ apt search ubuntu-desktop
Sorting... Done
Full Text Search... Done
edubuntu-desktop/bionic 15.12.9 amd64
  educational desktop for Ubuntu

kubuntu-desktop/bionic 1.370 amd64
  Kubuntu Plasma Desktop/Netbook system

lubuntu-desktop/bionic-updates 0.94.1 amd64
  Lubuntu Desktop environment

qtubuntu-desktop/bionic 0.64+17.10.20170707-0ubuntu7 amd64
  Qt plugins for Mir support on Ubuntu (desktop)

**ubuntu-desktop**/bionic-updates 1.417.5 amd64
  The Ubuntu desktop system

xubuntu-desktop/bionic 2.225 amd64
  Xubuntu desktop system
```
Nope, it siad already instilled \



Now I am looking for that  fancy replacement  - by recent version of Ubuntu - for  "PrtScr" key   to take a screenshot and cannot find the name of it.

---

### Post by david504 on 2021-06-08
if  you want software + a light install

sudo apt-get remove ubuntu-desktop 
sudo apt-get install lightdm
sudo apt-get install xubuntu-desktop 
choose lightdm when it asks for the default display manager.

---

