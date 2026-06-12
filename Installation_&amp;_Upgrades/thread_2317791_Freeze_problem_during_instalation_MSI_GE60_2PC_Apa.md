---
title: "Freeze problem during instalation MSI GE60 2PC Apache"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by Y.E.S. on 2016-03-19
[COLOR=#111111][FONT=Ubuntu]I have a MSI GE60 2PC Apache and two SSD 120GB + 120GB and one HDD 1TB. I use Win10 on one of the SSD and I want to install Ubuntu 14.04 the other one. However, when I try install ,i think randomly, Ubuntu installation freezing.[/FONT][/COLOR]

[LIST=1]
[*]Disabled Fastboot, IntelSpeed Step and Secure Boot
[*]Enable UEFI with CSM
[*]I'm not sure, but there is no raid options on BIOS and AHCI selected under the SATA mode selection.
[*]1TB HDD is NTFS and i use this part for back up files, film etc. Additionally, all of the SSD and HDD are GPT.
[*]Bios and firmware are updated.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]I tried to install Ubuntu 14.04 on virtual machine and it works without problem.[/FONT][/COLOR]

---

### Post by oldfred on 2016-03-19
Some other MSI threads:

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by Y.E.S. on 2016-03-19
> **oldfred said:**
> Some other MSI threads:

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

Thanks for your reply. I read these topic. I'm not sure how I can add libita.force=noncq. Actually, I tried add it on syslinux.cfg. However, there is no change.

---

### Post by oldfred on 2016-03-20
You can add it like nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
This shows BIOS boot and further down a grub boot after install. If using UEFI, you get grub for both first boot and after install.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Y.E.S. on 2016-03-22
Thank you for your helping. I can solve this my problem with your guidance.

---

