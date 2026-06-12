---
title: "Grub broken"
date: 2022-02-21
forum: Installation &amp; Upgrades
---

### Post by stubor2796 on 2022-02-21
pastbin,ubuntu,com/p/YdmRmSx2QX

- Windows update trashed dual boot setup and Outlook 2016
- Boot Repair Disk only offers to scan and summarize; no recommended repair option

Am I going to have to re-install Linux?

Thank you for your help.

---

### Post by tea for one on 2022-02-21
[COLOR="#0000FF"]Line 66[/COLOR] - 1 OS detected 
[COLOR="#0000FF"]Line 68[/COLOR] - OS#1:   Windows 8 or 10 on sda3

[COLOR="#0000FF"]Lines 185 - 188[/COLOR] - 4 partitons found but no sign of a Linux file system.

What actually happened?
A bit unusual for a Windows update to delete partitions?

---

### Post by oldfred on 2022-02-21
Did you do a Windows restore, not a Windows update?
A restore with some systems, puts it back to the way it was when new. It may or may not save some of you data or configuration.
Every vendor seems to do it a bit different.

Your ESP - efi system partition shows a partition 5 that does not exist. And you still have a  UEFI boot entry for Ubuntu which uses the entry in the ESP. Those would not have been updated with a system restore.

---

### Post by stubor2796 on 2022-02-21
I'm assuming as a coincidence seems unlikely, following a routine update for Windows 10, KBxxxx3057, Outlook 2016 won't load due to no connection; perhaps an Autodiscover issue. Of more concern, upon reboot Grub drops to recovery mode. I can exit and Windows continues to boot. I tried BootRepairDisk but only scan and summary is offered, no recommended repair. This is with UEFI enabled and disabled. Thank you for your interest.

BootRepair image: [https://www.dropbox.com/s/k2bt1xx2scaz8q6/Screenshot%20from%202022-02-21%2019-20-02.png?dl=0](https://www.dropbox.com/s/k2bt1xx2scaz8q6/Screenshot%20from%202022-02-21%2019-20-02.png?dl=0)

---

### Post by stubor2796 on 2022-02-21
Opps, I failed to answer your question. No to Windows restore, it is working fine except for Outlook; curious that, Mail works fine.

---

### Post by oldfred on 2022-02-21
There is nothing to repair, as you have no Linux partition.
That used to be an issue with BIOS/MBR installs & Windows updates forgetting to write the Linux partition back into partition table. That then space for partition was there & could be restored.
You show no space, just NTFS partitions.

---

### Post by stubor2796 on 2022-02-21
Thank you, I finally understood what you were telling me. I am reinstalling Linux. I appreciate your assistance.

---

