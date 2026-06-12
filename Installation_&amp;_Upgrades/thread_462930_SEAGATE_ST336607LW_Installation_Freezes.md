---
title: "SEAGATE ST336607LW Installation Freezes"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by shashank314 on 2007-06-03
Hi,
I am trying to install ubuntu on my HCL infiniti global series workstation with two SEAGATE ST336607LW Hard disks. I tried alternate installation CD for 6.10 as well as 7.04. For both the CD's the "Installing the base system" step is very slow and gets stuck at various places. Infact at the 69% stage it got stuck for about 12 hours. I tried giving the option ide=nodma and acpi=off  and also tried installing in the command line mode but the situation does not change. Can anybody suggest what might be the problem with the system and a workaround.
Thanks in advance.

---

### Post by wpshooter on 2007-06-03
Did you burn the CD at 4X or slower ?

Did you do a Sumcheck to verify the integrity of the CD ?

---

### Post by shashank314 on 2007-06-03
I burned the cd at 24x but I did the check cd for defects. I dont think it is a problem with the CD. I tried three different CD: ubuntu 6.10, Xubuntu 6.10 alternate and Xubuntu 7.10 alternate. It is very improbable that 3 CD's would have the same problem.

---

### Post by shashank314 on 2007-06-03
I pressed ctrl+alt+F4 when the installion is stuck and there was a repitition of block of the form pasted below.
Maybe it would throw some light on what the problem might be

jun   3 19:54:30 kernal: [9769.722559] mptscsih: ioc1: attempting task abort! sc
=f21cf800)
jun   3 19:54:30 kernal: [9769.722559] sd 5:0:0:0:
jun   3 19:54:30 kernal: 00 00 00 00 00 00
jun   3 19:54:30 kernal: [9769.722559] mptbase: ioc1: IOCStatus(0x0048):SCSI Tas
k Terminated
jun   3 19:54:30 kernal: [9769.722559] mptscsih: ioc1: task abort: SUCCESS (sc=f6d5cb00)

---

