---
title: "Acer laptop, no boot priority choice"
date: 2022-06-07
forum: Installation &amp; Upgrades
---

### Post by habana on 2022-06-07
I have a new Windows 11 Acer Swift 3 SF314-511 laptop (i5, 8GB,500GB). I wish to set up a dual boot system with Ubuntu. The 'BIOS' setup utility (InsydeH20) looks fairly normal but under the Boot heading there is a single entry for the Boot priority order:

1. Windows Boot Manager

That's it. No USB option, nothing.

This obviously makes it rather difficult to install Ubuntu. I know there are a few other hurdles to jump over with Acer but I've fallen at the first! Acer don't deem interested - have I wasted my money?

---

### Post by ActionParsnip on 2022-06-07
Try spamming F11 and F12 at boot. Are you using SecureBoot or not, too?

---

### Post by oldfred on 2022-06-07
After install older Acer required "trust" on an "unknown" entry in UEFI with Secure boot on. Whether eventually booting with Secure boot on or off.
Some newer Acer required Secure boot on and Control-S to get to additional menu choices.
Do either of those still apply to your new system?

Often UEFI with Secure Boot on also has USB settings that need to be opened up. You may have an allow USB boot or full USB support type setting.
Allowing USB boot also is not considered secure as then someone else can boot system.
Often better to review manual as it may have additional info on settings where UEFI has just a short one line explanation.

Similar system mentions drives should be in "SATA" mode in last comment:

[https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8](https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8)

Some older systems with boot parameters required to see NVMe drive.
[https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19](https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19)

---

### Post by habana on 2022-06-07
@ActionParsnip
f12 at boot gives the same result as described above. Secure Boot Mode was 'Standard' and Enabled.

@oldfred
I have read about "trust" entries - that is one of the hurdles I was expecting.
The boot mode is UEFI. It is greyed out so I cannot change it. I have set a Supervisor Password and disabled Secure Boot. No difference. I have read the manual which doesn't help at all. 

I have not seen the Control-S option mentioned anywhere. At what step do I apply that?

---

### Post by oldfred on 2022-06-07
I think if you were able to set the supervisor password, you do not need control-S. 
I thought the posts I read was that was used to open the screen to set the password.
Never lose password or reset to blank when done reconfiguring system.

Do you have the SATA mode for drives like the other newer Acer model? Or what other settings are there?

I downloaded manual. Have not seen one with so little info on UEFI/BIOS. It just says all your settings are correct for use with Windows.
But it does mention booting from USB to fix things later on. I sure they assume a Windows repair disk, but all external drives boot from /EFI/Boot/bootx64.efi and they do not know whether that is a copy of Windows boot or Linux boot file.

---

### Post by habana on 2022-06-08
Hi oldfred

Thank you for looking into this.There are very few settings that can be changed. 

Under Main there is date/time, wake from LAN, D2D recovery, function key behaviour, a couple of minor items and fast boot which I have disabled
Advanced just has Intel VTX (which is beyond my pay grade)
Security has the Sup p/w, p/w on boot and TPM options
Boot has Secure Boot (currently disabled) and the one entry for boot priority as mentioned. Boot mode is set to UEFI and greyed out
That's it

I have seen on the Acer Community forum that a user with a similar machine installed Manjaro at some stage. Maybe I could try an earlier firmware version but that might be a bit dangerous!

If I was really desperate maybe I could remove the SSD, stick it in another machine, install from my Ubuntu iso, replace in the laptop and hope that the firmware recognizes the new boot file. I don't think I'm game to do that!

---

### Post by tea for one on 2022-06-08
> **habana said:**
> Security has the Sup p/w, p/w on boot and TPM options

TPM Options - Can you disable TPM?

---

### Post by coley9225 on 2022-06-08
Hello habana. Just a silly question, but when you reboot into uefi settings, do you have a bootable usb plugged in? On my Lenovo laptop, if I boot to uefi settings without a drive already plugged in, there is no boot from usb option. I plug in a usb drive(linux live, gparted, whatever),  and reboot to uefi setting, I get the usb boot option. I have zero experience with Acer, but just my thoughts based on past experience. Good luck.

---

### Post by habana on 2022-06-08
@coley9225

It wasn't a silly question! Following advice from the Acer Community Forum I did just that and it worked. For anybody else who has this issue, the f12 boot option has to be enabled in the Main BIOS (which I had already done). Then save and exit. Turn off the computer and insert the Ubuntu installation USB drive. Now press f12 whilst turning on again and the option to select the installation iso magically appears. It's a pity the manual doesn't explain this simple procedure.

Thank you everybody for helping with this. Hopefully the installation will go well when I have some time later. I will mark this problem as solved.

---

