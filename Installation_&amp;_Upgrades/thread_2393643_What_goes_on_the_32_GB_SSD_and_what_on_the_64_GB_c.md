---
title: "What goes on the 32 GB SSD and what on the 64 GB card?"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2018-06-06
I have a new netbook, a Lenovo 110s running Xubuntu 18.04.
It has a 32 GB SSD and no HD.
I am getting a 64 GB micro SD U3 card to act as a HD.

How should I set up the 2 devices? What goes on the SSD and what on the card?
I imagine I keep the system on the SSD.
But what about Home? And Usr? Var?
And will the the swap file be a problem?

Advice welcome

---

### Post by sudodus on 2018-06-06
If you do not store personal data [files] in you home directory, but in a data directory in a data partition on the SD card, it will be OK to have the whole 'system' in the 32 GB SSD (including /home and /usr and /var).

If you wish, you can put /home in a partition with the ext4 file system on the SD card and add a line for it in /etc/fstab, but I would not do it. I prefer using a separate data partition (in a HDD in my case), and I have added a line for my data partition in /etc/fstab. This makes it possible to have separate and straightforward backup strategies for the system and for the personal data files.

Edit:

Please notice that SD cards can easily be corrupted. They are not as rugged as HDD drives and SSDs concerning wear and corruption due to internal management of memory cells. SD cards are also much slower. For these reasons they are not suitable for system tasks, but can be good for storage, which does not mean too much repeated write operations.

Backup is recommended anyway - things can fail without a warning.

---

### Post by oldfred on 2018-06-06
Another user with that system.
       Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by hans12345 on 2018-06-07
Thanks Sudodus, this is good advice.

And an extra thanks to OldFred, who has been helping me on and off for many years.

---

