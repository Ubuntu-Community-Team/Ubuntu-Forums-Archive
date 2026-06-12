---
title: "Want to migrate my SSD w/ Ubuntu /home folder to a new system"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by remn on 2013-10-16
So the screen on my old laptop died and I want to move the SSD from it to the new (to me) computer I just bought. I just want to make sure my plan will work. I was running 12.04 on the old computer, and set it up with separate root and home partitions for just this type of situation. I want to pop the SSD into the new computer, install 13.04 and just keep using the same /home folder. This will work, right? 

Also I forget which file system to use for the root drive. Should I go with EXT4 or FAT32?

---

### Post by papibe on 2013-10-16
Hi remn.
> **remn said:**
> This will work, right?
Yes.

Another option that requires a little bit of work, is to recover your whole system, as it was, on the new machine. Let us know if you want to know more about that option.
> **remn said:**
> Should I go with EXT4 or FAT32?
Ext4 would be a fine option. BTW, FAT32 won't even work ;) on a root partition.

Regards.

---

### Post by heir4c on 2013-10-16
Even without install 13.04 the system will work. I moved a HD from a Acer Aspire Laptop to a (secondhand made) desktop, and it work without any configuration.

---

### Post by remn on 2013-10-17
Thanks for the replies. I'm surprised to hear it's possible to just switch the drive to a new machine and go. Either way I'm planning on switching from 12.04 to 13.04, so I'll just do a fresh install.

---

### Post by mörgæs on 2013-10-17
> **remn said:**
> Thanks for the replies. I'm surprised to hear it's possible to just switch the drive to a new machine and go. 

This is free software. There's no need to apply artificial hindrances like 'if the operative system senses that it is moved to bigger hardware it should freeze until given a new license file'.

Moving a hard disk is a good general solution for getting a new system working even when USB and / or CD drives are dead.

Please mark the thread 'solved' if you are good to go.

---

