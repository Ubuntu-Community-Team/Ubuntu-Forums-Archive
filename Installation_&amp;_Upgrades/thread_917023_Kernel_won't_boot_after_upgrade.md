---
title: "Kernel won't boot after upgrade"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by ganda99 on 2008-09-11
Hi,

I dying here - please help! :-\

Since upgrading to Kubuntu 8.04 via Adept_manager I can't boot the 2.4.24-21 kernel that came with the installation. It just hangs for about three minutes then I'm placed in an initramfs prompt. 

I can boot successfully from the previous 2.6.22-15 kernel, however xorg is very flaky. 

I believe there might be some kind of confusion in my system between the old kernel and the new. 

Is there anything I can do you either verify or confirm my kernel setups are proper? 

Thank you very much. 
-- Gary

---

### Post by ganda99 on 2008-09-11
Nevermind. 

After reading through a few lengthy threads and trying many of the options suggested I found adding the "pci=nomsi" to the kernel reference in menu.lst solved it. 

Thanks anyway!

---

