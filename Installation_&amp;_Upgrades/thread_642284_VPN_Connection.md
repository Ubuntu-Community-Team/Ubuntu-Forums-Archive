---
title: "VPN Connection"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by JustKoichi on 2007-12-16
Okay I'm trying to set up a vpn connection with my school so I can get wireless internet

I tried to follow these directions here
[http://lug.wsu.edu/vpn/ubuntu](http://lug.wsu.edu/vpn/ubuntu)

but when i go to my synaptic package manager and try to search for network-manager-pptp its not there. How do I get it so it'll be there? im using 7.10

---

### Post by mikewhatever on 2007-12-16
The package is in Universe, and can be downloaded from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager-pptp&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager-pptp&searchon=names&subword=1&version=gutsy&release=all)

You might need to check your sources list or simply reload it.

---

### Post by JustKoichi on 2007-12-16
> **mikewhatever said:**
> The package is in Universe, and can be downloaded from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager-pptp&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager-pptp&searchon=names&subword=1&version=gutsy&release=all)

You might need to check your sources list or simply reload it.

how do i download and install it?

---

### Post by Partyboi2 on 2007-12-16
> **JustKoichi said:**
> how do i download and install it?
Open up Synaptic Package Manager, 
click on "Settings" at the top,
 then click on Repositories
 When Software Sources open make sure that you have "Community-maintained Open Software Source software (universe) ticked.
 Close that window. 
Then click on reload in Synaptic Package Manager.
Search for your package and install.
or 
You can download the package (might need to manually meet dependencies) 
[http://packages.ubuntu.com/gutsy/net/network-manager-pptp](http://packages.ubuntu.com/gutsy/net/network-manager-pptp)
At the bottom after all the red dots, choose your system type.
amd64
i386
powerpc
Will take you to another page click on a download site. Save it to your desktop or where ever. Then double click on it (Gdebi will open) click on "install package".

---

### Post by JustKoichi on 2007-12-31
Thanks it worked perfectly!

---

