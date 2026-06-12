---
title: "Unable to boot into Ubuntu (Dual-boot Win 7 and Ubuntu)"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by SirRaiNWalKer on 2013-05-03
I downloaded and installed the Ubuntu 12.04 LTS 64 bit just now. I followed the [LinuxBSDOS dual-boot guide]("http://www.linuxbsdos.com/2012/10/11/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-hardware/") to install Ubuntu on my computer as previous attempt to install Ubuntu normally was unsuccessful (GRUB mess up the Windows MBR, none were able to boot).

So everything went pretty smoothly until the boot. After I picked the Ubuntu at the Windows boot menu, there are no Ubuntu boot screen, instead, I was greeted with an GRUB "error".

Here's the error I've encountered just now
[IMG]http://i.imgur.com/hNr4Xjr.jpg[/IMG]


Note: The "possible command" only shows up after I pressed the TAB button. entering the command /grub boot gives me the Error 8 message.

FYI, here's my partition scheme


250 GB NTFS Windows
500 MB boot (primary) (bootloader installed here)
40 GB / (logical)
200GB /home (logical)
4 GB swap (logical)


and the following is my system information


------------------Overview------------------

Processor :  Intel(R) Pentium(R) CPU G860 @ 3.00GHz
Memory : 4096MB(Speed  1333)
Mother Board : AsRock H61M/U3S3
Video Adapter : ATI Radeon HD 5670
Disk Drive :   WDC WD5000AADS-00S9B0 ATA Device(465GB, IDE)
DVD/CD-ROM Drive :   TSSTcorp CDDVDW SH-222BB ATA Device


Help are much appreciated! :KS

---

### Post by oldfred on 2013-05-04
This may offer to reinstall grub if everything else is ok or you can post link to Bootinfo report.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by SirRaiNWalKer on 2013-05-04
Just performed the Boot-Repair, it seems to solve the problem, as of now I'm running on Ubuntu on HDD, boot is a success, will restart later to check if there are any problem left.

Here's the BootInfo report
1st (before boot repair)
[http://paste.ubuntu.com/5631298](http://paste.ubuntu.com/5631298)

2nd (after boot repair, on live USB)
[http://paste.ubuntu.com/5631318](http://paste.ubuntu.com/5631318)

3rd (Ubuntu on local HDD)
[http://paste.ubuntu.com/5631336/](http://paste.ubuntu.com/5631336/)

Is there any problem with my GRUB or partition scheme?

Thanks for your help!

Update: The boot problem is solved, thanks! Can anyone tell me what's the problem (before boot repair) that prevent Ubuntu from booting?

---

### Post by oldfred on 2013-05-04
For whatever reason grub did not install. There seem to be a variety of reason why that may occur, but if Boot-Repair was able to fix it, then it could not have been anything major.

You have a separte /boot. A few older systems seem to need that as the BIOS & grub then do not let you boot when the files in /boot whether a partition or folder in / (root) are beyond the 137GB point on drive. Even with your /boot partition your grub & kernels are at 250GB point on drive, so you did not need the separate /boot.

You may find you do not use all of your 40GB / with the separate /home. I normally suggest 10 to 25 and use 25GB myself but find I actually use 9GB with lots of apps installed. But I would not change anything now. I find after a period of use my own optimal partition plan is obsolete and needs changes.

---

