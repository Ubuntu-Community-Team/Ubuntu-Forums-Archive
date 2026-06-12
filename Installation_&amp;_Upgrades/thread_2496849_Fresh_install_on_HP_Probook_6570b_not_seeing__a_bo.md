---
title: "Fresh install on HP Probook 6570b not seeing  a bootable drive"
date: 2024-04-14
forum: Installation &amp; Upgrades
---

### Post by penbrock on 2024-04-14
I am having a hard time running Ubuntu an older laptop.
I changed the BIOS from UEFI to Legacy. Ran the installer from USB with no issues at all.
When I reboot i keeps saying there is no boot disk. When I try to select the boot drive I only see the Notebook drive it it still doesn't boot.


What am I missing?

---

### Post by penbrock on 2024-04-14
I ended up finding a post with the answer.
You need to set a custom boot in BIOS to EFI\ubuntu\grubx64.efi
Then set the boot order to CUSTOM BOOT

---

