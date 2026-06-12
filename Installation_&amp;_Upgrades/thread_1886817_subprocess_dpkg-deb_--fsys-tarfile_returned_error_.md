---
title: "subprocess dpkg-deb --fsys-tarfile returned error exit status 2"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2011-11-25
I have been trying to install programs via the software center on 11.10 but I keep getting a failure message - 

subprocess dpkg-deb --fsys-tarfile returned error exit status 2

Any idea what this means and how I can fix it?

---

### Post by jerrrys on 2011-11-27
what happens when you use apt-get install?

also got some hits here, may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dpkg-deb+--fsys-tarfile+returned+error+exit+status+2&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dpkg-deb+--fsys-tarfile+returned+error+exit+status+2&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=exit+status+2&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=exit+status+2&sa=Search&cof=FORID:9)

---

### Post by summentier on 2012-05-21
As described here ([https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/881181]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/881181%20")),  try typing the following lines into your terminal:
```
sudo apt-get clean
sudo apt-get upgrade
```(see [https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal) if you do not know how to start a terminal)

Resolved the issue for me. Hope this helps!

---

