---
title: "CLI Commands"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by gb1986 on 2010-05-14
What are examples of CLI Commands? What are they used for?

---

### Post by lisati on 2010-05-14
"CLI" = "Command line interface", and is an alternative to "GUI" (Graphical User Interface). Back in the days of MS-DOS, it was your only option for telling your computer what you wanted it to do.

---

### Post by jerenept on 2010-05-14
some basic commands in linux -man <command>
shows advanced manuals on usage of programs
                  ls 
lists files and folders in active directory
                  cd <directory> 
changes active directory
                  cp <sourcefile> <newfile>
copies file from sourcefile to newfile
                  sudo <command>
gives a command temporary administrator privileges VERY DANGEROUS USE WITH CARE
                  apt-get 
installs, removes, upgrades application packages on your system (use with sudo)
                  gksu <command>
graphical version of sudo
 These are as many as i know. if they are unclear, please enter the command followed by '--help' (without quotes)

---

### Post by jerenept on 2010-05-14
[http://ubuntu-manual.org/]("http://ubuntu-manual.org/")
Try that. It's very helpful to many users

---

### Post by jerenept on 2010-05-14
Double Post... sorry

---

### Post by tgalati4 on 2010-05-14
Try this (open a terminal first) :

sudo apt-get install htop
htop

apt-cache search process monitor

apropos monitor

which which
apropos apropos
locate locate

which htop
apropos htop
locate htop

---

