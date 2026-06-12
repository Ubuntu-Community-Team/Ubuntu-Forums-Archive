---
title: "Gnome-settings daemon error"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by sprinkles on 2007-05-26
I'm trying to install Ubuntu 7.04 on my laptop.

When I put the CD in, everything goes fine until GDM loads, when I am presented with a blank beige background for ages. A grey rectangle then appears in the corner of the screen.

After a while, an error about starting Gnome-settings-daemon appears in the rectangle.

"There was an error starting the GNOME settings daemon.

Some things, such as themes, sounds or background settings may not work correctly.

The error message was:

Did not receive a reply.

(etc.)"

It then locks up like that. If I move my finger on the touchpad, the cursor does move, but after a very long delay.

The laptop also seems very hot.

Any ideas?

---

### Post by sprinkles on 2007-05-26
Sorry to bump, but does anyone have any idea what's causing this?

---

### Post by sprinkles on 2007-05-28
Bump, still can't get this to work.

---

### Post by aysiu on 2007-05-28
This link seems to propose several possible solutions, but I don't know if they'll work for you. They're worth a shot:
[http://gnomesupport.org/forums/viewtopic.php?t=454](http://gnomesupport.org/forums/viewtopic.php?t=454)

---

### Post by cgitz on 2007-05-29
I experienced this problem but everything is fine, now.  I'm fairly certain this is what fixed my problem:

As part of my standard configuration for Feisty, I open up /etc/network/interfaces and comment out everything but the following two lines:

```
auto lo
iface lo inet loopback
```

Network manager takes care of network connections in Feisty.  Commenting out everything but the loopback in interfaces gets rid of the huge wait during boot while it trys to configure the other interfaces.  In my case, I accidentally commented out everything including the loopback (lo) lines.  When I logged in I received the "unable to open the Gnome settings manager" error after waiting about 3-5 minutes.

I uncommented the loopback lines (above), leaving the rest commented, and rebooted.  Everything was fine after that.

---

### Post by xochi on 2008-05-30
> **cgitz said:**
> I experienced this problem but everything is fine, 

I uncommented the loopback lines (above), leaving the rest commented, and rebooted.  Everything was fine after that.

Uncommenting with gedit can be a tricky task. When I interpreted your post  I was found wirelessless until I opened System>Administration>Network, selected Wireless Connection, clicked on properties, deselected "Enable Roaming Mode", chose my local router, chose "Automatic Configuration (DHCP)", closed all windows and rebooted.

My mistake is that instead of uncommenting the entries I deleted them.

Don't know yet whether the Gnome Daemon is fixed, because that only comes up when I change my desktop settings once in a while.

Also, I'm running Gutsy.

My first post!

---

