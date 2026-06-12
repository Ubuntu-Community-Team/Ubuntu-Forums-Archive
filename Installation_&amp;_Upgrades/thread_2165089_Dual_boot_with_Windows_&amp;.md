---
title: "Dual boot with Windows &amp;"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by colin_turner2 on 2013-08-03
I am currently running Windows 7 and have decided to try Ubuntu 13.04. I made space available on my hard disk and booted from the installation DVD. I said I wanted to install Ubuntu alongside Windows. Everything appeared to go well. At the end of the process the DVD is ejected, the screen changes to black and displays text along the line of "closing all running tasks" (can't remember exactly. It then just sits at this stage and does not progress further. If I press any key the PC turns off. When I restart the PC it boots directly into Windows. If I check in Windows Disk Management it shows what was unformatted space is now Healthy (Primary Partition). Under Windows Startup and Recovery there is no mention of Ubuntu. Any ideas?

---

### Post by oldfred on 2013-08-04
Windows does not see Linux partitions, so from Windows you will not see anything. Did you install the grub2 boot loader to sda, or do you have an UEFI system?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by surf223 on 2013-08-04
Use a tool to look and see if there is a linux partion. Use ext2fsd and you should be able to tell if there is anything there or not.

---

### Post by colin_turner2 on 2013-08-06
The boot-info report  URL is paste.ubuntu.com/5955723

---

### Post by oldfred on 2013-08-06
You must have had sdb set as BIOS boot device when you installed Windows. Your install is in sda1, but Windows put its boot partition in sdb1. Normally that is on the same drive.

You have Windows boot loader in the MBR of sdb, which should boot Windows and have grub installed to the MBR of sda. Have you changed BIOS to boot from sda? Or try with one time boot key (f12 on my system).

Since you have two large drives I might have installed Windows on one drive and Ubuntu on the other drive.

---

### Post by colin_turner2 on 2013-08-09
Started again and installed Ubuntu on a separat disc. All appears to be working now. Thanks for the help.:D

---

