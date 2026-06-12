---
title: "Install Ub13.10 alongside Win8.1, lost access to Win and cant install Ub13.10"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by rodicurus on 2014-02-15
I tried installing wubi from live usb, when I reboot can't get to installed Ub13.10.Turned off Secure boot & fastboot, only 2 real boot options;  Try Ubunt without install and Install ubunt. 
Lost window image and dont have restore usb. Partition with windows has ubuntu title with unknown contents. Vaio restore therefore doesnt work. Cant get boot-repair into the try unbuntu feature so I can not alter the boot screen. 
Tragedy, how can I get unbuntu installed and new win image. Laptop is three days old :-(
 Any suggestions would be cherished

---

### Post by oldfred on 2014-02-15
Run Boot-Repair from live installer flash drive or DVD.
You may have to run it in UEFI or BIOS boot mode.
If you erased Windows you may have to buy another copy. Only some better vendors offer a replacement image.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[URL="http://ubuntuforums.org/showthread.php?t=2200818"]http://ubuntuforums.org/showthread.php?t=2200818

[/URL] Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

[URL="http://ubuntuforums.org/showthread.php?t=2200818"]
[/URL]

---

### Post by rodicurus on 2014-02-18
I finally git a boot-repair usb and got booted up, but I cant proceed any further, I have no ethernet connection on laptop, and it is not detecting wireless.
Is there a way to get wireless working. seems that it should be but it cant detect my wireles signal. Can anyone please advise how to get it going? please?

---

### Post by rodicurus on 2014-02-18
thanks for all the info

---

