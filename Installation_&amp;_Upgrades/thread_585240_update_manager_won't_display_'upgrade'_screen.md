---
title: "update manager won't display 'upgrade' screen"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Tuxoid on 2007-10-21
I have been trying for nearly 8 straight hours to upgrade from feisty to gusty. The update manager will not get to this screen: [IMG]http://www.ubuntu.com/files/u1/710_update-manager-upgrade.png[/IMG]

I have only changed sources.list to include the medibuntu repo  (now removed). I have followed the instructions to upgrade here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
 But it just won't go to the upgrade screen for getting gusty. I have tried the gusty livecd and gusty works off the cd, but I don't want to do a fresh install if I can avoid it. I would have too much stuff to backup before-hand.

---

### Post by solar george on 2007-10-21
Open a terminal and type
```
sudo update-manager -c 
```

---

### Post by Tuxoid on 2007-10-21
the command did not solve the problem. Here's th output:

```
mike@Mike:~$ sudo update-manager -c
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
mike@Mike:~$
```

Would it matter if I had automatix installed (even if I uninstalled it)?

---

### Post by solar george on 2007-10-21
Try downloading the alternate cd and upgrading from that.

---

### Post by Tuxoid on 2007-10-22
I upgraded on the alternative CD. Gusty is working well.:)

---

