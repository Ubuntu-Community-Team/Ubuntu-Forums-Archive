---
title: "eth0 disappeared after hardy upgrade"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by raistlin_kell on 2008-04-28
I've just completed a successful(?) upgrade from Gutsy 7.10 to Hardy 8.04 on 2 of my desktops but 1 has lost its ethernet connection. 

The ethernet adapter is on an Asus CUSI-M mobo. I've disabled in the BIOS and re-enabled which had no effect. I installed a D-Link DFE530TX PCI NIC & an Intel Dual E100 PCI NIC. Any & all ethernet adapters i insert are not being recognized in the knetworkmanager. They will not enable in the System Settings.

the onboard ethernet adapter was working fine prior to the upgrade. If i open the knetworkmanager and enable any of the eth? shown in the list, the following error appears onscreen:
"could not parse XML output from the network config backend"

**Is there a way to reset the network config backend?**

If i do a lcpci, all the ethernet adapter appear in the output. All Ifconfig's are only reporting "lo" adapter in the list.

---

### Post by richcoosa19 on 2008-04-28
Can you try and give us the output of your /etc/network/interfaces?

---

### Post by pro003 on 2008-04-28
just type in your terminal:

```
ifconfig eth0 up
```

```
ifconfig
```

---

### Post by richcoosa19 on 2008-04-28
> **raistlin_kell said:**
> 
**Is there a way to reset the network config backend?**

If this is the package it is referring to, you can try to run ```
sudo apt-get install --reinstall network-config
```
More than likely it is referring to knetworkconf since you are running kubuntu in that case:
```
sudo apt-get install --reinstall knetworkconf
```

---

### Post by richcoosa19 on 2008-04-28
> **pro003 said:**
> just type in your terminal:

```
ifconfig eth0 up
```

```
ifconfig
```

The problem with this is that when they reboot they won't have networking again.  Making sure this is in /etc/network/interfaces will fix that:
```
auto eth0
iface eth0 inet dhcp

```

If they can run ifconfig eth0 up and have networking, adding this to the config file should fix it.
 :guitar:

But I am kinda worried about the error message involving the XML.

---

### Post by raistlin_kell on 2008-04-29
Well i went back to basics. 
1- Pulled the 2nd NIC
2- enabled the onboard NIC
3- edited /etc/interfaces/network so only the following was shown
   auto eth0
   iface eth0 inet dhcp
4- reboot

After the reboot, eth0 worked fine. knetworkconf still showed no valid ethernet adapter so i reinstalled that. Now knetworkconf doesn't want to start up at all which is fine with me. 

I have a happy desktop again. thanks to everyone for the above input! kubuntu and the devout followers make this flavour of linux ROCK!
:)

---

### Post by raistlin_kell on 2008-04-29
.

---

