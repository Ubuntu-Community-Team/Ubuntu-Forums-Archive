---
title: "Can I open and view the main MBR 'Bootloader' file?"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by davidc60 on 2012-02-08
Hi,
I have 4 primary partitions on my HDD, 3 of them booted by Grub Legacy which is installed in the MBR on /dev/sda, ie. 
 - Windows (chainloaded) on /dev/sda1, 
 - Archbang (a Grub Legacy distro) on /dev/sda2 and 
 - Ubuntu 11.10 on /dev/sda3. 

During that installation of Ubuntu I deliberately chose to place its (Grub2) MBR 'bootloader' on to an empty partition, /dev/sda4. I did this _**not **_with the intention of ever expecting to use it but rather for experimental reasons because:
a) I hoped that it may deposit a MBR Bootloader file there that I could actually open and examine, and in any event,
b) I did not want Grub2 taking over the booting function at this time.

When I subsequently opened sda4 in various File Managers there was no sign of any Grub2 MBR BootLoader file(s) (hidden or otherwise). However, when I ran a 'boot_info_script.sh' in the terminal it does indicate that Grub 2 had been installed in the MBR on the first sector of /dev/sda4. 

My questions are simply:
i) why can I not access whatever is on the (Ubuntu-related) MBR on this "first sector" of partition (sda4) via any File Manager?
ii)Is it ever possible to access and examine the MBR Bootloader contents of the "first sector" (512 bytes), whether it is placed onto the first sector of an ordinary partition (eg. /dev/sda4, as in my experiment) or whether it is placed on the "first sector" of the whole hard drive (eg. /dev/sda) as is more usually the case?
Thanks,
davidc

---

### Post by oldfred on 2012-02-08
I hate to recommend dd for anything as it can be very dangerous. That said.

sudo dd if=/dev/sda4 bs=512 count=1 | hexdump -C

Also part of grub2 is core.img. When you install to a PBR it converts to using blocklists which are hard coded addresses to find grub files. The normal install to a MBR then also installs core.img to the sectors after the MBR. If using gpt partitioning instead of MBR, you have to create a bios_grub partition for the core.img file.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


I have also used testdisk to see details of boot sectors. Attached are from reviewing my Windows PBR and the backup that NTFS has.

---

### Post by davidc60 on 2012-02-08
Hi,

Another excellent reply from oldfred. 

Many thanks,

davidc

---

