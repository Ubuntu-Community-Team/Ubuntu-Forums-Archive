---
title: "[regression] nvidia powersaving on demand interrupts feature"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aldeby on 2009-03-14
With recent (post 9 march) updates nvidia restricted drivers do not accomplish to "On Demand Interrupts" enabled any more.
This results in increased power consumption and reduced battery life.

Despite stating in Xorg.0.log
(**) NVIDIA(0): Option "OnDemandVBlankInterrupts" "true"

Powertop reports:  15.2% ( 49.5)       <interrupt> : nvidia 

with nvidia interrupts ranging from 45 to 60.

Since powertop reports video card interrupts along with USB host controller I have previously removed uhci_hcd module from kernel.

Installed packages are: 
ii  nvidia-180-kernel-source                   180.37-0ubuntu1                              
ii  nvidia-glx-180                             180.37-0ubuntu1                              

Linux 2.6.28-9-generic #31-Ubuntu SMP Wed Mar 11 15:43:58 UTC 2009 i686 GNU/Linux

---

