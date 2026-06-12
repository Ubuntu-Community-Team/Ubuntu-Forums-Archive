---
title: "Software Updater - Security Update"
date: 2022-02-10
forum: Installation &amp; Upgrades
---

### Post by jamesyuan on 2022-02-10
Hi,

I am using Ubuntu 20.04.3 which is out of the support. Meanwhile, the kernel I used 5.11 is alo out of support. However, I am still receiving the security and base updates weekly. Does anyone know the reason?

---

### Post by grahammechanical on 2022-02-10
Ubuntu 20.04.3 has support until April 2025.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

P.S. I have Ubuntu 20.04.3 on a laptop I purchased with Ubuntu pre-installed about a month ago. The kernel was 5.8 and since then Software Updater has upgraded the kernel to 5.13.0-28-generic.

Regards

---

### Post by deadflowr on 2022-02-10
20.04.3 is still supported.
20.04.3 is 20.04.
Why do you think it's not supported?

---

### Post by jamesyuan on 2022-02-10
Thanks! I forgot I saw somewhere written it is not supported. Anyway, it is good news for me.

---

### Post by jamesyuan on 2022-02-10
Thanks!

---

### Post by guiverc on 2022-02-10
Ubuntu 20.04 LTS is still supported as already covered.

Ubuntu 20.04 LTS is a LTS release, so two kernel stack options exist; for server installs the default is GA which remains on 5.4 the life of the product.  For desktop installs for Ubuntu Desktop it'll default to HWE (*skipping flavors here*) it changes over the life of the product.

- At 20.04.2 the HWE kernel upgraded to 5.8
- At 20.04.3 the HWE kernel upgraded to 5.11

- At 20.04.4 the HWE kernel upgraded to 5.13 - this upgrade started rolling out ~two weeks ago so I'd already expect you to have 5.13 installed, and when you reboot you'll likely be using it..  When you've all of the 20.04.4 upgrades your system will report itself as 20.04.4; nothing special is required except the usual `sudo apt update` to ensure your software lists are up-to-date (*and no errors*) and `sudo apt full-upgrade` to ensure all upgrades are applied

- At 20.04.5 the HWE kernel will upgrade to 5.15, but that's near 6 months into the future. This will be the *final* landing place for the HWE kernel, ie. the GA kernel from the next LTS stack (ie. *5.15 is the [expected] GA stack for Ubuntu 22.04 LTS when it releases*)

---

