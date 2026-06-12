---
title: "Operating System not found during installation with USB stick on x121e"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by fabiank on 2011-12-17
Hi,
 
I am trying to install Ubuntu 11.10 on a brand new Lenovo x121e via an USB stick and followed the instructions on this page:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 
However, I always get the error message "Operating System not found" before the installation process even begins.
 
This is what I tried but nothing helped so far.
1) Prioritize USB stick in BIOS boot sequence
2) Set UEFI/Legacy Boot to "Both" or "Legacy Only"
3) Set UEFI/Legacy Boot Priority to "Legacy First" or "UEFI First"
4) Changed to all available USB ports
5) Tried to use USB stick with a different laptop and it booted perfectly fine
 
Laptop details;
UEFI Bios Version: 8RET30WW (1.12)
UEFI Bios Date: 2011-09-15
CPU Type: AMD E-450
Mem: 4096
USB Stick: HP v135w
 
Thanks for your help,
Fabian

---

### Post by fabiank on 2011-12-17
Found the solution: Used a different USB stick and it worked perfectly fine. Apparently, the HP one is incompatible with the x121e.

---

