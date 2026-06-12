---
title: "Kernel errors after upgrading from Edgy to Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by brdhse1 on 2007-04-21
I just upgraded from Edgy to Feisty using the Update Manager.  After upgrading my Terminal windows are flooded with these messages from syslogd:

Apr 21 07:38:40 jcomputer kernel: [35273.930290] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:41 jcomputer kernel: [35274.930089] EDAC MC0: UE page 0x1fffc, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Apr 21 07:38:42 jcomputer kernel: [35275.929888] EDAC MC0: UE page 0x1fff0, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

I get one message every second.  I suspect this has something to with my motherboard, an ASUS p4c800-Deluxe, as it uses an Intel 875p chipset.

Has anyone seen these messages?  Do you know how to fix it?

Cheers,
Jacob

---

### Post by bdowd on 2007-04-21
I have the same error except that this was on a blank install (on a machine which had previously run 6.10. The MB speaker is beeping each and every second. It stopped when I re-booted my computer, but syslogd is announcing the error occurs every second which is apparent when the console (within the GUI) is opened ... making it most useless. 
EDAC MC0: UE page 0x1f908, offset 0x0, grain 4096, row 0, labels ":": i82875p UE
Funny thing: P4C800 Motherboard from ASUS :-(

---

### Post by bdowd on 2007-04-24
:) Solution --> You have to disable the Error Correcting Memory (ECC-DRAM) in your system. Just go into the BIOS. Choose "Advanced", "Chipset", "DRAM ECC Capability" and set it to "Disabled". Hopefully the next kernel will have this problem fixed as it has been in and out of the source code since the Dapper betas. They did fix it in the released Dapper, though.

---

### Post by brdhse1 on 2007-04-24
Thanks for the solution.  I'd prefer not to have to disable ECC, hopefully this is a short term bug.

---

