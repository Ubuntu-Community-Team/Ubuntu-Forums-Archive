---
title: "Synaptic Package Manager Removed Ubuntu"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by Saiede on 2013-11-26
I am a newbie to Ubuntu. Using it since a couple of months back and still learning it. But today something weird happened. I was trying to free some disk space from my /boot directory. To do that I have launched Synaptic Package Manager and found initramfs package dependency update is broken and then I tried to remove this package and wanted to re install it.


I selected that package and clicked on Completely remove option thus all my ubuntu system went removed completely. Nothing left !!! Except the grub loader and Win7 in another partition of my HDD.


I have some important documents and files inside ubuntu.


So I am looking forward to if there any option if I can get back my system as it was before . I have searched google but found nothing that much helpful.


Can anyone please help?

---

### Post by heir4c on 2013-11-26
Start up with a live-cd/dvd or live-usb. And see if you can locate your files. Beside that: do nothing else with it before you have help from more advanced users!!!
Normally when you uninstall any program and there are more packages there will be removed, your getting a window with some info about that and you must give the permission to go further.
And if you want make more free space on the boot than you must uninstall old linux kernels via synaptic. I don't now where you get that to remove the initramfs. That's an important part of the system.
I don't now at the moment how you can fix that, that's beyond my knowledge at the moment, but others here can help you with that, I think.
I don't think your Ubuntu is gone, but he can't start it because of the removing of initramfs. 
More info about initramfs: [https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs)

---

### Post by ian-weisser on 2013-11-26
heir4c is right. Do you still have your install media? If so, use it to boot. Use the Live session to mount your old Ubuntu partition(s) and recover your files onto some external (or cloud) media. DO NOT reinstall until AFTER you have safely backed up your data.

Your system is probably unbootable in its current state, and will need to be reinstalled.
However, the filesystem is likely undamaged, and any non-package-installed files (like your data) are probably still there, in good shape, and can be easily recovered.

During the reinstall, the installer will *try* to preserve existing data (if you don't reformat), but it's not guaranteed, and reinstalling is NOT a reliable form of data recovery.

> **Saiede said:**
> I was trying to free some disk space from my /boot directory. To do that I have launched Synaptic Package Manager and found initramfs package dependency update is broken and then I tried to remove this package and wanted to re install it.

Initramfs is part of the boot sequence, and an essential component of your Ubuntu system.
Removing your kernel or initramfs or grub or upstart or other boot-essential components is expected to break your ability to boot.
Synaptic *did* try to warn you about the full list of packages it was about to remove. You're not the first person to click past without reading the list. We have all done it...once.

---

### Post by Saiede on 2013-11-26
Thanks [heir4c]("http://ubuntuforums.org/member.php?u=739011")  for the reply.

---

### Post by Saiede on 2013-11-26
Many thanks [ian-weisser]("http://ubuntuforums.org/member.php?u=1841707")

---

### Post by heir4c on 2013-11-27
Always welcome.
What have you done now? Have you backup your files? And make a new install or.... ??

---

