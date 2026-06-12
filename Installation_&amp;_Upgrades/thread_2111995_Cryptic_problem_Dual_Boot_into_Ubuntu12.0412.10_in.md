---
title: "Cryptic problem: Dual Boot into Ubuntu12.04/12.10 in windows8 failed"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by cxpdx on 2013-02-03
I purchased the HP Pavilion p7-1447cb Desktop (AMD Quad-Core A8-5500 and Radeon™ HD 7560D Graphics et al)with pre-installed Windows8. 

After doing a lot search on dual boot ubuntu with windows8, I create a partition for ubuntu in windows, burn a bootable DVD (surprisingly, the bootable USB stick did not work and simply goes to black screen), disable security boot and fast boot, enable Legancy boot only, force boot from CD-ROM. It does goes to Ubuntu installation page. Surprisingly, I did see "Installation Alongside Windows8" option (the Ubuntu did detect windows8 in contrary to many others' experience) and finish the intallation.

Then it comes with the problem. It does not boot into Ubuntu but windows directly. I disable the Windows loader in Boot Order under BIOS, the computer said "No boot disk found or disk failer". 

I noticed that the Ubuntu installation comes with no internect connection even though windows8 DOES (I tried again to boot from CD-ROM using the "Try Ubuntu" ). I tried the Disk Repair included in 12.10.remix but couldn't finish the boot repair because it requires internet connection.

I also tried to install ubuntu in UEFI mode but it boots into windows8 directly. 

Many trails have failed and I sincerely look for some help in this forum.Thank you in advance!

---

### Post by oldfred on 2013-02-04
So we can see details of your install.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

You also need Boot-Repair to convert a BIOS install to UEFI and create correct grub menu chain load boot entires for Windows due to a current bug in grub's os-prober.

Both Windows & Ubuntu have to be either UEFI or BIOS to dual boot and Windows is UEFI, so Ubuntu has to be UEFI.
Is system an UltraBook with a small SSD as that has RAID which complicates issues.

Other HP, UEFI/BIOS should be similar.

       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by antsys on 2013-02-04
May be this helps :
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)
look also at the workaround that is given here : 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
(this is the same as the link given in the forum post).
Antoine

---

