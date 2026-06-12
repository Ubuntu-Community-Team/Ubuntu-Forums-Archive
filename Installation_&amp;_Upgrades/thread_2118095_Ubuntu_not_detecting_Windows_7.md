---
title: "Ubuntu not detecting Windows 7"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by flintdk on 2013-02-20
Hi folks,

I'm trying to install Ubuntu 12.10 64-Bit on a Windows 7 laptop:
-> The laptop is a Lenovo Z580, it has a UEFI BIOS and is set to boot in UEFI only mode (legacy support is not enabled)
-> Secure Boot is not enabled (it's currently running Windows 7).
-> There's a good chunk of free, unpartioned space on the disk ready and waiting for Ubuntu.

Ideally - I'd like to dual boot Ubuntu and Windows 7.  But when I install Ubuntu it doesn't detect Windows 7 (I get a message "no operating systems detected")) and the only options available to me are to erase the entire disk or "something else" (i.e. a manual install).

I had a look here before I registered and saw a couple of posts similar to this - but the fixes suggested don't seem to apply to my situation (e.g. tinkering with "dmraid" - I don't have a raid controller).

I appreciate there's probably not enough information above to help diagnose the problem but if someone suggests some extra information I could post... then I'll post it.  I'll admit - I'm new to Ubuntu (as in totally, utterly new).  But have been using different OS's for years, some linux based, so happy to dig around for answers.

---

### Post by flintdk on 2013-02-20
Nuts - just spotted another message about a utility "fixparts" - hadn't seen that one before.  I'll download it, try it from the live CD, and post the results.

---

### Post by offgridguy on 2013-02-20
There is a how to here regarding an install using UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also in this thread , lots of info, regarding windows 8, but same principle as windows 7 if
you are using UEFI.

[http://ubuntuforums.org/showthread.php?t=2107873](http://ubuntuforums.org/showthread.php?t=2107873)

---

### Post by oldfred on 2013-02-20
When you reinstalled Windows 7, did you install in BIOS/MBR or UEFI/gpt.

If in BIOS mode you will need fixparts as Windows do not correctly convert from gpt to MBR(msdos) partitioning. It removes primary partition table but gpt has a backup (on of its advantages) and Windows leaves backup. Then Linux sees MBR and backup gpt and gets confused.

Only if now MBR.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    Windows only boots from gpt partitioned drive with UEFI. 
Ubuntu will boot from either gpt or MBR with BIOS. 
UEFI requires gpt.

---

### Post by flintdk on 2013-02-20
@offgridguy:  Yup, I had already read the article on installing Ubuntu in EFI mode.  Windows 7 is already installed in EFI mode.  The BIOS is set to boot UEFI only (legacy support is not enabled).  The 64-bit Ubuntu 12.10 live CD boots nicely with this setup.  In the link you recommended there is a section "Identifying if the computer boots the CD in EFI mode" - and yes I see that screen, the CD is booting in EFI mode.

The thread on Windows 8 is indeed interesting - but I haven't attempted using the 'Something else' option yet.  I was hoping to find a way to get Ubuntu 12.10 to recognise the existing Windows install and install itself to the free drive space.

@oldfred: I installed Windows 7 in UEFI/gpt (from a UEFI bootable USB Drive)

I didn't realise that fixparts was only for fixing MBR disks when I read about it here, that's not applicable in my case so as the disk is GPT.


So... I could go down the "something else" install option but would prefer to figure out why Ubuntu isn't seeing my existing Windows 7 install.

---

### Post by oldfred on 2013-02-20
If you have installed an do not get a working Windows boot entry then it is this bug. Boot-Repair can fix it.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
If not post link to BootInfo report that Boot-Repair can create.

---

### Post by flintdk on 2013-02-21
Hi - nope I've not installed.  I'll post a link to the boot information as soon as I can, thanks!

---

### Post by oldfred on 2013-02-21
This was Windows 8, but other than secure boot it should be the same.

       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

---

