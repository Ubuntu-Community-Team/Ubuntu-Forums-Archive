---
title: "no graphical display after upgrading from 8.04 to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Mateus909 on 2008-11-02
hey yall,
just upgraded yesterday and it seems that my graphical display is completly gone...
when it boots its as if i have the terminal and nothing else. when trying to load something like firefox i get a graphical display error...im guessing during the upgrade i must have deleted the X file and now im stuck with no graphical display at all...
i still have my 7.10 CD so im not worried about starting from scratch(plus i liked 7.10 alot better than 8.04).

any and all help would be appreciated.

-Matt

---

### Post by PmDematagoda on 2008-11-02
You can try and create an xorg.conf file using:-
```
sudo X -configure
```
which creates a new xorg.conf file in /root as xorg.conf.new, once the configuration is complete, copy the new xorg.conf file over with:-
```
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```
then try starting X with:-
```
startx
```

---

### Post by Pumalite on 2008-11-02
Can you get into Recovery Mode?
If so; try 'xfix'

---

### Post by Mateus909 on 2008-11-02
i will give it a shot tonight see how it goes.
you'ill be hearing from me soon enough hehe.

---

### Post by Mateus909 on 2008-11-02
reporting back
xfix doesnt fix the problem.
and as soon as i type sudo X -configure the screen goes black and nothing happens...
any suggestions or should i just pop in the 7.10 CD and re-install?

---

### Post by yobster on 2008-11-02
is it the same as this problem??
[http://ubuntuforums.org/showthread.php?t=966315](http://ubuntuforums.org/showthread.php?t=966315)

because that's what I've got, and it's to do with the Nvidia drivers, and there's a fix for it. But I didn't really understand the solution well enough to start editing my xorg.conf

---

### Post by Mateus909 on 2008-11-02
> **yobster said:**
> is it the same as this problem??
[http://ubuntuforums.org/showthread.php?t=966315](http://ubuntuforums.org/showthread.php?t=966315)

because that's what I've got, and it's to do with the Nvidia drivers, and there's a fix for it. But I didn't really understand the solution well enough to start editing my xorg.conf

i dont believe so as mine did this after the reboot of the upgrade.
im also running an ATI graphics card and not an NVIDIA.

---

### Post by yobster on 2008-11-02
ok, well good luck finding a solution!
Exactly the same symptoms so if you have crossfire then it's because one isn't set as the primary I'd guess.

---

### Post by bensei on 2008-11-02
That sounds exactly like the problem I am currently struggling with:

[http://ubuntuforums.org/showthread.php?t=966032&highlight=bensei]("http://ubuntuforums.org/showthread.php?t=966032&highlight=bensei")

Friendly people have suggested solutions to me, but unfortunately nothing helped. Maybe some of their suggestions work for you. Please let me/us know!

---

### Post by Mateus909 on 2008-11-02
sorry to dampen your hopes but i am re-installing 7.10 as we speak.
going to try and run the upgrade later again and hope it works this time. cheers.

---

