---
title: "Win 7 Ubuntu 18.04 dual boot UEFI"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by andreberg on 2020-01-21
Soooo... let's go. Win7 has run out of support and I'm pulling the plug on the OS.

I've been trying to install Ubuntu alongside my Win7 install for quite some time (months), unsuccessfully until now. Every time I install I boot from a live USB stick, install goes flawlesslly, but when rebooting it dives directly into Win7.

After pressing ESC key on boot, the only bootable OS showing up is Win7.

My BIOS is set to boot in EFI mode. So I burned an ISO image using GPT EFI. USB boots OK, but normally the machine boots directly into windows. Also tried an ISO image burnt in MBR and BIOS/EFI using Rufus. No luck.

There is no option in the BIOS to select which OS to boot first.

There is no Secure Boot or Fast Boot option either in BIOS or Windows.

I thoroughly read all of what I could find regarding UEFI and dual boot. As far as I can see, my copy of Win7 boots in EFI mode, thus Ubuntu should do the same. 

Installed Boot-Repair, but before running a black box process (at least to me) I prefer to seek some advice. So I have not tried repairing the boot loader.

My partition info shows an EFI system partition 260Mb in size.

Attached is the result of the Boot-Repair's Bootinfo Summary 

[http://paste.ubuntu.com/p/GpkfQVCfTn/](http://paste.ubuntu.com/p/GpkfQVCfTn/)

Appreciate any insights this forum can give me.

---

### Post by oldfred on 2020-01-21
It looks like you have a standard UEFI install of Ubuntu, but are missing the ubuntu entry in UEFI.
sudo efibootmgr -v

Line 682 from report:

```
=================== efibootmgr -v
BootCurrent: 0000
BootOrder: 0000,0001
Boot0000* EFI USB Device    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(0,0)/HD(1,GPT,d2f4dc3f-67d5-4d36-8f36-4235ff10f6af,0x800,0xf097df)RC
Boot0001* Windows Boot Manager    HD(2,GPT,09ce7cd2-80cd-4e4c-9d52-05e2e41c14df,0x25cd001,0x82001)/File(EFIMicrosoftBootbootmgfw.efi)RC

```
You can let Boot-Repair reinstall grub which uses efibootmgr to put entry into UEFI or try the entry to see if it works.
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP. Since your ESP is sda2 entry is /dev/sda -p 2 at end.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected)


What brand/model system? Some have more issues than other.
And have you updated UEFI to newest available for your model from vendor? That is required anyway.

---

### Post by andreberg on 2020-01-21
Hi OldFred, thanks for the reply.

My machine is a Sony Vaio around 6-7 years old running Win7 OEM.

BIOS/UEFI is updated to the latest version as per vendor option (notebook comes with proprietary software that allows you to search for driver/software/bios updates).

As per your instruction I ran the command

```

sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sda -p 2

```

and now the output of 

```

sudo efibootmgr -v

``` 

is

```

BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,GPT,d2f4dc3f-67d5-4d36-8f36-4235ff10f6af,0x800,0xf097df)RC
Boot0001* Windows Boot Manager    HD(2,GPT,09ce7cd2-80cd-4e4c-9d52-05e2e41c14df,0x25cd001,0x82001)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0002* ubuntu    HD(2,GPT,09ce7cd2-80cd-4e4c-9d52-05e2e41c14df,0x25cd001,0x82001)/File(\EFI\ubuntu\shimx64.EFI)

```

Will reboot and see what do I get and post back.

Thanks

---

### Post by andreberg on 2020-01-21
Back with news.

After rebooting the notebook boots straight into Win7 (good news at least that that OS still boots).

However, the option of booting either into windows or ubuntu does not show up. I pressed ESC at the splash screen and the only thing I get is the "Windows Boot Loader" offering to boot Win7.

I fired the USB version of ubuntu and ran sudo efibootmgr -v and got the same list as before, without the ubuntu option labeled Boot0002* which had been previously added.

Perhaps I was not clear enough before. I cannot boot Ubuntu from the HDD, I can only boot from the live USB stick.

I ran Boot-Repair and got this

[http://paste.ubuntu.com/p/jZx5h94DMv/](http://paste.ubuntu.com/p/jZx5h94DMv/)

As far as I see, anything I do while running on the live version won't commit to disk (e.g. the efibootmgr instruction).

I rebooted and dived straight into Win7 again, no ubuntu boot option.

I used a usb stick with ubuntu ISO configured with GPT partition scheme for UEFI for installation. I read in some post that GPT won't work with MBR. Might be that is the problem. Perhaps If use a MBR partition scheme for UEFI it will boot? I'm not sure what the partition scheme on the Win7 OS is.

My machine is a Sony VAIO S Series, specifically, model SVS13112FXB. Intel Core i5 2.5GHz, 12Gb RAM, and a 1Tb SSD. Thought this last part may be important as per [URL="https://ubuntuforums.org/showthread.php?t=2147295"]https://ubuntuforums.org/showthread.php?t=2147295

Also, I found this post [https://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](https://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi). My partition table is simpler though.

Will the suggestions of the first reply (that is, renaming and copying/pasting files work).
[/URL]
Thanks

---

### Post by oldfred on 2020-01-21
My older notes had Sony with HP as one that modified UEFI to only boot Windows by description. That is not allowed per UEFI standard, but that is what you have. Only valid description is "Windows Boot Manager".  Some with only Ubuntu change description from ubuntu to Windows but have that description boot using shim or grub to boot Ubuntu.

Another work around is most UEFI will allow an internal drive to boot with the fallback or hard drive boot entry. That entry is the same as what UEFI uses to boot external drives or /EFI/Boot/bootx64.efi. Grub now adds bootx64.efi to /EFI/Boot. Originally that file is often just a copy of Windows .efi boot file.

Old instructions and very old versions of Boot-Repair copied grub to be the Windows boot file in the /EFI/Microsoft folder. Its just that Windows updates overwrite that. And if Windows breaks, grub will not boot Windows and then you have no way to boot Windows. Or a bunch of restoring/repairing Windows .efi boot files to temporarily boot Windows to fix it. 

Do you have /EFI/Boot/bootx64.efi but no UEFI hard drive boot entry.
But some UEFI need specific description for the drive entry.
You can try this:
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2

Another is to add an entry to BCD in Windows that does a reboot. UEFI has a one time reboot option.
[https://ubuntuforums.org/showthread.php?t=2227580](https://ubuntuforums.org/showthread.php?t=2227580)


> One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
[quote]The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
[/QUOTE]

rEFInd is another work around:
Sony VAIO E-series  19.10  Used rEFInd, could not otherwise change boot order
[https://ubuntuforums.org/showthread.php?t=2431243](https://ubuntuforums.org/showthread.php?t=2431243)

---

### Post by andreberg on 2020-01-23
oldfred,

I followed the instructions per this thread [https://ubuntuforums.org/showthread.php?t=2227580&](https://ubuntuforums.org/showthread.php?t=2227580&) which you kindly mentioned. The thread says to create an ext2 250MB partition labelled as /boot, plus the remaining swap and / partition for the OS. Then select /boot partition to install the bootloader in.

However, install does not allow me to select that particular partition. It simply does not appear as an option (see attached pic). It should be /dev/sda6, but the only available options are /dev/sda4, 7 and 8.

Any ideas?

---

### Post by oldfred on 2020-01-23
I do not recommend the separate /boot partition. 
It is standard with LVM or LVM with encrypted installs, but I am not sure that is required anymore either. Grub can boot encrypted drives now at least in some cases.
Standard desktops do not need /boot unless very old BIOS only based system with BIOS limits on where boot files are on drive.

---

### Post by andreberg on 2020-01-24
Made it! Thanks for your help oldfred!

After following the instructions everything works fine. I can dual boot between Ubuntu and Windows through Grub without problems.

Best

---

