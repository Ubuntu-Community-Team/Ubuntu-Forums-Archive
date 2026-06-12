---
title: "Kubuntu does not load after update"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by G. Rodrigues on 2014-06-06
Asus M11AD, on Kubuntu 14.04 freshly installed from usb live disk. The kernel version is 3.13.0-24. Opening the update manager there is a boatload of package updates including 3.13.0-24 -> 3.13.0-29. Upon installing, Kubuntu does not load, rather I have a black screen filled with text, the last line being

x86_64_start_kernel +0x143/0x152

I've reinstalled kubuntu and deferred updating so that I have a guaranteed usable system. Some googling tied this problem with dual booting scenarios and grub issues. Kubuntu is the only OS installed and the parted command spits out the following:

```

Model: ATA TOSHIBA DT01ACA1 (scsi)                                                                                                                                                  
Disk /dev/sda: 1000GB                                                                                                                                                               
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   992GB   991GB   ext4
 3      992GB   1000GB  8526MB  linux-swap(v1)

```

My question now is how to proceed? I *could* wait for another kernel iteration (I am assuming the problem is with the kernel, but really, this is just a guess), but of course I run the risk of the same thing happening all over again. I confess that I am at a complete loss on what to do -- this specific problem never happened to me, so count me a complete newb -- so any help is greatly appreciated.

---

