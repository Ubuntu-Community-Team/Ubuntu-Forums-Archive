---
title: "Transfer Drivers to Compiled Kernel"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by dafinga on 2007-03-18
I just bought a Gateway MT3705 Notebook and installed Ubuntu 6.10.  The kernel is 2.6.17-11.  I compiled the newest Kernel to 2.6.20.3.

My wifi was working fine in kernel 2.6.17-11, though wasn't detected in 2.6.20.3.  I know there has been issues with making this [wifi card to work]("http://www.ubuntuforums.org/showthread.php?t=352553"), but how do I take my working drivers and compile them to my new kernel.

I am using this tutorial to compile my kernel: [How to Comile A Kernel - The Ubuntu Way]("http://www.howtoforge.com/kernel_compilation_ubuntu").

Here is my lspci report on my Ethernet Controllers:

02:00.0 Ehternet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)

[COLOR="DarkOrange"]08:09.0 Ehternet controller: Realtek Semiconductor Co., Ltd. Unknown device 8185 (rev 20)[/COLOR] - *(This is my wifi card, it shows Unknown but works on Mac Address Filtering named; **wlan0**.)*

---

### Post by dafinga on 2007-03-19
*bump*

Is this the right thread to post this?

---

