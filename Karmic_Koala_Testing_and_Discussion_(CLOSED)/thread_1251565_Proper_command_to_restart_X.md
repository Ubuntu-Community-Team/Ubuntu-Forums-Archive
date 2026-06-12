---
title: "Proper command to restart X?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-08-27
OK, I get that Ctrl > Alt > Bckspc can no longer be enabled, but I'm playing with my own remix of Enlightenment + Gnome and I'd like to frequently be able to restart X without doing a full reboot.

The command 'sudo /etc/init.d/gdm restart' no longer works. What would the proper command be?

---

### Post by cyberkilla on 2009-08-27
> **kansasnoob said:**
> OK, I get that Ctrl > Alt > Bckspc can no longer be enabled, but I'm playing with my own remix of Enlightenment + Gnome and I'd like to frequently be able to restart X without doing a full reboot.

The command 'sudo /etc/init.d/gdm restart' no longer works. What would the proper command be?

Does it do the crazy blinking screen thing for you? Whenever I enter that command it seems to loop infinitely.

---

### Post by kansasnoob on 2009-08-27
Yes, a lot of text that I don't understand and just a blinking cursor.

Then I have to Ctrl > Alt > Del which causes a full reboot.

It's impractical (and rough on hardware) to reboot dozens of times in an hour or so trying different desktop configs.

---

### Post by caryb on 2009-08-27
```
sudo startx
``` Will do it.


Cary

---

### Post by almostlinux on 2009-08-27
Right Alt + Print Screen + k

---

### Post by xebian on 2009-08-27
Logout to KDM, and then Alt+e will restart .

Not sure about GDM.

---

### Post by MacUntu on 2009-08-27
> **kansasnoob said:**
> OK, I get that Ctrl > Alt > Bckspc can no longer be enabled

Just enable: System > Preferences > Keyboard > Layouts > Layout options... > Key sequence to kill the X server.

---

### Post by kansasnoob on 2009-08-27
> **caryb said:**
> ```
sudo startx
``` Will do it.


Cary

Nope. Results in "fatal server error".

---

### Post by kansasnoob on 2009-08-27
> **almostlinux said:**
> Right Alt + Print Screen + k

Yes! That works, many thanks!

Now, if they'd only get gdm straightened out:)

---

### Post by kansasnoob on 2009-08-27
> **MacUntu said:**
> Just enable: System > Preferences > Keyboard > Layouts > Layout options... > Key sequence to kill the X server.

Correct, now that I know the sequence:)

---

