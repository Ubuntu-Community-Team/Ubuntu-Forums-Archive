---
title: "startx"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by alcho on 2005-02-19
please help at the moment im on my third reinstall on ubuntu it goes through all the install stages but fails to install some packages brings me to a screen with packages installed and stuff i can press f10 there eventually i get outta this and go to like a dos prompt where i can logon with my username and password then i try to type startx and it says it cant find it.how do i install the gui from a command prompt

i used the live cd first an it installed no probs and even picked up my wireless card so i thought id give the hard drive install a go first time ever to use linux btw.

any help would be great.

---

### Post by grj on 2005-02-19
after you are logged in you can install new packages as follows:

sudo su
enter your user password when asked

apt-get update
apt-cache search <text to search for>
for example apt-cache search gnome will search for all packages with gnome in the name and description.
apt-get install <package from the above search> will install the package

If a package has dependencies they will also be installed. If you add -s to the end it will simulate the install. You can install multiple packages by simply listing them on the line with a space between package names.

Also at the command line type
man apt-get and you will get help.

---

