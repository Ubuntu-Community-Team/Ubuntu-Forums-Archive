---
title: "Ubuntu Breezy won't boot after install - SATA/IDE problem?"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by Luuraja on 2006-04-13
Got brand new hard disk - Seagate Barracuda 250GB SerialATA. Installed WinXP on it (don't blame me, I need Adobe Illustrator and some other graphics apps for creativity).

So, the old disk - WD Caviar 80GB IDE decided to use as Linux testing ground, particularily for Ubuntu.

Install process went without errors, but after ejecting CD/reboot there's no sign of grub, just WinXP starts automatically.

Ubuntu partitioner showed my IDE disk as hdb slave. BIOS tells me that both disks are present...PartitionMagic shows linux partitions...

Is there a problem with SATA master and IDE slave disks in same computer for Breezy? Or should I download Dapper (ok, i'm doing it right now, 78 % to go)?

What to do?

---

### Post by waster on 2006-04-13
You need to install GRUB on the boot disk. You could reconfigure your BIOS to boot from the SATA disk, then use chainloader in grub to give youa windows option.

---

### Post by Luuraja on 2006-04-13
BIOS **IS** configured to boot from SATA. Windows is sitting on SATA...

I can't see no grub and can't see any option to find it. WinXP just starts automatically...

Install process says that grub will be installed on Master Boot Record. Maybe Breezy-install can't change  SATA drive's MBR?

Any other advice?

---

### Post by Luuraja on 2006-04-13
Ok, let's see what Dapper Flight 6 has to say on this case.

---

### Post by Luuraja on 2006-04-15
Dapper has'nt anything to tell. Same thing - after install WinXP boots up automatically.

But - it seems to be common problem for Linux'es. 
Installed OpenSuse 10.0 with same issue. 100 points to Suse - I can boot to Suse using 1st installation disk inserted to CD-ROM and in GRAPHICAL mode. Without any problems...

Ugh, searching further... 

P.S. Maybe the problem is in my compu's BIOS. 
Some specs:
Motherboard MSI (Microstar International)-6788 or MSI 848P Neo-V
Intel 848P Chipset
Amibios  - upgraded to last known version.

I have all hard disks set to "Auto"
SATA drive (250GB Seagate) shows as "Third IDE Master" - there are Windows partitions
IDE drive (80GB Western Digital) shows as "Primary IDE Slave" - for linux

---

### Post by tigerstripedcat on 2006-04-15
The problem (I think) is that there is no grub/lilo residing in the master boot record area.  Windows either overwrote this area, or it's defaulting to look at beginning of this drive you just installed windows to.  (this is why it's always, install windows first then linux)   I don't suppose reinstalling linux is an option?  I'm sure there's a way.  Maybe the "upgrade" option of the ubuntu cd (i.e. without formating).

---

### Post by Luuraja on 2006-04-17
Mandriva 2006  asked me during install process where to write bootloader :-D Chose sda (SATA disk)  and it's ok now!
Suse 10.0 write on SATA drive MBR too

Installed Dapper once more - and investigated installation/configuration process thoroghly. There's no option to choose location other than hda or hdb

---

