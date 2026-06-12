---
title: "Can't display on monitor after full install"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by smeagoly1 on 2007-01-19
Hi new to linux and ubuntu.

Just installed to a spare drive Ubuntu 6.10, no other OS on it, from dowloaded iso and blown to Live CD.

CD is perfect, boots up from cd, and isnatlled from CD, once i remembered to press F4 and chage the Live CD from VGA to 1040 mode, used to get unusuable graphics prior to that attempt.

Boot screen comes up fab, rolling bar nice ubuntu logo, then once the full ubuntu is loaded i get the "Can't display in this mode" error message displayed crossing my monitor.
I know there are issues with Nvidia cards, i'm using a 6800 at the moment.
Read the various articles about NVida drives etc... 

bare in mind i have never used any form of linux in the past, 6.10 is running what looks like a windows style user interface, how do i change the boot reselution or input the code i have read in various articles on here?

I am probably missing some very in my face easy option here lol wood for the trees sydrome i expect.
Main Specs:-

AMD 64 3000
Ubuntu 6.10
Nvidia 6800
1 gig 
60 Gig HD fresh install.

Regards 
Smee

---

### Post by renzokuken on 2007-01-19
at a guess it sounds like its trying to display a resolution your gfx card or monitor cant handle.

if you get to a terminal (Ctrl+Alt+F1) then type 

```
sudo nano /etc/X11/xorg.conf
```

and scroll down and find the listed resolutions, and list em in this thread

EDIT: if you can get it working in normal mode then try installing the nvidia drivers for a better performance. there are plenty of helpful and easy to follow nvidia driver guides in the forums

---

### Post by smeagoly1 on 2007-01-19
Cheers for the quick reply. Much appreciated, will try that when i get home from work lol.

---

### Post by renzokuken on 2007-01-19
thinking about it, on installing the nvidia drivers (search the forums for "envy script") it should write the xorg.conf for you sorting out the resolutions automatically.

so may be an idea to just install them anyway

---

