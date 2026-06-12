---
title: "Can't Boot Ubuntu 20 (or any distro) from Flash Drive (multiple flash drives tried)"
date: 2020-08-30
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2020-08-30
I'm on a HP ProBook 450 G3

It came with UEFI. But I was already running (not multiboot) Ubuntu 16. I decided to upgrade and do a fresh install of Ubuntu 20. I installed Ubuntu 20 to the root partition. Now I can't  boot into anything, not even to a flash drive.

Trying to boot from Legacy - Samsung SSD 850 EVO 1TB

takes me to 

"error: file '/boot/grub/i386-pc/normal.mod not found

Entering rescue mode ...

grub rescue>



Right now I am able to use F10  to get to the Setup Menu. Then I can get to 

Advanced / Secure Boot Configuration 
It is set to: Legacy Support Enable and Secure Boot Disable. 

I guess I did that shortly after buying the laptop and installing Ubuntu.



Under Advanced / Boot Options I see that "USB Storage Boot" is checked, as is CD-ROM.



Then I reboot and press F9 to get to the

 Boot Menu. It doesn't show my USB Flash drive.

I only see:

Legacy: hp DVDRW

Legacy N/W - Intel Corporation: Realtek PXE 

Legacy - Samsung SSD 850 EVO 1TB

Why is this?

---

### Post by webmanoffesto on 2020-08-30
Never mind, I successfully installed from an old Ubuntu 14 DVD or CD. Now I'm upgrading, 14-16, 16-18, ...

---

### Post by furesuka on 2020-08-31
Remember to mark the thread as solved

---

