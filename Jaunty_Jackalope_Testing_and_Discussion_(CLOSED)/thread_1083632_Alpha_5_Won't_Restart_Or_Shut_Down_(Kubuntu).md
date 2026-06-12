---
title: "Alpha 5 Won't Restart Or Shut Down (Kubuntu)"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-03-01
I just did a fresh install of Jaunty Alpha 5 (64 bit) and find that neither "Restart" nor "Shut Down" function.  The only way I can shut down or restart is to manually shut down via the power button on the computer.  This is the case on two computers on which I have done clean installs.  Is anyone else experiencing this?

Cheers,
zenarcher

---

### Post by ruik on 2009-03-01
Happening here too..

---

### Post by zenarcher on 2009-03-01
Okay, happy to know it's not just me.  I've been away for a few days, so I was behind on reading about issues with Alpha 5, but hadn't discovered any comments about this with a quick search, so thought I would ask here.

Thanks again, 
zenarcher

---

### Post by Aries K on 2009-03-01
Happening here as well, has this been filed as a bug yet?

---

### Post by kde4-core-user on 2009-03-01
> **Aries K said:**
> Happening here as well, has this been filed as a bug yet?

[https://bugs.launchpad.net/ubuntu/+bug/335879](https://bugs.launchpad.net/ubuntu/+bug/335879)

---

### Post by gjoellee on 2009-03-01
To restart:
```
sudo reboot
```

to shutdown:
```
sudo shutdown -h now
```

---

### Post by perlluver on 2009-03-01
I actually just updated everything on my install, and it shutdown alright, however I assume I will find out later.

Edit:  Well I take that back, I just went to shutdown, and what do you know, there are no options to do so.  lol, oh well, going into the terminal to shutdown.  I love alphas.

---

### Post by cecilpierce on 2009-03-01
Right click on the panel and click on "Add to Panel"and add "Shut Down" or "Log Out".

---

### Post by zenarcher on 2009-03-01
Thanks for those terminal commands.  I hate it when I'm left with nothing but the brutal power button!

Cheers,
zenarcher

---

### Post by Aries K on 2009-03-01
> **zenarcher said:**
> Thanks for those terminal commands.  I hate it when I'm left with nothing but the brutal power button!

Cheers,
zenarcher

X2 on that one. Anything beats having to use the power button. I am fine using the terminal to reboot and shutdown until they release a new version of the Nvidia driver.:P

---

### Post by firstc624 on 2009-03-01
how odd..  i to am runnig Kubuntu but i cna shutdown just fine, w/o terminal.   I just go to the kicker menu or whatever it is called now and click the leave icon and then shutdown.

wonder Y some are like this and some not....

---

### Post by Aries K on 2009-03-01
> **firstc624 said:**
> how odd..  i to am runnig Kubuntu but i cna shutdown just fine, w/o terminal.   I just go to the kicker menu or whatever it is called now and click the leave icon and then shutdown.

wonder Y some are like this and some not....

You might be running the Nvidia 180.29 driver(Previous) instead of the 180.35 driver(Latest) or you might be ATi/Intel or some other manufacturer. Maybe just lucky as well. :)

---

