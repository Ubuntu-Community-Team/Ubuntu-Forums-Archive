---
title: "fsck fail during boot-up"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by satellite5 on 2008-01-06
Hi! I'm a newbie and have recently installed Ubuntu. Running on dual boot with Ubuntu and Vista. After installing, I have followed a tutorial to mount my Windows partition in Ubuntu so that I can read/write my Windows files in Ubuntu. Thereafter I got out and restarted Vista. From Vista, I used Partition Manager to resized my Windows partition to allocate more space for Ubuntu. However, when I restart, I have encountered fsck of the root filesystem failed and unable to boot Ubuntu. Screen shot below :

[COLOR="Red"]* Checking root file system...
fsck 1.40.2 (12-Jul-2007)
UBUNTU: Resize inode not valid.

UBUNTU: UNEXPECTED INCONSISTENCY: RUN FSCK MANUALLY.
     (i.e., without -a or -p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root filesystem failed
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the 
root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D 
to terminate the maintenance shell and restart the system.[/COLOR]

URGENT help require !!!!!

Many thanks in advance.

---

### Post by Pumalite on 2008-01-06
dis you allocata space for Ubuntu FROM Vista first?

---

### Post by satellite5 on 2008-01-06
I have allocated some when I install Ubuntu. Later I then decided to allocate more. Is there any solution? What can I do now?

---

### Post by Pumalite on 2008-01-06
Have to start from scratch. Use Vista partitioner. You have to format the new partition. Ubuntu does not in unallocated space.

---

### Post by satellite5 on 2008-01-06
Sorry I may not totally understand you. Firstly I started with a Vista, Unallocated Space & Ubuntu partition. I then when into Vista and resized the Ubuntu partition to take up the entire Unallocated Space partition. Thereafter when I boot up, the above message appealed.

Could you pls provide me with a solution and give me a step by step guide to execute it.

Many thanks in advance.

---

### Post by Pumalite on 2008-01-06
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by satellite5 on 2008-01-06
Thanks for the link. But my problem is, I can't even boot into Ubuntu to change the boot setting at Terminal. Can someone please help be to solve this.

Thanks in advance.

---

### Post by Pumalite on 2008-01-06
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)
[https://help.ubuntu.com/7.04/install...oot-parms.html](https://help.ubuntu.com/7.04/install...oot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317
__________________

---

### Post by satellite5 on 2008-01-06
Pumalite, thanks again for your speedy reply. I am not able to open the above links that you have attached. Based on my situation, is there a way to solve it? Can I still boot into Ubuntu without any missing files etc or reinstalling or reformatting?

---

### Post by Pumalite on 2008-01-06
Try Super Grub Disk. See if it works:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can boot Ubuntu with Super Grub. That's one of a thousand things it can do.

---

### Post by confused57 on 2008-01-06
This has some info on running a manual filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

Did you resize your Vista partition with Vista's partitioner to create unallocated space, then use gparted to resize your Ubuntu partition?  It probably wouldn't work to use Vista's partitioner to resize your Ubuntu partition.

It was an excellent suggestion by Pumalite to try Super Grub Disk.

---

