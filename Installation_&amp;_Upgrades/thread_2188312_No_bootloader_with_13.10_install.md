---
title: "No bootloader with 13.10 install"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by Howski on 2013-11-16
Hi, 

Just finished a reinstall of my laptop and I decided to go for ubuntu alongside windows 7. Install went as expected,  I already had partitions set up so formatted them. Installed Windows 7 sp 1 64bit first and once that was all done installed ubuntu 13.10. The installer recognised that windows was installed and I chose the option to install alongside windows. Everything went as expected, connected to the Internet and selected to download updates. Installer finished and I rebooted. 

There is no boot menu at all. The laptop pops into windows straight away with no boot options. 

I tried booting from the install disc and it recognises the install of Ubuntu and I can see files in the target drive when I open it using live cd mode so it seems that there is just a problem with the bootloader not the actual install. Any ideas on a fix? 

Thanks in advance 
Howard

---

### Post by oldfred on 2013-11-16
It sounds like grub did not install its boot loader into the MBR.

From LiveDVD or flash drive installer you used:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Howski on 2013-11-16
Tried the auto repair of the second link and it worked a treat. Thanks ever so much!!

---

