---
title: "Replacing a system hard drive in 16.04.6-LTS"
date: 2020-02-04
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2020-02-04
My Hot Rod gPC™ is getting temperamental as of January 2020.  All three Toshiba® MQ01ABD050's (500 GB per each) on GIGABYTE® GA-A78GM-S2HP v2.0 ports SATA1 through SATA3 are as consistent as the day they were installed.  But on cold power-up, the Western Digital® WD1600JS-55NCB1 (160 GB; on GA-A78GM-S2HP v2.0 port SATA0) that holds /boot, root, /srv, and an 8.2GB swap partition  has been reporting to the CPU inconsistently, meaning imminent failure.  As of 4 February 2020 I have purchased a brand-new Western Digital® WD5000LPCX-22VHAT1 to replace the failing WD1600JS.  I also installed a Seagate® ST380215A E-IDE HDD (80 GB) on port IDE0 as master; the TSST Corporation SH-S182D optical drive is slave on the same port.

The rub is, GA-MA78GM-S2HP v2.0 BIOS F6D does not consistently treat ports SATA4 and SATA5 as intel® Advanced Host Controller Interface on self-test even with the Setup configuration of (SATA0-3) AHCI and (SATA4-5) As SATA0-3.  I anticipate needing the ST380215A as a temporary System drive for formatting the WD5000LPCX and DD'ing Paritions 1, 5, 6, and 7 from the WD1600JS to the WD5000LPCX.  How does one go about the necessary procedures?

---

### Post by TheFu on 2020-02-05
Use UUIDs in the fstab.
**blkid** will show the UUID to device mapping. Those can change at every boot, but the UUID doesn't change.
Use **ddrescue**, not dd.  ddrescue will continue after failures.  Or use **fsarchiver** which can be smarter or just use rsync for all the partitions. This way resizing can happen BEFORE moving data. Something to consider.  Plus, rsync won't copy enpty space.  When complete, do a **grub-install** and **update-grub**. This assumes no UEFI involved.

For doing all the work, boot from a *Try Ubuntu* setup/disc/flash drive.
Don't forget to fix the fstab.

---

### Post by bcschmerker on 2020-02-05
**As it turns out, the BIOS *did* cooperate;** but ddrescue failed me writing the old data to the new WD5000 - the target data was garbled in the attempt to clone /srv and several critical settings files pointed to the WD1600 in ways I could not correct.  I ended up reinstalling 16.04.6-LTS, saving the BTrFS home partition and re-formatting the balance of the ext4 partitions (with /boot as ext2) after copying the accessible parts of /home to the PATA Seagate as a hedge against overwrite.

---

### Post by TheFu on 2020-02-05
Be very careful using BTRFS.

---

