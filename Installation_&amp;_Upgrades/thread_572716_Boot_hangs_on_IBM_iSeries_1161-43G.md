---
title: "Boot hangs on IBM iSeries 1161-43G"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by amartinwest on 2007-10-10
Package: installation-reports

Boot method: CD
Image version: 7.04
Date: 2007-Oct-7

Machine: IBM Thinkpad iSeries 1161-43G
Processor:
Memory: 176M
Partitions: N/A

Output of lspci and lspci -n: N/A

Base System Installation Checklist:
[O] = OK, [E] = Error (please elaborate below), [ ] = didn't try it

Initial boot worked:    [E]
Configure network HW:   [ ]
Config network:         [ ]
Detect CD:              [ ]
Load installer modules: [ ]
Detect hard drives:     [ ]
Partition hard drives:  [ ]
Create file systems:    [ ]
Mount partitions:       [ ]
Install base system:    [ ]
Install boot loader:    [ ]
Reboot:                 [ ]

Comments/Problems:


Hangs in boot even after specifying

BOOT_DEBUG=3 noapic nolapic fb=false debian-installer/probe/usb=false

photo of console attached.

This machine boots on the base FC3 but needs nousb once updated.

---

### Post by Pumalite on 2007-10-10
If your RAM is 176 MB  you should stick to a lighter Desktop. You might try:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Nomeaning25 on 2007-12-18
I have the same problem. Did you solve this. And How?

@Pumalite: I've tied that one, it doesnt work either (tried both Live and Alternate CD)

---

### Post by Pumalite on 2007-12-18
Then is DSL or Puppy.

---

