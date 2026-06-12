---
title: "Alternate install to clean ssd/hdd fails. Grub doesn't install properly"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by Aybara on 2012-04-19
Got my new pc at work today. It was delivered with no OS preinstalled, and with a 240GB SSD, and a 1TB HDD. I installed from the AMD64 Alternate CD, in the following scheme.

HDD (/dev/sda):
Whole disk encrypted, LLVM volume group with swap, /var and an ext4 /data.

SSD (/dev/sdb):
1 GB unencrypted /boot with the boot flag set
The rest of the disk encrypted, LLVM volume group with sysroot (/ and /home) 

The install went well until it installed Grub. It failed writing grub to mbr (it chose /dev/sda). I continued without bootloader, booted into rescue mode, and tried to install grub manually with:

sudo mount /dev/sdb1 /mnt && sudo grub-install --bootdirectory=/mnt /dev/sdb

That threw the error "This GPT partition label has no BIOS Boot Partition". The same error came if I tried /dev/sda.

What's wrong/missing? Should I partition the drives in GParted and do <something> before installing?

---

### Post by Aybara on 2012-04-19
Hmm. Reading the Grub manual (as I should have done before posting), I'm guessing that I should create a dedicated BIOS Boot Partition in the beginning of the SSD.

Edit: And, now that I've read about the BIOS Boot Partition, the error message is quite clear. Sorry for the obvious question.

---

