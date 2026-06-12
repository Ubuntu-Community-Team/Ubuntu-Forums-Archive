---
title: "NetworkManager VPN &quot;add&quot; button is disabled"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2008-08-15
Hello,

I'm trying out Intrepid Alpha 4 under VMWare 1.0.5 Server on WinXP with NAT networking option.

I noticed NetworkManager (0.7?) has a "VPN" option but the "Add" button is disabled.

I've installed the openvpn, vpnc, network-manager-openvpn, network-manager-vpnc[-gnome] packages. Trying to install network-manager-pptp gives a package error/conflict asking to uninstall network-manager and network-manager-gnome :)

How can I enable the VPN configuration so I can test it out?

- Vishal

---

### Post by grumpymole on 2008-08-15
Excerpt from [this page]("http://www.asoftsite.org/s9y/archives/149-guid.html"):

> Known issues

1. We have dropped all driver tweaks for now. This means you most likely see regressions with orinoco and madwifi/ath drivers.
2. /etc/network/interfaces is currently not recognized. Better remove all entries (except the “iface lo” one) from it to avoid confusing behaviour. The long term idea is to provide legacy backend for network-manager that parses your /etc/network/interfaces as good as possible. If thats not enough for some you probably will have to uninstall network-manager. In case our legacy backend will not reach a stable enough state for intrepid, we might go back to the dumb “blacklisting” approach we used in hardy.
3. network manager applet has no UI to disconnect a particular interface. So do not get confused if you suddenly are connected to wired and wireless at the same time.
4. VPN plugins are not yet available. I added an initial package for the openvpn plugin to the Network Manager PPA (intrepid only) for now. Once I have good feedback I will do the same for the other vpn variants and eventually upload those packages to the real archive.

I think point 4 is related to the VPN stuff not working.

Regards

---

### Post by temcat on 2008-08-16
AFAIK VPN is not supported yet in NM 0.7. I too have this problem: I've updated to current Intrepid but cannot update further because VPN doesn't work :-(

---

### Post by pferraro on 2008-08-16
You can either wait for NM-0.7 compatible vpn packages to be uploaded to the main repos, or use the following ppa, which contains the appropriate functional packages for openvpn, vpnc, and pptp:
[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

---

### Post by Nullack on 2008-08-17
And, have you all subscribed to existing bugs on these problems or created new ones in cases where an existing is not present?

---

### Post by temcat on 2008-08-17
> **pferraro said:**
> You can either wait for NM-0.7 compatible vpn packages to be uploaded to the main repos, or use the following ppa, which contains the appropriate functional packages for openvpn, vpnc, and pptp:
[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Thank you! I'll try that.

---

### Post by vishalrao on 2008-08-24
Did an update this weekend and the VPN "add" button is now working :)

Now I just to get some VPN settings to test on Intrepid then I'll report back...

---

### Post by ephro on 2008-10-01
This thread hasn't been updated in a while, but if you run into this issue make sure you add the right package, for example 'network-manager-vpnc'.


Ephro

---

