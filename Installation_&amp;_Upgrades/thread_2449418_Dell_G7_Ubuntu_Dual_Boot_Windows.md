---
title: "Dell G7 Ubuntu Dual Boot Windows"
date: 2020-08-26
forum: Installation &amp; Upgrades
---

### Post by jhungerman on 2020-08-26
I have been having an issue booting Ubuntu from a Del5l G7. I installed  as a dual boot setup alongside Windows 10. I have tried installing 5 or 6  times. The boot option 'ubuntu' shows in the boot startup order. I have  tried booting in secure and non-secure mode. I tried installing using  default a couple times with the standard 'Boot alongside windows'  option. I have also tried partitioning my freespace into /boot, /, and  /home mounts. When restarting, the computer boots directly to Windows  10. I have tried setting the boot sequence in Windows Command Prompt. I  also ran the Boot-Repair utility. The paste file is:  [https://paste.ubuntu.com/p/JzsYbs6Rb9](https://paste.ubuntu.com/p/JzsYbs6Rb9).

I have 2 drives: 500 GB M.2 SATA, and a 1TB storage drive. Windows boots  to the M.2, which includes the windows efi partition. When setting  partitions the Ubuntu installation manager defaults to my 1TB storage  drive (sda), where I want it installed to boot from the M.2 (sdb).

I ran an Ubuntu dual install on an older Dell Inspiron with 1 drive  set-up, and that went flawlessly. That setup does run an older BIOS  utility.

I did notice that after install and the installer requires reboot, after  it tells me to remove installation media, a bunch of errors flash  across the screen about failing to unmount (it flashes quickly). I have  tried installing from both a DVD and a USB.

Any help would be appreciated, as this is driving me crazy.

---

### Post by jhungerman on 2020-08-26
New information. I removed my secondary 2.5" SSD and reinstalled ubuntu with just the M.2 mounted. It rebooted into GRUB as expected. I put the 2.5" disk back in and its back to the same problem. When selecting ubuntu from the load options, it sends me to the Dell system performance Pre boot check.

---

### Post by oldfred on 2020-08-26
Have you updated UEFI & SSD firmware?
Are drives set to AHCI. Make sure Windows has AHCI driver installed first.
Is Windows fast start up off.
Is UEFI Secure boot off and fast boot off.

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

See also link in my signature.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by jhungerman on 2020-08-27
Thank you so much for your reply. I found the problem while navigating through the Dell documentation you provided. It ended up being a fairly simple fix. The boot option created during install was faulty. I went into the UEFI Boot Menu, deleted the auto created ubuntu boot option, clicked to add a boot option, navigated to my EFI partition, found the SHIM64 file, and finalized the boot option, moving it to position 1 in the boot order. Starting now successfully brings up the GRUB menu at boot.

---

