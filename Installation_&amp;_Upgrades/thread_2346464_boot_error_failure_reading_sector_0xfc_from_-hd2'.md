---
title: "boot error: failure reading sector 0xfc from -hd2'"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by peter.hewett on 2016-12-15
This is a fresh install of Kubuntu 16.10, with two disk drives sda and sdb.
On startup, it stops at the grub prompt with error message:
error: failure reading sector 0xfc from -hd2'
error: failure reading sector 0x0 from -hd2'
error: no such device: 575728d7-.....

If I use command exit twice at the grub command line, it boots into Kubuntu ok.
My understanding is that hd2 refers to sdc, and there isn't one on this machine.

How do I reconfigure grub2 to not look for sdc? (If that is the problem)
Running sudo update-grub didn't make any difference.

TIA

---

### Post by oldfred on 2016-12-15
Do you have a flash drive or DVD/CD plugged in?

I also had BIOS/UEFI think I had different drives when I had DVD in SATA1 with sdb drive in SATA2. Booting was ok using UEFI, but grub commands used different drive numbers.
Found best to always have drives in SATA port order starting at SATA0, and DVD last if you still have one.

---

### Post by peter.hewett on 2016-12-15
There is no flash drive plugged in at start up.
There is a dvd drive, but nothing in it.

The install was from a USB stick. I don't know if that confused grub when setting things up, but I haven't had this trouble before and I have done several full installs on this hardware.

---

### Post by aljosa2 on 2016-12-15
Lenovo Y700-17ISK Boot Error: Failure writing sector 0x21c8800 to 'hd0'
**"I didn't have this error when I installed Xenial first time at the beginning of February, it appeared later after some updates."**

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1553687](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1553687)
[http://lists.gnu.org/archive/html/bug-grub/2016-06/msg00002.html](http://lists.gnu.org/archive/html/bug-grub/2016-06/msg00002.html)

---

### Post by peter.hewett on 2016-12-16
aljosa2, if the hd0 in your error message is /dev/sda and that is the disk you are booting from, then it is a different type of error to what I am seeing.

In my case, hd2 refers (I think) to /dev/sdc which doesn't exist, so it is no surprise that grub can't read it. I just want to know how to tell grub to not even try to access /dev/sdc.

---

### Post by oldfred on 2016-12-16
The hd2 drive may be just sdb.
Again SATA port order determines what UEFI/BIOS see and report for booting. But then each drive is given a letter, by Ubuntu but that may not be UEFI/BIOS and grub hd#.

Does your UEFI/BIOS show ports & drive plugged into it? And is SATA0 or SATA1 not used or skipped?

And does this show HDs first like mine?

```
fred@Asusz97:~$ sudo lshw -C Disk -short 
[sudo] password for fred: 
H/W path       Device      Class          Description
=====================================================
/0/1/0.0.0     /dev/sda    disk           128GB Samsung SSD 840
/0/2/0.0.0     /dev/sdb    disk           1TB WDC WD10EZEX-00B
/0/3/0.0.0     /dev/cdrom  disk           CD/DVDW SH-S183L

```

---

### Post by peter.hewett on 2016-12-16
peter@hook:~$ sudo lshw -C Disk -short
[sudo] password for peter: 
H/W path              Device        Class              Description
=====================================================
/0/1/0.0.0          /dev/sda             disk                   240GB OCZ-ARC100
/0/2/0.0.0          /dev/sdb              disk                   2TB WDC WD20EZRX-00D
/0/3/0.0.0          /dev/cdrom    disk                   DRW-24B1ST
peter@hook:~$

---

### Post by oldfred on 2016-12-16
That looks just like mine, does UEFI/BIOS show same?

It then seems like an error reading DVD, which of course does not exist.

Do not know if this will show anything or not:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by peter.hewett on 2016-12-16
Boot-Info report link:
 [http://paste2.org/VC1XJ9YK](http://paste2.org/VC1XJ9YK)

---

### Post by oldfred on 2016-12-16
I do not understand how it boots at all?

You have grub installed to MBR of sda which is a gpt partitioned drive. For that grub to work you must have a bios_grub partition. It must be unformatted, 1 or 2MB and with bios_grub flag. It can be anywhere on drive.

You also show the ESP - efi system partition as sda1 for UEFI boot, but your fstab does not show the mount of the efi partition.

Boot-Repair says Secure boot may be on, usually it is correct. But you cannot boot in BIOS mode with it on, unless it somehow lets you switch while booting after giving the errors.

You either need to use Boot-Repair booted in UEFI mode to totally un-install grub-pc(BIOS) and install grub-efi-amd64 (UEFI). You have to use Boot-Repairs advanced options.
Or add the bios_grub partition. I typically have both ESP & bios_grub but with new UEFI systems boot only in UEFI mode. And then reinstall grub to MBR of sda.

Your sdb drive is also MBR. Perhaps you are using it to boot? Not familar with libparted boot.

Better to only use gpt with new UEFI systems. Your sdb drive is MBR(msdos) partitioned. You may be able to convert, but best to have good backups. If you just change with gparted it will erase drive.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by peter.hewett on 2016-12-16
Thanks for your help on this.

> **oldfred said:**
> I do not understand how it boots at all?
No. That's why I posted the problem here. Previous version of Kubuntu have installed ok to this hardware without causing these errors.

I'll check out the fixes you advise.

---

