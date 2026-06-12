---
title: "Problem with SATA drive"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by EBrown on 2008-01-09
I'm having some troubles getting Ubuntu to recognize my second SATA disk.

I have a Dell SC440 machine with 1 GB of RAM & 2 SATA drives - 1 80 GB, and another 160 GB.

When I try to partition the 160 GB drive, the partition editor tells me I need to write a disklabel; when it tries to write the disklabel, however, it fails (and then the partition editor crashes).

I am running Ubuntu 7.10 AMD64 live DVD; booting the x86 live CD doesn't make any difference.

The system log looks like this:
Jan  8 07:11:28 ubuntu syslogd 1.4.1#21ubuntu3: restart.
Jan  8 07:11:29 ubuntu kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan  8 07:11:29 ubuntu kernel: Loaded 26084 symbols from /boot/System.map-2.6.22-14-generic.
Jan  8 07:11:29 ubuntu kernel: Symbols match kernel version 2.6.22.
Jan  8 07:11:29 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Jan  8 07:11:29 ubuntu kernel: 4.613693] ata3.00: configured for UDMA/33
Jan  8 07:11:29 ubuntu kernel: [   94.613699] ata3: EH complete
Jan  8 07:11:29 ubuntu kernel: [   94.613984] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan  8 07:11:29 ubuntu kernel: [   94.613988] ata3.00: (BMDMA stat 0x25)
Jan  8 07:11:29 ubuntu kernel: [   94.613994] ata3.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jan  8 07:11:29 ubuntu kernel: [   94.613996]          res 51/04:08:00:00:00/04:00:13:00:00/e0 Emask 0x1 (device error)

There are several repetitions of the text starting with ata3.00: configured for UDMA/33 - then this shows up:

Jan  8 07:11:29 ubuntu kernel: [   94.775655] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan  8 07:11:29 ubuntu kernel: [   94.775660] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Jan  8 07:11:29 ubuntu kernel: [   94.775665] Descriptor sense data with sense descriptors (in hex):
Jan  8 07:11:29 ubuntu kernel: [   94.775668]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan  8 07:11:29 ubuntu kernel: [   94.775678]         00 00 00 00 
Jan  8 07:11:29 ubuntu kernel: [   94.775682] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
Jan  8 07:11:29 ubuntu kernel: [   94.775689] end_request: I/O error, dev sda, sector 0
Jan  8 07:11:29 ubuntu kernel: [   94.775698] ata3: EH complete
Jan  8 07:11:29 ubuntu kernel: [   94.775792] sd 2:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
Jan  8 07:11:29 ubuntu kernel: [   94.776026] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan  8 07:11:29 ubuntu kernel: [   94.776030] ata3.00: (BMDMA stat 0x25)
Jan  8 07:11:29 ubuntu kernel: [   94.776036] ata3.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jan  8 07:11:29 ubuntu kernel: [   94.776039]          res 51/04:08:00:00:00/04:00:13:00:00/e0 Emask 0x1 (device error)

I have several of these 160 GB disks, and the same error occurs on every drive I've tried.  I don't believe that the disks are bad, as they pass several diagnostic tests.

Any help would be welcome.

---

### Post by Shotgun25 on 2008-01-09
Please post if you are using the partition editor that comes with the live cd, or if you have tried any alternatives (presuming your internet connection is available using the live CD).

If you have the internet accessible, then maybe you could drop to the terminal and apt-get update and see if it grabs any GParted bugfixes.

Looking at the specifications for your server you are fine up to 2TB of Sata drives which is nice :)

EDIT
If the application is not available for any reason, test to see if it is by following these steps to attempt an installation of GParted [http://www.ubuntux.org/how-to-install-partition-editor-gparted](http://www.ubuntux.org/how-to-install-partition-editor-gparted)
END EDIT

---

### Post by EBrown on 2008-01-09
I've tried a number of different schemes, none of which work (different Linux distros, a spare Windows install).

I did run some diagnostics from the Ultimate Boot CD that might indicate the problem; according to the diagnostics, the disk is password protected (which is odd, since I didn't remember doing that, but the controller might have done so behind my back).

Unfortunately, while this might indicate the problem, it doesn't get me any nearer to a solution, as I can't find any (free or reasonably priced) utilities to reset the password on a SATA disk.  

I **can** find utlities to reset the password on a PATA disk, but the utlility dates from 2001 and doesn't seem to have been updated since then.  (The utility, incidentally, doesn't work on my SATA disk.)

---

### Post by Shotgun25 on 2008-01-31
Hi,

I just noticed that you have a dell machine.

Having recently acquired a dell machine myself, I noticed the bios is admin password protected.
During my research on how to remove the bios password I found that the hard drive can also be password protected in the same way.

This website, [http://www.download.centre4service.com/software1.html]("http://www.download.centre4service.com/software1.html"), has tools to remove the password from the bios for you.

The iso for burning a cd is found at [http://www.download.centre4service.com/DSTCD.rar]("http://www.download.centre4service.com/DSTCD.rar")

The password for the zip files (if any are protected) is 'smellyalater' (no quotes) as mentioned (on post number 7) here [http://www.techspot.com/vb/post558517-7.html]("http://www.techspot.com/vb/post558517-7.html")

Go into bios, write down the dell service tag(s).
Burn the iso, set the cd to be booted from first, follow the dell service reset tool,You will need your original dell service tag for entry when finishing up running the program.

The above steps are not very comprehensive but once I found the tool and burned it I had an operational bios within 2 minutes of booting.

Removing the admin service password should allow you the rights to remove any other passwords via the bios if still set.

Hope this helps other dell owners....as far as I am aware this software is generic for all dell laptop bios password resets.
FYI, I used it on a Dell Latitude D600.

---

