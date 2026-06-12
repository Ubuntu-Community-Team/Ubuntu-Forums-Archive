---
title: "installationg trouble"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by keeanrunt on 2008-07-17
Hello, im not a relatively new user but im running ubuntu 8.04 Hardy Heron and when i tried to install limewire it went through the process but stopped half way through so i gried to exit the manager and had to log out.  the problem is when i try to install anything else it dosn't let me it give me the error to close updater or apt-get im not sure why.  but anyway is there a simple way to just stop that install and be able to erase it ever happening.  thanks :confused:

---

### Post by Pumalite on 2008-07-17
sudo apt-get update
sudo apt-get dist-upgrade
Post the output.

---

### Post by keeanrunt on 2008-07-17
ok so i pasted both lines and it still gives me the msg E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. im not sure wat that means and im still not sure how to get rid of it. and do u by any chance know the shortcut for run it worked once but not anymore.  hope anyone can help

---

### Post by Pumalite on 2008-07-17
Go to Terminal and run:
sudo dpkg --configure -a
Post the output.

---

