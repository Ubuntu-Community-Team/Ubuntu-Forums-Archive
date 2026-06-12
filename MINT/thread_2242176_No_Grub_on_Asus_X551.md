---
title: "No Grub on Asus X551"
date: 2014-08-31
forum: MINT
---

### Post by JohnMorrow on 2014-08-31
Hello:

I have a new laptop, an Asus X551MAV-RCLN06 with Windows 8.1 pre-installed. I am trying to install Linux Mint 17 (MATE edition), which is based upon Ubuntu 14.04. My goal is a dual boot system. I have tried several times, and Mint seems to be on the hard drive, but I cannot get the Grub menu to appear. On most attempts I used the Boot-repair program afterwards but I could not get grub to reinstall. Current status of the system is here: [http://paste2.org/nyPZXW7N](http://paste2.org/nyPZXW7N). 

What I have done:
1. Shrank the C: drive the maximum recommended amount using the Windows "Disk Management" utility.
2. Disabled "Secure Boot", and "Fast Boot" in the UEFI BIOS. 
3. Enabled CSM (Legacy mode), also in the BIOS, thus disabling EFI.
4. Burned the Mint 64-bit edition to a USB drive.
5. Booted from the thumb drive and installed Mint. Note that the only way I could boot from the USB stick was to implement steps 2 and 3, above.
      a.  In consecutive attempts I have created both Primary and Logical partitions for the root (/), /home, and BIOS-EFI partitions. In the last attempt, I created a 110MB Primary and formatted it FAT32 with GParted. Then booted from USB, and made sure I marked this partition (/dev/sda6) as the place to install the bootloader. In previous attempts I had marked /sda1 without success.
      b.  I have run the Boot-repair program after booting from the USB stick but have been unable to repair (or activate) Grub. I used first the default option ("Recommended repair"), then tried to pick out the appropriate options in the advanced menu, with the latest result shown in the pastebin link, above. It has displayed some troubling error messages about dependencies and not being able to reinstall grub in /dev/sda6.

UEFI BIOS setup - there is an option in the BIOS (Aptio Setup Utility to be precise) Boot menu menu to prioritize boot devices. Called "Boot Option Priorities", I need to set the USB stick as "Boot Option #1" before I can boot the live CD. I was expecting to find Grub, or a Linux listing, here. There is also a menu entry to "Add New Boot Option", which would then become options, 2, 3, 4, etc. To create a new Boot Option, you are prompted to select the "Path for Boot option". The path menu prompts me to select from one of two file systems, one on "Part 1", and the other on "Part 6".    After choosing the file system, the next menu item prompts you to select a boot file. I am totally shooting in the dark at this point.

Any advice is welcome.

Thanks!

---

### Post by JohnMorrow on 2014-09-01
So the key question is still how or where to install Grub, or how to repair it so it works.

I found a tutorial which describes what I am doing here: [http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/]("http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/")

The instructions say to:  Make a note of the partition marked as type efi. "That takes the place of the traditional /boot partition. It will come into play at the end of this step." and "Did you notice that we did not create a boot partition? That&#8217;s because on these systems, the EFI partition, which on the system used for this tutorial is /dev/sda2, serves as the boot partition. Boot files for GRUB will be installed there. GRUB (the GRand Unified Bootloader) is the boot program used by Linux Mint and virtually all Linux distributions. Before clicking Install Now, change the entry in the &#8220;Device for boot loader installation&#8221; from /dev/sda to /dev/sda2."

There was no partition marked efi displayed on the installer's partitioning screen. I chose /dev/sda1, which is a 101MB FAT partition, where I think the Windows bootloader lives. Still no Grub menu. I watched a command along the lines of 'install-grub /dev/sda1' execute, so I think its there. I will reboot with the linux mint usb and grab a new Boot-repair report and put it on pastebin, and will put the link here.

---

### Post by JohnMorrow on 2014-09-01
Here is the Boot-repair report, after installing Grub to /sda1, without running any repair utility after Mint was installed. [http://paste2.org/8tLyKMFm](http://paste2.org/8tLyKMFm)  

Any advice is welcome!

---

### Post by JohnMorrow on 2014-09-02
Well I hosed the system today, trying to install the bootloader at /dev/sda. Boot-repair could not repair it and the hard drive no longer showed up in the EFI BIOS. So I booted from the Restore USB drive I made earlier and restored the laptop to factory defaults. I'm back to square one, but I think I should try the "Install alongside Windows" option in the Mint setup, instead of the "Something else" option. Film at 11.

BTW, a little feedback would be nice so it doesn't feel like I'm out here all by myself. Just sayin'....

---

### Post by JohnMorrow on 2014-09-02
Finally got Mint installed. Happy Day. The difference is that "efi" showed as the "Partition Type" column in the Mint installer, and I put the bootloader in /dev/sda2, the one marked as efi. Originally (first attempts), no partition was marked as efi. "Install alongside Windows " was not one of my choices. I think this only shows up if you don't do any partitioning ahead of time, which I did. I followed these directions: [http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/)

---

### Post by aaronp on 2014-10-17
Hi @JohnMorrow. Sorry to be the first response here for you and asking for help, not providing a solution but I have the exact same laptop and trying to do the exact same thing as you (except Cinnamon instead of MATE). I also came across the latest link you posted and followed these instructions but have not managed to get to a Grub menu.
If I enter the UEFI (BIOS) and turn on Secure Boot then I go straight into Win8.1. If I turn it off and tell it to being up CSM menu then I go straight into Mint. I haven't been able to figure out which key to press to get to the boot list and I'm also not convinced I've done the right steps so far to get to a point where that would have both options to choose from.
Like you, I didn't get an EFI option when partitioning, but noted that the FAT32 partition /dev/sda1 looked like it was the right one so I stuck the bootloader there.
I had partitioned my drives in Win 8.1 before trying to install Mint - are you saying this is the problem?
thanks
Aaron

---

