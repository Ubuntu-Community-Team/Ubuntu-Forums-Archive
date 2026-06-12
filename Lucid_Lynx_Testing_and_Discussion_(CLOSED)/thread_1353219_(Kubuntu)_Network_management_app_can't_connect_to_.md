---
title: "(Kubuntu) Network management app can't connect to wireless?"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Taoye on 2009-12-12
So I've installed alpha 1 Kubuntu on my laptop to try out, and everything seems to be working out of the box except for the network management widget. It connects to my wired network automatically, but I can't get it to connect to a wireless network. Clicking on the widget should bring up the menu of connections to connect to, but for me it does nothing. I did go into settings and configure my wireless network and set it to connect automatically, but still nothing.

Has something been changed in the latest version that's broken it? Anyone else getting this?

---

### Post by koso on 2009-12-12
I am using knetworkmanager, plasma widget for network management seems to by unusable. I placed it on desktop, and was able to open some menu, but little playing with changing dimensions, and it totaly messed up my desktop :P

---

### Post by bennachie on 2009-12-12
I have the same problem - since I depend on a wireless network for my connection to the internet, I guess that I'll have to hold off testing Kubuntu until the problem is fixed. Fortunately, Ubuntu Lucid is working very well indeed. I'm sure there will be bumpier times ahead as new features are introduced ...

---

### Post by caryb on 2009-12-12
+1 for me! I had to reinstall the network manager widget as well.


Cary

---

### Post by Taoye on 2009-12-12
Yeah installing knetworkmanager works, gets me wireless.

---

### Post by ronacc on 2009-12-12
I stumbled across that fix last night , I think its a bug that knetworkmanager isn't installed by default ,

---

### Post by SalvoMaltese on 2009-12-14
> **Taoye said:**
> Yeah installing knetworkmanager works, gets me wireless.

Where can I get knetworkmanager and install in kubuntu lucid?

I've only wireless, so no eth connection...

---

### Post by johwel on 2009-12-16
> **SalvoMaltese said:**
> Where can I get knetworkmanager and install in kubuntu lucid?

I've only wireless, so no eth connection...

Hi SalvoMaltese,
You can download it here from another computer with internet connection: [http://packages.ubuntu.com/lucid/network-manager-kde](http://packages.ubuntu.com/lucid/network-manager-kde)
and install with sudo dpkg -i <file name>.deb

I also downloaded and installed "knm-runtime" - can be searched for at [http://packages.ubuntu.com/lucid](http://packages.ubuntu.com/lucid). Then I right-clicked the existing network applet and chose "Manage Connections..." -> "wireless", set up a new connection and set to "Connect automatically". Only after a restart my wireless connected without any interaction and the KnetworkManager shortcut appeared in the KDE menu.

---

