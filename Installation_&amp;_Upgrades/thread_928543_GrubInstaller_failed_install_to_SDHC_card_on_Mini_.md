---
title: "GrubInstaller failed: install to SDHC card on Mini 9"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by scgroup on 2008-09-24
I'm trying to install Ubuntu 8.04 on a Dell Mini 9.  It has a 16 GB PATA SSD that came with Win XP preinstalled.  If at all possible, I'd like to avoid overwriting the MBR or other boot-related info on that drive.  This machine does not have an optical drive, so I put the Ubuntu .iso onto a 2 GB USB flash drive using UNetbootin.  The flash drive boots ok and Ubuntu runs normally.  The desired target drive is an 8 GB SDHC; I'd like to install grub on its MBR and select the OS to boot from the BIOS.  Ubuntu sees the SSD as /dev/sda, the USB flash as /dev/sdb, and the SDHC as /dev/mmcblk0.

The installer 'advanced' dialog allows me to select /dev/mmcblk0 for bootloader install, but early in the install process /var/log/install/debug shows:
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:2194: GtkWarning: gtk_cell_layout_set_attributes: assertion `GTK_IS_CELL_RENDERER (cell)' failed
  self.grub_device_entry.set_text_column(0)

The install proceeds ok until shortly after displaying "configuring boot loader", the installer window closes with no error message.  The debug file now shows:
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 428, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 797, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1913, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 419, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1422, in configure_bootloader
    "GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 1

I can't find any file with the actual error from GrubInstaller, but if I run install-grub manually, I get:
/dev/mmcblk0 does not have any corresponding BIOS drive

and /target/boot/grub/device.map has only:
(hd0)   /dev/sda
(hd1)   /dev/sdb

In the BIOS boot menu, there is an entry for "removable devices", but it does not have a + in front, which means that the device is not available as a boot source (the "hard" drive and the USB drive both have the +).  This is true even after I set the 'boot' flag for the SDHC's EXT2 partition, though possibly the BIOS is complaining about the MBR content (which of course doesn't contain any boot code yet).  I don't know whether this BIOS is even capable of booting from SDHC, but would assume that the presence of the menu item indicates that it is at least intended to work.

If the BIOS turns out to be incapable of booting SDHC, is there a good way to put minimal boot code on the SSD and run Ubuntu from the SDHC?

---

### Post by scgroup on 2008-10-01
I have given up attempting to solve this.  I made an image copy of a USB flash drive (that the Mini 9 can boot) onto an SD card of the same capacity, but it was not seen as bootable; my conclusion is that the Mini 9 cannot boot from an SD card, even though the BIOS boot menu includes a "removable devices" entry.

I asked Dell about a newer BIOS.  Unfortunately, as of this writing, the installed version A00 is the latest.

I used GParted to reduce the size of the XP partition and was able to install Ubuntu on the freed space with no problem.

The SDHC card is now used just for data.  There is one issue: the card often gets corrupted if the machine is placed in suspend mode.  Upon coming out of suspend, an error is displayed:
MMC: killing requests for dead queue
Unmounting the card before suspending appears to prevent the corruption, though the error message still appears.

---

