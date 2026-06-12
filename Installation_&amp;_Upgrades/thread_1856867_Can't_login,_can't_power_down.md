---
title: "Can't login, can't power down"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Cushie on 2011-10-09
I have just upgraded from a very stable 11.04 to the latest daily version of 11.10 (Beta2+) on my Acer Aspire One netbook, but with no great success getting many hangups and errors so I reinstalled the upgrade option again from live usb, keeping my original separate 'home' directory and username. I chose auto login during the install which did not succeed but get to a login screen yet _**I cannot login or shut down.**_
 
I reset the 'passwd' just in case, then did another reinstall to make sure I was using the correct password (same one I have always used) but still cannot login or shut down.
Is there a simple fix to reconfigure or reinstall something to get over this problem. suggestions would be appreciated.

PS I can get to # prompt terminal via recovery option and I can login with 'username' and password, this allows me to list the home directory and all the file are intact. As a point of interest what command would run the desktop manager gdm? startx? or something new to 11.10?

---

### Post by Cushie on 2011-10-14
Problem solved by knulp79 on Linuxquestions .org
[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/#post4496128]("http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/#post4496128")

Quote: 
>>There was a .Xauthority file in my home folder owned by root and that prevented me from logging in.
Logging in a text console (Alt+Ctrl+F1 at the login screen) and issuing:
sudo rm ~/.Xauthority
solved the issue. <<

---

