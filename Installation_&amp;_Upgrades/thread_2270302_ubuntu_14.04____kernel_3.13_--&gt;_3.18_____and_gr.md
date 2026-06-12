---
title: "ubuntu 14.04    kernel 3.13 --&gt; 3.18     and graphics issue/error on screen"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by xigen on 2015-03-21
I would like to install the 3.18 kernel to get some audio stuff working (specifically Focusrite 6i6).

I followed the instructions here:
[http://www.linuxandubuntu.com/home/install-linux-kernel-to-3183-stable-in-ubuntu-linux-mint-peppermint]("http://www.linuxandubuntu.com/home/install-linux-kernel-to-3183-stable-in-ubuntu-linux-mint-peppermint")

Then upon reboot I get degraded graphics and "system program problem Detected    Do you want to report the problem now?"
[ATTACH=CONFIG]260812[/ATTACH]

lspci -v

```

05:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 2650
	Flags: bus master, fast devsel, latency 0, IRQ 75
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at c000 [size=128]
	[virtual] Expansion ROM at fe000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia


```

How do I get graphs back with the new kernel?

---

### Post by dino99 on 2015-03-22
[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

3.18 is not a supported ubuntu kernel; better to use a genuine tested one.

---

### Post by xigen on 2015-03-25
ah.. I was wondering.  OK.

Time to use 3.19 and perhaps just wait for the release of 15.04
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Linux-3.19]("http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Linux-3.19")

---

