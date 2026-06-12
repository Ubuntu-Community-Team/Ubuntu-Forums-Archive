---
title: "Ubuntu doesn't boot from SSD on a Dell Precision T5600"
date: 2024-08-12
forum: Installation &amp; Upgrades
---

### Post by vbhamidipati on 2024-08-12
I have a 11 year old Dell Precision T5600 with the old SATA hard drive replaced by a M2 SSD installed in a PCIe 3.0 slot. I followed Dell instructions and changed the SATA setting to AHCI. I also chose UEFI as the boot option instead of 'Legacy Boot'. Installation (Ubuntu 24.04) from a USB drive was seemingly successful (the SSD was detected) and prompted me to restart after removing USB media. When I hit F12 I see Ubuntu under UEFI boot options. When I select it however nothing seems to happen. I tried turning off RAID but that didn't help. There is no 'Secure Boot' option in BIOS settings to disable. There seems to be no obvious problem. Can someone help me diagnose the issue?

---

### Post by currentshaft on 2024-08-12
.

---

### Post by vbhamidipati on 2024-08-12
> **currentshaft said:**
> Is there an "allow third party CAs" secure boot option in the BIOS/UEFI?

I didn't see any such option. Attaching a screenshot.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294082&stc=1[/IMG]

---

### Post by currentshaft on 2024-08-12
!

---

