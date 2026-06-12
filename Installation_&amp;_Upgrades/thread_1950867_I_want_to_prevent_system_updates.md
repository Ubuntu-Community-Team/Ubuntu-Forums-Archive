---
title: "I want to prevent system updates"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by AustenB on 2012-04-01
My network card driver module does not update correctly with each system update.  Specifically, it tries to install r8169 when it will only work with r8168.  I have to manually adjust this with each update.  I would like to be able to make my machine either

not update the network card driver module with each system update

or

not update anything.

Suggestions?

---

### Post by hakermania on 2012-04-01
Update Manager lets you select the updates you want to install (it has a checkbox in each suggested update), but in case this doesn't work for you you can manage updates through Software Center->Edit->Software Sources->Updates
[http://i.imgur.com/DjDbi.png](http://i.imgur.com/DjDbi.png)

---

### Post by arpanaut on 2012-04-01
If you have synaptic package manager installed you can lock the driver package to the current version and it will not be upgraded.
In synaptic select Installed then find the package you want to lock click on that then in the menu select package, then select Lock Version, done. It wont be upgraded until you unlock it.

---

### Post by jerrrys on 2012-04-01
> **arpanaut said:**
> If you have synaptic package manager installed you can lock the driver package to the current version and it will not be upgraded.
In synaptic select Installed then find the package you want to lock click on that then in the menu select package, then select Lock Version, done. It wont be upgraded until you unlock it.

+1 on that

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

in terminal enter:
sudo apt-get install synaptic

---

### Post by AustenB on 2012-04-01
Thanks a bunch for the replies, I'll try the synaptic package manager!

---

