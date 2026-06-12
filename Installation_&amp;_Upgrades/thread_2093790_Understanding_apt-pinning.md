---
title: "Understanding apt-pinning"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by mabra on 2012-12-11
Hello !

At installation time of ZFS (to boot my system from a zsfs pool),
I followed the recommendation and added apt-pinning for this
package.

Ok, but I made a very big mistake and installed from
deb [http://ppa.launchpad.net/zfs-native/daily/ubuntu]("http://ppa.launchpad.net/zfs-native/stable/ubuntu")

instead of 

deb [http://ppa.launchpad.net/zfs-native/stable/ubuntu](http://ppa.launchpad.net/zfs-native/stable/ubuntu)

The pinning priority is 1001.

I fixed this error by modifying the pinning files.
What will happen, if I now update/upgrade ??
Will these version be kept on my box ??

Thanks so far and
best regards,

++mabra

---

### Post by verzx on 2012-12-11
Go in the Software center and in History select the 'updates' tab and from there you can uninstall the updates, once you have done that just install the updates from the stable ppa instead of the daily one.

---

### Post by mabra on 2012-12-13
Hi !

Thanks !
I went to the history and there is no updates -tab.
Anyway.
The box was installed via debootstrap.
My wish is to fix the current state for ever, not un-install
and re-install. This would break my system, because the
ZFS packages are in the kernel.

Regards,
++mabra

---

