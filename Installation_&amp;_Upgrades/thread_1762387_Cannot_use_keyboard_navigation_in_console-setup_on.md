---
title: "Cannot use keyboard navigation in console-setup on Thinkpad Edge 15"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by claretnbluester on 2011-05-19
After installing Ubuntu 10.10 Server 64bit in VMPlayer on my laptop (Thinkpad Edge 15), I was unable to use the keyboard correctly - "|" appeared as ">" etc.
I checked the language = en_US.
I live in the uk and so want to change this to en_GB.
The locales package contains both so I thought I would be OK.
I ran the following
 
```
dpkg-reconfigure console-setup 
```
 
However, I was not able to use keyboard navigation (arrow keys) to select my keyboard or change the language from US to UK.
 
Does anyone know how I can change settings to enable me to navigate using arrow keys? Is there another way to navigate through the options?

---

### Post by lechien73 on 2011-05-19
Hello & welcome to the forums :)

You could try editing the /etc/default/keyboard file directly. You may need to change the XKBMODEL value as well, to match the Thinkpad keyboard.

---

### Post by claretnbluester on 2011-05-19
Thanks Matt

There was no /etc/default/keyboard file.  But there was a /etc/default/console-setup.
Editing this I changed the language setup.
XKBMODEL="evdev"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS="lv3:ralt_switch"

This alone didn't do anything.... so, I tried to run the init.d scripts:
sudo /etc/init.d/console-setup restart

But this didn't do it either!

Finally I reverted to running the dpkg-reconfigure command, and hey presto.... my change was there and more importantly even though I didn't make any further changes, when I exited the program it completed the necessary system changes and now i get "|" instead of ">" from my keyboard.  The arrow navigation keys still don't work, but I'm happy enough now and can get on with what I wanted to do!

---

### Post by kalle_mod on 2011-06-01
Any idea on how to activate the Alt Gr button and arrows so that it is made possible to navigate in eg. vim (I can only use the down arrow) and when I try using Alt Gr + 2 (@ in danish qwerty keyboards) or something like that it goes all wrong!

---

### Post by claretnbluester on 2011-06-04
I wish I could help you with that one, but I have no experience of the Alt Gr problem.

I wonder if you can find an answer in any of the following links?

[http://ubuntuforums.org/showthread.php?t=1489406](http://ubuntuforums.org/showthread.php?t=1489406)

[http://ubuntuforums.org/showthread.php?t=984948](http://ubuntuforums.org/showthread.php?t=984948)

Simon

---

### Post by kalle_mod on 2011-06-06
Nope none of them helped me out. It doesn't matter anyway since I was just running ubuntu 10.04 server in a virtual machine that is now deleted :)

---

