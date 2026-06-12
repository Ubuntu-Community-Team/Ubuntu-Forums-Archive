---
title: "[SOLVED] New Kernel does not work"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by vijaychandilya on 2008-07-27
Hi,
I am running Ubuntu on a Dell 600m laptop with a Pentium M. I downloaded the kernel source for 2.6.26 from kernels.org and followed the instructions to compile the new kernel. I only changed one thing in the kernel config - I changed the processor type to Pentium M (the previous config was x586). Everything went through fine but the new kernel just does not sense wireless. There are no wireless networks even visible now whereas the previous kernel shows me a choice of about 12. Can someone please help?

Vijay

P.S. I did the same build on Fedora and it worked without any issues.

---

### Post by sdennie on 2008-07-27
There are possibly 2 things going on here:

1) You didn't build support for your wireless card into the kernel (probable if you used the Ubuntu config as your base config)

2) You don't have the wireless card firmware setup properly.  You can fix that by making a symlink to a working kernels firmware in /lib/firmware.

If it's the latter you'll see the problem using "dmesg".

---

### Post by vijaychandilya on 2008-07-27
> **vor said:**
> There are possibly 2 things going on here:

1) You didn't build support for your wireless card into the kernel (probable if you used the Ubuntu config as your base config)

2) You don't have the wireless card firmware setup properly.  You can fix that by making a symlink to a working kernels firmware in /lib/firmware.

If it's the latter you'll see the problem using "dmesg".

dmesg says that the Intel 2200 card was loaded so I guess it is #1 above. When I installed Ubuntu it came with a kernel that worked with wireless. I used the config that belonged to that kernel thinking that the same config would work. Is that statement incorrect? In other words, if #1 is what the problem is, then how do I fix it?

Thanks!

---

### Post by sdennie on 2008-07-27
See if this gives any output:

```

lsmod | grep ipw

```

If you are using the ipw driver, you will need to make symlinks to the firmware and also the controller daemon in /sbin for your new kernel version.  I don't have a machine to test this on but, it sounds like it's the problem.

---

### Post by gjoellee on 2008-07-27
can I see exactly which kernel you are using?
> uname -r

---

### Post by vijaychandilya on 2008-07-27
> **vor said:**
> See if this gives any output:

```

lsmod | grep ipw

```

Thanks for the help thus far.

If you are using the ipw driver, you will need to make symlinks to the firmware and also the controller daemon in /sbin for your new kernel version.  I don't have a machine to test this on but, it sounds like it's the problem.

The ipw module is indeed loaded. However, I do not quite know how to follow the rest of your instructions above (sorry!). I tried creating a soft link in /lib/firmware for a new kernel directory

ln -s /lib/firmware/2.6.26-custom /lib/firmware/2.6.24-19-generic

However, that did not really make wireless work. Can you please explain?

---

### Post by vijaychandilya on 2008-07-27
> **gjoellee said:**
> can I see exactly which kernel you are using?

2.6.24-19-generic

---

### Post by sdennie on 2008-07-28
The link in /lib/firmware looks correct.  I looked around and it doesn't look like ipw2200 needs anything beyond the firmware so, I'm not sure what the problem might be.

---

### Post by vijaychandilya on 2008-07-28
> **vor said:**
> The link in /lib/firmware looks correct.  I looked around and it doesn't look like ipw2200 needs anything beyond the firmware so, I'm not sure what the problem might be.

My mistake - the link that I created was wrong! The target goes first, not the directory. Wireless works in 2.6.26-custom now.

---

### Post by sdennie on 2008-07-28
Glad it works.  If you are going to be frequently building new kernels and you are using make-kpkg to build them, you can set it up so that the firmware is auto-linked when it gets installed.  The script I use is:

```

#!/bin/bash

ln -s /lib/firmware/base /lib/firmware/$1

exit 0

```

I name it update-firmware and, to install it:

```

sudo mkdir -p /etc/kernel/postinst.d
sudo install update-firware /etc/kernel/postinst.d

```

There is no /lib/firmware/base by default so, you will also need to:

```

cd /lib/firmware
sudo mkdir base
sudo cp -R 2.6.24-19-generic/* base

```

You can also use that method with other drivers like, [Virtualbox]("http://ubuntuforums.org/showpost.php?p=5271094&postcount=7") or [nvidia]("http://ubuntuforums.org/showthread.php?t=835573").  Hope that helps.

---

