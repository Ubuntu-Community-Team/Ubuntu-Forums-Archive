---
title: "ubuntu 18.04(usb drive) and Windows 10 grub promt while booting."
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by simtcr on 2018-12-07
Hello,

Mine is a windows 10 laptop.
I recently Installed ubuntu 18.04 to a usb drive. While performing the install, I had selected usb drive as the location to install boot loader.

It all goes fine, if I boot with usb plugged in. I have the option to go to windows 10 or ubuntu.
_**When I boot without usb drive, I am taken in to a grub prompt. Where I have to type 'exit' to continue boot in to windows 10.**_

How can I fix it?

Thanks.

---

### Post by oldfred on 2018-12-07
UEFI or BIOS system? And are both systems installed in same boot mode, UEFI or BIOS?
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It sounds like grub is installed to internal drive, which is normal default for grub in UEFI mode, even when you specify otherwise.
       
 Ubuntu Installer uses wrong bootloader location for USB UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

Multiple related bug reports, but all we can do is a work around, if an UEFI install to any drive other than first drive.
You have to partition in advance using gpt and include an ESP - efi system partition as FAT32 with boot flag.

Then copy all the files from ESP on internal drive twice, once to /EFI/ubuntu and then to /EFI/Boot. In /EFI/Boot rename shimx64.efi to bootx64.efi.
That is because grub only installs to first drive's ESP and /EFI/ubuntu.
And UEFI only boots external drives from /EFI/Boot/bootx64.efi. And full install of grub using renamed shimx64.efi expects more files in /EFI/ubuntu so both folders needed in the USB's ESP.

---

### Post by simtcr on 2018-12-08
I am a newbie to all this.
Could you please little more be specific on what I need to do?

---

### Post by yancek on 2018-12-08
What is being suggested for you as your next step is to provide more information.  Go to the first link posted by oldfred above, the BOOTREPAIR link. From there, follow the instruction to download it while you are booted from the Ubuntu install usb.  Use the 2nd option to use the ppa as explained.  After it downloads, run it by selecting the option to Create BootInfo Summary and do NOT try to make any repairs.  When boot repair finishes, it will give you a link which you can copy and post here and this will provide detailed information on your system and you should be able to get some help.

---

### Post by simtcr on 2018-12-09
> **yancek said:**
> What is being suggested for you as your next step is to provide more information.  Go to the first link posted by oldfred above, the BOOTREPAIR link. From there, follow the instruction to download it while you are booted from the Ubuntu install usb.  Use the 2nd option to use the ppa as explained.  After it downloads, run it by selecting the option to Create BootInfo Summary and do NOT try to make any repairs.  When boot repair finishes, it will give you a link which you can copy and post here and this will provide detailed information on your system and you should be able to get some help.

> **oldfred said:**
> UEFI or BIOS system? And are both systems installed in same boot mode, UEFI or BIOS?
May be best to see details, use ppa version with your live installer or any working install, not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you.
Here is the link for BootInfo  [http://paste.ubuntu.com/p/Zxg7R7tgdd/](http://paste.ubuntu.com/p/Zxg7R7tgdd/)

---

### Post by oldfred on 2018-12-09
You can just make Windows the default boot entry in UEFI and only when you want to boot Ubuntu use UEFI to boot into the ubuntu install on the flash drive.
But all the boot files for the ubuntu install on flash drive are on your internal hard drive.

You also are showing old BIOS boot loader for Windows in MBR of internal drive. That will (or should) never be used and space is not used for any other purpose. Just do not boot in BIOS mode as those boot loaders will not work.

You should Windows hibernation still on (fast start up), see lines 505 and up in report. Line 624 says UEFI secure boot is on. Often better with it off, but if system is working with it on, and you want it you can leave it on. But if you need proprietary drivers you will need to have secure boot  turned off. And if  you want Linux to read from NTFS partitions you will need fast start up off.

If you want flash drive to boot on any other system, it will need boot files on it. And you then must partition in advance so it has an ESP - efi system partition so you can copy boot files from internal drive to flash drive (as in post above) and do some updates to make it directly boot. Then you can set flash drive as first in boot order & Windows second. And then when UEFI does not see flash drive it will directly go to Windows.

---

### Post by simtcr on 2018-12-15
> **oldfred said:**
> You can just make Windows the default boot entry in UEFI and only when you want to boot Ubuntu use UEFI to boot into the ubuntu install on the flash drive.
But all the boot files for the ubuntu install on flash drive are on your internal hard drive.

You also are showing old BIOS boot loader for Windows in MBR of internal drive. That will (or should) never be used and space is not used for any other purpose. Just do not boot in BIOS mode as those boot loaders will not work.

You should Windows hibernation still on (fast start up), see lines 505 and up in report. Line 624 says UEFI secure boot is on. Often better with it off, but if system is working with it on, and you want it you can leave it on. But if you need proprietary drivers you will need to have secure boot  turned off. And if  you want Linux to read from NTFS partitions you will need fast start up off.

If you want flash drive to boot on any other system, it will need boot files on it. And you then must partition in advance so it has an ESP - efi system partition so you can copy boot files from internal drive to flash drive (as in post above) and do some updates to make it directly boot. Then you can set flash drive as first in boot order & Windows second. And then when UEFI does not see flash drive it will directly go to Windows.
I read your post multiple times, But unfortunately I am not able to understand what needs to be done to get rid of the grub prompt?
I want default boot as windows 10 (timeout 10 sec), manual selection (within 10 sec) as Ubuntu which in my pen drive.
Pen drive will not be always plugged in.

---

### Post by yancek on 2018-12-15
Set windows to boot first.  If you look at the output of boot repair under efibootmgr near the bottom of the page, you can see that Ubuntu is set to boot first.  The windows entry is 0000 so boot Ubuntu, open a terminal and run:

> sudo efibootmgr -o 0000, 0003, 0004  

That is a lower case Letter o in the command as in order.

The problem you have is a result of having an EFI partition on the first (windows) drive and the Grub bootloader installs some of its boot files to that partition in a second directory, the one on which the Ubuntu system is installed.  Unfortunately in your case, those other files are on your usb drive.  It should have worked properly if you had created another EFI partition on the usb drive then you could select that drive when attached or booted windows on the first drive from its bootloader.

You can set the timeout with the following command to 10 seconds:  

> sudo efibootmgr -t 10

You might want to bookmark the link below which has a pretty detailed description of the use of efibootmgr:

[https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027)

---

### Post by simtcr on 2018-12-15
> **yancek said:**
> Set windows to boot first.  If you look at the output of boot repair under efibootmgr near the bottom of the page, you can see that Ubuntu is set to boot first.  The windows entry is 0000 so boot Ubuntu, open a terminal and run:

  

That is a lower case Letter o in the command as in order.

The problem you have is a result of having an EFI partition on the first (windows) drive and the Grub bootloader installs some of its boot files to that partition in a second directory, the one on which the Ubuntu system is installed.  Unfortunately in your case, those other files are on your usb drive.  It should have worked properly if you had created another EFI partition on the usb drive then you could select that drive when attached or booted windows on the first drive from its bootloader.

You can set the timeout with the following command to 10 seconds:  



You might want to bookmark the link below which has a pretty detailed description of the use of efibootmgr:

[https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027)

I get below error,

```
sim_tcr@simon-linux:~$ sudo efibootmgr -o 0000, 0003, 0004
Malformed BootOrder order0000,
                                ^
```

---

### Post by oldfred on 2018-12-15
See 
man efibootmgr

I do do not see spaces in list, that often can be an issue, some commands have to have spaces.
Post this also as you must have the lines:
sudo efibootmgr -v

sudo efibootmgr -o 0000,0003,0004

My suggestion was to go into UEFI settings & boot tab (not UEFI boot menu) and reset boot order there.
Some systems (particularly HP) will not keep a change by efibootmgr, but may work if you use UEFI directly.

---

### Post by simtcr on 2018-12-20
> **oldfred said:**
> See 
man efibootmgr

I do do not see spaces in list, that often can be an issue, some commands have to have spaces.
Post this also as you must have the lines:
sudo efibootmgr -v

sudo efibootmgr -o 0000,0003,0004

My suggestion was to go into UEFI settings & boot tab (not UEFI boot menu) and reset boot order there.
Some systems (particularly HP) will not keep a change by efibootmgr, but may work if you use UEFI directly.

I ran [COLOR=#000000]sudo efibootmgr -o 0000,0003,0004 and now no grub prompt and boot straight to windows.
[/COLOR]But even when i plug in the pen drive, it doesnt boot to ubuntu.
How to fix that?

---

### Post by oldfred on 2018-12-20
Because grub is installed to the ESP on the internal drive you have to go to your UEFI boot menu.
       HP - escape + F9 for boot menu, F10 for bios setup 

The only way to have to default boot flash drive when plugged in is to have boot files on flash drive and then have UEFI set to boot flash drive first & Windows second. Then when flash drive not found it will boot Windows.

But you do not have an ESP - efi system partition (FAT32) on the flash drive. UEFI only boots from an ESP and on flash drives it is /EFI/Boot/bootx64.efi file. You would have to manually partition in advance to have an ESP on flash drive & reinstall. And grub still will not install to that ESP, you have to copy files from internal drives ESP to flash drive's ESP.

---

