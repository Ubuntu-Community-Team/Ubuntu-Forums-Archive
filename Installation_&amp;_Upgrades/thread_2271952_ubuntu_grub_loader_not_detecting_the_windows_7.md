---
title: "ubuntu grub loader not detecting the windows 7"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by saravananm-m on 2015-04-02
Please help me install ubuntu 14.02 along with windows 7. I try install ubuntu, its not detecting the windows 7.


Thanks,
Saravanan M

---

### Post by Bucky Ball on 2015-04-02
*Thread moved to **Installation & Upgrades**.*

Welcome. Have you booted to Windows and switched off faststartup? It may be called fastboot. If you have this on, the Windows partition is hibernating and as it is not unmounted will be inaccessible to the Ubuntu installer.

---

### Post by oldfred on 2015-04-02
Changed to grub in title.

May be best to see detail. Post link to summary report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

