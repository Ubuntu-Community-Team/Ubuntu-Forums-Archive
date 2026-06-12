---
title: "LMV partition after failed installation"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by dicaguido2 on 2014-02-19
Hi:

I have a Sony V**AIO l**aptop with Windows 8.1 installed.
I tried installing UBUNTU **13.10 **via live USB; I resized the Windows partition via **gparted **and created an ext4, swap and devided a Nfts partition in two
The installation **aborted **soon after and ubuntu was not installed; Windows is no longer available and a message saying that no operating system was found instead appears on startup.

The whole hard disk now appears as a **l[B]m**v2 pv i[/B]n gparted and is unaccessible by any operating system.

I cannot complete my installation, nor access any file.

Does somebody have an idea on what happened and how it can be solved?

Boot repair tells me that I have a RAID error and then another error and doesnt solve the problem.

What should I do?

---

### Post by dicaguido2 on 2014-02-19
The RAID error is
RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends

---

### Post by dicaguido2 on 2014-02-19
[http://paste.ubuntu.com/6962098/](http://paste.ubuntu.com/6962098/)

Is the link Boot Repair gives me

---

### Post by dicaguido2 on 2014-02-19
ubuntu@ubuntu:~$ sudo pvscan
  PV /dev/sda3   VG ubuntu-vg   lvm2 [697.92 GiB / 0    free]
  Total: 1 [697.92 GiB] / in use: 1 [697.92 GiB] / in no VG: 0 [0   ]

---

### Post by oldfred on 2014-02-19
LVM is a full drive install, and it now looks like you have no Windows.
You did make a full backup of Windows?

---

### Post by dicaguido2 on 2014-02-19
No full backup of windows made.
I had the laptop for a few days and moved to france three days ago.

Yes, it looks like there-s no more windows, linux or anything. Just the whole hard disk is a huge lvm partition.

Is there a way to restore the contents of the LVM?

---

### Post by dicaguido2 on 2014-02-19
ubuntu@ubuntu:~$ sudo lvs ubuntu-vg
  LV     VG        Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  root   ubuntu-vg -wi-ao-- 694.04g                                           
  swap_1 ubuntu-vg -wi-a---   3.88g                                           
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               697.92 GiB
  PE Size               4.00 MiB
  Total PE              178667
  Alloc PE / Size       178667 / 697.92 GiB
  Free  PE / Size       0 / 0   
  VG UUID               RfTDQz-ff7b-ADTd-a1D1-xA7Q-62ee-4N9W3n
More infos if needed!   


ubuntu@ubuntu:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               697.92 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              178667
  Free PE               0
  Allocated PE          178667
  PV UUID               n0wZrY-JIAc-Plh1-XSVe-0hUd-WXv6-9uec5Y
   
ubuntu@ubuntu:~$ sudo lvs ubuntu-vg
  LV     VG        Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  root   ubuntu-vg -wi-ao-- 694.04g                                           
  swap_1 ubuntu-vg -wi-a---   3.88g

---

### Post by oldfred on 2014-02-19
I do not know LVM.

But some with RAID had to help grub in UEFI boot mode find grub.cfg.
They add another grub.cfg in the efi partition with just one entry.

 configfile (hd0,gpt2)/boot/grub/grub.cfg

But Boot-Repair does not show any grub or kernels in sda2 and no efi files in sda1. You may need to totally reinstall grub2. I think Boot-Repairs purge & reinstall will work with LVM. It does have issues knowing if RAID or LVM as both use /mapper, so you may need to help it also.

---

### Post by dicaguido2 on 2014-02-19
So, oldfred, could you tell me more specifically what to do in detail?

---

### Post by oldfred on 2014-02-19
As I said I do not know LVM, just that Boot-Repair may help install grub. If other parts of system were not installed then it is a bigger issue.

---

### Post by dicaguido2 on 2014-02-20
Thanks, Oldfred! Does somebody know how to deal with the LMV partitions?

My best guess is to format the whole drive and install ubuntu, then order a repair cd by sony to reinstall windows

---

### Post by oldfred on 2014-02-20
Another thread on LVM.
[http://ubuntuforums.org/showthread.php?t=2205828](http://ubuntuforums.org/showthread.php?t=2205828)

---

