---
title: "56k modem installation?"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Kakalto on 2005-02-02
Hi, I'd like to know how to get a 56k modem working with linux?

I assume I require a driver? How do I find out what driver I need?

Then, how do I input my ISP's settings?

---

### Post by KiwiNZ on 2005-02-02
Modems are a problem especially winmodems .You may find [www.linmodems.org](www.linmodems.org) usefull.
  What type of modem do you have ?

---

### Post by Kakalto on 2005-02-02
I'm not sure, how do you find out?

EDIT: Never mind, the link helped quite a bit. I seem to have a supported card, and have downloaded the driver gz, but I'm not completely sure what to do next (not sure of the commands to compile).

I'll look through the 1stRead doc, and hopefully will find answers there.

Thanks for your help, and wish me luck.
- Young Kiwi Bloke ;)

---

### Post by az on 2005-02-02
Install build-essential and the linux-headers for your kernel.  Use the linux-headers as the kernel-source tree for your driver.

---

### Post by Kakalto on 2005-02-02
I'm sorry, but I'm rather new to linux, and can hardly understand your sentence, let alone what commands it would require.

---

### Post by az on 2005-02-03
If you would tell what driver you want to use, I can be more specific.  In general, use the linux-headers instead of the kernel source when needed.  You need them to compile drivers.

You cannot compile anything without a compiler - the package "build-essential" is the essential bits of what you need to compile stuff.

---

### Post by Kakalto on 2005-02-03
The computer is using a Lucent WinModem.

I've downloaded the driver for it, but I have not much idea of what to do to install it.

---

