---
title: "Sizing partitions during installation"
date: 2022-04-06
forum: Installation &amp; Upgrades
---

### Post by pabloamarina95 on 2022-04-06
Good afternoon,

I am trying to install Ubuntu in a laptop, in dual boot mode, to test 5G mobile phone connections between user terminal and base stations.

I have a 16 GB RAM and I've read on the Internet that the recommended size for swap is 4 GB, but in case of hibernation, this should go up to 20 GB.

I'm not sure if I will need hibernation for my purposes, and I wanted to know which size you would take by default so it's easier to resize later.

Thank you!

---

### Post by oldfred on 2022-04-06
Is your question about swap partition?
Default install now is a swap file of 2GB, so no swap partition required.
Some suggest a swap partition of 4GB as being a bit better. 

But with 16GB of RAM, you have to use some pretty large app like video editing that want everything in RAM to use swap. Hibernation is not recommended and with an SSD you can typically boot just about as fast as recovering from hibernation. And often safer to close apps when not using system. If laptop suspend does not use swap but continues to use power as RAM is maintained.

New users are best served with default install which is now just / (root). It will create a swap file and it will use an existing ESP - efi system partition if UEFI. 
If UEFI install to blank drive, you will probably need an ESP (FAT32 with esp, boot flags). 

Installer need a bit more than 4GB, so 8GB flash drive or larger required. It will totally erase flash drive, so do not use a large drive for installer. There are work arounds to use another drive, but those are not standard instructions.

And minimal size of / is 30 to 40GB, but that really only works for system and if your data is tiny or if you have separate /home or data partition(s) for your data. Your data needs determine sizes of partitions and we do not know what you need.

More advanced users with larger Ubuntu installs may want separate /home and/or separate data partitions. Or a shared NTFS data partition if dual booting with Windows.

---

### Post by pabloamarina95 on 2022-04-07
Yeah, sorry. It's about swap. I already edited it.

Thanks for helping.

---

