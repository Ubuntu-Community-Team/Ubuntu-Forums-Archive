---
title: "logout freezes my system"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by baza41 on 2005-03-10
I did a reinstall of my Hoary system tonight after yesterdays kernal panic problems. Now though when I click to logout my system (Dell Dimension 2400) freezes and I have to turn the power off to break out. Not a good plan.

Anyone else seen this? Know how to fix it?

Thanx

---

### Post by muriloq on 2006-11-01
Same problem here, using both Ubuntu and Xubuntu Edgy Eft (32-bit), after normal installation and using the live CDs.

After clicking at logout or pressing Ctrl+Alt+Backspace everything (windows, panel, etc.) disappears from the screen, except the wallpaper and the mouse arrow (which still can be moved).

After that I can't go to other consoles (Ctrl+Alt+F1), nor shutdown X (Ctrl+Alt+Backspace).

---

### Post by baza41 on 2006-11-01
The logout problem I posted was when I was running Hoary, some time ago now. I've not seen this on Edgy, you might like to file a bug report and see if it's you or if others are seeing it too.

---

### Post by neoflight on 2006-11-29
i have the same problem with edgy... logout freezes mysystem. i have to use the power button to get out of that...

i dont know why this happens...

i have T42, ati 9600, etc...

any help?

---

### Post by muriloq on 2006-11-29
After a few weeks trying to solve all the problems I gave up on Edgy - I have never seen such a buggy release of Ubuntu. Now I'm back running Dapper.

---

### Post by neoflight on 2006-11-29
i solved it..... i installed ubuntu-desktop .. which i had removed earlier... 

i am running on the new ati driver... 

```
x:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

---

