---
title: "Couldn’t get size: 0x800000000000000e - can not run!"
date: 2019-09-28
forum: Installation &amp; Upgrades
---

### Post by logibash on 2019-09-28
Good Morning All, I am new on this forum and new as a Ubuntu user.
I tried instal Ubuntu v. 18.04.3-desktop-amd64 LTS on my computer and their appear a problem, after installing the system cannot start. They are broken down as the screen shot present.

[ATTACH=CONFIG]284097[/ATTACH]

Machine: 
Dell Precision 5520 
Processor Xeon E3-1505M v6
Dysk SATA 512 - with windows 10 operating system
Dysk M2 PCIe NVMe 256 - with instalind mentioned Linux ubuntu - I create 3 partition (logical / ext4) (logical /home ext4) (logical swap) system has been installed on '/' partition
RAM DDR4 16GB

The more important information about the BIOS I suppose: there is UEFI

boot order:
ubuntu 
Windows 
This allow system to start the grub.
Choosing windows there is no any problem, but choosing Linus problem appear as I mentioned before.

I will be appreciated if sb know the solution.

---

### Post by jeremy31 on 2019-09-28
Boot up the Ubuntu ISO again, open terminal and post results for ```
sudo blkid
```

---

### Post by logibash on 2019-09-28
> **jeremy31 said:**
> Boot up the Ubuntu ISO again, open terminal and post results for ```
sudo blkid
```


results for 'sudo blkid'

---

### Post by jeremy31 on 2019-09-28
I only see the drive with Windows and the Ubuntu ISO in those results.  Might want to see is the NVME is still connected

---

