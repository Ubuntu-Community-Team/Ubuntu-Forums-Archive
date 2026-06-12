---
title: "Ubuntu 12.04 install ...Select proper Bood device..."
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by rupert160 on 2012-05-05
Boot* sorry the heading should sy Select proper boot device, dammit...

I'm hoping this is the right forum, might be more of a manufacturer question though:

I've recently purchased an 
i7-3770 with a 
Gigabyte GA-Z77X-D3H MB, 
 
the chipset has
2xSATA3(ports #0 #1) and 
4xSATA2 (ports #2,#3,#4,#5)
(There's a note that port #5 is switched off when mSATA is in operation)
My 3 drives are SATA2 - and given SATA3 is backwards compatible with SATA2 the drive setup is as follows:
#0 - Seagate ST3500413AS (500GB HDD) "/home"
#1 - Seagate ST3500413AS (500GB HDD) "/home_bkp"
#2 - Kingston SV100 (64GB SSD) "/" boot flag "on" contains boot loader
#3 - Pioneer DVD-RW ATAPI

I complete the UBUNTU 12.04 install process and check the BIOS points to the Kingston for my OS and I get the error:[FONT="Courier New"]
Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key[/FONT]

My original build did try to install this all on BTRFS however due to the failure I have changed it all back the EXT4 with and rebuild of the MBR on all drives. Still no joy. I've switch between AHCI IDE and RAID, no help either. The BIOS can see all drives and all are "healthy".

Ideas anyone?

---

### Post by darkod on 2012-05-05
Are you sure the bootloader is on the kingston? Have you tried booting from the seagates?

For many details about your setup you can download and run the boot info script from the link in my signature. You can do all that from live mode.

Post the results as explained there if you have any questions. We can check if the setup is OK.

PS. Keep the sata mode on AHCI.

---

