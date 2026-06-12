---
title: "GDM Crashes"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by macstevejb on 2010-03-31
After booting and arriving at the gdm login screen, when I click on my user name, the mouse freezes, I cannot input my password and after a few seconds the gdm screen closes then reopens and the loop keeps repeating.

This behaviour only started happening after this morning's updates.

I am using nvidia drivers (v96), have been using Lucid since alpha 3 and this has only just started happening.

Any ideas how to fix please?

regards.

---

### Post by dcordeiro on 2010-03-31
I'm having the same problem here. :(

Not only the gdm freezes after clicking in my name, but the entire gnome environment became much more unstable after the last upgrade.

I want to send a bug report, but launchpad is under maintenance and I'm not sure against which package I should fire the bug report.

---

### Post by scalawag_ on 2010-03-31
Same here [http://ubuntuforums.org/showthread.php?t=1436466](http://ubuntuforums.org/showthread.php?t=1436466)
Do the following as a workaround:
ctrl+alt+F2
Login with your username and password
sudo service gdm stop
insert your password again
startx

---

### Post by Down8ve on 2010-03-31
Same here, this morning's updates remove key elements in Gnome due to unmet dependencies. Obviously things are being worked on, which is the reason why it is not recommended to use Lucid as a production system.

While I wait for the various dependencies to arrive, I ran "sudo apt-get install lxde" and am using another desktop environment.

-Scott

---

### Post by jhansonxi on 2010-04-05
See **[bug #553200]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553200")** and **[553508]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/553508")** (probably a duplicate).  Subscribe and click the "Does this bug affect you?" link at the top of the pages and change status accordingly.

---

### Post by spotdog14 on 2010-04-08
> **scalawag_ said:**
> Same here [http://ubuntuforums.org/showthread.php?t=1436466](http://ubuntuforums.org/showthread.php?t=1436466)
Do the following as a workaround:
ctrl+alt+F2
Login with your username and password
sudo service gdm stop
insert your password again
startx
Whenever I try this it just boots to a black screen. Sometimes I get a cursor but go desktop. 

Any ideas?

---

### Post by jhansonxi on 2010-04-08
> **spotdog14 said:**
> Whenever I try this it just boots to a black screen. Sometimes I get a cursor but go desktop.Try booting with the nomodeset option.
**[Ubuntu 9.10 (Karmic Koala) release notes - Xv support]("http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS")** (also helps with other chipsets)
**[Grub2 documentation]("https://help.ubuntu.com/community/Grub2")**

---

