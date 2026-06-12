---
title: "[Ubuntu 22.04.4] Issue installing ubuntu via bootable stick"
date: 2024-07-25
forum: Installation &amp; Upgrades
---

### Post by flieps on 2024-07-25
Hello guys, 
I tried to install ubuntu 22.04.4 via bootable stick (image downloaded from the official website and was created with the startup disk creator) and got a very unfamiliar problem. 
It is a complete new hardware setup, nothing used before.

The installation "crashed" while setting up the user and led me into the live ubuntu OS on the stick. After retry the installation the exact same issue happened, but it shows me that there is already an installed ubuntu OS now.
I don't get any error messages or something similar.

Thanks for your help!
flieps

---

### Post by ActionParsnip on 2024-07-25
Did you SHASUM check the file you downloaded to make sure it is complete and consistent?

---

### Post by flieps on 2024-07-26
Hey, yeah I checked the hash and it is exactly the same.

---

### Post by oldfred on 2024-07-26
What brand/model system? What video card/chip?
Is system older that 22.04 or you may need newer version to have kernel & driver support.

Have you updated UEFI & SSD firmware to latest available? Even new or very old systems may have updates.
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

Are you dual booting or still have a NTFS partition on drive that has hibernation flag set? Windows fast startup sets hibernation flag & often resets it with updates. Installer then cannot correctly see hibernated partitions.

---

### Post by jebus42 on 2024-07-26
I don't know if this is helpful, but I recently ran into a similar issue while installing Ubuntu 24.04, and the problem was that I needed to boot it in graphics safe mode before the installer would cooperate.

---

### Post by flieps on 2024-07-30
Thank you guys, I will answer and try your suggestions within the next few days.

---

