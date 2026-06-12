---
title: "Fresh install of Kubuntu 23.10 - GRUB problems"
date: 2024-04-26
forum: Installation &amp; Upgrades
---

### Post by oygle on 2024-04-26
Lenovo running Windows 10 with a SSD. Installed Kubuntu 23.10 on an EXTERNAL SSD attached to the Lenovo. The first time I did the installation, the GRUB errors were

> Unable to install GRUB in /dev/nvme0n1 . Executing 'grub-install/dev/nvme0n1' failed. This is a fatal error

Tried the install again and it went okay. So 23.10 is installed on the external SSD. BUT every time I try to boot , it either drops into Windows 10 (which is fine) or drops down to a GRUB prompt. Like

```
>grub
```

Now what ?  Does GRUB have to be installed into the 'windows' partition on the internal SSD ??

---

### Post by oygle on 2024-04-27
Worked out a few basic GRUB commands but it didn't help much. All it told me was that the Windows 10 SSD was the OS I was booted to. Then looked in the BIOS. The external SSD is connected via a Thunderbolt port. Oh, I had to enable any USB devices on that port. Rebooted and went into Kubuntu now. Now, can I get back and boot to Windows if need be ...hahaha

---

### Post by sudodus on 2024-04-27
Thanks for sharing your solution :-)

---

### Post by oygle on 2024-04-27
> **sudodus said:**
> Thanks for sharing your solution :-)

You are welcome. Thanks heaps for all your help.  :)

---

