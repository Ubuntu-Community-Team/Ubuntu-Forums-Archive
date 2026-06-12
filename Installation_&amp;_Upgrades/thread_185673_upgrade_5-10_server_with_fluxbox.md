---
title: "upgrade 5-10 server with fluxbox"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by lex1 on 2006-06-01
Hi Folks

I have 5.10 server with a fluxbox desktop and i would like to upgrade to 6.06 with fluxbox what is the command
line please.?


Lex1:)

---

### Post by Sutekh on 2006-06-02
First copy and edit your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` When the nano text editor opens, you need to change all instances of **breezy** with** dapper**.  Make sure you use the keyboard to sroll to the end of the file and change them all.  When you are finished editing the file, use Ctrl +O to save the file and Ctrl + X to exit.

Finally use these commands to update the sources.list and perform the dist-upgrade to Dapper
```
sudo apt-get update
sudo apt-get dist-upgrade
``` You should be set then.

---

