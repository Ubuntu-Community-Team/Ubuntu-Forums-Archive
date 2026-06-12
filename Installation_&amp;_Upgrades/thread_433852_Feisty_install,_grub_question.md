---
title: "Feisty install, grub question"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by G Kaya on 2007-05-05
I'm installing Feisty on a hard drive that has multiple partitions...all with Linux distros. Normally what I do is have grub written to the / partition of the distro I'm installing then I grab info from that distro's menu.lst and paste it into the "primary" (hda1) distro's menu.lst. (god i hope that makes sense) I'm sure there are better ways of doing this but it has worked for the most part so far.

When I installed Dapper it overwrote the MBR without asking which meant I had to reinstall grub with the grub entries from the "primary" distro. I didn't want that to happen this time so I clicked on the "Advanced" button which asks where grub should be written. I chose hda5 (location for Feisty) but got a fatal error at the end of the install. 

If anyone can make sense of my post and help that would be great. Basically I want to write grub not to the MBR but rather to the partition where Feisty will reside. TIA

---

### Post by confused57 on 2007-05-05
> **G Kaya said:**
> I'm installing Feisty on a hard drive that has multiple partitions...all with Linux distros. Normally what I do is have grub written to the / partition of the distro I'm installing then I grab info from that distro's menu.lst and paste it into the "primary" (hda1) distro's menu.lst. (god i hope that makes sense) I'm sure there are better ways of doing this but it has worked for the most part so far.

When I installed Dapper it overwrote the MBR without asking which meant I had to reinstall grub with the grub entries from the "primary" distro. I didn't want that to happen this time so I clicked on the "Advanced" button which asks where grub should be written. I chose hda5 (location for Feisty) but got a fatal error at the end of the install. 

If anyone can make sense of my post and help that would be great. Basically I want to write grub not to the MBR but rather to the partition where Feisty will reside. TIA

Feisty recognizes all hard drives as sdx, regardless of whether they're IDE or SATA...Feisty may recognize the root partition as /dev/sda5.  You could boot up the Feisty live cd & check the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You can always use the live cd to install grub to your Feisty root partition:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then you could add an entry to your grub menu.lst  that's installed on the mbr:
```
title   Feisty
rootnoverify  (hd0,4)
chainloader +1
```

---

### Post by louieb on 2007-05-05
To get feisty to write to the boot sector of the root partition you need to look closely on the page with the install button. If its like Dapper live install was its hidden in there somewhereand looks something like this **_[COLOR=cyan](hd0)[/COLOR]_**. Or get the alt CD its clear about where GRUB gets installed. 
 
BTW: Try confused57 suggestion the chain loader method

---

