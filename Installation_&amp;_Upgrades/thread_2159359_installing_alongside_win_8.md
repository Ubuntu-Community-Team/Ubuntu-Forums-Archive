---
title: "installing alongside win 8"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by brfarris73 on 2013-07-02
When attempting to install ubuntu 13.04 alongside windows 8 on an acer aspire I get no option to install alongside the existing operating system.  Is this normal?

---

### Post by Frogs Hair on 2013-07-02
Hello and Welcome

From a tutorial I found, if you have more than two Windows patrtitions the along side option may not be availabe . A look at Windows disk management will display your partitions. OEM computers come pre-partitioned .

Ask Ubuntu: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by oldfred on 2013-07-02
Is this pre-installed Windows 8 with UEFI and secure boot. Or a system you upgraded that still is BIOS/MBR?

Post this from terminal in live version you are using to install:

sudo parted -l

If UEFI see also my signature.

---

