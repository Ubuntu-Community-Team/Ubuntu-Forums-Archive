---
title: "Choose kernel version to use during installation"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by fenix88 on 2011-09-09
Greetings!

I'm installing Ubuntu Desktop 10.4.1 LTS on my server to be used with Ncomputing L-130.

According to Ncomputing's website, the supported versions for Ubuntu are 10.4, 10.4.1 and 10.4.2. Also stated in their website, the kernel versions that are supported are 2.6.32-21 thru 2.6.32-31 generic.

After I installed Ubuntu, I checked the kernel version and it stated that the version installed was 2.62.32-33 generic pae.

Is there a way to manually set the kernel version to be installed during installation? Or do I have to downgrade the kernel version that's already installed?

---

### Post by 2F4U on 2011-09-10
I doubt that there is much difference between kernel versions 2.6.32-31 and 2.6.32-33. Both are long-term kernels and the -33 just indicates that there have been bug fixes or security updates.
Manually setting the kernel version at install time is not possible, as far as I know. It just installs whats included on the install medium.

---

### Post by mörgæs on 2011-09-10
It is possible to boot into an older kernel, but if the computer runs well, there is no need to do so. Ubuntu works fine on a whole lot of hardware where it is not officially supported.

---

### Post by fenix88 on 2011-09-11
Well actually I think the kernel version is causing problem with Ncomputing. So is there a way to downgrade the kernel?

Thanks!

EDIT: I downgraded the kernel from 2.6.32-33-generic-pae to 2.6.32-31-generic through the package manager and now Ncomputing is now working!

---

