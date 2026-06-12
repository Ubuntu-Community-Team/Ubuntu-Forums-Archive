---
title: "Ubuntu 21.04 install problem with Active Directory"
date: 2021-08-24
forum: Installation &amp; Upgrades
---

### Post by guillaume81 on 2021-08-24
[COLOR=#222222][FONT=Verdana]I am in training and I am asked to test the Ubuntu 21.04 version as a client workstation and I have to make it connect to a Windows Server 2016 AD-DC, DNS, DHCP.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]During the install, on the part to create the administrator user, I must be able to check "use Active Directory", but it's disabled, I' m on a hypervisor (VirtualBox) and I use as iso "ubuntu-21.04-desktop-amd64.iso" that I downloaded directly on the Ubuntu website.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I would like to know if it's possible to activate it or not and if I have another possibility to join my client workstation to the domain and if it's possible to apply GPOs.[/FONT][/COLOR]

---

### Post by guillaume81 on 2021-08-26
The problem came from my access to the internet because at the time of the installation Ubuntu 21.04 needs an access to the internet but also to AD server, DNS, DHCP, to have the option activated and thus to be able to inform the domain which one wants integrated

---

