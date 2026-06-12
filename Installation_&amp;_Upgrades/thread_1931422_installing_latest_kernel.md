---
title: "installing latest kernel"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by KRISHNASHK on 2012-02-25
Hi i am running ubuntu 10.10 and my kernel version is 2.6. can i install latest kernel ?
thanks

---

### Post by darkod on 2012-02-25
Usually you would need to upgrade the version. Newer versions automatically have newer kernels.

But not every upgrade is successful, there can be hardware conflicts. It's best to burn a cd with the version of ubuntu you want to install or upgrade to and try it in live mode (Try Ubuntu). If live mode works, most probably that version will work on your computer.

And since you haven't upgraded since 10.10, it might be best to wait few months for the new 12.04 LTS and make a clean install. Otherwise you would need to upgrade few times version by version, and the possibility of problems increase with the number of upgrades.

---

### Post by Lars Noodén on 2012-02-25
If you want to install the very latest you can install a mainline kernel.  Those are without any customizations that might come from Ubuntu.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Unless you have specific problem you are trying to sort or are helping test, there's not any advantage to doing so.  It's better to wait for the regular kernels.

Have you checked the 10.10 backports repository yet?

---

### Post by KRISHNASHK on 2012-02-26
> **darkod said:**
> Usually you would need to upgrade the version. Newer versions automatically have newer kernels.

But not every upgrade is successful, there can be hardware conflicts. It's best to burn a cd with the version of ubuntu you want to install or upgrade to and try it in live mode (Try Ubuntu). If live mode works, most probably that version will work on your computer.

And since you haven't upgraded since 10.10, it might be best to wait few months for the new 12.04 LTS and make a clean install. Otherwise you would need to upgrade few times version by version, and the possibility of problems increase with the number of upgrades.
i update using the update manager! i ubuntu is up to date.

---

### Post by KRISHNASHK on 2012-02-26
> **Lars Noodén said:**
> If you want to install the very latest you can install a mainline kernel.  Those are without any customizations that might come from Ubuntu.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Unless you have specific problem you are trying to sort or are helping test, there's not any advantage to doing so.  It's better to wait for the regular kernels.

Have you checked the 10.10 backports repository yet?
sorry what is backport reposotory?

---

### Post by darkod on 2012-02-26
> **KRISHNASHK said:**
> i update using the update manager! i ubuntu is up to date.

Update is not the same as upgrade.

I am not talking about updating the packages, I am talking about upgrading your 10.10 to 11.04 or 11.10. But as I already mentioned, when you have a non-LTS version like 10.10 you need to upgrade one by one. First to 11.04 and then that to 11.10. Usually so many upgrades in a row will definitely mess up something.

LTS releases you can upgrade from one LTS directly to the next one, for example 10.04 LTS to 12.04 LTS.

---

### Post by davidvandoren on 2012-02-27
you always can reinstall the current kernel.
Sometimes, something got broken.

It fixed the problems I got after installing Firefox 10

```
sudo apt-get install linux-image
```

---

### Post by Lars Noodén on 2012-02-27
> **KRISHNASHK said:**
> sorry what is backport reposotory?

[Backports](https://help.ubuntu.com/community/UbuntuBackports) are newer versions of software ported to the older versions of Ubuntu.  

Unfortunately that looks like it may not be an option for you:
[http://packages.ubuntu.com/maverick-backports/allpackages](http://packages.ubuntu.com/maverick-backports/allpackages)

I don't see the package linux-image there.

---

