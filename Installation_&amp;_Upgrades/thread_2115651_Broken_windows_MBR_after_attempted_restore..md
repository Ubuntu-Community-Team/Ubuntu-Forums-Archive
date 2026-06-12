---
title: "Broken windows MBR after attempted restore."
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by BTORogers on 2013-02-13
Hey all, I recently installed ubuntu onto a memory stick, thinking it would work the same way as the liveUSB. But however it did not run directly from the USB as the live version did, if I tried to it wouldn't find the operating system and would default back to the hard drive and I would select ubuntu in the windows boot manager which would run grub on the USB.
This was fine until I didn't want my hard drive to ask to boot Ubuntu anymore, so I followed some online advice to rest the windows MBR, and not much changed, except now when I select windows or Ubuntu from the MBR screen it cannot find either. 
I could change the USB with Ubuntu back into a liveUSB and then I would at least have some access back to my computer, but can someone recommend an actual method as to reseting windows 7 MBR through ubuntu?

---

### Post by oldfred on 2013-02-13
Did you install wubi to flash drive?

Best to see details, and this may fix issues.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by BTORogers on 2013-02-14
NVM, I fixed it by recovering from the windows 7 install disk. It still shows the MBR GUI on startup, but I guess that is more of a windows problem.

---

