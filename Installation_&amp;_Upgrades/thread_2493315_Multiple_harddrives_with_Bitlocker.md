---
title: "Multiple harddrives with Bitlocker"
date: 2023-12-11
forum: Installation &amp; Upgrades
---

### Post by timswait on 2023-12-11
I am looking to install Ubuntu as Dual Boot alongside Windows. The machine has several physical harddrives, at the moment all have bitlocker enabled. Is it possible to only turn bitlocker off on one harddrive and install Ubuntu onto that drive (that drive can be completely wiped) while leaving all the other drives (including the C:\ drive which has the bootmanager and Windows OS on it) with bitlocker turned on? Is there a tutorial that can guide me through how to set up the partition and boot flags, etc to do this?

---

### Post by tea for one on 2023-12-11
> **timswait said:**
>  Is it possible to only turn bitlocker off on one harddrive and install Ubuntu onto that drive (that drive can be completely wiped) 
The foolproof way is to isolate, de-activate or physically remove all the disks other than your target disk.
Then, there is no need to disable bitlocker.

Hopefully, your existing Windows OS is installed in UEFI mode and Ubuntu should be installed in similar fashion.
Allow the Ubuntu installer to automatically create the partitions (inc. an EFI System Partition).

---

### Post by timswait on 2023-12-11
OK, so then I guess I can't use grub to choose between which OS to boot into, but presumably instead when I reactivate the harddrives I'll just use the BIOS to choose which OS to load, yes?

---

### Post by tea for one on 2023-12-11
Each OS on a separate disk will allow independent boot via your dedicated UEFI access key.
After you have installed Ubuntu, you can then edit grub to add Windows to the grub menu (user choice).
Also, you will have to decide which disk has priority boot:-
[LIST]
[*]Windows Boot Manager
[*]Ubuntu with grub (with or without Windows)
[/LIST]

---

### Post by MAFoElffen on 2023-12-11
Change your perception of "drives"... MS has clouded description that for their OS, which is not reality nor the truth.

What Microsoft refers to as a drive, Drive D, drive D, etc. Are actually partitions on a drive. Bitlocker encrypts partitions on a drive, just like LUKS does. It does't not affect the whole drive.

You can install Ubuntu right alongside Windows, whether it is on the same drive or not, whether it has bitlocker enabled or not. 

The two things you need to ensure, is that Windows has it's fastboot (hibernation) turned off, and that the BIOS SATA Mode is set to AHCI, rather than RAID. There are ways to do those without wrecking your Windows Install. 

Another thing I do as a general practice when working on a computer with Windows Pro, and Bitlocker encrypted containers, is to go into Windows Control Panel, and suspend the bitlocker encryption until I am through working on it. Just less risk of being locked out, if you do that.

Safer, and less long-range issues, if you can keep your Windows install isolated to it's own drive, that you can install Ubuntu to another. I find that during Windows updates, that changes the UEFI EFI partition, that I have less booting problems if I set it up that way.

---

### Post by timswait on 2023-12-13
Thanks for your advice. Actually I don't really mind selecting which drive to boot from in BIOS when I turn on the machine, so having the two OS on different physical hard drives and just choosing from BIOS which one to boot is fine for me, so I went ahead.

I physically unplugged the drive that contained the Windows bootloader and C: drive partition while I was installing Ubuntu to reduce the risk of anything going wrong. I installed Ubuntu 22.04 on a completely different physical drive. I was prompted in the install process to create a password for the Secure Boot, which I did. When I rebooted then I selected 'Enroll MOK' and then clicked through some options that I don't remember exactly. It didn't seem to give any error messages at that stage but also didn't confirm that it had actually done anything successfully either!

When I rebooted then I got an screen saying "Secure Boot Violation. Invalid signature detected: Check Secure Boot Policy in Setup". However on clicking 'Continue' then it booted fine into Ubuntu and everything appears to work (including nvidia 3rd party drivers). So it seemed OK, I thought I'd just ignore the error message. I then shutdown, plugged the Windows drive back in and rebooted. It went into Windows fine, no problem. HOWEVER when I then rebooted again and chose the Ubuntu drive to boot to I got the same Secure Boot Violation message, but now clicking OK doesn't continue the boot into Ubuntu, it brings up a Windows Bitlocker window asking me to enter the key for that drive. I don't actually want to have anything to do with the Windows drive if I boot into Ubuntu, but I can't seem to make it ignore it if it's plugged in. The only way I can boot into Ubuntu is to either physically unplug the Windows drive, or to turn off Secure Boot, but then I can't boot into Windows.

So it seems that Secure Boot isn't properly configured for my Ubuntu install. Is there anything else I should have done?

```
mokutil --sb-state
``` returns: ```
SecureBoot enabled
```

```
sudo dmesg | grep "Secure Boot"
``` returns:

```
[    0.000000] Kernel is locked down from EFI Secure Boot mode; see man kernel_lockdown.7
[   13.936749] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing: xxxxxxxxxxxxxxx'
[   13.936783] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2017): xxxxxxxxxxxxxxxx'
[   13.936814] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (ESM 2018): xxxxxxxxxxxxxxx'
[   13.936847] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2019): xxxxxxxxxxxxxxxxxx'
[   13.936881] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v1): xxxxxxxxxxxxxxxxxxxxxx'
[   13.936924] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v2): xxxxxxxxxxxxxxxxx'
[   13.936956] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (2021 v3): xxxxxxxxxxxxxxxxxxxxxxxxxxxx'
[   13.936990] Loaded X.509 cert 'Canonical Ltd. Secure Boot Signing (Ubuntu Core 2019): xxxxxxxxxxxxxxxxxxxxxx'
[   13.961800] integrity: Loaded X.509 cert 'ubuntu Secure Boot Module Signature key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'

```
(NOTE: I have 'xxxxxxxxxxxx'd out the hash signatures for security, but they are all there.

To me that looks OK, so why I am getting this 'Secure Boot Violation' error on startup?

---

### Post by MAFoElffen on 2023-12-13
> **timswait said:**
> When I rebooted then I got an screen saying "Secure Boot Violation. Invalid signature detected: Check Secure Boot Policy in Setup". However on clicking 'Continue' then it booted fine into Ubuntu and [COLOR=#ff0000]everything appears to work (including **nvidia 3rd party drivers**)[/COLOR].
I think that is where the problem might be. With the NVidia drivers not getting signed or the keys for those not being enrolled.

To use linux with an nvidia driver and secure  boot mode on, the nvidia driver has to be signed.   You can usually trigger the  signing process by turning on secure boot, booting into Ubuntu, open a terminal session, then dpkg-reconfigure the driver.  It should prompt for a one shot password  that you need to give the MOK enroller next time you boot.  If you miss  the MOK prompt, you can try again, or try to manually enroll it.

You should be able to do that via
```

apt list nvidia-driver-* --installed
#note which package is installed. Use that in the next command below...

sudo dpkg-reconfigure nvidia-driver-<version>

```
If not signed, it should ask you for a MOK password, to enroll the key to sign the driver on the next reboot.

FYI... If you edit file /etc/default/grub
```

sudoedit /etc/default/grub

```
and uncomment / delete "#" cahracter, in front of this line
```

#GRUB_DISABLE_OS_PROBER=false

```
So it reads as 
```

GRUB_DISABLE_OS_PROBER=false

```
Then do
```

sudo update-grub

```
Then it will add Windows to the Grub2 boot menu... I find that more convenient, and practical.

---

### Post by timswait on 2023-12-20
Thank you for this, I'll try the grub update too when I get the secure boot issue resolved. Unfortunately it doesn't seem to be the nvidia driver at issue, the reconfigure command returns nothing (no errors, but no request to set up a password) and rebooting after it doesn't give any MOK enrollment options. The "Additional Drivers" GUI shows the nvidia driver as the only proprietary driver in use.

---

### Post by timswait on 2024-01-02
Does anyone else have any suggestions I could try?

---

### Post by MAFoElffen on 2024-01-02
Make sure that SecureBoot is enabled
```

sudo mokutil --sb-state

```
Then check if mokutl is installed
```

apt list mokutil --installed

```
If not, install it
```

sudo apt-get update
sudo apt-get install mokutil

```
Cehck to see if the key is generated...
```

ls /var/lib/shim-signed/mok/MOK.der

```
If not do this
```

sudo update-secureboot-policy --new-key

```
Then set it up to enroll it
```

sudo mokutil --import /var/lib/shim-signed/mok/MOK.der
sudo mokutil --sb-state
sudo reboot

```
Follow prompts to enroll the key

---

### Post by timswait on 2024-01-03
Thank you, but all of those things are already done.
```
sudo mokutil --sb-state
```
returns:
```
SecureBoot enabled
```

```
apt list mokutil --installed -a
```
returns:
```
Listing... Done
mokutil/jammy-updates,jammy-security,now 0.6.0-2~22.04.2 amd64 [installed]
mokutil/jammy 0.4.0-1ubuntu2 amd64

```

```
ls /var/lib/shim-signed/mok/MOK.der
```
returns:
```
/var/lib/shim-signed/mok/MOK.der
```

```
sudo mokutil --import /var/lib/shim-signed/mok/MOK.der
```
returns:
```
SKIP: /var/lib/shim-signed/mok/MOK.der is already enrolled
```

As I say, everything appears to be good, but I am still getting this error when I boot up!

---

