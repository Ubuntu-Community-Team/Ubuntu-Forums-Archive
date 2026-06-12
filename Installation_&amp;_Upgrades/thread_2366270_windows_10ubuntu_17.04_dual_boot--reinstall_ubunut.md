---
title: "windows 10/ubuntu 17.04 dual boot--reinstall ubunutu"
date: 2017-07-15
forum: Installation &amp; Upgrades
---

### Post by conomara on 2017-07-15
Hey,
First, big thanks in advance for reading. 
I am trying to  reinstall ubunutu as a dual boot  on a machine with one SSD, windows 10 and ubunutu already on it, secure boot disabled, UEFI  mode on. I installed ok the first time, then screwed up trying to  install nvidia drivers. I figured the easiest option was to reinstall  Ubuntu cos it was early days and I had nothing to loose.
When I try to install I get the following warning (see image)
It tells me 
[B]""The partition table format in use on your disks requires you to create a separate partition for boot loader code. This partition should be marked as an EFI boot loader and should be at least 35 MB in size. Note that this is not the same as /  boot.
If you do not go back and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition.""
[/B]
When I look a the window with the disk and partitions I can see
The root partition is 
/dev/nvme0n1
and I can see already (this is a reinstall)
/dev/nvme0n1p1 fat32 /boot/efi   .....................524MB (size:40MB used) (system:windows Boot Manager)
From what I've read I should be able to install the boot loader on the same partition as the windows boot loader??
However I get that scary warning (above) when I try that.
Since this is my second install of ubunutu here, this should be pretty straight fwd, but not sure what to do.
Anyhow any suggestions very welcome

[ATTACH=CONFIG]276009[/ATTACH]

---

### Post by oldfred on 2017-07-15
Whether UEFI or BIOS you always install grub2 boot loader to a drive like sda, sdb not a partition like sda1 or sda2.
You have newer NVMe drive, so you install to drive like /dev/nvme0n1 which is drive. And p1 or p2 at end is the partition of nvme0n1.

But with UEFI installs, it normally with sda type drives does not matter what you suggest, it finds first ESP - efi system partition and correctly installs a new folder /EFI/ubuntu and the boot files into that.

Not sure why it then is not correctly seeing your current ESP.
I would go ahead with install and then see if Boot-Repair's advanced mode can fully install grub. 
And if /EFI/ubuntu exists, you may only need to edit /EFI/ubuntu/grub.cfg with correct new UUID and partition to get it to boot, but may also need to add entry to UEFI. So better to get grub to install.

What brand/model system?

---

### Post by conomara on 2017-07-16
Hello [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711"),
Thanks alot of your advice, the system is a dell Precision 5510. Yeah, /dev/nvme0n1 is where I understood (in my basic capacity) 
that it needed to be installed to. I'm double/triple checking the boot mode now to make sure its correct (uefi usb instead of bios network)
Any other ideas about potential ways of getting rid of scary warning before I proceed appreciated

Conor

---

### Post by oldfred on 2017-07-16
Have you switched drive to AHCI, that seems to be common with these newer Dells.
Unless drives are RAID 0. 
Have you updated UEFI from Dell and the firmware for the NVMe drive?

But either way make sure you have good backups. 
My Inspiron-3647 wanted a Dell backup, a Windows backup & I made my own full image backup with Macrium Reflect. And all that took several flash drives & DVDs.

       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 
        Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN) 
            Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642) 
            Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

### Post by conomara on 2017-07-16
Thanks for this [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")
This info will take a bit of digesting, some I am familiar with but some not.
I will read through and post again later one I know where I am.
Thanks alot

---

