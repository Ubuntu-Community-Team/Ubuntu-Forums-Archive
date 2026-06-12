---
title: "[SOLVED] Recover 8.04 / deleted partition,"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by cecida on 2008-09-10
Hi folks,

I dual boot XP and Ubuntu. I recently upgraded to 8.04 from 7.10. As I needed more space (the joys of installing open source software!) I booted into Windows, and removed an old Windows partition (not the OS partition, just a data disk). I also removed what I thought was the 7.10 partition. I did not format it, just deleted the partition. I then restarted the computer to find a Grub 22 error. I fixed the grub partition using the live cd, but when I rebooted I found that the only entries were for 7.10 and XP, not 8.04! I deleted the wrong partition.

Is there anyway for me to recover the 8.04 partition? Can I "put back" the ext2 or ext3 filesystem on what is now freespace, and then set grub to boot from that? I did not format/resize the partition. I have looked at fdisk but am not comfortable with using its more advanced features.

So as it stands:

Have a working XP installation.
Have a working 7.10 installation.
Have freespace at the end of the drive which used to hold my 8.04 installation.
A great desire to be able to recover this partition as ext2/ext3 (whichever Ubuntu 8.04 uses by default) and eventually boot from this.

Any help or advice would be greatly appreciated.

D

---

### Post by cecida on 2008-09-10
Folks,

I resolved this issue. I used an application called testdisk to scan the hardrive and recover the lost partition. When I rebooted 7.10 I was able to see the 8.04 partition. I then used grub to set the boot to the new partition. Rebooted and 8.04 was listed as a choice. Am now back in!

Thanks.

---

