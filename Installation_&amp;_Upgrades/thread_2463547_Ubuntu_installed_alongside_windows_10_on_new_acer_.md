---
title: "Ubuntu installed alongside windows 10 on new acer laptop boots straight to windows"
date: 2021-06-13
forum: Installation &amp; Upgrades
---

### Post by TigrisAltaica on 2021-06-13
Hello, I've been struggling with his one for a bit. I'm hardly an advanced user so apologies in advance If something I say makes no sense.

I installed ubuntu 20.04 on a new acer aspire laptop alongside windows 10. The insallation went smoothly but the laptop then boots straight to windows. I've seen several solutions online that revolve around setting an uefi file as trusted in the BIOS. I did that, selecting grub64.uefi (I think that's the file name) and also moved ubuntu up in the boot order also in the BIOS but to no avail. I've also tried disabling "fast boot" in the BIOS but that also did not work. What can I do?

What can I do?

---

### Post by MAFoElffen on 2021-06-13
Before you do anything further, in Win 10. turn off "Fast Startup" in Windows itself. Do this by Settings > Power Options > Control What the Power Button Does > Uncheck "Fast Startup". This will allow your Windows System to shutdown the filesystems completely, without going into one of the 4 of 5 other hibernation states.

- What Model # of Acer Aspire Laptop?
- Did you install Grub2 and do you know to where?
- Did you turn off "Secure Boot" in the BIOS? That is a different option that "Fast Boot" in the BIOS.

---

### Post by TigrisAltaica on 2021-06-13
> **MAFoElffen said:**
> Before you do anything further, in Win 10. turn off "Fast Startup" in Windows itself. Do this by Settings > Power Options > Control What the Power Button Does > Uncheck "Fast Startup". This will allow your Windows System to shutdown the filesystems completely, without going into one of the 4 of 5 other hibernation states.

- What Model # of Acer Aspire Laptop?
- Did you install Grub2 and do you know to where?
- Did you turn off "Secure Boot" in the BIOS? That is a different option that "Fast Boot" in the BIOS.

1) Acer Aspire 5 N19H2

2) I do not remember installing it,

3) Secure boot in BIOS is disabled, I also turned off "Fast startup" in windows but still no luck. Thanks!

---

### Post by MAFoElffen on 2021-06-13
If you do not remember, then I will assume that you did. You would have to step in and say no, to not install it...

So, first, start up on your install media, and instead of using "Install", use the "Try" option. In the File Manager > Other > look for the /EFI directory and look for Ubuntu EFI file. You said in your first post that you found it. It should be in the path /EFI/ubuntu/... It's most likely going to be something in the path/filename like "\EFI\ubuntu\grubx64.efi" Write that down exactly, including the case.

Then shutdown the LiveCD Environment, Remove the Install media, reboot, and let it boot into Win 10...

In Win 10, hit the Windows Key, type CMD. Right click on "Command Prompt". Select Run as Administrator. At the CLI Command Prompt, type:
```
 bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```
Modify that to whatever that path and filename was. Shutdown Windows and reboot. It should be using the Grub2 menu now...

---

### Post by TigrisAltaica on 2021-06-13
Just to check, because I don't want to screw something up, the path I got was "/cdrom/EFI/BOOT/grubx64.efi" does that sound correct?

---

### Post by TigrisAltaica on 2021-06-13
> **MAFoElffen said:**
> If you do not remember, then I will assume that you did. You would have to step in and say no, to not install it...

So, first, start up on your install media, and instead of using "Install", use the "Try" option. In the File Manager > Other > look for the /EFI directory and look for Ubuntu EFI file. You said in your first post that you found it. It should be in the path /EFI/ubuntu/... It's most likely going to be something in the path/filename like "\EFI\ubuntu\grubx64.efi" Write that down exactly, including the case.

Then shutdown the LiveCD Environment, Remove the Install media, reboot, and let it boot into Win 10...

In Win 10, hit the Windows Key, type CMD. Right click on "Command Prompt". Select Run as Administrator. At the CLI Command Prompt, type:
```
 bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```
Modify that to whatever that path and filename was. Shutdown Windows and reboot. It should be using the Grub2 menu now...

It's telling me that the specified setting command is invalid.

---

### Post by MAFoElffen on 2021-06-13
Then do that from the "Recovery Environment" (WinRE).

In Windows 10, select Start > Settings > Update & Security > Recovery. Under Advanced startup, select Restart now. 

Or two other ways from a Windows Administrator Command prompt, either
```
reagentc /boottore

# or 
shutdown /r /o

```

---

### Post by oldfred on 2021-06-13
Your /cdrom/EFI/BOOT/grubx64.efi does not sound correct. Do you even have a CDROM?
Flash drive installer may have a CD/DVD mount as it often is a hybrid DVD/flash configuration.

It should be /EFI/ubuntu/grubx64.efi or /EFI/ubuntu/shimx64.efi.
You may also have a "fallback" or hard drive entry at /EFI/Boot/bootx64.efi. 
The hard drive entry is identical to the type of entry used to boot external drives.

Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
acer e5-571 new HDD
[https://askubuntu.com/questions/1312112/first-ubuntu-booting-takes-way-too-long/1312725#1312725](https://askubuntu.com/questions/1312112/first-ubuntu-booting-takes-way-too-long/1312725#1312725)

---

### Post by MAFoElffen on 2021-06-13
As I said before and oldfred implied, that PATH should be on your Boot drive... Not the one from your installation media.

---

### Post by oldfred on 2021-06-14
You mention new, but even new systems often have UEFI firmware updates.

Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)

---

