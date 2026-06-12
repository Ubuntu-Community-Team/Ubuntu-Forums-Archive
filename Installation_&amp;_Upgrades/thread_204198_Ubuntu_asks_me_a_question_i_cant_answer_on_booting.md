---
title: "Ubuntu asks me a question i cant answer on booting"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Nordmannnick on 2006-06-26
I have sucessfully installed Ubuntu and Windows on my newly built computer. Apart from one problem, when I try to boot into Ubuntu, it goes through its phases, and it ask for my login and password. Fine, I type them in and press enter. Then, I get a command prompt which is proceeded by some sort of explanation of 'sudo' commands and 'root' comamnds, or something like that. When I type in 'man sudo_root' to acess the suggested help, it only tells me advantages and disadvantages, not really a way to get past something like nickusername:$~ (or something like that. I can find out the exact text if it is needed. Also, XP is not effected and can still be booted up. I would appretiate any help on finaly getting my computer up and running.

---

### Post by scxtt on 2006-06-26
what video card to you have and what happens if you type "startx" after logging in?

---

### Post by Nordmannnick on 2006-06-26
My video card is a Sparkle GeForce 7600 GT. When i type in <startx> (I guessed this is how to enter commands after reading the screen) after the prompt

nick@ubuntunick:~$

I get

-bash: syntax error near unexpected token 'newline'

Does that help?

---

### Post by scxtt on 2006-06-26
at the prompt, type:

```
startx
```no <> or "" ...

also, if you can, put the output of:

```
cat /etc/X11/xorg.conf | grep Driver
```in this thread ...

---

### Post by Nordmannnick on 2006-06-26
It just comes back with

-bash: startx: command not found


what next?

---

### Post by scxtt on 2006-06-26
which version did you install, the server version perhaps?  what do you get for:
[indent]whereis startx
whereis gdm[/indent]

---

### Post by Nordmannnick on 2006-06-27
they come up with 

startx:

and

gdm:

respectively. It turns out that i have inadvertantly installed the server version. Would it be easier for me to uninstall and then re install with the desktop version? if so, what are the instructions for this. Does the desktop version benifit from being more user friendly, and if so, i would think its the ebst option for me.

---

### Post by scxtt on 2006-06-27
i would download the "alternate" CD and start over ...

---

### Post by Nordmannnick on 2006-06-29
Thanks alot. Ubuntu is now up and running, and boy does it looks nice. Thank you very much for all your help, and for pointing out my quite obvious error. I am now hooked on linux :D

---

