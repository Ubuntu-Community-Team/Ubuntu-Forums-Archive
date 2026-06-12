---
title: "from 16.04 to 18.04 - Lost Wifi"
date: 2018-08-10
forum: Installation &amp; Upgrades
---

### Post by opale7001 on 2018-08-10
Hello Ubuntu fans.

I have read in another thread to follow these steps

```

sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6

```

All worked as except  for the last command i get

```

sudo dkms install rtlwifi-new/0.6

Error! Your kernel headers for kernel 4.13.0-26-generic cannot be found.
Please install the linux-headers-4.13.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located



```

---

### Post by oldos2er on 2018-08-10
Did you install the linux-headers package as it suggests?

---

### Post by opale7001 on 2018-08-10
> **oldos2er said:**
> Did you install the linux-headers package as it suggests?

Never done this before but willing to learn

---

