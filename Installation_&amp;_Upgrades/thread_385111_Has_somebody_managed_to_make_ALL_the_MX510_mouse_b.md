---
title: "Has somebody managed to make ALL the MX510 mouse buttons work?"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by astrolabio on 2007-03-15
I managed to make the Thumb buttons work.

But the button above the wheel generate two events and works at the same time as "scroll up" and "thunmb down", which means that in firefox it make me go back of one page, instead to just scroll.

The application button (the one on top with two square on it) works as a simple click, whilst i'd  like to make it work as it pleases me (pressing F12 for instance).

That SUCKS!

Is there actually somebody who managed to make ALL the button works as he wish?

btw this is my mouse section in the xorg.conf file

Section "InputDevice"
	Identifier  "Configured Mouse"
  	Driver      "mouse"        
   	Option      "SendCoreEvents"
         Option      "Device" "/dev/input/mice"
         Option      "Protocol" "ExplorerPS/2"
         Option      "Emulate3Buttons" "false"
         Option      "Buttons" "7"
         Option      "ZAxisMapping" "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by astrolabio on 2007-03-17
bump

---

### Post by alextj on 2007-03-25
I have the same mouse and I would also like to know.

---

### Post by MindFork on 2007-06-01
Did you ever get this solved?  I'm glad to find this post, because at least I have working thumb buttons from your config.  

With the base config, the scroll up and scroll down buttons worked normally, but now I get the same thing with the scroll up button where it goes back a page.  I can live with that, because I almost never use that button anyway, but it would be nice to have it fully functional.

---

### Post by kaaskop on 2007-06-08
I found this a while back but never tried it.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Mouse%20Buttons](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Mouse%20Buttons)

---

### Post by KhaaL on 2007-06-09
this thread worked for me: [http://ubuntuforums.org/showthread.php?t=219894&highlight=mx510](http://ubuntuforums.org/showthread.php?t=219894&highlight=mx510)

---

