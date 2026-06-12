---
title: "Persistent Install of Ubuntu to USB Drive (not LiveCD)"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by ahickey on 2010-01-05
I want to do a persistent install of Ubuntu to a USB Drive, not just a LiveCD install which I can do.
I want to be able to install additional applications that I use for Web Development.  This is going to be even more important with GIMP being removed from the default install for 10.04.

I have a netbook that I share with my non-technical wife so I want the machine to boot to Windows as normal for her, but if I install a USB pen drive that it will boot from there and run from the drive.

I do not want to configure the system as a dual boot.  If no USB drive installed it goes to Windows.  If USB drive installed it goes to Ubuntu.

I know this means installing the boot loader on the usb drive and only having one option, making sure the boot order is set in the system bios.  I have no idea how to make sure I get this right and not just destroy my Windows install.

If somebody could point me to a HowTo it would be much appreciated.  The netbook is lovely and fast from a LiveCD and I'm starting to get frustrated at having to use Windows on it.

Thanks,
Albert.

Notes:
Yes, I tried Google and the forum already and I have not found anything other than how to do a LiveCD install.
Yes, I know most flash drives have problems with excessive read/writes, but I'm happy to take the chance.

---

### Post by tachuela on 2010-01-05
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by darkod on 2010-01-05
Plug in the ext hdd. Boot with the ubuntu usb stick and select Install Ubuntu. In step 4 select to use the ext hdd, either using Erase and use whole disk option or in the free space on your ext hdd. Note the name of the ext hdd device at this step. Usually your int hdd would be /dev/sda and the external /dev/sdb. Sometimes it can get named /dev/sdc if your bootable usb stick is /dev/sdb.
When you reach the last screen of the installer, step 7, before clicking the Install button, click on Advanced. That will show you where the bootloader (grub2) will be installed. If the default selection is not your ext hdd, select your ext hdd. That way it will leave the windows bootloader on the int hdd, as you want.
So, if the ext hdd is /dev/sdb in step 4, then in advanced settings in step 7 select /dev/sdb for the bootloader. If it's /dev/sdc, then use /dev/sdc. Be careful not to use a partition number, not /dev/sdb1, it should be /dev/sdb (/dev/sdc).
That's it.

---

### Post by ahickey on 2010-01-05
@tachuela - thanks.
I should have mentioned I saw this but it looks like a bit of a kludge to me as I don't want to open the case and remove the hard drive.

@darkod - thanks.
This looks like what I need.
Now I just have to do it and hope I follow all the steps and get it right.  

10 minutes for 2 helpful responses.  Now that's what I call excellent support.

---

### Post by AndresM on 2010-01-30
thanks darkod! seems to be exactly what I need as well!

---

