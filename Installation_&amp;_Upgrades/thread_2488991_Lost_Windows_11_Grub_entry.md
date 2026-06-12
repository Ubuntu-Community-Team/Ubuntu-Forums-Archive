---
title: "Lost Windows 11 Grub entry"
date: 2023-07-14
forum: Installation &amp; Upgrades
---

### Post by lvdude on 2023-07-14
Hi fellow Ubuntuns,

     I've tried several different solutions found on various forums to no avail. Most solutions are getting Ubuntu to be seen in the boot entries and not vice-versa. Its a convoluted story FYI.

1. Bought a refurbed Clevo laptop. To my surprise it came with Windows 10 installed; "Oh cool, I don't have to buy it."; proceeded to install a free update to 11 and numerous security patches.

2. Having Ubuntu is a necessity because its my everyday OS since I was a kid. However! I planned to install (2) 2 TB NVME's. So I install one and migrated Window's to that drive.

3. I uninstall the OEM 128 GB drive and replace it with the second 2 TB drive. Now its time to install Ubuntu. I haven't done this in years so I'm rusty.

4. The installer refuses to install Ubuntu on the second blank drive automatically. It keeps insisting on installing it next to Windows on the other drive so I manually forced the root directory onto the drive I wanted.

5. Upon reboot the Windows entry in Grub is gone. The partitions are there, I can see them in Gparted, however I can't get Grub to see them via update or mount them either with Gparted or in the terminal.

6. I know Windows was untouched because I installed Ubuntu on a separate drive, however, lost the Grub entry and want to recover/reinstate it. I have not tried using a windows live usb yet because I don't think it would play well, if at all, with Grub.

Thank you kindly in advance for any and all advice or pointers,
Tiloylin Speigel

---

### Post by ActionParsnip on 2023-07-14
Did you test the windows boot once you switched the drive?
What opinions did you use in the installer?

---

### Post by oldfred on 2023-07-14
Are both installs UEFI? on gpt partitioned drives? And do you have an ESP - efi system partition on Ubuntu drive or only on Windows drive?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

    Note that grub only boots working Windows. Or if Window need chkdsk or is hibernated then grub will not boot it, but if UEFI install, you should still be able to boot from UEFI boot menu.
    Windows updates also turn fast start up back on which is just hibernation. That then grub will not boot it, or any NTFS partitions will not mount read/write in Ubuntu. 

Best to install with Windows drive disconnected. Since often difficult to disconnect NVMe drives, most systems have an UEFI setting to disable or turn off a drive, temporarily.

If version of Ubuntu you used still uses Ubiquity installer, you need to review this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
If latest Ubuntu (not flavors, yet) then it uses newer Subiquity installer which supposedly works ok.

---

