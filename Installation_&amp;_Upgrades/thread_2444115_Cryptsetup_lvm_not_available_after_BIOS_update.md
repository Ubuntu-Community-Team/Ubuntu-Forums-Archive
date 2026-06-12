---
title: "Cryptsetup: lvm not available after BIOS update"
date: 2020-05-24
forum: Installation &amp; Upgrades
---

### Post by eefa1 on 2020-05-24
Hi everyone,

I'm a bit of a newbie and haven't figured out how to fix this problem: I recently installed a BIOS update but afterwards, when I try booting into ubuntu, I get this error: "cryptsetup (nvme0n1p7_crypt): lvm is not available".

For background:
-Lenovo machine
-dual boot with Windows
-I'm able to get past the screen that asks me to choose between booting into Windows or Ubuntu
-had installed ubuntu onto an encrypted partition, following the steps in this I believe [https://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/](https://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/)
-I installed the BIOS update from Windows, and actually also had problems with booting into Windows after the update (was stuck at "Preparing Automatic Repair") but eventually got that fixed and I'm now able to boot into Windows fine

Searching for fixes, one included reinstalling lvm which I tried from the live ubuntu installation on the USB drive I had used, but I was not able to install it. Wondering if anyone might have any tips before I have to reinstall ubuntu altogether? Thanks in advance!

---

### Post by TheFu on 2020-05-25
The initrd needs to understand both mdcrypt+LUKS and LVM.  Instructions from 2012 are pretty old.  I didn't think it was possible to setup a dualboot system with encryption.

So, you'll need to convince **mkinitramfs** to include the tools needed to open the encrypted partition and read the LVM stuff.  I don't know how to do that, but google should help.

---

### Post by eefa1 on 2020-05-25
Thanks for replying! Even though the instructions are from 2012, they still managed to work for me (fortunately!). However I just noticed this thread [https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092) and I'd probably go with that in the future.

In case this helps other people in the future, the fix ended up being: in BIOS setup, had to change SATA mode to AHCI, then it was able to find everything appropriately. I had pretty much given up trying to fix this problem and was about to re-install Ubuntu following the steps in [https://www.reddit.com/r/Lenovo/comments/9ya9np/ubuntu_1804_dual_boot_on_yoga_730_13/](https://www.reddit.com/r/Lenovo/comments/9ya9np/ubuntu_1804_dual_boot_on_yoga_730_13/) when I recalled reading somewhere that updating BIOS causes configurations to reset to their default values so when I came across that step, I decided to see if that would fix things - so happy it did!

---

