---
title: "Two Drives"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by Gilgen on 2011-02-16
I am about to start a clean installations of XP on one drive and ubuntu on another.

Question is how do I configure the drives i.e. one as a master and the other as slave?
How can I select which OS I want to use when booting up and are there anythings I need to consider before I start?

---

### Post by mikewhatever on 2011-02-16
> **Gilgen said:**
> 

Question is how do I configure the drives i.e. one as a master and the other as slave?
Yes, if those are IDE hdds. With SATA hdds, there is no master/slave distinction, and you don't have to configure anything.

> How can I select which OS I want to use when booting up and are there anythings I need to consider before I start?

If everything goes well, a menu with available OSs will appear at boot. Essentially, the separate hdds setup is not that much different from the separate partitions setup, and if anything goes wrong, you can always boot Ubuntu from cd/usb and cry out for help.

---

### Post by poljpocket on 2011-02-16
Make sure you first install Windows XP and after that Ubuntu. Ubuntu will install grub2 - a bootloader - which will provide you all the OSs installed on the computer at boot time. You can choose which to boot per default by editing the grub2 configuration in Ubuntu. There are many ways to do that.

---

