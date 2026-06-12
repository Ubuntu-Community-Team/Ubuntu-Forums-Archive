---
title: "Ubuntu Server 9.04 Will Not Boot on DFI LAN Party JR X58-T3H6 Mobo"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by ironmonkee1 on 2010-03-05
I will try to be brief.
 
I am currently trying to make my current desktop system into a new server to replace my old server.  I recently installed a second 1 TB SATA drive on the motherboard to run in a RAID 0 array for media with a 2.5" 60 GB SATA drive from my PS3 as the OS drive.  I formatted all drives with GParted, set up the two 1 TB SATA drives in a RAID 0 using the built in Intel Matrix RAID BIOS, and ran the Ubuntu 9.04 x64 install CD.  The CD detected the raid array and the 60 GB drive.  I mounted root and /swap on the 60 GB drive and mounted /home on the RAID array.  The install process went through with out any issues after that.  Upon ejecting the disk and rebooting, the system tried to boot from my DVD-ROM drive.  It did not try to boot from any hard drives installed.  I tried moving the RAID to a SATA card that I borrowed from a friend and the installer did not detect them.  I also tried moving the OS drive to the SATA card and the same thing occurred.  I then tried installing everything to the RAID array, foregoing an OS drive.  The same thing also occurred.  I then went into the BIOS and set the SATA behavior from RAID to ACPI (or is it AHPI?) and it still will not boot.  The only thing I have not tried is to install the OS to an IDE drive and replace my SATA DVD drive with an IDE one so that only the two 1 TB HDDs are on the onboard SATA ports.  If anyone has some insight or other ideas that I have not thought of, please feel free to comment.  Thanks in advance for any assistance.
 
Here are the current system specs if you need them
[LIST]
[*]Intel i7 920
[*]6 GB DDR3 1333 RAM
[*]2 X 1 TB SATA HDD
[*]1 X 60 GB SATA HDD
[*]DFI LAN Party JR X58-T3H6 Mobo
[/LIST]

---

### Post by ironmonkee1 on 2010-03-05
Bump.

---

### Post by ironmonkee1 on 2010-03-06
Issue resolved by installing OS on a separate IDE drive.

---

