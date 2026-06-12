---
title: "Upgrading non-pae from 12.04 to 14.04"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by hvn2 on 2014-04-28
Hi,

I want to upgrade a current non-pae Pentium M laptop to 14.04 and read [https://help.ubuntu.com/community/EnablingPAE#Upgrading_to_14.04_on_Pentium_M_laptop](https://help.ubuntu.com/community/EnablingPAE#Upgrading_to_14.04_on_Pentium_M_laptop)**. **It mentions kernel 3.11, but that is Saucy, not Precise. I already installed a 3.2.0-pae kernel. Should I really install that 3.11 Saucy kernel to get the upgrade going ?

Thanks

---

### Post by sudodus on 2014-04-28
What clock frequency is it? Most Pentium M CPUs (with the exception of the very oldest and slowest ones) will run a PAE kernel. The 'only' problem is that there is no PAE flag. This can be fixed with the boot option ***forcepae*** in 14.04 LTS. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

In 13.10 you can use fake-PAE according to this link [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE").

---

### Post by hvn2 on 2014-04-28
It's 1.4 GHz, so I figured it should be possible to install. Suggestion(s) ?

---

### Post by sudodus on 2014-04-28
I'm almost sure it will work in 14.04 LTS with forcepae. There are other Pentium M CPUs with 1.4 GHz, that work.

How much RAM is there, and what graphics chip is it? That might also make a difference. I have an IBM Thinkpad T42 with 1.7 GHz CPU and 1.25 GB RAM, and it runs well with all versions of Lubuntu and Xubuntu. With less than 1 GB RAM you should use Lubuntu or some re-spin of Ubuntu 12.04 LTS.

Good luck :-)

---

### Post by hvn2 on 2014-04-28
It has 500 MB RAM, dmesg shows graphics as radeon.

---

### Post by sudodus on 2014-04-28
With 500 MB RAM I would recommend ***Lubuntu***, and/or to get more RAM. You can probably run the Radeon graphics with the built-in driver.

---

### Post by hvn2 on 2014-04-28
Already running Lubuntu 12.04, so I figure that after the upgrade it will be Lubuntu again (or as well). Will try the 3.11 kernel, reboot and upgrade.

Ok, the 3.11 kernel is refused since it's not Precise. Looks like it's going to be a fresh install of 14.04 ..

---

### Post by chrb on 2014-04-30
> **hvn2 said:**
> Hi,

I want to upgrade a current non-pae Pentium M laptop to 14.04 and read [https://help.ubuntu.com/community/EnablingPAE#Upgrading_to_14.04_on_Pentium_M_laptop](https://help.ubuntu.com/community/EnablingPAE#Upgrading_to_14.04_on_Pentium_M_laptop)**. **It mentions kernel 3.11, but that is Saucy, not Precise. I already installed a 3.2.0-pae kernel. Should I really install that 3.11 Saucy kernel to get the upgrade going ?

Thanks

[http://packages.ubuntu.com/precise/linux-image-3.11.0-17-generic](http://packages.ubuntu.com/precise/linux-image-3.11.0-17-generic) - the 3.11 kernel source package was taken from saucy, but it was rebuilt for precise and precise-updates. You can skip installing it if you already have a PAE kernel. The reason for that step is to encourage people to get a pae kernel working before upgrading, because if if their CPU doesn't support PAE and they upgrade, then their system will be broken.

---

