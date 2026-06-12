---
title: "Can´t install Ubuntu on Toshiba laptop"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by David_Martnez_Ma on 2015-08-14
Hello,

I had an old computer with Ubuntu and I was very happy with it, but it broke down and I bought a Toshiba Portégé Z930-145 laptop. It had Windows 8 already installed and I tried it, but I'm fed up with it. I have 4GB of RAM, 4 times the RAM I had in my older computer and it always uses 2.5GB without doing ANYTHING, so I erased it and tried to install Ubuntu with no success.

I've tried so many things and I changed a lot of options in my BIOS so I restored default values and tried one last time to install Ubuntu. It didn't work and now I ask you for help.

If I write too much information, sorry but I just have no idea why it's not working.

First, I used Universal-USB-Installer-1.9.6.1 to install in a pendrive "Ubuntu 14.04.2".

I already downloaded it with uTorrent, so I selected:

Step 1 -> Ubuntu

Step 2 -> ..\ubuntu 14.04.2\ubuntu-14.04.2-desktop-amd64.iso

Step 3 -> my pendrive

I selected to format (We will format E:\ Drive as Fat 32.)

Step 4 -> I set a persistent file of 799MB

I press create, Yes and wait.


Then I switch on my laptop with my pendrive in the USB 3.0 port and press F12. I select my pendrive and then I use the "install" option.

I use the English version of the install.

I connect it to my Wifi network.

I select "Download updates while installing" and "Install this third-party software - Fluendo MP3 plugin includes MPEG Layer-3 audio decoding technology licensed from Fraunhofer IIS and Technicolor SA."

I select "Erase disk and install Ubuntu", I don't select "Encrypt" or "Use LVM".

I select my location (Madrid, Spain)

Keyboard Spanish - Spanish

I set up my name (it has capital letters, spaces and dots), username (no capital letters) and password (it sais "Strong password"), I select "Require my password to log in" and I don't select "Encrypt my home folder".

Then after 30 or 40 minutes it's installed.

It doesn't work, it just appears the TOSHIBA logo and does nothing, until it boots up the pendrive. I pressume it couldn't start from the HDD and then it tried to boot up with the next available device, but just in case I reboot with no pendrive. It did nothing at the Toshiba logo for 5 minutes.

I follow these instructions (Boot-repair):

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It gave me this address:

[http://paste.ubuntu.com/12079199/](http://paste.ubuntu.com/12079199/)

And asked me to reboot. It didn't work.

In the past I tried to disable "Secure Boot", I tried to disable turbo Boost (it wasn't called that way where I found this tip), I tried to install another Ubuntu version, I tried to change the "Boot Mode" from UEFI to another thing, I even tried to install Windows 8 from an original DVD i have, nothing works.

I can't think of anything else I can do, help will be much appreciated.

Thank you for your time. Regards,

David


-------------------------------------------

Additional information:

System BIOS Version: 6.40
EC Version: 1.20

-------------------------------------------

Even more additional information:

ALL BIOS options (I found many options that people tell me to change doesn't exist on my BIOS, that's why I write it down)

Main ->
-> System Time: 12:14:05
-> System Date: 08/14/2015

-> CPU Type: Intel(R) Core(TM) i5-3317U CPU
-> CPU Speed: 1.70GHz

-> HDD/SSD: TOSHIBA THNSNS128GMCP

-> Total Memory Size: 4096 MB

-> System BIOS Version: 6.40
-> EC Version: 1.20

-> Language: English

Security ->
-> BIOS Password
->   User - Not Registered
->   Supervisor - Not Registered

-> HDD/SSD Password
->   Mode <User Only>
->   User - Not Registered

-> Secure Boot - Enabled

Power Management ->
-> Wake-up on LAN - Disabled
-> Wake-up on LAN on Battery - Disabled

-> Wake on Keyboard - Disabled
-> Critical Battery Wake-up - Enabled
-> Panel Open - Power On - Disabled

-> Dynamic CPU Frequency Mode - Dynamic Switch
-> Core Multi-Processing - Enabled
-> Intel Turbo Boost Technology - Enabled
-> Intel Display Power Management - Enabled

-> SATA Interface setting - Performance
-> Keyboard Backlight Control Mode - TIMER
-> Backlight Lighting Time - 15

-> BIOS Power Management ->
->-> Battery Save Mode - Full Power
->->   Processing Speed - High
->->   CPU Sleep Mode - Enabled
->->   Cooling Method - Maximum Performance

->-> PCI Express Link ASPM - Enabled

Advanced ->
-> Execute-Disable Bit Capability - Available
-> Virtualization Technology - VT-x Only
-> Intel(R) AT - Enabled
-> Intel(R) AT Suspend - Disabled
-> Intel(R) Rapid Start Technology - Enabled
-> Rapid Start Entry after - 2 hours

-> Beep Sound - Medium
-> Sleep and Charge - Disabled
-> System ON CDP Charge Mode - Disabled
-> USB Power in Sleep Mode - Disabled

-> USB Legacy Emulation - Enabled

-> Change Boot Order ->
     1 HDD/SSD
     2 USB Memory
     3 USB ODD
     4 FDD
     5 LAN
-> System Configuration ->
->-> Built-in LAN - Enabled
->-> Wireless LAN - Enabled
->-> Auto Wireless LAN RF Switching - Disabled
->-> Bluetooth - Enabled
->-> Internal Pointing Device - Enabled
->-> Web Camera - Enabled
->-> SD Host Controller - Enabled
->-> Internal USB3.0 Controller - Enabled
->-> Memory Performance Mode - Enabled

->-> Boot Mode - UEFI Boot

->-> Power On Display - Auto-Selected
->-> Boot Up NumLock Status - ON

Exit ->
-> Exit Saving Changes
-> Exit Discarding Changes
-> Load Setup Defaults
-> Save Changes and Power Off

---

### Post by oldfred on 2015-08-14
It seems Toshiba is now like Sony & HP.
They modify UEFI to also use description and only valid description is "Windows". That is not per UEFI standard.
But we can add a boot of grub or shim(secure boot) with a different description if you are not booting Windows. If dual booting there are several other work arounds.

From live installer booted in UEFI mode, to list UEFI boot entries. (is shown in Summary report also)
sudo efibootmgr -v

 This should create a new entry, using Windows description but ubuntu's shim:
       sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

check that in UEFI
sudo efibootmgr -v

And then see if you can boot "Windows".

Other work arounds in link below in my signature. Many dual booting create /EFI/Boot and copy grub or shim into that folder and rename shim to bootx64.efi. That is a hard drive boot entry, but may also have to add that to UEFI boot options.

 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

### Post by David_Martnez_Ma on 2015-08-14
Hello oldfred,

Thank you for your fast answer.

When I use this command:

sudo efibootmgr -v

Appears this error:

sudo: efibootmgr: command not found

It happens the same with other command, so I looked for what is "efibootmgr".

I searched for it in the Software Center (efibootmgr) and installed it.


After the installation I used the first command and this is what appeared:

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0004,0001,0000,0003,0002
Boot0000* USB Memory    ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0001* HDD/SSD    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)
Boot0002* LAN2    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b7e45d68,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0
Boot0003* LAN1    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b7e45d68,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000
Boot0004* ubuntu    HD(1,800,100000,7c450dd1-2f43-4871-86d8-ce9d93cd07d9)File(\EFI\ubuntu\shimx64.efi)

I used the second command and I got:

BootCurrent: 000_0
Timeout: 1 seconds
BootOrder: 0005,0004,0001,0000,0003,0002
Boot0000* USB Memory
Boot0001* HDD/SSD
Boot0002* LAN2
Boot0003* LAN1
Boot0004* ubuntu
Boot0005* Windows Boot Manager

And then used the third command (the same as the first one):

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0005,0004,0001,0000,0003,0002
Boot0000* USB Memory    ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0001* HDD/SSD    ACPI(a0341d0,0)PCI(1f,2)ATAPI(0,0,0)
Boot0002* LAN2    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b7e45d68,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0
Boot0003* LAN1    ACPI(a0341d0,0)PCI(19,0)MAC(e8e0b7e45d68,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000
Boot0004* ubuntu    HD(1,800,100000,7c450dd1-2f43-4871-86d8-ce9d93cd07d9)File(\EFI\ubuntu\shimx64.efi)
Boot0005* Windows Boot Manager    HD(1,800,100000,7c450dd1-2f43-4871-86d8-ce9d93cd07d9)File(\EFI\ubuntu\shimx64.efi)

I rebooted and it doesn't work, BUT now a new message appears before it starts live Ubuntu. It appears for one microsecond, I had to record it and then write it down. It sais:

Could not open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 800000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi - 800000000000000E
Failed to load image
Could not open "\EFI\BOOT\fallback.efi": 14
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_acorn.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_amiga.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_bsd.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_dfly.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_dvh.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_plan.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_sun.mod
error: Secure Boot forbids loading module from (hd1,msdos1)/boot/grub/x86_64-efi/part_sunpc.mod

So I tried to disable secure boot. No luck. Now the message that appears is:

Could not open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 800000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi - 800000000000000E
Failed to load image
Could not open "\EFI\BOOT\fallback.efi": 14

The same but without the secure boot errors.

I enabled secure boot again and I tried the solution provided in the first link. No luck.

I disable secure boot and rebooted... oh my gosh... IT WORKS!! You rock man!! THANK YOU VERY MUCH!! :D:D:D:D:D

I'll mark it as solved :D

---

### Post by oldfred on 2015-08-16
Glad it worked.

Did after bebooting a couple of time, that UEFI found /EFI/Boot/bootx64.efi and add that as an entry to UEFI. Is another entry now in this?
sudo efibootmgr -v

It may have been possible to also copy & rename shimx64.efi to /EFI/Boot/fallback.efi. Or specifically add a UEFI boot entry for the bootx64.efi entry.

---

