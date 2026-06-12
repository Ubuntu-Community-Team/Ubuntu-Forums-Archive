---
title: "Adding mirror to Ubuntu 20.04 ZFS install"
date: 2020-07-07
forum: Installation &amp; Upgrades
---

### Post by gourmetsaint on 2020-07-07
I think I have this but am interested in your feedback. Newbie here. Aim was to add mirror to bpool and rpool so as not to brak the snapshotting system used by Ubuntu.

Note: I didn't use the by-id for the drives as the original ubuntu zfs install didn't and the attach was simpler/worked...

I've tested this in a Hyper-V VM in preparation for migrating my home server once LSI HBA controller arrives and is flashed:

1. Created 11 VHDX drives to match my target Dell T620 environment. 2 x 127Gb on SSD (sda, sdb), 8 x 64Gb (sdc-sdj) to match my 6 x 4Tb SAS and 2 x 4Tb SATA HDDs and a 64Gb (sdk) on SSD to match a SATA SSD I also have in the system (currently used for Dell Cachecade).
2. Spooled up VM with the 11 drives attached and installed Ubuntu 20.04 Desktop using ZFS on sda
3. After reboot, copied sda partitions to sdb using sfdisk ([COLOR=#000000][FONT=&amp]sfdisk -d /dev/sda > partitions.txt, [/FONT][/COLOR][COLOR=#000000][FONT=&amp]sfdisk /dev/sdb < partitions.txt).[/FONT][/COLOR] sda1=EFI, sda2=swap, sda3=boot, sda4=root.
4. Added relevant sbb partitions as mirror to both bpool and rpool (zpool attach bpool /dev/sda3 /dev/sdb3, zpool attach rpool /dev/sda4 /dev/sdb4). zpool status showing all good.
5. Created dpool with 6 drives (sdc-sdh) to simulate my 6 sas drives using raidz2
6. Added last SSD drive (sdk) as cache for dpool (zfs add dpool cache /dev/sdk). Checked with zpool status again - all good
7. Created tpool with last two drives (sdi-sdj) to simulate by two SATA drives I use for temp storage. Status ok.
8. Created two datasets on dpool and one on tpool with mounting point under /mnt (eg zfs add -o mountpoint=/mnt/zfs-fs-01 dpool/zfs-fs-01)
9. Configured smb.conf for three shares pointing at the two datasets and fixed chown and chmod.
10. All shares successfully accessed from windows workstations on network

Have I missed anything? Feedback?

---

### Post by gourmetsaint on 2020-07-14
No feedback guys?

I believe I can change the drive references in the pool by using the export/import method? that seemed to work by cannot do that with bpool and rpool on the running system?

Waiting for my delivery of LSI IT mode controller before doing this for real....

---

