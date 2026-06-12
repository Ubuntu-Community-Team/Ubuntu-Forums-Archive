---
title: "transmeta crusoe processor"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by stevetxt on 2005-02-10
I installed Ubuntu on my Fujitsu P2040 laptop a couple weeks ago.  This laptop has a Transmeta Crusoe processor.  The install went pretty well, though it gets set up with the standard i386 option in the kernel, whereas there is another section of kernel configuration where Crusoe support may be selected instead.

Later I recompiled the kernel selecting Crusoe support and selecting apm instead of apci (which doesn't seem to work with this computer).  Those were basically the only changes I made, starting from the configuration file that Ubuntu had set up on installation.

The problem I ran into though, is that when I tried setting up my wireless pc card (d-link dwl 650 with atheros chipset), the madwifi driver modules would not load with the Crusoe supporting kernel.  So I went back to using the kernel that Ubuntu had set up automatically with i386 selected.  It appears that the Ubuntu packages with the madwife drivers (linux-restricted-modules) are specific to i386, i686, and maybe amd64 and ppc kernels.  

It appears my Ubuntu default i386 kernel works ok, but then I don't get whatever support was built into the kernel specifically for the Crusoe processor.

Any suggestions here?

Thanks,

Steve

---

### Post by refactored on 2007-03-22
I've installed the latest (edgy) server edition with the generic kernel. Is it stil nessesary to compile my own kernel to get the most out of a transmeta processor?

/refactored

---

