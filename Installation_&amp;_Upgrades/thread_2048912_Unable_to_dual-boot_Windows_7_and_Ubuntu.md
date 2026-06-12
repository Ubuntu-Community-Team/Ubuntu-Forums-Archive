---
title: "Unable to dual-boot Windows 7 and Ubuntu"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by daenth on 2012-08-27
I've been trying to dual-boot Windows 7 and Ubuntu on my laptop for a while now and every time I've tried, it's always failed. I got a Windows 7 and Ubuntu dual-boot going on my desktop but that's going to be unavailable to me for a while. Here's what I'm doing.

1) Making my USB into a bootable USB drive.
2) Booting into the bootable USB and selecting "Install ubuntu."
3) Install everything like normal, selecting the option "Install alongside Windows."

When I reboot, it goes straight into chkdsk for the first reboot and then straight into Windows 7. No boot menu, no indication I even have ubuntu on my system. I tried getting it to work with EasyBCD, by selecting GRUB2 boot loader and adding that, it just took me to a command line. I've wiped my entire hard drive, reinstalled Windows 7 and ubuntu with no luck. I've ended up with "ubuntu" in my BIOS boot menu once before, if that's relevant at all.

---

### Post by Mark Phelps on 2012-08-27
I would boot from the USB into Ubuntu, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out your partitions -- and you can then see if the Linux partitions are there.

From the same desktop, you can try mounting one of the Linux partitions to see if there are any files there.

---

### Post by d.atanasov on 2012-08-27
Hi, 
If there is no partitions (after what Marc Phelps asked you to do) You can try and learn how to partition your hard drive to logical sections (this is the advanced option during installation of Ubuntu). Try also to investigate the grub loader of the Installed Ubuntu by the help of the LiveCD(USB). 

cheers

---

### Post by darkomano on 2012-08-28
I would start again but first clean disk.
Maybe there is something wrong with current partitioning.
 
To clean disk using Windows you go to command prompt 
and use:
diskpart.exe
>list disk
>select disk # (# is your disk number, should be 0)
>clean
>exit
 
Then install Windows. 
Shrink c: to free space for Ubuntu.
Then install Ubuntu.
Ubuntu will create the dual-boot menu.
 
Hope this helps.

---

