---
title: "BIOS doesnt show fast boot/quick boot and I want to disable it/them"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by spacefrog on 2016-03-05
I am trying to install Ubuntu on an HP Pavilion dv7. I previously installed Elementary OS a year or two ago following weeks of failed attempts to install Ubuntu. I am trying again now, and the first step I have read is to disable fast boot and /or quick boot, but they don't appear on the boot menu. Can anyone help please?

---

### Post by buzzingrobot on 2016-03-05
Isn't that hardware several years old?  If so, it pre-dates Fast Boot, Secure Boot, UEFI, and the other things that were included to deal with Windows 8. You might be looking for something that isn't there. 

Are you successfully burning an ISO install image to DVD/USB stick and booting it?

You've seen all the how-to's here?
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by oldfred on 2016-03-05
There are two totally separate entries, both should be turned off.

UEFI fast boot. This speeds boot and assumes no hardware nor configuration changes. But you also then have no time to press a key to get into UEFI or boot keys. You then only can get into UEFI to change settings or UEFI boot menu from Windows, grub also now has an entry to get into UEFI. And if Windows breaks you have major difficulty getting into UEFI. Some can cold boot from full power shutdown, others have to jumper pins on motherboard, and a very few have a new brick/doorstop & have to return to vendor. Screen shot of Asus UEFI showing fast boot and normal boot setting on cold power boot.

Windows has a fast start up setting that is really always on hibernation. If hibernation is on, the Linux NTFS driver will not mount NTFS partition. Also then grub cannot boot Windows as it is hibernated and os-prober will not see Windows to add it to grub menu. And if BIOS, you have to temporarily restore a Windows boot loader to MBR to boot Windows. If UEFI you should be able to boot from UEFI menu, but not grub if hibernation left on. And Windows may turn it back on with major updates. So keep a Windows repair flash drive handy.
Fast start up needs to be off if BIOS or UEFI for Windows 8 or later versions.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by spacefrog on 2016-03-05
Yes, it's an old laptop. As I say, I've tried this before to no avail and I ended up installing Elementary OS simply because the DVD worked whereas with Ubuntu it didn't, with several different copies both ob DVDs and USBs. I am still completely lost as to what the trouble might be. I would prefer to switch to Ubuntu if I could, but it doesn't look like I can.

---

### Post by spacefrog on 2016-03-05
What happens is that it boots up directly from the hard disk regardless of the boot order I establish in BIOS, and I end up looking at the Elementary log-in screen. There doesn't seem to be any way of getting around this.

---

### Post by oldfred on 2016-03-05
Are you using DVD or flash drive? How did you create it.

You do not boot from grub, but from BIOS which should show flash drive or DVD. Or one time boot key, usually shown on BIOS boot screen before any system starts, often f10 or f12, where f2 or del is to get into BIOS.

Some show flash drives as a sub menu under hard drives.

---

