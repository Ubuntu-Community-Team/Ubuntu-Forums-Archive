---
title: "kubuntu latest alpha - wirless won't connect"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ELD on 2008-09-24
Basically with no error message or anything i try to connect to my unsecured wireless and it does nothing :(

---

### Post by igknighted on 2008-09-27
> **ELD said:**
> Basically with no error message or anything i try to connect to my unsecured wireless and it does nothing :(

What wireless card do you have?  I've been having similar issues with a broadcom card running on b43, it will see networks but never connect.  Not to mention the network list wont refresh.  ever.

Anyone else have issues similar?

---

### Post by jfernyhough on 2008-09-27
I have an issue with an Intel 3945, which normally works everywhere.

In Mandriva 2008.1 rc1 it wouldn't connect in KDE4, I think down to my having a ) in the WPA key. I could connect manually using wpa_supplicant, however.

I had a similar issue in Kubuntu Alpha6, though I gave up quickly and tried 64-bit Ubuntu instead...

---

### Post by ELD on 2008-09-28
> **igknighted said:**
> What wireless card do you have?  I've been having similar issues with a broadcom card running on b43, it will see networks but never connect.  Not to mention the network list wont refresh.  ever.

Anyone else have issues similar?

I am using a netgear pci card, works fine in ubuntu but not kubuntu.

---

### Post by gnomeuser on 2008-09-28
> **jfernyhough said:**
> I have an issue with an Intel 3945, which normally works everywhere.

Welcome to the club, I have not been able to connect to my WPA2 PSK AP using that chipset in Intrepid.. in fact all the way back to Hardy, it has not worked. I know the card is fine since out of the box F9 works (but upgraded does not).

---

### Post by mrboojive on 2008-09-28
The reason you can't connect is probably because the latest version of KNetworkManager doesn't work. A workaround is to install the networkmanager-gnome package.

This thread has some more info:
[http://ubuntuforums.org/showthread.php?t=897144](http://ubuntuforums.org/showthread.php?t=897144)

---

### Post by FuturePilot on 2008-09-28
networkmanager-gnome apparently doesn't work either.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/271097]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/271097")
I can't connect to any wireless either.

---

### Post by ELD on 2008-09-30
My network has no password though so it should not matter?

And plus how can i install a package with no net ;)

---

### Post by caryb on 2008-09-30
I set mine up in knetworkmanager & it connects but not automatically I have to right click on the taskbar icon & tell it to connect on every boot. I have the box ticked for auto connect.


Cary

---

### Post by ELD on 2008-09-30
> **caryb said:**
> I set mine up in knetworkmanager & it connects but not automatically I have to right click on the taskbar icon & tell it to connect on every boot. I have the box ticked for auto connect.


Cary

See mine won't do anything when i tell it to connect.

---

### Post by mrboojive on 2008-09-30
The newest version of KNetworkManager is working for me. Autoconnect works too. I haven't tried it on a secure network, but it's working properly on unsecured networks.

---

### Post by ELD on 2008-09-30
Well i will try it again when it hits beta, could always try a daily cd i spose as well :|

---

### Post by mrboojive on 2008-09-30
If you can connect to the web using another computer, you can go to packages.ubuntu.com and search for and download the knetworkmanager deb package for intrepid. Then move that over to your Kubuntu machine using a flash drive or something. Then you should be able to install that and get connected and you won't have to burn another cd.

---

### Post by ELD on 2008-09-30
Good idea i might just do that from my windows partition, still got the alpha 6 cd lying around ^_^

---

### Post by ELD on 2008-10-01
I tried looking for it but it only finds hardy packages?

edit > found it but there is no deb?

---

### Post by mrboojive on 2008-10-01
[http://packages.ubuntu.com/intrepid/knetworkmanager](http://packages.ubuntu.com/intrepid/knetworkmanager)

Kinda down at the bottom of the page there where it says "all" under architecture is where you need to click to download it. Layout of the page is a little confusing. Looks like you probably need to download this other one, too:

[http://packages.ubuntu.com/intrepid/network-manager-kde](http://packages.ubuntu.com/intrepid/network-manager-kde)

---

### Post by ELD on 2008-10-02
Ah yes thank you, have downloaded and will stick it on a partition so i can use it from within Kubuntu :)

---

