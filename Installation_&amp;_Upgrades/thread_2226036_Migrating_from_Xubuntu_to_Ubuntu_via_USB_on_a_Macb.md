---
title: "Migrating from Xubuntu to Ubuntu via USB on a Macbook Pro"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by donoharm on 2014-05-24
Hello, I'm trying to migrate from Xubuntu to Ubuntu on a Macbook pro 5,2 (Mid 2009 15"). I've created the usb, I restart and push alt/option, but I get stuck on the page with the following text:
> 
GNU Grub version 1.99-21ubuntu3.9

Minimal Bash-like line editing is supported.  For the first word, tab lists possible command completions.  Anywhere else  TAB lists possible device of file completions.

grub> _


Can someone explain what I have to do next?  I've tried searching online/on these forums, but I'm probably just not seeing the proper page.  Thanks for your time, everyone. ):P

---

### Post by dannyboy79 on 2014-05-24
what do you mean trying to migrate from xubuntu to ubuntu? if you want to run straight ubuntu instead of xubuntu than simple issue the following command within a terminal
```
sudo apt-get install ubuntu-desktop
```
psyhcocats website even has instruction for removing the apps and libraries that were installed within xubuntu
there's no need for a usb stick unless i am misunderstanding something.

---

### Post by donoharm on 2014-05-24
ha ha, ok, so it's that easy then?  That's awesome. I'm definately a  newbie, so you definately weren't missing anything.  Thanks for the  help.

---

### Post by donoharm on 2014-05-24
1. Nice youtube channel!

2. After running the command, my desktop wallpaper changed, but it still looks like xubuntu.  Is there any other step I need to do?

> **dannyboy79 said:**
> what do you mean trying to migrate from xubuntu to ubuntu? if you want to run straight ubuntu instead of xubuntu than simple issue the following command within a terminal
```
sudo apt-get install ubuntu-desktop
```
psyhcocats website even has instruction for removing the apps and libraries that were installed within xubuntu
there's no need for a usb stick unless i am misunderstanding something.

---

### Post by Bucky Ball on 2014-05-24
When you boot the machine, at the log in screen you should get a 'Sessions' option. In there you'll find 'xfce4 session', or something like it, and 'Unity' or 'Ubuntu'. Choose whichever of the two pops up (NOT the xfce or Xubuntu options) and login. You should now be in Ubuntu. ;)

---

### Post by dannyboy79 on 2014-05-25
what bucky ball said. also, as I said If you want to remove some of the xubuntu junk like mousepad (text editor) and other xubuntu stuff just check out this website: [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

