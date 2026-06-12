---
title: "Feisty Won't Boot - Grub Error 18"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by SirReal on 2007-04-10
After having played with Feisty in VMWare for a bit, I decided to take the plunge and install it on my laptop (HP Compaq NC6000).  I ran from the live CD with no problems, so it looked like everything would work fine.  I have encountered two issues, one largely fatal, but I'm not sure whether they are related.

1) I have a 160GB hard disk that I had previously left as a single partition with Win XP installed.  I decided to resize this partition, leaving 30GB free space at the end for my Ubuntu installation.  I ran gparted to perform the resizing.  

Unfortunately, at the end of the resize process, I encountered a failure of the form "Resize Operation Failed," followed by an error message that I failed to write down, but which I recall as not being very informative (vis-a-vis "the operation could not be completed" or something like that).  However, when I checked the partition map, it looked as though the operation had actually completed correctly.  Hence, I decided to proceed with the installation.  At no time did Ubuntu indicate any error with the installation process after this point.

2) Once the installation was completed, I was prompted to remove the CD and reboot.  At this point, I received the following error from Grub:

Error 18

Now nothing will boot.  I am not sure whether this is related to my partitioning issue from before.  Here is a description of Error 18:

[INDENT]Error 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is ttempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).[/INDENT]

There have been volumes written on this error already, however, I would like to know if there is anything I can easily do to fix this, and whether there is any real.  Here are some pertinent links:

[https://launchpad.net/ubuntu/+source/grub-installer/+bug/9006]("https://launchpad.net/ubuntu/+source/grub-installer/+bug/9006")
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/79578]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/79578")  

The latter was rather helpful in understanding the nature of the issue.  However, I don't have the option of putting a boot partition at the beginning of my drive (for now), because I don't want to clobber my WinXP partition just yet.  I am planning to toy with the BIOS (change geometry to "auto"; upgrade version if necessary), but I would like to know if anyone has any other suggestions as to how I can easily escape this trap.  I don't want to lose my partition, and I don't want to spend all night trying to recover.  I know I can use my rescue disk to clean the MBR if necessary, but would rather not have to resort to that, if there is a clean way to make this work.

Other links of interest:

[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/87921]("https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/87921")
[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/94647]("https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/94647")

---

