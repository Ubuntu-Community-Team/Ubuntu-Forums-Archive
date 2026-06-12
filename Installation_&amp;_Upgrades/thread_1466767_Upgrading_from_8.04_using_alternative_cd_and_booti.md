---
title: "Upgrading from 8.04 using alternative cd and booting from a flash drive"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by threefcata on 2010-04-30
Hi all,

I'm trying to upgrade my 8.04 to 10.04 using my flash drive since there is not enough space for me to upgrade using the iso file.

I installed syslinux to the MBR of my flash drive, extracted all the files from the iso file and put them in the root directory of the flash drive. Then I renamed the folder isolinux into syslinux, and two files: isolinux.cfg and isolinux.bin into syslinux.cfg and syslinux.bin respectively, for syslinux to pick them up.

So far so good, my laptop booted up from the flash drive, and the installation interface appeared, proceeding with the installation until I reached the step of detecting CD-ROM. The installer somehow thinks that the installation files are on a cd and insists on looking for the drive it thinks it is from, but the reality is there is none! And I'm stuck!

Is there anyway for me to 'deceive' the installer so it thinks the flash drive is a cdrom? 

One idea might work that is creating sym-links to '/'. However I'm not very familiar with '/dev' folder so I don't know which one to link to which one. Can anyone point out a direction?

Thanks.

---

