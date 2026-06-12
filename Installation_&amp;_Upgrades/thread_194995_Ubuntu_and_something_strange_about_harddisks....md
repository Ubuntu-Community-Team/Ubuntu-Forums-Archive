---
title: "Ubuntu and something strange about harddisks..."
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by wezzer on 2006-06-12
Hi there,

Fresh Dapper-AMD64 installed to harddrive /dev/hda1 and 1 GB swap located in /dev/hda2. The problem is that there are 4 more harddisk, some of them are IDE and some are SATA, but the problem is same - ubuntu does count the available free space in some very odd way... Take a look what the command "df -h" returns...
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             146G   52G   87G  38% /
varrun                503M   84K  503M   1% /var/run
varlock               503M  4.0K  503M   1% /var/lock
udev                  503M  140K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   22M  482M   5% /lib/modules/2.6.15-23-amd64-generic/volatile
/dev/sda1             294G  256G   23G  92% /home/eezee/storage-1
/dev/hdb1             147G  129M  140G   1% /home/eezee/storage-2
/dev/hdd1             147G  129M  140G   1% /home/eezee/storage-3
/dev/sdb1             294G  129M  279G   1% /home/eezee/storage-4

```
Tell me, how come this can be true 147 GB - 129MB = 140 GB? and what comes to /dev/sda1 and /dev/sdb1 there is missing even more free space! What on earth could cause this?

---

### Post by wezzer on 2006-06-12
Thanks to guys in #ubuntu irc-channel, this "problem" was solved in less than 1 minute. Ext2/3 reserves 5% to handle file fragmentation was the solution. It can be turned off, but I think I'll leave it on...

---

