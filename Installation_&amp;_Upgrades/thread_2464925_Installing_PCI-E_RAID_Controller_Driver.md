---
title: "Installing PCI-E RAID Controller Driver"
date: 2021-07-16
forum: Installation &amp; Upgrades
---

### Post by hoathy on 2021-07-16
Hi all,
I am pretty new to Ubuntu in general, so don't judge me too harshly if I am missing something obvious.

I have a custom machine running 20.04 its with a PCE-E LSI 3ware 9750 SAS hardware RAID controller and 8 2TB drives all ready to go. I know that I need the drivers to use this device, and have found this: [http://manpages.ubuntu.com/manpages/hirsute/man4/tws.4freebsd.html](http://manpages.ubuntu.com/manpages/hirsute/man4/tws.4freebsd.html)
It says that I need to place two lines in my Kernel Configuration File, which I understand should be in usr/src/linux/
The thing is I don't have a file called that in that location. Is the location different or am I doing something else very wrong?

Thanks,

John

---

### Post by ActionParsnip on 2021-07-16
what is the output of:
```

sudo lshw

```
Thanks

---

### Post by MAFoElffen on 2021-08-01
ActionParsnip asked you to open a terminal and query the PCI bus and post the output from it... I would have asked you the same. The reason for asking that, is to see "the How" of what Linux sees and identifies the Hardware RAID Controller Card as...

I understand that you want instructions and help... as you said, step-by-step. That all depends on how ity is see by "your system," which can vary by the BIOS and the SouthBridge, and how it ID's what is in your PCIe Bus.
```
sudo lspci | grep -i 3ware
sudo lshw -C storage
```
I can'r read minds "well"... But I am using an educated guess and reading tea leaves...And am thinking that your output is going to look similar to
```
PCI: 13C1:1004 3ware Inc 9650SE SATA-II RAID PCIe
PCI: 13C1:1005 3ware Inc 9690SA SAS/SATA-II RAID PCIe
```
If what you run and the output is similar to the above (except for the bus/slot numbers... Then we will go from there.

The Debain page is dated: [https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins) 

That page is dated and the links are broken, but I have updated links, based on the output you post. Yours would be under 3w-9xxx...

---

