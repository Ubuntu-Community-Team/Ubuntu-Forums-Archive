---
title: "lubuntu 18.10, install on encrypted fs, grub cmd line"
date: 2019-02-26
forum: Installation &amp; Upgrades
---

### Post by Vasu_Muppalla on 2019-02-26
Installation on a HP probook 455 G4 notebook went fine without errors and even got the finish prompt. Then, after the prompt to remove media and hit enter, and the reboot, it takes me to a grub prompt. I know I had installed kubuntu on this before with encryption and it had worked fine.

I let the disk partition default to "erase entire disk" with the encryption box checked. It did all the partitioning, asking for passphrase and install completely finished. In the bios, secure boot is turned off.

What do I need to do to recover ?

TIA.

---

### Post by Vasu_Muppalla on 2019-02-26
It seems that grub is not configured (informed) that the root FS is encrypted so grub does not recognize the root FS. It can only recognize the EFI partition which is fat32. This means that we cannot even go and change the grub configuration which is on the encrypted partition. At least not on this system.

---

