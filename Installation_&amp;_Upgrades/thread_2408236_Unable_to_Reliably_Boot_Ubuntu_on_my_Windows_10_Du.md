---
title: "Unable to Reliably Boot Ubuntu on my Windows 10 Dual-Booted Computer"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by dwygant2 on 2018-12-15
Hi,

I am a Computer Science major who (after taking some classes on systems and architecture) has decided to tinker a little with the operating systems on my computer to better understand how they work.

I began with a computer that ran with Windows 10 and successfully removed it by running Derik's Boot and Nuke.
Then, I burned a USB with Ubuntu 18.04 and successfully installed it onto my computer as the sole operating system. Ubuntu ran fine and operated as expected.
After that, I attempted to reinstall Windows 10 alongside my Ubuntu OS. While Windows 10 was successfully installed, it appeared to mess up my Ubuntu OS.

I have since been attempting to figure out how to successfully dual-boot Ubuntu from Windows 10.

Paying heed to partitions, I have made the following progress:
[INDENT]I created a 300 GB unallocated partition of my SSD from Windows.
I burned an Ubuntu 18.04 iso file onto a USB drive.
I booted from the USB drive and installed Ubuntu, which was placed inside the 300 GB unallocated partition.
[/INDENT]

After Ubuntu has been installed, however, I run into a few issues.

Upon turning the computer on, I am prompted to choose between booting Ubuntu or Windows Boot Manager (I believe this interface is called GRUB2).
While the Windows 10 option still works perfectly fine, I am unable to reliably boot from Ubuntu.

I have gotten it to boot Ubuntu successfully 2 or 3 times (out of roughly 30+ attempts) and the operating system works as expected.
However, the majority of the time I cannot and I am presented with text similar to the following:

[INDENT=2][1.084001] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
[1.084085] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
[1.142468] Couldn't get size: 0xB000000000000000e
[1.820866] nouveau 0000:02:00.0: bus: MMIO read of 00000000 FAULT at 022554
[ IBUS ]
[1.827491] nouveau 0000:02:00.0: bus: MMIO read of 00000000 FAULT at 10ac08
[ IBUS ]
/dev/sdb3: recovering journal
/dev/sdb3: clean, 177875/18423808 files, 3210932/73665792 blocks
[36.044004] watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [plymouthd:352]
[/INDENT]

I have attempted to find a solution online but have not been successful and Ubuntu continues to boot very unreliably.

I have a Dell Inspiron 7559 with an i7-6700HQ CPU @ 2.6GHz. I'm not really sure what other technical information I should provide, but I can definitely provide it if it helps in solving the issue.

Any help in solving this booting problem is much appreciated. I would love to be able to use Linux on my system.

---

### Post by oldfred on 2018-12-15
Have you updated UEFI from Dell? And if an SSD, updated firmware?

Are you installing in UEFI boot mode? Both system need to be in same boot mode.
Did you change drives in UEFI settings from RAID or Intel SRT to AHCI?

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

Some other 7000 series installs

 DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by dwygant2 on 2018-12-15
> **oldfred said:**
> 
Have you updated UEFI from Dell? And if an SSD, updated firmware?

Are you installing in UEFI boot mode? Both system need to be in same boot mode.
Did you change drives in UEFI settings from RAID or Intel SRT to AHCI?



Today I used Dell's SupportAssist to detect any necessary driver updates.
Updating the BIOS was one of the suggested actions that I took.

I believe I am indeed installing in UEFI boot mode.

I am unsure what RAID, SRT, or AHCI are aside from a quick Wikipedia glance.
Sorry, a lot of this is above my head at the moment and this is the first time I'm hearing these terms.

I feel like I have a general understanding of how file systems, partitions, and such work from my intermediate architecture classes. However, implementation in the real world is a whole different ball game.

---

### Post by oldfred on 2018-12-16
More details on Dell AHCI.
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

[https://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](https://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)

[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

