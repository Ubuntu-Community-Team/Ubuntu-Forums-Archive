---
title: "Problem getting the PHC undervolting patch to work in 2.6.17.10"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by D-- on 2007-01-30
Hi, I'm not a pro with this stuff and am running a fairly new Ubuntu install (whichever was the latest on the official site 2 days ago).

I followed the undervolting guide exactly ([https://wiki.ubuntu.com/UndervoltingHowto)](https://wiki.ubuntu.com/UndervoltingHowto)), step by step, and it looked like everything was going to be fine up until this command:

```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```

The package builder dies out with the following error. Any insight into fixing this would be very appreciated.

```
6.17/debian/linux-headers-2.6.17-10-665/usr/src/linux-headers-2.6.17-10-665/arch/i386/kernel/asm-offsets.s not created: newer or same age version exists
28 blocks
dpkg-gencontrol -isp -DArchitecture=i386 -plinux-headers-2.6.17-10-665 \
                                          -P/home/d/undervolt/linux-source-2.6.17-2.6.17.1/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-665/
dpkg-gencontrol: error: package linux-headers-2.6.17-10-665 not in control info
make[2]: *** [debian/linux-headers-2.6.17-10-665] Error 255
make[2]: Leaving directory `/home/d/undervolt/linux-source-2.6.17-2.6.17.1/debian/build/linux-source-2.6.17'
make[1]: *** [binary/linux-headers-2.6.17-10-665] Error 2
make[1]: Leaving directory `/home/d/undervolt/linux-source-2.6.17-2.6.17.1/debian/build/linux-source-2.6.17'
make: *** [binary-debs] Error 2
```

---

