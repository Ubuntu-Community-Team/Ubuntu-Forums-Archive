---
title: "Fixed: no NetworkManager icon in notification area"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-04-14
I had this Dell Latitude E6400 laptop with latest LucidLynx, after starting with the 2/23/2010 daily build and upating since then.

The NetworkManager icon would never show up in the NotificationArea on the top panel. From another posting, I did manage to click the exact spot (possibly a 1x1 icon) to show me that eth0 was not managed and that the wireless not managed.
So the icon was there but mangled or maybe purposely
not displaying itself, cause it was ashamed that it had nothing
good to tell me?

My syslog did have this in it:
  NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced.

The nm-applet is running, and restarting it, doesn't help.

But by removing the following from /etc/network/interfaces
and rebooting, it fixed the problem for me:
    auto eth0
    iface eth0 inet dhcp

I now have the NetworkManager icon. I do have a "eth0" connection
and wireless networks to choose from.

I can only surmise, that NetworkManager wanted to discover the
Ethernet card itself, and assign it "eth0" rather than having
it be hard coded in the /etc/network/interfaces file.
(but I am only guessing)

---

### Post by Ancanus on 2010-04-14
Good find! Fixed it for me as well.
I thought about reporting it as a bug to launchpad, but they have circa 800 open bugs going on in there :S.

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553115](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553115)

---

