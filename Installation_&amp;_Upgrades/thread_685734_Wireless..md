---
title: "Wireless."
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Commodore13 on 2008-02-02
I'm using a pre-built compaq presario c700 notebook pc, and when i boot up ubuntu or similar distro's on a live cd/usb, I can't seem to configure the internall Wireless card. mostley because on this laptop, there is an actuall button you press to turn it on, and in linux, the button wont ******* work.
is there any drives i can install to fix this problem?

---

### Post by jan quark on 2008-02-02
first some input

please post the result of the following terminal commands

```
lspci
```
```

iwconfig
```
```

ifconfig
```
```

sudo iwlist scan
```

then check in the restricted driver manager if there are some drivers not enabled

---

