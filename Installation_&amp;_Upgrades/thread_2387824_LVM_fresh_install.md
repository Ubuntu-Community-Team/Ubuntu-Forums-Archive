---
title: "LVM fresh install"
date: 2018-03-24
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2018-03-24
I will be installing at least two linux versions on fresh with UEFI. (PS, Any point to have UEFI if linux only system?)
If I want to be able to easily snapshot and save installs/images I read to use LVM. How would this occur?
How would this setup with LVM be initiated when I first install Ubuntu 16.04? ubuntu/ centos/ swap/ data/

---

### Post by TheFu on 2018-03-24
UEFI is a best practice for Linux security according to TLF - [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

Snapshots probably don't work the way you think they do.  They prevent storage blocks from being modified. That means any changes to the data in those blocks will eat new blocks.  How you choose to "save installs/images" is something outside using an LVM snapshot.  Snapshots **are** very helpful in getting that data to be static as you backup what you want, but they don't protect against data corruption or disk failures. [https://askubuntu.com/questions/930803/lvm-snapshot-tutorial-on-ubuntu-server/930810#930810](https://askubuntu.com/questions/930803/lvm-snapshot-tutorial-on-ubuntu-server/930810#930810) might be helpful in more understanding.  There is also an LVM example ... how-to : [https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots) - LVM works the same across all Linuxen.

Nothing replaces good, versioned, automatic, backups.

I haven't dual-booted OSes in over 10 yrs, so can't really speak to those needs. I've found that using virtual machines works for those sorts of requirements since the Core2Duo CPU was released.

---

### Post by Dennis N on 2018-03-24
"Snapshots" in LVM are an ongoing process after they are initiated. After initiation, sectors that are modified are saved to the snapshot so that they can be restored if necessary. Sectors that are never modified are not part of the snapshot. If a sector is modified twice, only the original is in the snapshot, not the previous version. LVM snapshot is therefore not a good backup, since unmodified sectors are not in the snapshot - they have only the one original copy on the disk.

That said, I use LVM for installing whenever possible - it can help make some otherwise difficult problems easy to deal with. 

I always use UEFI on computers that support it. UEFI makes multiboot much easier to have a maintenance-free multiboot system - for some OS, I think it is the only way to incorporate them into a maintenance-free setup. Fedora comes to mind. There is an long thread on this forum that was active a while back that exhaustively discussed this.

---

