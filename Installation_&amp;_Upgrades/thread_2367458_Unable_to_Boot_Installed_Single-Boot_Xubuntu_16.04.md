---
title: "Unable to Boot Installed Single-Boot Xubuntu 16.04 (UEFI OEM Windows 10 System)"
date: 2017-07-30
forum: Installation &amp; Upgrades
---

### Post by ssnover on 2017-07-30
Hello,

I recently decided to attempt to install Xubuntu 16.04 over my previous Windows 10 OS that shipped on my Acer Aspire E15 laptop with UEFI firmware. After creating an install media on a flash drive, I followed the procedure to completely erase the Windows OS and install Xubuntu on the drive in it's place. However, on restart it shows no bootable device. How can I get the bootloader registered with the firmware?

Some settings in the InsydeH20 Setup Utility that might be relevant:
- Boot Mode: UEFI
- Secure Boot: Disabled
- Supervisor Password Is: Set
- Secure Boot Mode: Standard (a number of greyed out options underneath here; erasing secure boot settings, selecting trusted UEFI files, factory restore to secure boot settings)

Note I am not trying to keep the Windows 10 OS for dual boot, it is gone already. Is there a way I can circumvent whatever issues the UEFI firmware introduces directly?

---

### Post by ubfan1 on 2017-07-30
Did your install create (or leave the one existing) in place?  Does it have an /EFI/ubuntu directory with grubx64.efi and (optionaly) shimx64.efi?  Did you set trust on the efi files, or was that option greyed out (maybe because they weren't there?)?  Did you try the EFI menu (some function key at power-up) to allow selection of boot device or OS, and select ubuntu?

---

### Post by ajgreeny on 2017-07-30
Acer machines in UEFI mode require a trust setting in the EFI bootloader system contrary to the UEFI standard.

See all the info in the thread from oldfred at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
> All Acer require supervisor password & enable "trust" on Ubuntu/grub efi files. Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238)

---

### Post by oldfred on 2017-07-30
Might be this? :)
[https://askubuntu.com/questions/941296/how-to-boot-xubuntu-16-04-from-uefi-firmware](https://askubuntu.com/questions/941296/how-to-boot-xubuntu-16-04-from-uefi-firmware)

Just for posterity here, when others search forum.

---

### Post by ssnover on 2017-07-30
> **oldfred said:**
> Might be this? :)
[https://askubuntu.com/questions/941296/how-to-boot-xubuntu-16-04-from-uefi-firmware](https://askubuntu.com/questions/941296/how-to-boot-xubuntu-16-04-from-uefi-firmware)

Just for posterity here, when others search forum.

Good eye, that's me alright.

The solution was as mentioned above, I needed to use secure boot options to trust the grubx64.efi file. I'm unsure what sequence exactly allowed me access to those, as they were greyed out when I initially attempted to do so.

---

