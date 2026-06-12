---
title: "update to 12.04 does not upgrade kernel"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by Jzz5 on 2012-06-15
Hi all,

I've searched around but could not find an appropriate answer. Yesterday I upgraded my production machine to 12.04. All went well, except for the kernel. It did not upgrade to 3.2 (uname -r shows 3.0.0-16-generic-pea). In /boot this is the newest kernel as well.

I think this has to do with me downgrading the last kernel update in 11.10, because of Nvidia driver problems. This should be fixed now in 12.04, so I would like to upgrade to 3.2 kernel now. In my test environment it went without a glitch, but this is a 64 bit install, while my production machine is on 32 bit (not usefull, I know).

How do I force Ubuntu to upgrade my kernel? sudo apt-get install ..?.. what? Or is there another trick?

Thanks,

Jzz

---

### Post by Jzz5 on 2012-06-15
Update:

I tried 'sudo apt-get dist-upgrade' and it tried to install the 3.2.0-25 kernel but gave the following error:


```
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.

```

I then tried to clear apt-get of any errors by:

```
sudo apt-get install -f

```
and 
```
sudo apt-get clean
```

but no succes. Another

```
apt-get dist-upgrade
```
gave no available upgrades.

---

### Post by Lipaugus Vociferans on 2013-02-04
[SIZE="2"]It happened to me on an Ubuntu Server-x64, I removed manually some old kernels and now Aptitude fails to offer me any kernel upgrades, The rest of the packages are upgrading normally, so I've been upgrading manually since kernel 3.2.0.29... Maybe I erased something else? Any info would be greatly appreciated[/SIZE]):P

---

