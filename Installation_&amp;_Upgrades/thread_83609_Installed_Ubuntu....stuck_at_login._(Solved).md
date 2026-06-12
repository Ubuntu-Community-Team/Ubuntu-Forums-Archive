---
title: "Installed Ubuntu....stuck at login. (Solved)"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by bulletbutter on 2005-10-29
So after 3 days of frustration of not being able to get my networking going with gentoo I decide to try this distro of linux.  Downloaded, burned and installed Ubuntu Breezy Badger 5.10!  Every thing worked out fine I think.  After everything was said and done I was staring at 'myname'@ubuntu:~$.  So, from that confusion I started looking for some kind of documentation on what I was supposed to do next and read that after I log in it's supposed to install and load GNOME?  Well, this didn't happen and I have no idea what to do now.  For kicks I decided to ping www.yahoo.com........it's still spitting out stuff on my screen and I can't get it to stop.

Anyways, what's the deal?  Do I need to manually install a desktop environment?

---

### Post by heimo on 2005-10-29
Default install should install Gnome. Maybe something didn't finish as it should have - you could try to (after pressing ctrl+C to stop pinging...) run:
```

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install ubuntu-desktop

``` 
Do you get any errors?

---

### Post by aysiu on 2005-10-29
You can also try typing ```
startx
``` or typing control-alt-F7. I'm not sure if that'll work, though.

---

### Post by bulletbutter on 2005-10-29
Uhm....I can't input commands because the only thing I can do is login, anything I type will ask me for a password.  Sorry, I am really new at this. :confused:

Lol, nvm.  I am trying out what heimo suggested now.

---

### Post by heimo on 2005-10-29
[quote=bulletbutter]Uhm....I can't input commands because the only thing I can do is login, anything I type will ask me for a password.  Sorry, I am really new at this. :confused:[/quote]

Hmm... did you try your password? ;)

---

### Post by aysiu on 2005-10-29
[QUOTE=bulletbutter]Uhm....I can't input commands because the only thing I can do is login, anything I type will ask me for a password.  Sorry, I am really new at this. :confused:[/QUOTE] My suggestions would be after you log in, actually... except for Control-Alt-F7--you can try that even before logging in.

---

### Post by bulletbutter on 2005-10-29
Ok that worked, sorta.  After it was finished it prompted me with 'myname'@ubuntu:~$ again so I just put in startx.  I heard a short tune and now I am at a black screen :(

---

### Post by aysiu on 2005-10-29
[QUOTE=bulletbutter]Ok that worked, sorta.  After it was finished it prompted me with 'myname'@ubuntu:~$ again so I just put in startx.  I heard a short tune and now I am at a black screen :([/QUOTE] Totally black or the black screen with the white login prompt?

---

### Post by bulletbutter on 2005-10-29
It's just black, no prompt or blinking cursor...it's so dark :p

---

### Post by aysiu on 2005-10-29
[QUOTE=bulletbutter]It's just black, no prompt or blinking cursor...it's so dark :p[/QUOTE] Believe it or not, that's a good sign. If it's totally black and you hear music, it means you're able to get to the GUI--you're just not able to see the GUI.

What you need to do is get back to that login prompt. Try either Control-Alt-Backspace or Control-Alt-F1. If that works, log in with your username and password and then type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bulletbutter on 2005-10-29
Ok now it gives me a list of video card drivers to choose from.  I use 2x GIGABYTE GV-NX68T256DH Geforce 6800GT 256MB 256-bit GDDR3 PCI Express x16 Video Cards.  On my windows partition I have it set up for sli.  With the list they give me I am unsure which I should choose...chipset is from nvidia

EDIT: I am guessing that I should use nv.  Would I be correct in assuming that nv stands for nvidia?

---

### Post by tseliot on 2005-10-29
[QUOTE=bulletbutter]... I am unsure which I should choose...chipset is from nvidia

EDIT: I am guessing that I should use nv.  Would I be correct in assuming that nv stands for nvidia?[/QUOTE]
Yes you have to choose nv (which is the open source driver)

---

### Post by bulletbutter on 2005-10-29
hmmm...got the same problem.  Guess I just have to keep messing around with the xserver configuration.  :(

---

### Post by bulletbutter on 2005-10-29
Went through the options several times, setup my gfx card, named it, redid the keyboard,set up the monitor and named that as well.  Ran startX and got the same black screen with the cool music.  What is the problem?  Is it my gfx settings or my monitor settings?  I looked at lspci to make sure my gfx was labeled in the correct pci place and even changed it to my second gfx pci.  When I changed it to my second one it gave me a fatal error.  So I just put it back to the first one.  

Should I be looking at the gfx or the monitor to blame for not being able to get this to work? :(

---

### Post by tseliot on 2005-10-29
[QUOTE=bulletbutter]hmmm...got the same problem.  Guess I just have to keep messing around with the xserver configuration.  :([/QUOTE]

can you post (copy and paste here) your /etc/X11/xorg.conf and your /var/log/Xorg.0.log ?

---

### Post by bulletbutter on 2005-10-29
Anything in particular you need to see?  The files are on another computer and thats a lot of stuff to type :(

EDIT: Got it!  I looked in the /var/log/Xorg.0.log and it said my gfx card was located at PCI :05:0:0 instead of the default PCI :4:0:0 I just changed it and I can now see the desktop.

---

