---
title: "Ubuntu 21.04 no longer boots"
date: 2021-10-13
forum: Installation &amp; Upgrades
---

### Post by 80sdweeb2 on 2021-10-13
I was having trouble with my mouse pointer, jumping around, slowing down. Rebooted and I got a blank screen with what looks like a cursor in the very top left corner. I tried to re-install 21.04 from USB, and I get the error:

"No EFI System Partition was found. This system will likely not be able to boot successfully, and the installation process may fail.

Please go back and add an EFI System Partition, or continue at your own risk."

I'm not really clear on what to do, I did realize that I had run out of space (cause of initial slowing and failure to reboot) but after making space (using live USB boot) still won't boot.

Thanks for any recommendations! Need my laptop (not a dual boot, just Ubuntu.)

---

### Post by zebra2 on 2021-10-13
If your bios is set to legacy mode you can ignore those warnings and continue the installation. You may get an additional warning but it doesn't matter, the system will boot. I would be interested in knowing your partition type and if Windows is involved in this. Ubuntu doesn't need secure boot nor UEFI.

---

### Post by oldfred on 2021-10-13
If UEFI hardware, usually better to install in UEFI boot mode.
How you boot install media is then how it will install & then boot after install.
With UEFI you should use gpt partitioning and need an ESP - efi system partition which is FAT32 and often 300 to 500MB, but will share one with Windows if already one on the drive.

Post this from live installer in live mode:
sudo parted -l

What brand/model system?
What video card/chip?

---

### Post by 80sdweeb2 on 2021-10-14
It's a Dell Latitude E5570, was a Windows laptop, but I replaced that with Ubuntu 21.04. It does have a fat32 system partition. When I look at the partition table, I see:

/dev/sda1 fat32 /boot/efi

So like I said, I thought that re-installing would solve it, but I get the error message. Not sure what step to take next to get past the error. I ran the "boot-repair" utility in hopes that it would fix it, but I don't understand this message it gave after saying it was successful: 

"You can now reboot your computer. 

Please do not forget to make your UEFI firmware boot on the Ubuntu 21.04 entry (sda1/EFI/ubuntu/shimx64.efi file) !"

I don't know if that helps. I really would like to get back into my files before a job interview I have in a few days.

I'll look at that UEFI boot page, but it gets frustrating to have to become an expert at each part of Linux just to get it to work. Most places I read about UEFI boot stuff keep mentioning dual-boot, which is not what I'm doing. 

Thanks,
Scott in Snowflake AZ

---

### Post by oldfred on 2021-10-14
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2021-10-14
>  did realize that I had run out of space (cause of initial slowing and failure to reboot) 

You can easily ascertain how much space you have left on a mounted partition which will always include the / system partition.  If you are still able to boot the system, the first place to look to delete files is in the /var/log directory.  You can also do this using a live cd/usb.

>   I ran the "boot-repair" utility in hopes that it would fix it 

If you are not familiar with Grub, you should follow the instructions on the boot repair site and select the Create Bootinfo Summary option and post the link you are given when it has finished running. Boot repair gives a lot of useful information to help users repair Grub but for that to work, you need some knowledge of Grub.

>  Please do not forget to make your UEFI firmware boot on the Ubuntu 21.04 entry (sda1/EFI/ubuntu/shimx64.efi file) !"

You need to do that (select the proper boot option) from your BIOS firmware and the way to access it varies by manufacturer.  I don't use Dell so can't help with that.  Your best option is to follow the advice of oldfred in the post above.

---

