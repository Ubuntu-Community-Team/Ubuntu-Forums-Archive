---
title: "Resolution option are vanishing from the display option"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-23
not long ago i'v used 1280x1024 but after restart it dissappear from the display menu and now i only have these option 1360x768
1152x864 1024x768 832x624 800x600 640x480 720x400 640x400 640x350 in that order how can i fix this problem and get my 1280x1024 back?

thanks in advance.

---

### Post by byStanderone on 2010-02-24
...if you are using a monitor capable of that missing resolution, no harm in adding that into your xorg.conf file. add it on the section "screen" in line with the other resolutions listed.

---

### Post by aviramof on 2010-02-24
this is very strange but i don't have 
/etc/X11/xorg.conf and i can't find the file by searching.

i even tried to install xorg again from synaptic but no file.

---

### Post by mdurham on 2010-02-24
> **aviramof said:**
> this is very strange but i don't have 
/etc/X11/xorg.conf and i can't find the file by searching.

I think we don't use xorg.conf any more

---

### Post by aviramof on 2010-02-24
ok so what do we use now day and how can i fix this problem?

and by the way my simple 17 inch crt aoc screen is recognize as unknown how can i fix that as well?

---

### Post by byStanderone on 2010-02-24
...still in karmic, and haven't tried lucid as of yet, but i think lucid would still acknowledge xorg.conf as it does in karmic.

as/pietjanjaap


A xorg.conf hass priority above the new autodetection system.
This way you can make a xorg.conf file:
- start the computer in Recovery Mode
- choose: drop to root shell
- type: Xorg -configure
(watch uppercase X and the soace between Xorg en -configure)

Now your system will make a file: /root/xorg.conf.new
- do wat the terminal says. Do you see a gray grafical screen + mouse arrow, then it's good. Close with Ctrl-alt-backspace.

- type: reboot
- restart normaal.
- copy /root/xorg.conf.new in /etc/X11/xorg.conf
- restart the computer.

---

### Post by VMC on 2010-02-24
> **mdurham said:**
> I think we don't use xorg.conf any more

Your right, its a driver issue or its missing the capabilities of the monitor.

---

### Post by aviramof on 2010-02-24
but it was fine not long ago.

i think the problem is that the new auto detection doesn't always detect my screen properly now he does he recognize it as AOC Intl 16 but next time i restart he might not recognize it again in time the detect mecanisem would be better i hope at the moment i still 
have a problem with my lcd tv showing the computer in pink and in solorize colors even thoughe he does recognize the tv as toshiba america info system inc 95.

i'm wandering if the america doesn't mean that he recognize it as ntsc and not as pal as it should be.

---

