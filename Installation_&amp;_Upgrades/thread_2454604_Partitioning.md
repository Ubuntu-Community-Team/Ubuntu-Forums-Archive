---
title: "Partitioning"
date: 2020-12-02
forum: Installation &amp; Upgrades
---

### Post by tqtim on 2020-12-02
Ubuntu 20.04.1 LTS

Here's the fdisk -l output:

Disk /dev/sda: 298.9 GiB, 320072933376 bytes, 625142448 sectors
Disk model: WDC WD3200BEVT-6
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xed9293e1

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 468685278 468683231 223.5G 83 Linux
/dev/sda2       468686848 469735423   1048576   512M  b W95 FAT32
/dev/sda3       469737470 625141759 155404290  74.1G  5 Extended
/dev/sda5       469737472 625141759 155404288  74.1G 83 Linux


I created an additional partition for a second version of ubuntu. I had a 20.04 fresh install (default boot) on the new plus an earlier 18.04.

I now want to go back to whatever the default settings were. I don't know which partition has which version so which one to delete, then resize the other?

As I now just want a single 20.04 OS I don't care if I start completely fresh, can the installation from USB sort out the partitions? I've no idea if the above fdisk output is normal. Just read  *How to correctly partition ubuntu* which says sda/1 doesn't need to be more that 100Mb, not my 223.5Gb?

If you need to know why I did the above it's because an update to 18.04 in early September killed my wireless mouse, touchpad and keyboard. I created the 20.04 partition to test out some suggested cures, none worked. An update today has now sorted that problem.

Thanks
Tim

---

### Post by crip720 on 2020-12-02
Don't count on sda(x).  The 100MB partition they talking about is your sda2(512MB) which okay and does not need changing.  If installing 20.04, the easiest way would be to use erase disk and install  option.  No worries except data would be lost.  Will install Ubuntu using the whole disk.  Backup all data before doing this, if wanting to save any.

---

### Post by tea for one on 2020-12-02
> **tqtim said:**
> 
As I now just want a single 20.04 OS I don't care if I start completely fresh, can the installation from USB sort out the partitions? 

I think that you have already answered your own question.

Back up your data.
Prepare your USB device.
Boot in [COLOR="#0000FF"]UEFI[/COLOR] mode.
Let the Ubuntu installer automatically organise the partitions.
Reboot and check that you are satisfied.
Restore your data when ready.

Happy days.

---

### Post by TheFu on 2020-12-02
If you boot into either Ubuntu and run this command, you'll be able to tell which OS is using which partition:

```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

Most of that command is to hide fake-storage.
So, if you know which OS release (18.04 or 20.04) you are running, then that partition will be mounted on /
The other one will be for the other OS and probably won't be mounted - but it might. If it is, you can go look at the /etc/lsb-release file to see which OS it is.  Of course, that lsb-release file will be relative to the other mounted storage.

---

### Post by tqtim on 2020-12-03
Thanks, all sorted now.
Tim

---

