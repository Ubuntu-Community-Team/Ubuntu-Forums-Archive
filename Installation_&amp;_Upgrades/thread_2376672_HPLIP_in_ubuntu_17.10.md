---
title: "HPLIP in ubuntu 17.10"
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2017-11-04
What is (or is there a) the terminal command to install HPLIP in Ubuntu 17.10?
Thanks in advance.

---

### Post by rbmorse on 2017-11-04
sudo apt install hplip will get you the basic package and drivers.   

If you want the fancy graphical front-end the command is sudo apt install hplip-gui. It shows up as "HP Toolbox" on your activities page.

---

### Post by bob brazie on 2017-11-04
I do want that front end!! <G>
I know there are several modules in HPLIP. Will that command install all of them?
Scan, address book etc.
Thanks for the response. Bob.

---

### Post by rbmorse on 2017-11-05
I installed both, i.e., the base hplip package and then the hplip-gui package.  Seems to work fine with my CP2025DN Laserjet.

---

### Post by bob brazie on 2017-11-06
Thanks for the help. All is working because of your help. Bob.

---

### Post by kkaemail on 2018-01-16
I downloaded the latest hplip.. 3.17.11 and used instructions here
[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)
it removed old hplip.. installed new on..
and scanner is now working..

---

