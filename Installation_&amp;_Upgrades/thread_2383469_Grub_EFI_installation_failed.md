---
title: "Grub EFI installation failed"
date: 2018-01-25
forum: Installation &amp; Upgrades
---

### Post by olegipman on 2018-01-25
Hello guys!
Can you help me please?
When I install Ubuntu, or mint I have the same problem "GRUB INSTALLATION FAILED. The "grub-efi-amd64-signed" package failed to install into /target/. Without the GRUB boot louder, the installed system will not boot."
I can't solve this problem all day. My work stopped. Help me please!!!

---

### Post by ubfan1 on 2018-01-25
This is a UEFI install, does your target disk have a EFI partition?  Is your target disk sda (which is used for UEFI bootloader installs regardless of what you specify as the bootload location)?

---

### Post by olegipman on 2018-01-26
Yes, ofcourse...

---

### Post by olegipman on 2018-01-26
It solved!!!
Guys... I used UNetBootin to make load flash. But today I used "dd" in terminal and it's alright!!)))

---

