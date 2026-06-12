---
title: "Installation 19.04 ok - but update crash the system"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by antenac on 2019-07-11
Hi!
I installed Ubuntu 19.04 without problems, but after install updates and restarted it never started again. 
Now, the third time I am trying, I don't know what update is causing the problem, so, I don't know how to continue.
I filmed a video with the behavior but I can't upload here.
Some idea?

---

### Post by oldfred on 2019-07-11
What brand/model system?
What video card/chip?

UEFI or BIOS install & then is default boot of internal drive set for same boot mode as you booted live installer which is then mode installed?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

 Note that grub only boots working Windows. Or if Window need chkdsk or is hibernated then grub will not boot it, but if UEFI install, you should still be able to boot from UEFI boot menu.
Windows updates also turn fast start up back on which is just hibernation. That then grub will not boot it, or any NTFS partitions will not mount read/write in Ubuntu.

---

### Post by antenac on 2019-07-11
> **oldfred said:**
> What brand/model system?
What video card/chip?


Motherboard Intel 2140, video card integrated.

This time I installed  it without updates and then installed the updates. Shuted down and it started until now.

I gonna install some programs and restart to check if  it keep working.

Thanxs!

---

