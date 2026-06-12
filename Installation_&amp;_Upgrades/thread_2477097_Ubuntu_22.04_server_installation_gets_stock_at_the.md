---
title: "Ubuntu 22.04 server installation gets stock at the beginning"
date: 2022-07-14
forum: Installation &amp; Upgrades
---

### Post by sydney1342 on 2022-07-14
I am facing problems during the installation process of Ubuntu 22.04 server. The process already gets stocked in the beginning, when the checks at the black screen are run (see screenshots in attachments).
During my installation tries it got stock at similar lines, but not necessarily always at the same line. But always near to: 
"[sda] Write Protect is off", 
"[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FVA", which seems that it might be some memory issue. 
On the other hand often close to some lines related to graphics: "switching to nouveaufb from VESA VGA".

System configuration:
CPU: i7 920 
HD: SSD which is empty (no windows or other system installed). 
Graphic card: Gigabyte Geforce GTX 970 G1 Gaming

From another PC I have created a boot able USB stick using the Startup Disk Creator Program. Thats how I boot and how I trigger the installation process.

I have also tried to install the Version Ubuntu 20.04 Server. There the error message was clearer and also related to the graphic card:
„nouveau 0000:02:00.0: bus: MMIO write of 800001f4 FAULT at 10eb14 [ IBUS ]“

---

### Post by TheFu on 2022-07-17
"stock"?  Are they common shares or preferred?   Or is this a typo?

I had a i7-920 CPU. That's from 2009-ish for everyone lurking.  Retired mine for a Ryzen 5 and in 2 yrs, the electricity savings paid for the new system.  I'm looking at upgrading the Ryzen 2600 to a 5600G now that prices have dropped again. The upgrade will raise performance by about 40% and let me drop all nvidia GPUs.

I can only suggest that reading the release notes for both the distro and the DE being installed will likely point out issues and work-arounds for the GPU used in the system.  Seems odd that a "server" distro needs a GPU, but that's the default for some reason. There are ways using an alternate installer to use a serial port connection for installation without a GPU.  I've had 2 GPUs from the same time fail. They just wear out.  I've also seen 2 from the same period loose nvidia support, so the F/LOSS drivers had to be used, but at a much lower resolution than was supported with the exact same hardware in the 16.04 release.

---

