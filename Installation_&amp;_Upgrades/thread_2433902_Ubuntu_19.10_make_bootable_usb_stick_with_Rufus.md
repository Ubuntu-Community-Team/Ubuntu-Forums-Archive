---
title: "Ubuntu 19.10 make bootable usb stick with Rufus"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by besi1 on 2019-12-27
Hello people want to switch from windows to Ubuntu now I downloaded the Iso 19.10, then I downloaded the rufus tool.
Now I have started the program and this iso I have partition scheme as MBR or GPT. I have GPT with UEFI non CSM.
But with Filesystem there is Large Fat 32 and NTFS now I do not know what to take? Large Fat 32 or NTFS?
Thank you for your answers.

---

### Post by oldfred on 2019-12-27
I am surprised it even offers anything other than FAT32.
UEFI only boots from FAT32.

Newest Windows ISO has one file .wim that is larger than what FAT32 supports, so it requires exFAT.

More info on UEFI install in link in my signature.

I would suggest a full backup of Windows.
Many users find one application or game that only runs on Windows so then want to reinstall Windows to dual boot.

---

