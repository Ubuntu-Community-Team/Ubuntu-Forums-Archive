---
title: "Windows Install - No Boot Screen on Reboot"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by maxcap on 2011-04-25
This is my first time using Ubuntu and any Linux OS.

I installed Ubuntu using the Wubi installer. Everything went fine. When the install wizard completed and asked to Reboot Now, I did. When my computer rebooted, the Windows Boot Manager doesn't appear and it goes straight to Windows.

I'm using 32 bit Vista and have an AMD Athlon X2 Dual Core Processor 5000+. When using Wubi, the download defaults to the AMD 64 version and that is what I have installed.

---

### Post by wilee-nilee on 2011-04-25
Check the time out in the windows boot menu, have you changed it to 0.

---

### Post by maxcap on 2011-04-25
Is that in System-System Properties-Advanced-Time to Display List of Operating Systems?

It's currently set to 30 seconds. Should I change to 0 or just uncheck the box?

---

### Post by wilee-nilee on 2011-04-25
> **maxcap said:**
> Is that in System-System Properties-Advanced-Time to Display List of Operating Systems?

It's currently set to 30 seconds. Should I change to 0 or just uncheck the box?

Leave it as is, I was wondering if it had been set to 0 so that the boot menu you should be seeing was being bypassed.

---

