---
title: "Just can't log in! Problem with GDM?"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by blazemore on 2009-09-17
This happens if I use the LiveCD, or if I upgrade from Jaunty.
It loads that xsplash animation, then goes black and then just loops that same thing over and over. If I Ctrl+Alt to a different tty, it just kernel panics (No change on Numlock etc)

this is with Alpha 6 (The most recent development snapshot, less than an hour old) I've had it since alpha 4

---

### Post by tchock on 2009-09-20
Same exact problem. I only installed this because I'm desperately trying to find any damned version of linux that will work with both my ATI vid card and my X-FI sound card. It appeared that ALSA included support for X-FI in this kernel version.

Unfortunately I can't login to the damned thing. If it's not one thing it's another...

---

### Post by tchock on 2009-09-20
OK, fixed, in my case:

1. Boot to 'recovery' mode.
2. Do apt-get update, upgrade, dist-upgrade.
3. Reboot.

I'm now able to login to GNOME in regular mode.

---

### Post by ELD on 2009-09-20
Sounds like the ATi problem i am having, although it got fixed a day after alpha6 i think so i am waiting for the daily cds to start being built again so i can use one of them (none have been built since 17th?).

---

### Post by Marat89 on 2009-09-20
> **tchock said:**
> OK, fixed, in my case:

1. Boot to 'recovery' mode.
2. Do apt-get update, upgrade, dist-upgrade.
3. Reboot.

I'm now able to login to GNOME in regular mode.

With a LiveCD?

---

### Post by Punish3r on 2009-09-20
I had that problem since alpha 5.

you can do this:
> tchock  	
Re: Just can't log in! Problem with GDM?
OK, fixed, in my case:

1. Boot to 'recovery' mode.
2. Do apt-get update, upgrade, dist-upgrade.
3. Reboot.

I'm now able to login to GNOME in regular mode. 

or you can do what I did.

1- boot normally
2- in the logon screen, put your user, password and instead of logging on gnome, choose xterm. (in case you don't know were, it's in the bottom of the screen).
3- when the terminal windows appear do: (in my case this was enough) ```
sudo apt-get upgrade
```
4- exit and in the new logon choose gnome again.


My guess its some problem with the ati driver.

Hope it helps

---

