---
title: "OSDisc Xubuntu 14.04 LTS Flash Drive can not run to replace Win 7"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by Brother_Dave on 2014-06-14
I originally had Xubuntu 14.04 beta on sdb drive and Win 7 64bit on C: drive with dual boot grub v2.  When I reinstalled WIN 7, that killed my grub and access to Linux on the sdb 250 GB drive.  Now I want to remove Win 7 and use that 500 GB drive sda for data backup, and use my OSDisk Xubuntu 14.04 LTS to get my Linux 3 partitions on sdb to run again and get upgraded.

I have tried about a dozen times to configure my bios and boot sequences, nothing works to allow the USB flash drive run; as WIN 7 always runs.  Should I get  EaseUS partition manager to wipe out WIN 7 if that will work when EaseUS is also installed in the Win 7 C: main partition?  Or do something else?   Thanks for your help !

I have a Gigabyte Ultra Durable 3 Motherboard GA-MA785GM-UD2H

---

### Post by grahammechanical on 2014-06-14
It should be possible to boot from a USB memory stick. If you erase the Windows partition you will erase Windows 7 and you may find that you still cannot boot from the USB memory stick and now you have a busted machine.

Have you tried looking in the BIOS USB settings? Have you tried accessing the BIOS with the USB memory stick already in the USB port? It then might show up in the BIOS boot section as an external USB drive.

Regards.

---

### Post by Brother_Dave on 2014-06-14
I can't boot from the USB stick so far.

I just thought of a possible easy solution. I will remove the power and data cables from the C: drive having Win 7; and then I should be able to boot to the sdb (D :  drive) having my Linux OS, or boot from the Linux stick, then run Linux and upgrade it, then hook up the C: cables and format away the Win 7. I'll try that tomorrow, unless someone on here has a better way to fix it.

---

### Post by Brother_Dave on 2014-06-15
Removing  just the power plug on my C: drive with WIN 7 on it, booting up my computer (without the USB stick) worked ! The GRUB boot menu came up, and I went into Xubuntu 14.04 LTS Great !  Then I ran all the software updates.   However, then plugging live the power plug into my C: drive, it didn't show up in this Linux running. I think I will have to change the master and slave jumpers on those two drives.  Until I can run Gparted ( or something else ? ) to remove WIN 7, I should not boot up with both drives configured and running, or WIN 7 will again take over !  What should I now do?  Thanks for your help !

---

