---
title: "Getting GRUB on external HDD"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Hologide on 2010-01-08
Hi all,

I had a problem a week or so ago installing Ubuntu - the OS went on the external HDD but GRUB went on my internal HDD rendering me unable to boot Vista or Ubuntu. I rescued the situation using the vista disc to put the original boot loader back on the internal HDD and then sorta gave up :(

So I'm ready ti give it another go but I'd rather avoid the stress of the original situation. I'm guessing I'll have to re-format the Ubuntu partition of the external HDD to re-install, but how can I be absolutely sure to make sure GRUB goes onto the external HDD and stays away from the internal HDD?

Would it be safe to remove my internal HDD during installation, or would that be unnecessary?

Thanks!

---

### Post by darkod on 2010-01-08
No need to reinstall ubuntu and no need to disconnect int hdd, not right now.
Boot with ubuntu cd, Try Ubuntu option, and follow the instructions to reinstall grub2 for 9.10 from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

As per the instructions, depending of the results fdisk gives you, and under the assumption your ext hdd will be /dev/sdb, the commnds to reinstall grub2 would be something like:
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

In the above commands replace /dev/sdb1 with the ubuntu partition, and /dev/sdb with the ext hdd device name, depending on your fdisk results.
If unsure, post the fdisk results here before reinstalling grub.

PS. After this don't forget you will need to set the USB device as first in BIOS boot order, or BIOS will just boot vista straight away from the int hdd.

---

