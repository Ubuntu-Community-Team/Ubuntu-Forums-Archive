---
title: "Making my 12.04 distrubution like new"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by jskallz on 2013-03-18
[COLOR=#333333][FONT=Ubuntu Beta]I recently did a project involving a lot of messy installs. After manually undoing what evil I have done I realize I have broken a lot of dependencies and instead of manually slaving over each one, I'd like to 'go back in time', before I messed up my installation. How can I do this?[/FONT][/COLOR]

---

### Post by aarons6 on 2013-03-18
first you have to be more specific on what DE you are using.
gnome
gnome shell
unity
kde
xfce
etc....
first id try this
sudo apt-get -f install

if that doesnt work 
then you prob just can purge it and reinstall it.
sudo apt-get purge kde-desktop
sudo apt-get install kde-desktop

---

### Post by ibjsb4 on 2013-03-19
> [COLOR=#333333][FONT=Ubuntu Beta]I'd like to 'go back in time', before I messed up my installation. How can I do this?[/FONT][/COLOR]

You have to build a time machine :P

Some terminal commands that may help:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Another thought:  If you like to do a lot of playing around and don't want to bork your system, consider VirtualBox.  There is a learning curve, but in the end you will have that "time machine" :)

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

