---
title: "console (tty): keyboard"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by forlau on 2006-06-04
Hi,

on the console tty (not under X) i always get error messages while typing with the normal letters a-z:

"atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known..."

Im not using special multimedia keys or something, just the normal ones.

There is no problem with the keyboard if im running KDE, everything works fine there.

I have the following machine: ECS K7S5A, XP2000+, 512MB Ram, Geforce 4, DVB-T Card Ads-tech and a wireles desktop keyboard.

With Kubuntu 5.10 the keyboard had no problem in the console (tty).
Need help!

---

### Post by forlau on 2006-06-05
After installing Kubuntu again i now installed Ubuntu, but i still have the problem.

Is there anybody using TTY without problems? Can´t believe im the only one, espacially with my standard hardware!

---

### Post by llamakc on 2006-06-05
[http://www.ubuntuforums.org/showthread.php?t=12159](http://www.ubuntuforums.org/showthread.php?t=12159) may be of some help.

---

### Post by forlau on 2006-06-06
Its not that every time a key is pressed i get an error mesage. After pressing 15 keys i get an error message.

Hints:
- Its not every time the same key
- its only under tty1-6 (which means pressing  ALT+STRG+F1 to F6) 
- no problem with this in an Gnome/KDE console
- why do i get this message on the screen? It should be in "dmesg"

I just can not use UBUNTU anymore! :twisted:

---

### Post by llamakc on 2006-06-06
So you tried that recommended fix and it did not work at all for you? Weird, because I had the exact same symptoms you describe and it worked for me just fine.

---

### Post by forlau on 2006-06-06
Thanks for your help, im **not** trying to configure some multimedia keys. The keys im talking about are the normal ones e.g. a to z or 1 to 0

but the link shows how to use the multimedia keys. The keys i want to use are already defined.

_Example:_
Pressing the key "a" 15 times brings 14 times an "a" and then an error, that this key is undefined.

Strange, isn´t it?

---

### Post by forlau on 2006-06-06
Finally i could solve my problem by changing the keyboard!

Before: M$ Wireless Desktop Elite

Now: my old Cherry Cybo@rd

So be aware of the M$ Wireless Keyboard with Kernel 2.6.15.

Strange, the M$ Keyboard has worked before with Kernel 2.6.10 perfectly. Something must have changed in Keyboard support!

---

### Post by llamakc on 2006-06-06
I understood you perfectly and I had the same problems and symptoms you did. By assigning that one key that was erroring I fixed my problem without switching keyboards. Glad to hear you found a solution for the time being.

---

### Post by forlau on 2006-06-07
It is not only one key, that made this error message. Every key can produce this message, from a to z. And this you can not fix by defining the keymap for one single key. 

Its not, that the keymap is not defined. Every key is working, but not always. Its a matter of how many inputs are done. And i counted round about 15 times you can press any key without error messages, but the 16. key is making an error.

There is a real bug with this new release of Dapper. Maybe its this hotkey definition, but i uninstalled it already, so for me it can not be.

I always thought that it doesnt matter what kind of keyboard im using, as long as im not using the Multimedia keys. Maybe every manufacturer is making the keycode different.

---

### Post by llamakc on 2006-06-07
Once more, I understand the problem. All I did was reply that THAT link fixed MY problem. 

Perhaps you could try with a hand-rolled kernel or the -22-* series?

---

### Post by forlau on 2006-06-09
@llamakc
You are right. I finally solved my problem with your help:

1.)i created a file: /etc/init.d/microsoftkbd.sh

```
sudo touch microsoftkbd.sh
```

2.) Wrote this lines inside:
```
setkeycodes e059 254
setkeycodes e001 255
```

3.) updated the runlevel:

```
sudo update-rc.d microsoftkbd.sh defaults
```


I found out with the newsgroups, that this bug (also in Debian) is more than 2 years old!

---

