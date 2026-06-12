---
title: "Update-iinitramfs error"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2020-07-03
Hi all,
 
 
 I’m trying to create a fresh install of Ubuntu 20.04 which needs to be encrypted, and it’s to dual boot with Windows 10. I have been following the instructions on this [page]("https://medium.com/@chrishantha/encrypting-disks-on-ubuntu-b50bfc65182a") and everything went well until the last step ```
update-initramfs -k all -c
``` which produced the following output ```
update-initramfs: Generating /boot/initrd.img-5.4.0-26-generic
 W: Possible missing firmware /lib/firmware/amdgpu/navi12_vcn.bin for module amdgpu
 W: Possible missing firmware /lib/firmware/amdgpu/arcturus_vcn.bin for module amdgpu
 W: Possible missing firmware /lib/firmware/amdgpu/navi12_smc.bin for module amdgpu
 W: Possible missing firmware /lib/firmware/amdgpu/arcturus_smc.bin for module amdgpu
```
 
 
 Evidentally you’re supposed to be able to remove these files from modinfo according to bugs.launchpad. I can only find one directory looking thing with the name modinfo which is modinfo.8.gz but this only contains one file not related to the above errors.
 
 
 Can anyone explain to me how exactly to find and delete these files?
 
 
 Thanks in advance

---

### Post by dino99 on 2020-07-04
My feeling is that should have been silenced since a while by lintian; seems to be harmless.

---

