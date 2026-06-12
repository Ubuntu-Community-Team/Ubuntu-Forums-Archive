---
title: "Replacing GRUB in MBR"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Gambler Z on 2007-10-20
I just installed Xubuntu 7.10. Everything works fine, but I installed it on hd1, I thought that it will install GRUB on the same drive, but id did not. So now I have hd0 with windows and GRUB, and hd1 with Xubuntu. Not exactly what I wanted.

Is there any relatively easy way to fix the situation, i.e, to restore windows loader on hd0 and put GRUB on hd1? My goal is to make each physical harddrive independent of another, and to choose which one to load via BIOS.

---

### Post by rsambuca on 2007-10-20
Just plop in the XP installation disc and type "fixmbr" from the command line in the recovery mode.

---

### Post by Gambler Z on 2007-10-20
Sound easy enough, thanks.

But before that, I guess I'll try to copy MBR with dd and see what happens.

---

### Post by poltiser on 2007-10-20
I use Acronis Disk Director - saves time and I can avoid surprises. Grub in Ubuntu always does mistakes and on my 3 drives and 10 partitions I have XP+5 different linuxes for training...
I do always custom partitioning and it works well...
Regards!

---

### Post by Gambler Z on 2007-10-20
The bad news is that dd didn't work, or rather after I copied the boot sector from sda to sdb neither of them booted.

The good news is that fixmbr worked. Nice utility. I didn't know Microsoft CDs have stuff like that.

Okay, I guess I'll have to reinstall Xubuntu now. This time I'll disable windows disk from BIOS so GRUB is installed properly. (Is there any way to actually specify the partition for GRUB?)

---

### Post by rsambuca on 2007-10-20
> **Gambler Z said:**
> The bad news is that dd didn't work, or rather after I copied the boot sector from sda to sdb neither of them booted.

The good news is that fixmbr worked. Nice utility. I didn't know Microsoft CDs have stuff like that.

Okay, I guess I'll have to reinstall Xubuntu now. This time I'll disable windows disk from BIOS so GRUB is installed properly. (Is there any way to actually specify the partition for GRUB?)

You don't have to re-install xubuntu, you can just use a live CD to re-install grub to the location of your choice.

---

