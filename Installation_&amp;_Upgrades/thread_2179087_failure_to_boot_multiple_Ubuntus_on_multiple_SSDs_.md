---
title: "failure to boot multiple Ubuntus on multiple SSDs on Lenovo W530"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by poncenby2 on 2013-10-06
Hello

I've tried using 12.04 amd64 and 13.04 amd64 on a Lenovo W530, on two different SSDs.
Installation goes fine, but boot hangs at the same point each time:

Adding 7991292k swap on /dev/mapper/ubuntu--vg-swap_1. Priority -1 extents:1 across:7991292k SS
EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro

I've left it for a few hours and nothing changes.
I've removed quiet splash $vt-handoff from grub and no change.

Weird thing is, I had a working 12.04 amd64 installation the other day and suspended to RAM.  The next day I tried to use it and it wouldn't boot, hanging at the point above.
It seems any fresh installation on two different SSDs are hanging at the same point.

The disks I'm using are: Corsair Force GT 240Gb and Kingston SSDNow 200 60Gb

What is going on?

Any help greatly appreciated.

---

### Post by oldfred on 2013-10-06
Are you using RAID or LVM. I do not know either except that they make it a bit more complicated.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

