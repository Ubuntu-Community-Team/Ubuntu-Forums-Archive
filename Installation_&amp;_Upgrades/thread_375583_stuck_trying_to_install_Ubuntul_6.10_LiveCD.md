---
title: "stuck trying to install Ubuntul 6.10 LiveCD"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by elitelinuxnoob on 2007-03-03
I have tried so may different things but keep getting corrupted line after the loading bar screen. I think its my nvidia 7800GT or maybe because im on sata2 raid0. whateverit is i just want to try Ubuntu out on my damn computer and I have no others to test the burned CDs on. I redownloaded the 6.10 ISO many times but nothing them I tried the alternate and nothing. On the alternate though it said to Insert the disc with the OS but it was in so wth? The only other thing maybe is that im burning the images at 8x. I can't go any lower in Infra Recorder. Are all buring programs the same with burning speeds or is my burner messed up? Should I try another burning program and which one?

Also I tried OpenSuse 10.2 DVD and I get the same exact issue with the freezing after the loading. I get a corrupt part of what looks like a windows and my pc just freezes.

Please, what the hell is wrong and what should I do. If I cant fix this im sticking with just Windows.

---

### Post by didu on 2007-03-04
that's probably because the ubuntu installation cd tried to use a non-vesa driver for your X. I had the same problem with my desktop which had an ati card, and ubuntu guessed "ati" as the driver in /etc/X11/xorg.conf, I just switched to a virtual terminal (ctrl-alt-f1), and changed the driver from ati to vesa, I then deleted the pid file for gdm (it's in /var/ somewhere), and restarted gdm and was able to proceed with the normal installation.

---

### Post by elitelinuxnoob on 2007-03-04
> **didu said:**
> that's probably because the ubuntu installation cd tried to use a non-vesa driver for your X. I had the same problem with my desktop which had an ati card, and ubuntu guessed "ati" as the driver in /etc/X11/xorg.conf, I just switched to a virtual terminal (ctrl-alt-f1), and changed the driver from ati to vesa, I then deleted the pid file for gdm (it's in /var/ somewhere), and restarted gdm and was able to proceed with the normal installation.

Can you please explain more on how you change it to "vesa" driver and how to delete this pidfile?

---

### Post by didu on 2007-03-04
> **elitelinuxnoob said:**
> Can you please explain more on how you change it to "vesa" driver and how to delete this pidfile?

In the file /etc/X11/xorg.conf, there is a "Section" that specifies what driver should be used for the video card, in this "Section", there should be an "Identifier" that's the name of your graphics card, under it, there should be a line that says:

```

Driver  "xxxx"

```

Replace the "xxxx" with  "vesa"



To delete the pid file, just remove the file /var/run/gdm.pid .

Then restart gdm by: sudo invoke-rc.d gdm restart

To edit the xorg.conf file, you have to use "sudo vim /etc/X11/xorg.conf", to delete the pid file, you need to use "sudo rm /var/run/gdm.pid".

-D

---

