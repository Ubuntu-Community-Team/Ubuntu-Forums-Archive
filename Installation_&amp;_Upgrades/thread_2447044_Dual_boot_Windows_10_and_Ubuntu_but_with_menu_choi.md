---
title: "Dual boot Windows 10 and Ubuntu but with menu choice?"
date: 2020-07-11
forum: Installation &amp; Upgrades
---

### Post by bloodyskullz on 2020-07-11
Hi Everyone,

Is this scenario possible? 2 SSD, 1 with Ubuntu and the other with Windows 10. Can they be configured for a dual boot scenario where I can choose which OS rather than having to modify it in the BIOS/UEFI all the time?

I want to take this opportunity to use a spare SSD I own to start learning linux.

Thanks

---

### Post by ajgreeny on 2020-07-11
Yes, no problem doing that as long as you make sure both OSs are installed in the same manner as regards UEFI/BIOS.

See all the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and 
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

You must make sure that Windows does not use **Fast-Start** which is a form of hibernation and causes problems with dual boot, but if done correctly and the Ubuntu disk is first boot priority it should go to the grub manu where you can choose either OS.

---

### Post by oldfred on 2020-07-11
What brand/model system?
What video card/chip?
Some require extra boot parameters or settings.

Ubuntu will share ESP on first drive seen, usually Windows drive.
If you want Ubuntu drive totally separate, you can disconnect all other drives either physically or logically in UEFI settings.

You do need to partition in advance and if UEFI, only use gpt partitioning.

If you cannot disconnect drives or prefer not to, you can do this work around.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by bloodyskullz on 2020-07-11
system specs:

Gigabyte board (can't remember exact model but does it matter?)
Intel Core i5 7600k
16GB of Ram
GTX 1070
Kingston SSD for Ubuntu
Adata SSD for Windows 10
4TB WD Red pro HDD for storage

Will I experience any issues related to drivers or will tweaking be necessary?

---

### Post by oldfred on 2020-07-11
Make sure you have updated UEFI to latest version available.
Check for SSD firmware updates also.

Windows needs fast start up off, just so installer can see the NTFS partitions. If all on SSD and Windows unplugged then not required, but other NTFS partitions on HDD may still be locked with hibernation flag that fast startup uses.

You need nomodeset or safe graphics mode to boot with nVidia. Newest installer now offers to install nVidia driver as part of install, otherwise you need the nomodeset parameter on first boot or until you install driver. Only install from Ubuntu repositories.

I also have Gigabyte Z170 board. Had to make a few settings and updates but it does not have Windows.

Other threads with Gigabyte.
Gigabyte Z490 with 20.04 needs kernel update  to 5.6 for Ethernet to work.
[https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1)
Gigabyte X399 Aorus fixes/fast boot setting for keyboard
[https://ubuntuforums.org/showthread.php?t=2428618](https://ubuntuforums.org/showthread.php?t=2428618)
Gigabyte B360M LGS 1151 Intel needs pci=nomsi
[https://ubuntuforums.org/showthread.php?t=2425172](https://ubuntuforums.org/showthread.php?t=2425172)
Gigabyte American Megatrends UEFI screen shots Slow Boot USB related
[https://ubuntuforums.org/showthread.php?t=2401568](https://ubuntuforums.org/showthread.php?t=2401568)
Gigabyte Z97 need csm off for nVidia to work
[https://ubuntuforums.org/showthread.php?t=2384409](https://ubuntuforums.org/showthread.php?t=2384409)
Gigabyte E2200 Killer Set grub IOMMU first, then UEFI setting or mouse/keyboard will not work
[https://ubuntuforums.org/showthread.php?t=2347115](https://ubuntuforums.org/showthread.php?t=2347115)
Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04) & 
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
Gigabyte H170
[http://ubuntuforums.org/showthread.php?t=2312650](http://ubuntuforums.org/showthread.php?t=2312650)

---

### Post by bloodyskullz on 2020-07-29
Sorry a little late to this response - busy with a few things.

I noticed on that a z270 board isn't on the list. Does this mean I don't have to worry about anything other than making sure fast boot is disabled (which I believe I normally do anyways). I will do a UEFI update sometime soon and I will check to see if there is an update to my kingston SSD.

Is the best route to unhook the Windows SSD then attach it later and create a dual boot menu?

---

### Post by oldfred on 2020-07-29
If you want systems totally separate, then either physically or logically in UEFI disconnecting/disabling Windows drive will ensure Ubuntu is on one drive. If installed in same boot mode as Windows after adding Windows drive 'sudo update-grub' will add Windows to grub menu.
But grub only boots working Windows, and that also means Windows fast start up must be off.

The Intel or AMD family of motherboard are often very similar, so best to review similar models even if your exact model not shown.

Some have said that temporarily removing boot/esp flags from Windows drive then allows install to ESP on Ubuntu drive. That has not worked for me, but I directly boot an ISO with grub2's loopmount from my hard drive to install to another hard drive.

---

### Post by pbear42 on 2020-07-29
> **bloodyskullz said:**
> ... fast boot is disabled (which I believe I normally do anyways) ...
Be aware, fast boot and fast startup are different things.  The first is a firmware setting.  The second is a Control Panel - Power Options setting.  The second is the one which puts the drive in a semi-hibernated state.

By the way, I'm one of the people who uses unflagging the first drive's EFI partition.  Used recently with ISO boot and many times with conventional USB boot.  There are several options, but do something.  There's a bug in the installer, where it places the boot loader on the first EFI partition it sees.  Can be fixed, but easier if avoided.

---

### Post by bloodyskullz on 2020-08-04
For the nvidia driver ubuntu falls under the linux 64bit driver correct? I am going to attempt this today.

EDIT: I also forgot to mention that since I disabled hibernation (something I do on all my machines), fast startup isn't in my control panel.

---

