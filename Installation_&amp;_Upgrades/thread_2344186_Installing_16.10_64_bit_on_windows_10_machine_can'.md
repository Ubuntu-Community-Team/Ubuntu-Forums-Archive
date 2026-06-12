---
title: "Installing 16.10 64 bit on windows 10 machine can't find operating system"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by Ross_Munro on 2016-11-23
My specs:


Drives:


OK. first things first. Can someone please explain how to attach screenshots to a post. They're on my computer but I'm asked for a URL. I tried the File:\\\... thing to no avail. I uploaded to imgur and pasted the link. To no avail. If necessary I'll manually type out all the details but, damn, there has to be a way to add a screenshot?


Fast startup and fast boot are both disabled. The USB installer is 64 bit Ubuntu 16.10, formatted for UEFI. I force USB loading with f12 at startup. It loads to the purple (EFI?) screen. But when I choose to install it returns with the message that the computer has no operating system and my only option is to wipe the drive and install Ubuntu. In the "Other" menu option I can see all the drives are listed but they are showing as empty. When I back out I am taken to what I assume is the live install running off the USB. From here I can see the drive structure and my files (I think - sorry, it's been a whirl:-) Where I'm up to is wondering if I need to shrink the windows drive? There is about 45gb available there but when I go to shrink the volume it shows as much less. My plan was to choose a chunk of D: for the install, but now I'm wondering if Ubuntu has to be on the same drive as Windows? Any help appreciated.

---

### Post by Ross_Munro on 2016-11-23
Found it: Disks and system screenshots:

[ATTACH=CONFIG]272317[/ATTACH][ATTACH=CONFIG]272318[/ATTACH]

---

### Post by yancek on 2016-11-23
The image from windows you posted above shows the entire drive used by various windows partitions.  You can't install any Linux system on a proprietary windows filesystem and expect it to work.  You need to shrink one of your partitions (probably the largest referred to as 'D') using windows Disk Management.  You probably should run windows disk defragmenter and definitely chkdsk after changing the partition.  You may need to repeat this process (chkdsk) from windows until it reports no errors.

I would suggest you use the Something Else manual install option rather than one of the other auto-install options.  See the link below at the Ubuntu documentation site for dual booting in UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

>  I'm wondering if Ubuntu has to be on the same drive as Windows? Any help appreciated. 		

Not sure if you are mixing terminology here as you only have one 'drive' showing.  You need Ubuntu on a separate partition but it can certainly be on the same 'hard drive'.

---

### Post by oldfred on 2016-11-23
If the Installer is not seeing Windows, it almost always is that fast start up or hibernation is still on. Or NTFS needs chkdsk. Linux NTFS driver protects NTFS by not mounting it if it is hibernated or needs chkdsk to prevent damage to the NTFS.

Only use Windows to shrink the NTFS partition and reboot immediately so Windows can run chkdsk to update to its new size.

Do not confuse partitions with drives. In Linux a drive is the entire physical device. Windows will call a partition or a device a drive. So if Linux says it is overwriting a drive, it will not save any partitions.

Lots more info on UEFI installs (perhaps too much?) in link in my signature.

---

### Post by Ross_Munro on 2016-11-24
Finally got there and I wish I could say how. Fast start - off, fast boot - off, I thought hibernate was off but it wasn't. Turned off hibernate (windows + x -> Command Prompt(Admin) -> 'powercfg -h off'). But that didn't help on it's own - maybe in addition to: I shrunk the volume on 'D:' drive by 50gb for Ubuntu and finally found the boot sequence options in my bios setup (by reverting to "classic" view). I changed that to UEFI (from legacy) and booted from the USB and it finally worked. Thanks to all for your help.

---

