---
title: "Kubuntu and Ubuntu 6.06 installed"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by infoseeker on 2006-10-29
I have both Kubuntu and Ubuntu 6.06 installed and I would like to upgrade to Edgy.  I would somehow like to 'disable' Ubuntu for now and upgrade only Kubuntu, as I use Kubuntu more than Ubuntu.  I have downloaded the Kubuntu-alternate CD (6.10) and would like to use that as much as possible.  I would most likely even consider removing Ubuntu (Gnome) for now.
> If you have the edgy alternate install CD, you can save bandwidth by using:
    *sudo apt-cdrom add 


[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

The best way forward?

---

### Post by kidders on 2006-10-29
Hi there,

Why try to disable your Ubuntu?

---

### Post by infoseeker on 2006-10-29
> Why try to disable your Ubuntu?

For bandwidth reasons, or will 'dist-upgrade' happily do both at the same time, and without a huge difference in bandwidth needed?
```
#sudo aptitude dist-upgrade

1292 packages upgraded, 152 newly installed, 63 to remove and 0 not upgraded.
Need to get 947MB of archives. After unpacking 233MB will be used.
```

---

### Post by kidders on 2006-10-29
No, you won't be able to upgrade them both in one go, although you might be able to share some of the .deb files used in the upgrade between the two, if you don't want to waste bandwidth.

Your original post suggested you won't want to upgrade your Ubuntu though ... If you don't want to update it, then don't update it. Just because Edgy is available doesn't mean you *have* to install it. You can safely carry on using Ubuntu Dapper with Kubuntu Edgy.

---

### Post by infoseeker on 2006-10-29
> You can safely carry on using Ubuntu Dapper with Kubuntu Edgy
Please be more specific. How do I upgrade Kubuntu only, leaving Ubuntu 'as is'.
Thanks

---

### Post by kidders on 2006-10-29
Hey again,

Unless you've done something odd, like somehow shared the same system files between the two installs, it would be impossible to update Kubuntu *and* Ubuntu at the same time. Just boot Kubuntu, upgrade it, and leave Ubuntu alone :-)

---

### Post by infoseeker on 2006-10-29
> Just boot Kubuntu, upgrade it, and leave Ubuntu alone
Thanks for the help. Will give it a go.

---

