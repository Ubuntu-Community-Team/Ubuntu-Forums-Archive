---
title: "Install on Laptop w/o CD-ROM, w/o Flash Drive Boot"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by outernational on 2011-11-23
Hello

I need to install on my laptop that has a broken CD-ROM and from which it is impossible to boot from a USB Flash Drive (already created one via Universal-USB-Installer-1.8.7.0 that worked on other laptops but not on this one. This one does not have a BIOS option to boot from USB Flash though it IS using the latest BIOS)

So I have the Ubuntu 11.10 ISO mounted via Virtual Clone Drive. No matter if I access the WUBI in the ISO or the standalone downloadable WUBI, I do NOT get the screen on the third step in [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Instead, I get to [this screen]("http://i.imgur.com/1PY5q.png"), which requires a reboot and capacity to boot from an external device, which I cant do (see 1st paragraph).

Am i SOL ?!

Thanks

---

### Post by bcbc on 2011-11-23
> **outernational said:**
> Hello

I need to install on my laptop that has a broken CD-ROM and from which it is impossible to boot from a USB Flash Drive (already created one via Universal-USB-Installer-1.8.7.0 that worked on other laptops but not on this one. This one does not have a BIOS option to boot from USB Flash though it IS using the latest BIOS)

So I have the Ubuntu 11.10 ISO mounted via Virtual Clone Drive. No matter if I access the WUBI in the ISO or the standalone downloadable WUBI, I do NOT get the screen on the third step in [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Instead, I get to [this screen]("http://i.imgur.com/1PY5q.png"), which requires a reboot and capacity to boot from an external device, which I cant do (see 1st paragraph).

Am i SOL ?!

Thanks
Download wubi.exe and save it in the same folder as the desktop CD ISO. Run wubi.exe from there and it will use the ISO.
No need to do a virtual mount of the ISO.

---

### Post by outernational on 2011-11-23
> **bcbc said:**
> Download wubi.exe and save it in the same folder as the desktop CD ISO. Run wubi.exe from there and it will use the ISO.
No need to do a virtual mount of the ISO.

You the man! Thanks!

---

### Post by darkod on 2011-11-23
With the difference that you now have Wubi, not ubuntu dual boot.

---

### Post by outernational on 2011-11-23
> **darkod said:**
> With the difference that you now have Wubi, not ubuntu dual boot.

damn, i wasnt aware that i would end up with a crippled ubuntu on NTFS. Thread NOT solved: how do I get Ubuntu dual boot running?

---

### Post by bcbc on 2011-11-23
You can't do a real install with wubi or from windows. If you can't boot an ubuntu cd/usb you need to remove the hard drive and install it on another machine.

If you can create a separate partition then it's possible to migrate a wubi install and take over the drive that way. But you cannot partition the windows host from Wubi e.g. with gparted. It has to be something that can do it without needing a live CD obviously. Windows Vista/7 can do this, but not XP.

---

### Post by outernational on 2011-11-23
> **bcbc said:**
> You can't do a real install with wubi or from windows. If you can't boot an ubuntu cd/usb you need to remove the hard drive and install it on another machine.

If you can create a separate partition then it's possible to migrate a wubi install and take over the drive that way. But you cannot partition the windows host from Wubi e.g. with gparted. It has to be something that can do it without needing a live CD obviously. Windows Vista/7 can do this, but not XP.

I am on win7. is it possible to migrate the current wubi install to dual boot? i could use something like acronis disk manager or paragon partition manager if needed.

thanks again

---

### Post by bcbc on 2011-11-23
Use windows 7 to shrink the partition. Boot the wubi install, use gparted to create an extended partition with 2 logicals. Migrate using the script here: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Then uninstall wubi.

Note... dual booting has risks - if you do run into issues, not having the ability to boot a rescue disk could be a problem.

---

### Post by darkod on 2011-11-24
> Note... dual booting has risks - if you do run into issues, not having the ability to boot a rescue disk could be a problem.

This is something to think about. You have no way of starting the computer for any type of rescue attempts. Although this applies even if you keep only win7. You still have no way to boot with win7 dvd for example.

---

### Post by outernational on 2011-11-24
> **bcbc said:**
> Note... dual booting has risks - if you do run into issues, not having the ability to boot a rescue disk could be a problem.

Thanks for the warning, but the DVD-ROM will be fixed soon!

---

