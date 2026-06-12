---
title: "Installation of 13.04 in VM causes blue screen of death and corrupted SSD"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by shannon.jacobs on 2013-07-06
Can't find a similar report, but it's clearly reproducible, so I'll go ahead and report it... 

When the 64-bit version of Ubuntu 13.04 is installed on a Fujitsu Lifebook SH76/H (less than one year old) it does the initial boot (from the ISO) and later on during the installation it crashes to a blue screen of death. The SSD is corrupted and will eventually crash the 64-bit Windows 7 host OS. Sometimes the crashes are bad enough to make Windows almost unbootable. The virtual machine is running in the latest version of VMware Player. If 13.04 is installed as an upgrade from 12.10, roughly the same thing happens, including the residual disk corruption. I've been through this cycle several times. (Hint: If you can get Chkdsk to run on booting it may avoid a total restore.)

Personal background: Experienced using Ubuntu for some years, but these days mostly using VMware Player (and generally disillusioned with the later versions of Ubuntu). Running the 13.04 in VMs on at least two Toshibas, one notebook and one desktop, without any particular problems (apart from the usual glitches, especially with the Japanese input stuff). I better note the host OSes on those three machines are Japanese versions of Windows 7, all 64-bit. Pretty sure I tried to install it on a couple of other machines, but was warned it might not work, so I didn't try... Evidently the Fujitsu should have the same warning or something stronger.

Basically not eager to spend much time on this, but if someone wants some simple help like the chipset data from the Fujitsu, then let me know. What's the appropriate post icon for a warning?

---

