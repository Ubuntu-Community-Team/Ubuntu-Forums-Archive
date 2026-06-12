---
title: "Custom repository"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by dlublink on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95817](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95817) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I have compiled my own kernel since the default kernel causes a kernel panic on my system. I would like my system to use this as the default kernel.

In Gentoo, I could mask packages and add my own repository with a package of the same name. An update would cause Gentoo to change to the custom kernel.

I have created my repository with my custom kernel.

How can I override the default linux kernel with mine ? ( replace linux-image-generic w/ linux-for-my-laptop ).

I would like simply to be able to run apt-get upgrade so it goes to my custom kernel.

Thanks,

David

---

### Post by Ehtetur on 2007-11-23
If you want to install your own kernel just run this:
sudo dpkg -i <name of package>.deb

Of course, you wanna boot wuth your new kernel to check that everything works before removing the older kernel.

---

### Post by dlublink on 2007-11-23
I just use the live CD for when it screws up.

Thanks,

David

---

