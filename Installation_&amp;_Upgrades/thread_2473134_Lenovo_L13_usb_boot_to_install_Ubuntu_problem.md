---
title: "Lenovo L13 usb boot to install Ubuntu problem"
date: 2022-03-25
forum: Installation &amp; Upgrades
---

### Post by solenkoliad on 2022-03-25
Hello, I have a problem that i can't resolved.. Help please.
I have a Lenovo L13 laptop with Windows 11.
I want to install a fresh Ubuntu but I can't make it to boot from bootable ubuntu usb - when I choose from bios to boot from usb it go to black screen for a second and come back to bios. It's recognized the USB stick but not enter the Ubuntu installer.
Things that i try - 
1. 2 different disk on key (one of them new).
2. In Rufus app - MBR/GPT. Both with UEFI. Quick/Not quick format.
3. Redownload ISO file.
4.  In Lenovo BIOS - Secure/Not Secure boot. OS optimized default On/Off. Quick/Not quick boot. UEFI/Legacy/Both.
THANKS

---

### Post by tea for one on 2022-03-25
I would think that a UEFI setting is obstructing your progress.
Can you see if any of the following appear in your UEFI Set Up?

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

Turn off Bitlocker or equivalent in Windows
Ensure Windows is not hibernating

---

### Post by solenkoliad on 2022-03-25
[COLOR=#000000]Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting) **- V**[/COLOR]
[COLOR=#000000]Disable Fast Boot **- V**[/COLOR]
[COLOR=#000000]Disable Legacy mode **- V**[/COLOR]
[COLOR=#000000]Check that Legacy USB Support is enabled** - How to do this?**[/COLOR]
[COLOR=#000000]Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver) **- **[/COLOR]**[COLOR=#000000]How to do this?[/COLOR]**
[COLOR=#000000]Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) **- **[/COLOR]**[COLOR=#000000]How to do this?[/COLOR]**
[COLOR=#000000]Disable Optane memory and storage **- **[/COLOR]**[COLOR=#000000]How to do this?[/COLOR]**

[COLOR=#000000]Turn off Bitlocker or equivalent in Windows **- V**[/COLOR]
[COLOR=#000000]Ensure Windows is not hibernating - [/COLOR][B][COLOR=#000000]How to do this?

Sorry but i am not a tec guy..[/COLOR][/B]

---

### Post by tea for one on 2022-03-25
Can you access the UEFI pages with your dedicated key (probably F2 for Lenovo)?

What are the options under the Security tab?

---

### Post by oldfred on 2022-03-25
Some Lenovo also have this setting, which you also need to change.

The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

Is this your system?
[https://ubuntu.com/certified/202011-28408](https://ubuntu.com/certified/202011-28408)
Have you updated UEFI and if SSD, the SSD firmware?
You may need the newest version of Ubuntu for ease of install. What version are you using.

---

### Post by tea for one on 2022-03-25
> **oldfred said:**
> Some Lenovo also have this setting, which you also need to change.
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

That's a new one for me, oldfred.
These UEFI obstacles keep appearing and being re-invented with all sorts of different names.

---

### Post by solenkoliad on 2022-03-26
Yes (F12).
[COLOR=#000000]The options under the Security tab: Password, Security Chip, UEFI BIOS Update Option, Memory Protection, Virtualization, I/O Port Access, Internal Device Access, Absolute Persistence Access, Secure Boot, Intel SGX, Device Guard, ThinkShiels secure wipe[/COLOR]

---

### Post by solenkoliad on 2022-03-26
> **oldfred said:**
> Some Lenovo also have this setting, which you also need to change.

The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.

Is this your system?
[https://ubuntu.com/certified/202011-28408](https://ubuntu.com/certified/202011-28408)
Have you updated UEFI and if SSD, the SSD firmware?
You may need the newest version of Ubuntu for ease of install. What version are you using.

I checked and Device Guard is OFF.

Yes, this is my system.

"Have you updated UEFI and if SSD, the SSD firmware?" - I don't know.. hoe do i check it?

I try to install 22.04 daily Ubuntu

---

### Post by tea for one on 2022-03-26
> **solenkoliad said:**
> Yes (F12).
The options under the Security tab: Password, Security Chip, UEFI BIOS Update Option, Memory Protection, Virtualization, I/O Port Access, Internal Device Access, Absolute Persistence Access, Secure Boot, Intel SGX, Device Guard, ThinkShiels secure wipe

Lots of choices in your UEFI security - some trial and error exploration necessary.

Click on Security Chip > TPM or PTT there?
Intel SGX > Set to Software Controlled or Disabled

Some options are foreign to me and I would not know what lies in the sub-menus i.e. Internal Device Access, Absolute Persistence Access, ThinkShiels secure wipe?

When you change a setting in the UEFI pages, please confirm that you save the configuration before trying to boot the USB installer?
Sometimes, in our haste to reach a solution, it's easy to overlook the obvious. We've all done it and we will all do it again.;)

---

### Post by oldfred on 2022-03-26
In the past Windows made it easy to update most systems.
Now there is fwupdate with Linux and many systems are supported.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
I do see several L13 items listed, not sure if it includes SSD or not.

I have a motherboard & have to separately download UEFI update into a FAT32 partition and the SSD update from Samsung was a bootable ISO for  just my model and newer firmware.

---

### Post by solenkoliad on 2022-03-26
Thank you very much but TPM and SGX - Disabled and nothing work... 
I think i give up and stuck with windows...

---

### Post by tea for one on 2022-03-28
Do you have a UEFI Setting [COLOR="#0000FF"]OS Optimised Defaults[/COLOR]?
If so, then, it should be set to Disabled.
Info found here [https://pra-dan.github.io/blog/ubuntuonl13/](https://pra-dan.github.io/blog/ubuntuonl13/)

---

### Post by solenkoliad on 2022-03-28
> **tea for one said:**
> Do you have a UEFI Setting [COLOR=#0000FF]OS Optimised Defaults[/COLOR]?
If so, then, it should be set to Disabled.
Info found here [https://pra-dan.github.io/blog/ubuntuonl13/](https://pra-dan.github.io/blog/ubuntuonl13/)

[COLOR=#0000FF]OS Optimised Defaults is Disabled.. Nothing. [/COLOR]

---

### Post by tea for one on 2022-03-29
That's a pity.
There must be something that's preventing your PC from booting the USB?

Do you boot the USB in UEFI mode?

Out of curiosity, it would be helpful if you could verify that the USB installer is in good order?
Have you managed to boot your USB on another PC?

---

### Post by solenkoliad on 2022-03-31
> **tea for one said:**
> That's a pity.
There must be something that's preventing your PC from booting the USB?

Do you boot the USB in UEFI mode?

Out of curiosity, it would be helpful if you could verify that the USB installer is in good order?
Have you managed to boot your USB on another PC?

Hi, 
Yes - I boot in UEFI.
I select the USB from the boot startup menu.
Yes - I managed to boot your USB on another PC.
I can't figure it :(:(:(

---

### Post by oldfred on 2022-03-31
Since allowing USB boot is not Secure, you may also have UEFI settings to allow USB boot or full USB support?
You need to download manual and review settings. The short explanation inside UEFI does not always fully explain everything.

---

### Post by tea for one on 2022-03-31
> **oldfred said:**
> Since allowing USB boot is not Secure, you may also have UEFI settings to allow USB boot or full USB support?
You need to download manual and review settings. The short explanation inside UEFI does not always fully explain everything.

Yes, agreed.
It is essential that all PC owners fully understand the UEFI Settings.

This thread concerning the prevention of booting a USB device is troubling.
For example, if Windows 10/11 crashes and then requires a repair via USB.
The owner discovers that it is impossible to boot an external device?
What do you do?

Anyway, I would encourage the OP to search the UEFI settings for Hardware/Devices to see if there is another setting to manipulate.
Failing that, search the Lenovo support forums and/or contact Lenovo direct.

There has to be a solution.
Or the hardware is faulty?

---

### Post by #&amp;thj^% on 2022-03-31
I've never seen one this hard, I've been lucky I guess with:

    Attach the USB device to the system via any available USB port.
    Press and hold the Power Button for few seconds to turn off the system completely.
    Note: For Windows 8/8.1/10, restart the system before using the following steps.
    Power on the system. Press F12 immediately as the Thinkpad logo appears.
    There should be a pop-up menu with a list of choices. Select the USB drive using the arrow key and press Enter.
    The system should now boot from the USB drive.
Otherwise I'd check the system hardware.

---

