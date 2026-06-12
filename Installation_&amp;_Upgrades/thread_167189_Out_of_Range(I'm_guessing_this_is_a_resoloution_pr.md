---
title: "Out of Range(I'm guessing this is a resoloution problem)"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by likewhiteonrice on 2006-04-27
But I don't know exactly what to do...
When I choose all of the res options I know I should have choosen all of them but I didn't...
and now when, i'm guessing it's about to go to the login screen becuase it loads all of the moduels, it says Out Of Range.
I really hope someone can help me with this...
thanks
LWOR.

Edit: if you want to contact me on msn, it's: [email]likewhiteonrice777@sbcglobal.net[/email]

---

### Post by Kapre on 2006-04-27
[QUOTE=likewhiteonrice]But I don't know exactly what to do...
When I choose all of the res options I know I should have choosen all of them but I didn't...
and now when, i'm guessing it's about to go to the login screen becuase it loads all of the moduels, it says Out Of Range.
I really hope someone can help me with this...
thanks
LWOR.

Edit: if you want to contact me on msn, it's: [email]likewhiteonrice777@sbcglobal.net[/email][/QUOTE]

likewhiteonrice - check your video cable as out of range also happens when no signal is being received by the pc. If is not the cable, try ctrl-alt-f1 to log-in the text mode. Then try "dpkg-reconfigure xserver-xorg" and try to configure your video mode.

K

---

### Post by likewhiteonrice on 2006-04-27
I know this is probably a stupid question but here I go:
It says ''reconfigure must be run as root.''
lol
How to I run it as root?
sorry for stupidity
LWOR.

---

### Post by nanotube on 2006-04-27
[QUOTE=likewhiteonrice]I know this is probably a stupid question but here I go:
It says ''reconfigure must be run as root.''
lol
How to I run it as root?
sorry for stupidity
LWOR.[/QUOTE]
to run stuff as root use "sudo". as in, 
```
sudo dpkg-reconfigure xserver-xorg
```
if you want to know more about running stuff as root in general (and you do, trust me), then visit [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) :)

---

### Post by likewhiteonrice on 2006-04-27
Thanks so much you guys.
I'll probably be back with more dumb questions but not before reading ALOT.
](*,) ](*,)

---

### Post by likewhiteonrice on 2006-04-28
It worked, thanks again...
I looooved this!!
Linux is like a thousand 1000 virtual orgasams on my screen: :-D :-D

---

### Post by nanotube on 2006-04-28
[QUOTE=likewhiteonrice]It worked, thanks again...
I looooved this!!
Linux is like a thousand 1000 virtual orgasams on my screen: :-D :-D[/QUOTE]
hehe
in your spare time, make sure to read around in the wiki documentation [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
you will find it very helpful. ;)

---

