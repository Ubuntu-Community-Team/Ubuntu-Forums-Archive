---
title: "Upgrade to 10.4 broke my dual screen settings (ATI card)"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by puccio on 2010-05-17
I upgraded from Ubuntu 9.10 to 10.4 and _the dual screen does not work anymore_.

I have a laptop with an ATI Radeon Mobility X1400 with xorg drivers (no fglrx).

I have to use this laptop for work, and I'm now losing my working time having discovered the dual screen does not work anymore, and I'm considering re-installing Ubuntu 9.10.

Deleting the xorg.conf file and hoping Xorg figures it out how to fix it does not resolve my problems. Playing around with the graphical apps in Gnome allowing to set up the monitor does not change the situation either. The external monitor is detected, but I only see a black image on it. The screen aerea is "dual" however: with the mouse pointer I can navigate "to the left", on the black aerea.

Can someone help me? Thanks in advance!

---

### Post by MichealH on 2010-05-17
You will have to edit your xorg.conf to match your 9.10 one.

---

### Post by MichealH on 2010-05-17
Sorry for the double post but Goto Terminal and type
```
sudo service gdm stop
```
Now switch to one of the tty's by using CTRL-ALT-F1,F2,F3,F4,F5 and F6 and then
```
Enter your username
```
```
Enter your password
```
Type:
```
sudo bash
```
then
```
Xorg-configure
```
then you are done! Go back to you Graphical Interface by typing:
```
service gdm start
```

---

### Post by puccio on 2010-05-17
> **MichealH said:**
> You will have to edit your xorg.conf to match your 9.10 one.

Hi I have overriden the new xorg.conf file with the one backupped by Ubuntu during the upgrade. It does not work either..

---

### Post by puccio on 2010-05-17
> **MichealH said:**
> Sorry for the double post but Goto Terminal and type
```
sudo service gdm stop
```
Now switch to one of the tty's by using CTRL-ALT-F1,F2,F3,F4,F5 and F6 and then
```
Enter your username
```
```
Enter your password
```
Type:
```
sudo bash
```
then
```
Xorg-configure
```
then you are done! Go back to you Graphical Interface by typing:
```
service gdm start
```

Hi,

I have no "Xorg-configure" command. Am I supposed to install a package ?

---

### Post by MichealH on 2010-05-17
Did you switch to TTY's or turn off GDM?

---

### Post by puccio on 2010-05-17
> **MichealH said:**
> Did you switch to TTY's or turn off GDM?

Yes, it does not change the result unfortunately :(

---

### Post by puccio on 2010-05-17
What is strange is that even in "cloned" monitors mode I don't see anything on the external monitor (I remember a few distros before I struggled to have separate screen aereas, but the "cloned" monitor was always the one working..). Any clue?

---

### Post by puccio on 2010-05-17
Now the monitor prints on it "Switch input signal to 1600x1200 at 60hz" which I did..

---

### Post by MichealH on 2010-05-17
That is steange. Have you tried it in the ATI settings?

(I Will be away for a while.)

---

### Post by puccio on 2010-05-17
> **MichealH said:**
> That is steange. Have you tried it in the ATI settings?

Which application / command line tool is it? On the command line typing "ati" it auto-completes only for "atitvout".

Is it worth the try instead if I try to use the fglrx driver instead of the xorg ones?

Hope to get news from you soon!

---

### Post by puccio on 2010-05-17
Ehi!! I installed the driver radeon-hd, I exited X, from a terminal I removed xorg.conf then run Xorg -configure... and now in the monitor preferences the settings actually take place!! :-)

Thanks for the support!!

---

