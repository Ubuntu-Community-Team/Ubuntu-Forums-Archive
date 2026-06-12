---
title: "Installing to external USB drive fails partition"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by LavaHot on 2007-01-14
Hi guys. I have a laptop that recently had the HD die on it, and rather than waiting to get the cash to buy a new one, I decided that I could use ubuntu on an external drive that I have as a temporary measure. However, during installation the partitioner takes a while to work and it freezes on 15% then comes back with an error that says that the partition failed. This drive was formerly a windows XP boot drive, but I used partition magic to remove that partition. The option I select for drive selection is simply to erase the drive I have. When I look at the manual partition screen after I retry the installer, it shows that all of the partitions have successfully been made and the ext3 main partition appears to have some data on it. Any help in this regard would be lovely, as well as a suggested way to boot to Ubuntu without the CD, as the BIOS doesn't support booting to USB, but that's only a minor problem.

I should probably also say that I'm using the desktop x64-bit distro. Thanks for your help guys!

---

### Post by logos34 on 2007-01-14
> as well as a suggested way to boot to Ubuntu without the CD, as the BIOS doesn't support booting to USB
AFAIK booting from cd is the only way...the linux kernel with the required usb modules apparently won't fit on a floppy (see [this]("https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29%7C%28floppy%29")). But you can always take the cd out as soon as it boots.  

As to the main problem...you could try partitioning and formatting the drive with the gparted livecd first, then try the install again

---

