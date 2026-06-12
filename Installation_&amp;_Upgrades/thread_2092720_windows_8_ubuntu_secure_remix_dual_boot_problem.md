---
title: "windows 8 ubuntu secure remix dual boot problem"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by sqwiggly on 2012-12-08
I am trying to install the secure remix version of ubuntu amd64 alongside windows 8. The livecd won't boot unless i set to legacy mode in the bios.
I installed successfully but neither would boot afterwards in both uefi mode or legacy. I booted up the livecd and ran boot-repair and after rebooting got an image not found access denied error and still could not boot. The link from boot-repair this time was [http://paste.ubuntu.com/1419474](http://paste.ubuntu.com/1419474)

I then tried boot-repair again but this time checking the secure boot box in advanced options. Now when booting in uefi mode it goes to a dark screen for 30 secs then returns to a screen asking which device to boot from. The link from boot repair this time was [http://paste.ubuntu.com/1419544](http://paste.ubuntu.com/1419544)

Can anyone help get my system working or how to just revert to a windows 8 machine if not. Thanks

---

### Post by oldfred on 2012-12-08
What computer and what video do you have?

From UEFI/BIOS menu do either Windows boot or Ubuntu boot to grub menu?

From grub menu the new Windows UEFI entries that Boot-Repair should work if you can boot Windows directly from UEFI menu.
And does Ubuntu the boot?

Grub2 does have a bug and creates incorrect boot entries, so any of the entries with Windows .... (on /dev/sdaX) will not work with efi.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

---

### Post by sqwiggly on 2012-12-09
It's a lenovo z580 laptop. 
In uefi mode it does not boot to grub just a black screen pauses for a moment then bios menu asking for device to boot from. If i select hdd this process repeats.

---

### Post by oldfred on 2012-12-09
Other Lenovo's have worked, but some do not.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    
Grub has a gfxmode setting for video. It tries to use the video mode from system but may have issues, you can try resetting. Boot Repair has an option to change the gfx mode.

This site has no info on your specific model
[http://www.linlap.com/lenovo_ideapad_z580](http://www.linlap.com/lenovo_ideapad_z580)
Other models close to yours seem to be AMD.
But this looks like Intel & worked.
[http://www.linlap.com/lenovo_ideapad_z560](http://www.linlap.com/lenovo_ideapad_z560)

General Info
       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by sqwiggly on 2012-12-09
Thanks i will update you where i am now.
I can now boot ubuntu via legacy from grub menu, windows still not working at all.
At some point during this the partition table has become corrupt but i can still mount my windows partition and see the files are all still there.
I have tried repairing the table with testdisk but when i reboot it brings me to grub rescue. 
Can you advise how to repair windows8 boot (boot folder still there on windows partition) as i think just reverting system back to windows would be the safest option for now.

---

### Post by oldfred on 2012-12-09
With UEFI, both Windows & Ubuntu boot from efi partition, not any others. If you are trying to boot Ubuntu in BIOS mode you then cannot get to Windows in UEFI mode.
Both systems have to be installed in UEFI mode.

Why do you think you have a partition error? Or are you trying to Boot  Windows in legacy mode and it sees the gpt partitions. With gpt Windows will only boot in UEFI mode.

---

### Post by sqwiggly on 2012-12-09
There was an error with the partition table when running testdisk, it said it could not read the partition with windows on but it did find it and on the last page where you write the new table it showed up. 

In UEFI mode I cannot do anything, windows does not boot and has no error message, I can't boot any usb/cd/dvd, I have tried with various different settings in the bios but cannot get it to boot. The windows 8 recovery disk won't even boot.

---

### Post by oldfred on 2012-12-09
Was testdisk in gpt mode? I do not know if Windows partition boot sector PBR for Windows 8 would be written. Test disk always wrote an XP NTFS  PBR and then with Windows 7 systems you have to run chkdsk to repair it again to convert to Windows 7 NTFS PBR. Not sure about Windows 8? At the least I would expect you need to run chkdsk, but you have to be able to boot into a Windows repair.

There have been several threads where users with different models of UEFI Windows 8 could not get back into UEFI menu. I think some fixed it, but did so many different things and different brands, so we do not have a easy fix.

---

### Post by sqwiggly on 2012-12-11
I managed to get hold of a windows 8 installation disk and it booted ok in uefi mode and refreshed the system. After running chkdsk everything is working ok and my files intact.
Not sure where to go from here in trying to dual boot on this laptop.

---

### Post by oldfred on 2012-12-11
So what boots now?

Do you have Windows booting? Did you uninstall Ubuntu or run the full image restore so Ubuntu was removed?

---

### Post by grahammechanical on 2012-12-11
You say this:

> I am trying to install the secure remix version of ubuntu amd64 alongside windows 8. 

Which version of Ubuntu secure Remix are you using? The version based upon Ubuntu 12.04 or the version based upon 12.10? Ubuntu 12.10 is better at booting with windows 8 than 12.04 because it can handle secure boot.

[http://sourceforge.net/projects/ubuntu-secured/files/]("http://sourceforge.net/projects/ubuntu-secured/files/")

Regards.

---

### Post by sqwiggly on 2012-12-11
I booted in to the ubuntu live cd and used the OS uninstaller tool. I then used the windows 8 installation disk and did a refresh and now have just windows working. 
It was the 12.10 secure version of ubuntu I was using, which would not boot in uefi mode only legacy. 

I read somewhere someone had windows 8 running in uefi mode and then installed linux in legacy mode and just switched modes when they wanted to use the other OS. Is this a bad idea/risky? 
I only want windows for gaming so could just change back to uefi mode when I need to.

---

### Post by oldfred on 2012-12-11
I have not seen anyone do that with one drive. Might work better with two drives.

How did you originally shrink Windows. Always best to shrink Windows from inside Windows and reboot several times. But only use gparted to create new partitions.

---

### Post by sqwiggly on 2012-12-11
Yes I used windows to shrink the partition then manually created the new partitions during ubuntu installation.

---

### Post by oldfred on 2012-12-11
Do not know what else to suggest at this time.

---

### Post by sqwiggly on 2012-12-11
Thanks for your help, hopefully there will be a simple solution in the future.

---

