---
title: "Gnome wont start in Intepid Ibex, errors here"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by respider on 2008-10-03
Hi there, already tried alpha 5, alpha 6 and the beta

It boots ok, but when going to enter gnome, it stays in and clear-orange screen and doenst leave it...

I go to another tty, killed gdm and tried startx and got screen blinking a lot with a lot of messages...

I shot the errors, hope it helps:

clear orange screen at boot
[http://img133.imageshack.us/img133/842/snc00014vi9.jpg](http://img133.imageshack.us/img133/842/snc00014vi9.jpg)

blinking errors
[http://img359.imageshack.us/img359/5127/snc00015ae7.jpg](http://img359.imageshack.us/img359/5127/snc00015ae7.jpg)

errors when stop blinking
[http://img509.imageshack.us/img509/2328/snc00018xi8.jpg](http://img509.imageshack.us/img509/2328/snc00018xi8.jpg)

My machine is an asus f8, vga card is ati radeon hd3650 mobility

sorry for the bad english

---

### Post by Sef on 2008-10-03
1) How much ram do you have?

2) Instead of booting or installing, go down to 'Check Disk for Errors' and make sure all is ok.

---

### Post by respider on 2008-10-03
> **Sef said:**
> 1) How much ram do you have?

2) Instead of booting or installing, go down to 'Check Disk for Errors' and make sure all is ok.

I have 4gb of ram

The problem is not the disk  :(

---

### Post by spectre_hfx on 2008-10-03
.

---

### Post by napels7 on 2008-10-03
same here, it stays in clear-orange screen

---

### Post by jerrylamos on 2008-10-04
Thinkpad R31 gnome won't start either, Orange (brown?) screen only.  On Beta or Alpha 6.

Clue: Xubuntu & Kubuntu work.  It's just Ubuntu that's dead.

Rather involved way to get something running on Ubuntu:
It's a dual boot so I can play with one image and still have something that works.
Install which works, doesn't use Gnome.
Boot in recovery mode which works doesn't use Gnome
Root prompt dhcp to get the network running.
Fix broken packages which loads up Synaptic with lots of stuff.
Root prompt apt-get install xfce4
Root prompt startxfce4 which works, doesn't use Gnome. 

That's how I'm running.  See Launchpad bug 277344 for various error logs.

Jerry

---

### Post by StevieS on 2008-10-04
I've had a similar problem and it seems to be related to Network Manager.  To resolve it I booted into the recovery mode (selected when you first switch on your machine) and selected the root prompt.  At that point I removed Network Manager

```
apt-get remove network-manager
```

which will remove network-manager, network-manager-gnome and possibly network-manager-kde.  

**A quick word of warning here,** I don't know whether removing this will disable your network access, so you should ensure that you have the means of reinstalling this before you continue, ie a live CD of a known working release of Ubuntu.  If you do lose network access I have posted instructions to get it back which work for me below.

At this point I typed "exit" to get back to the screen which will allow you to resume the normal boot process, now all works well.

As mentioned above, once you get to the desktop you may not have network access, open a terminal and type

```
ifconfig
```

and look for the name of your network interface which will be something like eth0 or wlan0.

To enable the network type

```
sudo ifup <network interface>
```

replacing <network interface> with the name of your interface that you found in the previous step.

---

### Post by jerrylamos on 2008-10-04
Tried removing network manager.  Gnome still hangs up on starting, same problems, black screen or orange screen and dead on IBM Thinkpad R31.

install network manager seemed to restore me where I was before, which is to say xfce4 works, gnome doesn't.

Thanks anyway, Jerry

---

### Post by respider on 2008-10-05
no possibles solutions then? =(

where do I report this bug "officially"?

---

### Post by respider on 2008-10-24
problem continues in 8.10 release candidate

8.04 starts without problem

---

### Post by pecanov on 2008-10-30
I just installed Ubuntu 8.10 final and the problem is present on HP Pavilion dv6700. 

Too bad since it worked fine on 8.04.

---

