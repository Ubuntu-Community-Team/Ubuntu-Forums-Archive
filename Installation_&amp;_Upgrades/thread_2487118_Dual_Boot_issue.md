---
title: "Dual Boot issue"
date: 2023-05-23
forum: Installation &amp; Upgrades
---

### Post by siddarthareddyl on 2023-05-23
I have installed ubuntu by flashing my usb in my laptop. Initially it had shown dual boot option. But a later it disappeared.
I have tried almost all methods from YouTube. I don't get what is the problem . 

Here is the diagnosis report :[https://paste.ubuntu.com/p/5kK5fn79K5/](https://paste.ubuntu.com/p/5kK5fn79K5/)

---

### Post by oldfred on 2023-05-23
Did you install with UEFI Secure Boot off? And then a Windows update (which you may not even see) updated UEFI firmware & reset system to defaults?

Check UEFI settings. Try with Secure Boot off?
Boot-Repair is suggesting to install the UEFI secure boot (signed) version of grub. But then you would also need signed kernel & if proprietary driver or Wi-Fi, you have to create your own MOK machine owner key to say they are signed as Ubuntu cannot say that.

---

### Post by siddarthareddyl on 2023-05-24
I am not good with this terminology "[COLOR=#000000]Boot-Repair is suggesting to install the UEFI secure boot (signed) version of grub. But then you would also need signed kernel & if proprietary driver or Wi-Fi, you have to create your own MOK machine owner key to say they are signed as Ubuntu cannot say that."
Help me if you can.[/COLOR]

---

### Post by tea for one on 2023-05-24
[COLOR="#0000FF"]Line 117[/COLOR] - Disk nvme1n1: 13.41 GiB, 14403239936 bytes, 28131328 sectors
[COLOR="#0000FF"]Line 141[/COLOR] - nvme1n1:14.4GB:nvme:512:512:unknown:INTEL HBRPEKNX0101AHO:;

This info from the boot-repair report indicates that nvme1n1 is an Intel Optane device.

In your UEFI settings, can you disable this drive and also disable secure boot?
[s]Reboot.[/s]
Also, check that SATA is set to AHCI.
Reboot

---

