---
title: "KNetworkManager (vpn/static-ip/wifi etc) still generally broken?"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-02-11
Looks like networking may still be problematic for those users who don't want the default auto/dhcp mode.

Is this just a lucid/packaging issue or the problem exists upstream as well? Or is it just my install thats borked? :)

I am going to try the same workaround like I did last release - remove it and install network-manager-gnome so I can get PPTP VPN, wifi, static IP etc working... I don't have mobile broadband dongles to test.

edit: My knetworkmanager version is: 1:0.9~svn1075616-0ubuntu1

```

vishal@thunderbird:~$ sudo apt-cache policy network-manager-kde
network-manager-kde:
  Installed: 1:0.9~svn1075616-0ubuntu1
  Candidate: 1:0.9~svn1075616-0ubuntu1
  Version table:
 *** 1:0.9~svn1075616-0ubuntu1 0
        500 http://fr.archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status

```

---

