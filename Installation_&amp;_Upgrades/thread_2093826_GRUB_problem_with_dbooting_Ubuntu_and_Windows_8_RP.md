---
title: "GRUB problem with d/booting Ubuntu and Windows 8 RP"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Kiyamudeen on 2012-12-11
Hi! ):P

I have a HP Pavilion dv6-2170ee which I installed Windows 8 Release Preview as a lone OS some time back.
And yesterday, I installed Ubuntu 12.10, but now I'm facing problems with booting into Windows 8... :confused:

Ubuntu seems to think it's a lone OS - "grub" doesn't show up at booting, and it boots directly into Ubuntu 12.10
And because of that, I've got no way to boot into Windows 8 RP..

Any help, guys? :-s

I'm kinda new to Ubuntu 12.10, so I'm not a genius with Terminal or what-so... simply step-by-step guides would be appreciated ;)

---

### Post by oldfred on 2012-12-11
Are you in BIOS/MBR or UEFI/gpt. If you installed yourself you may be BIOS. New systems with Windows 8 pre-installed all are UEFI.

To see what is where & details, you can run from your install, Ubuntu live ISO DVD or flash or full download of Repair system:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Mark Phelps on 2012-12-12
You DO know that the RP expires in less than a month, right?

It's scheduled to expire on January 15th, 2013.

---

