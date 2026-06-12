---
title: "HH8.04 boots to text prompt....no Gnome..:("
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by lestrade on 2008-06-11
I installed v8.04 on my new Toshiba Satellite and, I think it was when I told Synaptic PM to "completely remove" Python and Glade developement stuff that I started having problems. Now it boots to a login prompt and then a command line. Everything "looks" intact in that mode....but no GUI.
StartX gets me to an X cursor and "graphical" background, but nothing else, no icons, nada. So I guess that that is XServer, without the Gnome desktop? (I am a noob, obviously).
I tried getting help from other similar posts, but they mostly assumed that you could run Synaptic PM to remove old kernels, e.g.  
I did try booting to the other 2 kernels (and their restore options) to no avail.
Any help would be appreciated.  I would rather "hang in there" and fix this than re-do the OS from scratch, as that seems the weinie way out. :)
thanks
JP

---

### Post by iaculallad on 2008-06-11
Had you tried re/installing ubuntu-desktop?

```
sudo apt-get install ubuntu-desktop
```

---

### Post by lestrade on 2008-06-11
thanks for the reply. When I try that it has a lot of "Failed to Fetch"..yadda yadda. Could not resolve 'us.archive.ubuntu.com'.  I guess that it is trying to install it from the internet?
JP

---

### Post by lestrade on 2008-06-11
hmmm.I noticed the -m switch which "tries to continue despite caca happening" and that seemed to finish.
now rebooting...
[edit] Nope. Stil "no resume image, doing normal boot"
JP

---

### Post by DBrocks on 2008-06-11
Yes you have to have it on the internet. :lolflag:

Do you know how to get it online from CLI (Command Line Interface)

---

### Post by lestrade on 2008-06-11
no, but if it is difficult to explain, I can probably find it on the net...
jp

---

### Post by DBrocks on 2008-06-11
Are you using CAT5 cables? Or, in lay-mens terms, are you using comcast? DSL? Fios? or Dialup?

---

### Post by lestrade on 2008-06-11
Cable modem.

---

### Post by DBrocks on 2008-06-11
Well it should be as easy as plugging it in, and entering:

```
sudo ifup eth0
``` If that doesn't work, post the contents of the "/etc/network/interfaces"

---

### Post by lestrade on 2008-06-11
```
sudo ifup eth0
``` If that doesn't work, post the contents of the "/etc/network/interfaces"[/QUOTE]

plugged in. Results are "Ignoring unknown inerface eth0"
/etc/network/interfaces:
_______________________________
auto lo
iface lo inet loopback
____________cut here___________
thanks
JP

---

### Post by DBrocks on 2008-06-12
Okay. Add the following 2 lines to your "/etc/network/interfaces":
```

auto eth0
iface eth0 inet dhcp
```

Now restart the network devices:
```
/etc/init.d/networking restart
```

now try again:
```
ifup eth0
```

---

### Post by lestrade on 2008-06-12
I added those two lines to interfaces (btw, that is eth(zero) not the letter "oh", right?)
The result when I try to restart is:
wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
etho: ERROR while getting interface flags: no such device.
.
.
Bind socket to interface: No such device.
Failed to bring up eth0.

thanks again,
JP

---

### Post by DBrocks on 2008-06-12
do you have an ethernet card?

---

### Post by lestrade on 2008-06-12
> **DBrocks said:**
> do you have an ethernet card?

99.9% sure that I do and that it is working -- although I only have used the wireless connection. I went to the Toshiba page here:
[http://explore.toshiba.com/laptops/satellite/P300/P305-S8820](http://explore.toshiba.com/laptops/satellite/P300/P305-S8820)
and it also claims that there is an ethernet card....and the cable I used to connect to the internet is a good one.

I would have thought that the gnome-desktop could be found on the Ubuntu cd and that I would not need to start the network from a command line to install it. no?
thanks
JP

---

### Post by lestrade on 2008-06-13
In the end I had to reinstall the os.
A local linux guru helped me to understand all of your suggestions. 
However, he said that the problem appeared more serious and that it was simpler to bite the bullet.  Done, but I learned a lot on the way.
JP

---

### Post by rwynns on 2008-07-16
Lestrade, I too am having the same problems.  Are you saying that the Toshiba P305-S8820 is not supported by Ubuntu?

You also said that you had only used the wireless, did you get the wireless to work under Ubuntu?

When you said that you reloaded the OS, did you mean Vista?

I just got this laptop this week.  Should I take it back and get something else?

Thanks,

---

