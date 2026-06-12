---
title: "After upgrade memory sticks/keys not being displayed."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by touchwood on 2007-10-19
Upgraded with only a few minor issues. one that is annoying me is - Memory sticks/keys when inserted appear in /var/log/messages - but I have to manually mount them for every use. They do not appear on the Desktop or in Computer.

Oct 20 13:50:35 laptop kernel: [  744.392000] usb 5-1: configuration #1 chosen from 1 choice
Oct 20 13:50:35 laptop kernel: [  744.392000] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 20 13:50:40 laptop kernel: [  749.392000] scsi 6:0:0:0: Direct-Access     USB 2.0  Flash Disk       5.00 PQ: 0 ANSI: 2
Oct 20 13:50:40 laptop kernel: [  749.392000] sd 6:0:0:0: [sdb] 4091904 512-byte hardware sectors (2095 MB)
Oct 20 13:50:40 laptop kernel: [  749.392000] sd 6:0:0:0: [sdb] Write Protect is off
Oct 20 13:50:40 laptop kernel: [  749.396000] sd 6:0:0:0: [sdb] 4091904 512-byte hardware sectors (2095 MB)
Oct 20 13:50:40 laptop kernel: [  749.396000] sd 6:0:0:0: [sdb] Write Protect is off
Oct 20 13:50:40 laptop kernel: [  749.396000]  sdb: unknown partition table
Oct 20 13:50:40 laptop kernel: [  749.400000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Oct 20 13:50:40 laptop kernel: [  749.400000] sd 6:0:0:0: Attached scsi generic sg2 type 0

---

### Post by touchwood on 2007-10-20
Found that the Haldaemon is missing from the system. I can start it with   /usr/sbin/hald.
Supposed to be started as  /etc/init.d/haldaemon start  looks as though the upgrade wiped that!

---

### Post by touchwood on 2007-10-20
Ok - found that Haldaemon is not starting. It is set to start, it could be starting and then be shut down by some other thread.

So looks as though I will need to insert a script in rc.d

---

