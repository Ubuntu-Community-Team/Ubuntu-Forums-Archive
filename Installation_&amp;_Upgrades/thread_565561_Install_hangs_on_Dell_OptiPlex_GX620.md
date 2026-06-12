---
title: "Install hangs on Dell OptiPlex GX620"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by tilmaniac on 2007-10-02
Ubuntu install fails on my Dell Optiplex GX620.

The machine has one SATA drive which is detected by the BIOS as SATA-0 (BIOS revision A01).  In the BIOS, SATA operation is set to Normal, not Combination mode.

This same drive shows up just fine when the installer brings up the partitioner.  I then select the "Guided - use entire disk" option since I want Ubuntu to be the only OS on this machine.  

After I click through the rest of the installer the install begins and then hangs at: 
"Starting up the partitioner - Scanning disks..."  It remains hung there indefinitely.

I have tried this with both 7.04 (desktop) and 7.10 beta (desktop) (I'm trying alternate next).

How can I get more information about what is going wrong or otherwise diagnose this problem?   Any tips/pointers/information/advice would be much appreciated!

---

### Post by tgalati4 on 2007-10-02
I successfully installed Dapper 6.06.1 on a GX620, but kept the original Windows XP install.  I simply squeezed the Windows partition to 1/2 the disk and put Ubuntu on the back half.

You might have better luck wiping the disk completely.  Use Darek's Boot and Nuke.  (DBAN).  That way the partitioner will see a clean disk to start with.

The other option is to use gparted and partition the drive from the Live CD--not during the install script.  This gives you a working system and allows you to partition the drive and test the partition by:

>sudo mkfs /dev/sda1

Depending on the size of your disk, you may want multiple partitions so you can load Gutsy when it gets stablized, but have a working Feisty install as well.

Your partitioning scheme will depend on how you will use the machine.  

How long did you wait for the partitioner to scan?  Perhaps it was doing a low-level scan of the drive to ensure partition integrity.  If its a large drive, it might take a while.

---

### Post by tilmaniac on 2007-10-02
I was successfully able to install Ubuntu using the "Alternate" disc.

Thanks for your replies, I'm posting from my new Ubuntu box now!
:KS

---

