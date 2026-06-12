---
title: "Encountering boot problems with an external HD partitioned &amp; installed with Ubuntu"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Shaq901 on 2013-05-09
*I'm using Windows 7 64bit on a Dell XPS, and my External Hard Drive is a 750GB "My Passport."*

I have recently installed Ubuntu 13.04 using a boot USB, and downloaded Ubuntu on another (not the USB) external hard drive. The entire installation process went smooth, using [this tutorial]("http://www.linuxbsdos.com/2012/02/20/install-ubuntu-11-10-on-external-hard-drive-with-an-ntfs-partition-at-the-end/"). 
Unfortunately, when I boot my external hard drive, I seem to get a black screen with an eventual "Read Error."
Searching online, it seems like the common antagonist is some sort of MBR/GPT problem. Except I have no idea what any of this means.

The reason I want to use an external hard drive to install Ubuntu is mostly just a lack of free space on my XPS's HDD. It's 3 years old and I'm planning on getting a new one before university. If the fix for this is indefinite or just over my head. 

I'd be interested in just installing a dual boot Ubuntu if I can use my hard drive to store downloads between Windows and Ubuntu and, (if someone knows how to do this, much appreciated), if I could install Steam on Ubuntu onto my external hard drive. Having my steam games on Ubuntu would be pretty sweet, and help my HDD space issue. I mostly want to use Ubuntu for general browsing and developing/programming. 

Thanks ahead for any advise. Much appreciated!

---

### Post by oldfred on 2013-05-09
Is your XPS in UEFI or BIOS boot mode? Only some Windows 7 systems have UEFI but those do not have the issues of secure boot that all Windows 8 UEFI systems have.

Best to see details with external drives plugged in:
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Shaq901 on 2013-05-09
[http://paste.ubuntu.com/5648413/](http://paste.ubuntu.com/5648413/)

I only did the Boot-Info, not the recommended repair (was I suppose to?). 

/sdc is my external harddrive, 
/sdb is the live-boot USB I was running, 
/sda is my HDD

---

### Post by oldfred on 2013-05-09
It looks correct as it is. You can run Boot-Repair fixes, but I think that just reinstalls grub to MBR of external and may reinstall a Windows equivalent boot loader to the internal drive.

Your issues have nothing to do with MBR(msdos) or gpt partitioning. I use gpt now, but you do not have that nor need to change to gpt. New systems with UEFI need gpt partitioning or drives over 2TB have to be gpt. If a drive is only Ubuntu you can use MBR or gpt.

Do you get grub menu when booting from external. Does Windows boot ok from that menu?

What video chip do you have? Often nomodeset is required, but some systems need other boot options.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

