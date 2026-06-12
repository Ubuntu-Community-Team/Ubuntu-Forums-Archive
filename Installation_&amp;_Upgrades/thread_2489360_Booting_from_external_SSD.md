---
title: "Booting from external SSD"
date: 2023-07-27
forum: Installation &amp; Upgrades
---

### Post by anthony1677 on 2023-07-27
Hi Team,

I installed Ubuntu 22.04 on my external SSD using a laptop with Windows 11. 
Post which I have installed programs and done extensive work on the Ubuntu system.

I then tried to boot it from another PC, where it did not boot. I had mistakenly installed grub or updated boot 
on the Windows system.

Now I cannot boot from the SSD on any other system. Is there any way that I can set boot on the SSD without reinstallation?
I do not want to make any changes to the Windows 11 laptop as it is being used for online schooling by my kid.

Any advice or help would be greatly appreciated.:KS

Regards,
Anthony

---

### Post by tea for one on 2023-07-27
Can you still boot into Windows 11 without the external SSD attached?

---

### Post by oldfred on 2023-07-27
You need an ESP on external drive.

External drives in UEFI directly boot from a drive type entry just like booting the live flash drive installer.
That entry is /EFI/Boot/bootx64.efi, but full installs also need /EFI/ubuntu folder.
So you can create an ESP, FAT32 with boot,esp flags on external drive. Normally first partition, but does not have to be unless drive is huge.

Then copy /EFI/ubuntu & /EFI/boot folders from existing ESP on Windows drive and update /etc/fstab with UUID of external drive's ESP.

Once fstab is updated, you can just reinstall grub using all the standard defaults. But if you do not boot from your install, then you need Boot-Repair or chroot into install using live installer to do a full reinstall of grub.

sudo grub-install

---

