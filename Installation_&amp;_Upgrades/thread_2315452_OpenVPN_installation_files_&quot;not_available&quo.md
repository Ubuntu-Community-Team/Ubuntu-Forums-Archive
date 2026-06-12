---
title: "OpenVPN installation files &quot;not available&quot;"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2016-02-29
I installed Lubuntu 15.10 on a thumb drive, and all seems to be working well.

But when I start to install the OpenVPN files needed to connect to a VPN, I get error messages.

I'm using the "sudo apt-get install" command in Terminal.

Here are the responses I get:

[INDENT](1) For _network-manager_: "network-manager is already the newest version."

(2) For _network-manager-gnome_: "network-manager-gnome is already the newest version."

[/INDENT]
[INDENT](3) For _network-manager-openvpn_:

[/INDENT]
[INDENT=2]    "Reading package lists... Done
    "Building dependency tree       
    "Reading state information... Done
    "**Package network-manager-openvpn is not available**, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
    "E: **Package 'network-manager-openvpn' has no installation candidate**"

[/INDENT]
[INDENT](4) _network-manager-openvpn-gnome_: [Same error message as No. 3 above.]
[/INDENT]

I have installed OpenVPN in Lubuntu several times and never encountered this problem.

Suggestions, please.

---

### Post by X-RED_Tech on 2016-02-29
I don't know why you're doing it that way. This is the official documentation: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
The problem of doing things without understanding them is things often change and in the Linux world they change fast...

---

### Post by QDR06VV9 on 2016-02-29
Here are a couple of links that should work..
[http://www.ubuntuupdates.org/package/core/wily/universe/base/network-manager-openvpn](http://www.ubuntuupdates.org/package/core/wily/universe/base/network-manager-openvpn)

[http://www.ubuntuupdates.org/package/core/wily/universe/base/network-manager-openvpn-gnome](http://www.ubuntuupdates.org/package/core/wily/universe/base/network-manager-openvpn-gnome)
Regards

---

### Post by steve169 on 2016-02-29
Thanks for the references. They did the trick.

---

### Post by QDR06VV9 on 2016-02-29
Good Job..:D

---

