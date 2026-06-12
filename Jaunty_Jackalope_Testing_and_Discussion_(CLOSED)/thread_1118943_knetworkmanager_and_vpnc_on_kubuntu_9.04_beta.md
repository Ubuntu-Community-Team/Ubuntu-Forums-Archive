---
title: "knetworkmanager and vpnc on kubuntu 9.04 beta"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mrmrmrmr on 2009-04-07
I am trying to run vpnc through knetworkmanager on Kubuntu 9.04 beta.
The knetworkmanager applet has the vpn panel and I can add a vpn of type vpnc (Cisco Vpn) ut its settings are not preserved when I open the panel again.
And it does not connect.

I've read on some other forum that to support vpnc, I have to install network-manager-vpnc and I did that already.
But that didn't change the result.

What else do I need to run vpnc on Kubuntu ?

Thanks.

---

### Post by vishalrao on 2009-04-08
i uninstalled the plasma-widget-network-manager ( i beleiev knetworkmanager is no more in kubuntu) and installed gnome's network-manager-gnome because vpn/pptp wouldnt work for kde network manager...

i had to also installed gnome-keyring and gnome-keyring-daemon and add KDE; to /etc/xdg/autostart/nm-applet.desktop file...

---

### Post by mrmrmrmr on 2009-04-08
> **vishalrao said:**
> i uninstalled the plasma-widget-network-manager ( i beleiev knetworkmanager is no more in kubuntu) and installed gnome's network-manager-gnome because vpn/pptp wouldnt work for kde network manager...

i had to also installed gnome-keyring and gnome-keyring-daemon and add KDE; to /etc/xdg/autostart/nm-applet.desktop file...

Thanks for your reply.
Actually, I don't like gnome and gnome tools.
That's the reason I selected Kuuntu instead of Ubuntu.
And I really liked the network manager applet in Kubuntu.
That's why I wanted to use it for vpn connection. Otherwise I can start vpnc from shell anytime.

IS there any way to run the default kubuntu network manager with Cisco vpn ?

---

### Post by at165db on 2009-04-16
I'm also curious about this.  I'm trying to do the exact same thing.

---

### Post by mrmrmrmr on 2009-04-16
but nobody else is replying...

---

### Post by harak on 2009-04-18
A google search shows that this problem exists since several past versions of Kubuntu.

---

