---
title: "Installation Issues"
date: 2017-06-27
forum: Installation &amp; Upgrades
---

### Post by kylemiller061 on 2017-06-27
I am having issues with what seems to be installation loop while trying to install Ubuntu 16.04.2 via usb onto my Dell XPS 13 (9343) that had Windows 10.

I had downloaded the ISO from Ubuntu directly and then used Rufus to format my 64GB USB device to become a bootable drive for the OS. When I attempted to boot my PC from the drive, I selected the "try ubuntu" option, and everything appeared to go well with the boot process. After playing around with the OS for a little bit, I decided to install Ubuntu permanently (as the sole OS). When at the Installation type window, I selected the option to "Erase disk and install Ubuntu" along with the Encrypt Ubuntu, and use LVM options. I proceeded through the rest of the setup and got to the "Installation Complete" notification. I removed the USB and then attempted to reboot my computer. 

I received the following output:

```
[1889.190163] blk_update_request: I/O error, devloop0, sector 1542504
[1889.190200] SQUASHFS error: squashfs_read_data failed to read block 0x2f12cf1e
[1889.190202] blk_update_request: I/O error, devloop0, sector 1542506
[1889.190271] SQUASHFS error: Unable to read fragment cache entry [2f12cf1e]
[1889.190271] SQUASHFS error: Unable to read page, block 2f12cf1e, size 697d
[1889.190271] SQUASHFS error: Unable to read fragment cache entry [2f12cf1e]
[1889.190271] SQUASHFS error: Unable to read page, block 2f12cf1e, size 697d
[1889.190271] SQUASHFS error: Unable to read fragment cache entry [2f12cf1e]
[1889.190271] SQUASHFS error: Unable to read page, block 2f12cf1e, size 697d
cat: /sys/block/sdb1/removeable: No such file or directory
Please remove the the installation medium, then press ENTER:
```

Then it just hangs and I have to manually shutdown the system. On boot the next time around, the system appears to have no OS installed. I tried going through the process several times. The next time around though the installer seems to identify that Ubuntu is installed because on the Installation type prompt, I see that I can erase Ubuntu and Install Ubuntu.

Any help would be greatly appreciated! I hope this makes sense, and if not I will provide amplifying details as needed.

-Cheers

---

### Post by slickymaster on 2017-06-27
Did you [check the integrity of the Ubuntu ISO]("https://help.ubuntu.com/community/HowToMD5SUM") used?

---

### Post by oldfred on 2017-06-27
I do not know LVM, nor encryption as that is a more advanced install.
Your system is UEFI, did you boot installer in UEFI boot mode to install in UEFI mode? How you boot install media is then how it installs.
If you have an ESP - efi system partition it is then UEFI. 

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Some possibly similar Dell:

 Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial

---

### Post by kylemiller061 on 2017-06-27
I checked the SHA 256 Hash, and it is valid.

---

### Post by kylemiller061 on 2017-06-27
I checked, and my BIOS is set to boot in UEFI mode. When I go to the advanced installation type prompt, I do have a esp efi partition, so I can confirm the UEFI piece. I will take a look at the Boot-Repair links you provided and see if that fixes anything. Thanks for all the Dell specific information.

---

### Post by kylemiller061 on 2017-06-27
I am having issues with both the pastebin option, so here is the output in a document. Sorry for the inconvenience.

Thought I would edit my post from earlier instead of continuing to carpet bomb this thread, but after running the repair application, I can now reboot successfully and run Ubuntu without my bootable USB drive. However I did want to confirm that the following is normal. When I do turn on my computer I receive a prompt with the following options:

*Ubuntu
  Advanced options for Ubuntu
  EFI/ubuntu/fwupx64.efi
  EFI/ubuntu/MokManager.efi
  System setup

When I select *Ubuntu everything functions as it should, but is there a way for this option to be the default and forward me through this without having to choose the option on startup everytime? Can someone tell me what the other options mean?

---

### Post by oldfred on 2017-06-27
You have just a standard install with ESP, / (root) and swap. No LVM nor encryption.

Dell usually just works, some need drivers for nVidia but it does not look like yours uses an add in video card/chip. And some needed updated drivers for newer M.2 that are NVMe devices. But standard M.2 drives look like any other SSD or HDD.

If you press escape key as soon as you start booting do you get grub menu.
And then can you boot recovery mode, in Advanced options menu or second item.

---

