---
title: "cannot log in ubuntu 16.04"
date: 2017-03-30
forum: Installation &amp; Upgrades
---

### Post by HappyAsHellas on 2017-03-30
Zoostorm laptop
8 gigs memory
sandybridge graphics
ubuntu 16.04

I ran a software update and after re booting cannot log in. I enter the password and the log in screen re appears asking for the password. I have tried online and youtube and this is not a new problem, but one which no one seems to have an answer for. I have tried the following from terminal:

lightdm
rm ~/.Xauthority
mv .Xauthority .Xauthority.bak
sudo chown username:username .Xauthority
sudo apt-get purge lightdm
update
upgrade
passwd (change)

All to no avail. I can log in as a guest which isn't much use as saving work is tedious. I just want my computer to work in a semi normal fashion. Is this really too much to ask for in 2017? Please, can someone help?

---

