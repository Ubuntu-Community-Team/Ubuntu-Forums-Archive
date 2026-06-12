---
title: "Unable to dual-boot (Win7/Ubuntu) on GPT disk."
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by hameerabbasi on 2011-05-20
At first, I installed Windows 7 on my GPT disk on a new partition of about 125 GiB (the (U)EFI system partition (ESP) was created, of course). I intend to dedicate the rest of the space on disk (approx. 173 GiB) to ubuntu. I created a swap file (5000 MB) and the rest, I gave to a root partition. Ubuntu installed okay, but at the end, it gave me a message that GRUB could not be installed to /dev/sda, and that this was a fatal error.

I've tried EasyBCD, it isn't able to modify the ESP, nor have I found any other way top modify it within Windows. I've tried the LiveCD, it doesn't mount /dev/sda or install GRUB2. Now, Ubuntu is installed, just doesn't boot. Please run me through the procedure to install GRUB2 to the EPS, preferably to be loaded through the Windows bootloader like EasyBCD.

I have 2 HDDs, one is 320 GB (the one I with Ubuntu and Windows on it), and the other, 1TB, if it helps. The 1 TB HDD is also GPT and doesn't have an ESP.

---

### Post by srs5694 on 2011-05-20
My suspicion is that when you installed Ubuntu, the ESP wasn't properly flagged in the installer. (It uses some different term to identify it and its role, like "EFI boot partition" or some such.) If the ESP isn't properly flagged in the installation, it won't work.

The only way I know to correct this problem without re-installing is highly technical, and is described [here.](https://help.ubuntu.com/community/UEFIBooting) It's conceivable you could get away without compiling GRUB and just go with a variant of what's described under "Make the firmware launch GRUB2 (U)EFI as default." I believe the files are under /usr/lib/grub/x86_64-efi. If you're up for that, go for it. If not, and if somebody doesn't have a simpler procedure, you're best off re-installing Ubuntu, but being sure you properly identify the ESP during the partitioning phase. (Note that there must be a relatively simple way of doing this from the installer in "live CD" mode; I just don't happen to know the precise commands to use, and it would probably take me an hour or so to figure out the correct procedure by experimentation.)

If you care to study the ESP, you *can* access it from the Ubuntu live CD. You can open a Terminal window and type:

```

sudo mount /dev/sda1 /mnt

```

It may be necessary to change /mnt to some other empty directory, although I think /mnt will work. It's also conceivable, but unlikely, that the ESP is located somewhere other than /dev/sda1. In any event, if you do this, you should see a directory called /mnt/EFI/ubuntu, and it should have a file called grubx64.efi on a properly installed system. If my hypothesis is correct, this directory and file will be missing. If those files are present, then my hypothesis is incorrect, and GRUB was at least partially installed, but something else went wrong -- perhaps in the generation of the GRUB configuration file. If that's the case, post back again with more details about what you find.

---

### Post by laichiwai on 2011-05-20
I have installed Ubuntu 11.04 on a similar configuration. Remember to use UEFI boot for the Live CD bootup in order to let the installation to know you are using UEFI as the boot option instead of BIOS.

The trick is, choose the normal GPT partition holding your /boot directory (mine is same as /) to install Grub2 instead of installing to the MBR or the UEFI system partition.

Afterward, boot again using the Live CD and try Ubuntu. Mount the UEFI system partition as well as /boot directory. Create a grub directory under the EFI directory in the partition. E.g. (hd1,gpt3)/EFI/grub. And then copy all the files from /boot/grub to (hd1,gpt3)/EFI/grub.

Then, follow the post as linked by hameerabbasi to install efibootmgr and install the option into UEFI firmware.

Finally, reboot and either choose to default boot from Grub2 within UEFI firmware manually or press the boot option key during "POST" and choose Grub2 over Windows.

There are a few caveats though. The framebuffer is default to 0 EFI VGA when booting from UEFI installed on HDD. This means, no high resolution console (only text mode). Also, Grub2 manual won't show but default booting to Ubuntu. And the splash screen is pooer VGA resolution instead of the high native resolution of your LCD when booting from Live CD.

---

