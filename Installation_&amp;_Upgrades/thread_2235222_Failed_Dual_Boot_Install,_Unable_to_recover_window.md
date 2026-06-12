---
title: "Failed Dual Boot Install, Unable to recover windows."
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by hjjr15 on 2014-07-19
After installing Ubuntu 14.04 I can no longer access windows 7 that i had already installed. Boot-repair won't work, and neither will a windows recovery disc. I know the partition is still there as Gparted shows it, but the filesystem appears as unknown and my attempts to get grub to boot have failed. I'm at a loss and any help would be greatly appreciated.

---

### Post by hjjr15 on 2014-07-19
I uploaded a screenshot of what gparted shows.

---

### Post by oldfred on 2014-07-19
If it is hibernated from fast boot or needs chkdsk then gparted cannot open it to see what it is.

And with Windows it has the system reserved partition which is unformatted space for stuff like serial numbers etc and must be just before main Windows partition. Since unformatted gparted will also show that as having issues. Do not delete that one.

You need to directly boot Windows from UEFI menu, not grub. 
Grub only can boot working Windows that is not hibernated and only if Ubuntu in installed in UEFI mode and secure boot is off.

HP's also are not dual boot friendly. what model is yours?

Some other HP:
       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)

---

### Post by hjjr15 on 2014-07-19
Thanks for responding. I have an hp envy h8 1240t desktop. Fast boot I'm pretty sure is a windows 8 only feature and i have windows 7. Grub shows ubuntu and lets me boot it no problem, but windows is the problem. I've tried disabling secure boot and i know both os' s are installed in uefi.

---

### Post by oldfred on 2014-07-20
Windows 7 could be hibernated, but often the reason then with Windows 7 not working is that it needs chkdsk.
Did you resize Windows 7 from outside it? Generally best to resize it using Windows tools and reboot immediately so it can run the chkdsk that is required on any size change.

Windows 7 also does not have secure boot.

Can you boot Windows directly from UEFI menu, not grub. Grub really only boots working Windows.
And then if not booting can you use the f8 to get into Windows repair console and run chkdsk or make other repairs?

HP is one of several vendors that modified UEFI to only boot Windows entry.

May be best to post link to BootInfo report to see details, but you may need a Windows repair disk to fix Windows. Boot-Repair can only do very minor fixes to Windows systems.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hjjr15 on 2014-07-20
The last time was able to boot into WIndows I shut it down completely so I don't think Its hibernated. Right now If i try to boot windows from the uefi menu it stays loading forever. I can access the repair console and I've tried to repair the MBR but I've had no luck getting it to work. I ran boot repair to get the boot info and this is the link it gave me. [http://paste2.org/WaD2CAtU](http://paste2.org/WaD2CAtU)

---

### Post by oldfred on 2014-07-20
Script is not even showing NTFS correctly in partition table for sda3. It does say boot sector is Windows type. 
It also seems to have trouble with sda5. And blkid is not showing UUIDs for either of those partitions.

The unknown type on sda2 is normal for system reserved partition. That is unformatted space and a partition Windows requires just before the main NTFS Windows install.
       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

