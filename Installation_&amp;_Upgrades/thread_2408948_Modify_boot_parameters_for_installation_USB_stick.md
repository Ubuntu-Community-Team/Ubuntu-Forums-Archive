---
title: "Modify boot parameters for installation USB stick"
date: 2018-12-26
forum: Installation &amp; Upgrades
---

### Post by tomascrespo on 2018-12-26
Hi, I want to add a kernel parameter for my ubuntu 17.10 (server) usb installation stick. 

I know how to add a kernel boot parameter in a installed system, editting /etc/default/grub, but now I want to do it for the installation procedure.

I also know that I can add params in the first installation screen, pressing F6 (or some other key) but that's not enough.

My problem is I need to enable VGA output with param **video=VGA-0:e** because the LCD panel of my laptop is broken and it doesn't automaticly detects an external monitor.

How could I add this param to the installation process of Ubuntu in a USB stick? Is there any file I could edit in the usb stick?

Thanks

---

### Post by Autodave on 2018-12-26
I have no idea how to do that.  I do, however, would like to know why you are trying to install a short term release that is already at its end of life.

  	 	 	 	   Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by yancek on 2018-12-26
You add/change a boot parameter on a Live system such as a usb by hitting the e key on the keyboard with the menu option highlighted on boot.  e for edit.  Scroll down to the kernel line in the menu, the line beginning with the word linux and put the parameter at the end of the line.

---

### Post by oldfred on 2018-12-26
Do not use versions that have reached End of Life.
       Ubuntu 17.10 reached End of Life (EOL) on July 19, 2018 
    
On desktop version, gui installer you can edit these files if flash drive. Not sure with server installer, there also now with18.04 are two versions, older text and newer Subiquity     gui.
But if you use an installer that uses dd or dd under the hood, the files are not editable as it is an image.
       UEFI boot
/boot/grub/grub.cfg
BIOS boot edit syslinux boot 
/isolinux/txt.cfg 

If UEFI you can do this:
      
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

The older installers essentially did the above to format a flash drive, extract files. But for BIOS boot they also had to install the syslinux boot loader.  You can also do that but more complicated to do it yourself. Its just most newer installers take advantage of the combined DVD/flash drive images and use dd to image a hybrid boot DVD image on a flash drive.

---

