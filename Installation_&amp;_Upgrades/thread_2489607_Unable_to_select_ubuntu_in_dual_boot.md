---
title: "Unable to select ubuntu in dual boot"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by caterhamfan on 2023-08-04
Hey all,

So, I had a screen replacement done by PCSpecialist. They replaced the screen but seemed to have messed up my system. I had a dual boot into Ubuntu 22.04 and Windows 11. Now even after repairing with the recommended settings using the live cd and boot repair my laptop boots into Windows immediately.

I'm completely at a loss. I have the paste from the boot repair here - [https://paste.ubuntu.com/p/6mppnMSffV/](https://paste.ubuntu.com/p/6mppnMSffV/)
I'd be grateful if someone can help me get my dual boot back.

Thank you,

---

### Post by oldfred on 2023-08-04
Both Windows & Ubuntu/grub on major updates will reset UEFI to have themselves as first in boot order.
You then can reset that, most systems work with efibootmgr (except HP). Or you boot into UEFI settings (not menu) and change boot order in boot settings menu.

Also both Windows & Ubuntu may update UEFI, which often resets many settings to defaults. that may turn UEFI Secure Boot back on, and change drives back to RAID, if you had to change to AHCI. You need to review settings, if  those kinds of issues.

You have NVMe drive, but UEFI boot thru an ESP on sda.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by mIk3_08 on 2023-08-05
> **caterhamfan said:**
> Hey all,

So, I had a screen replacement done by PCSpecialist. They replaced the screen but seemed to have messed up my system. I had a dual boot into Ubuntu 22.04 and Windows 11. Now even after repairing with the recommended settings using the live cd and boot repair my laptop boots into Windows immediately.

I'm completely at a loss. I have the paste from the boot repair here - [https://paste.ubuntu.com/p/6mppnMSffV/](https://paste.ubuntu.com/p/6mppnMSffV/)
I'd be grateful if someone can help me get my dual boot back.

Thank you,
I prefer to use boot loader for this. There are a lot of boot loader you can use like, BURG, Syslinux, rEFInd, Grub2, Clover EFI Bootloader, systemd-boot (Gummiboot) In my case, I have used GNU GRUB it works perfect for me. Regards and cheers.

---

### Post by mIk3_08 on 2023-08-05
Redundant Post due to some interruption Please ignore or admin please Delete

---

### Post by caterhamfan on 2023-08-06
Thank you everyone.
So, it turned out to be in the boot order. Something I didn't see.
Thankful for your help

---

