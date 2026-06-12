---
title: "Unistall Aircrack-ng"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by bandy2000 on 2010-05-25
Hi,

I tried to uninstal Aircrack-ng, in Ubuntu 10.04 because it doesn't work right.
I tried following code:

```
sudo apt-get remove aircrack-ng
```

It brings message:"Package aircrack-ng is not installed, this of it will not be removed."

But if I start it:
```
sudo airmon-ng stop wlan0
```

it gets started, why? How to be sure it is removed and how to do it?
I want to remove and install it again!

---

### Post by cariboo on 2010-05-25
How did you install aircrack-ng?

---

### Post by bandy2000 on 2010-05-25
> **cariboo907 said:**
> How did you install aircrack-ng?
```

cd aircrack-ng
make
sudo make install
```

like this

---

### Post by hyperAura on 2010-05-25
what problems are you having exactly with aircrack?

---

### Post by bandy2000 on 2010-05-25
> **hyperAura said:**
> what problems are you having exactly with aircrack?
It cant get the key and if I run

```
aircrack-ng -b (BSSID) wifi-01.cap
```

it returns ever the same number of IVs 13406.

Doesnt matter how long I collect packages and howmany.

---

