---
title: "Installing an app with no cd drive ?"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by PleaseHelp on 2007-11-22
Hi i have just installed Ubuntu via a usb cd drive
Im using a rack server with no cd drive 

Im trying to install postfix but it keeps asking for me to put the cd into the drive
I have my usb cd drive plugged in 
and still nothing

any ideas on what i could do

---

### Post by scrooge_74 on 2007-11-22
go to /etc/apt/sources.list

and comment out, the cdrom and usb, and enable the repositories if they are commented out

then do a sudo apt-get update

then sudo apt-get install package_name

---

