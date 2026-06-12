---
title: "Boot loader mess!"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Envergure on 2009-12-10
My boot loader is a mess.  How can I clean it up?

I'm dual-booting between Windows XP and Karmic.  I used to have Windows 7 installed, but I'm saving it for my next computer so I removed it.

To open Ubuntu, I just hit enter when GRUB appears, but to log into Windows:

GRUB offers me a choice of two memory tests, Ubuntu on six different kernels, Ubuntu "recovery mode" on each of those kernels, and Windows 7.  I select 7.  This opens the Windows 7 bootloader.  The Win7 boot menu gives me options of Ubuntu, Win7 and "Older version of Windows".  Ubuntu doesn't work from this menu.  I select "Older version of Windows".
That gives me the XP bootloader, where I can choose between Ubuntu and XP.  Again, Ubuntu won't boot from that menu.  I choose XP.

---

### Post by darkod on 2009-12-10
Windows combines two or more versions into single bootloader. That's why you have both 7 and XP in the windows bootloader. The only way to have ubuntu in there too is if you had wubi installed and didn't remove it properly, or if you were trying procedures to add ubuntu to windows bootloader.
Otherwise by default windows bootloader can't see ubuntu dual boot installations.
After you removed 7 you can restore the XP bootloader with XP disc. It should find your XP installation and write a default bootloader to the MBR which will start XP directly. But don't do this if you installed wubi.
After you restore XP bootloader as default, you will need to restore grub2 on the MBR and with update-grub it will change the menu accordingly (it should have XP in the menu to boot directly).

Restoring various bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Grub2 basics for adjusting the grub menu:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by presence1960 on 2009-12-10
why don't you run the boot info script to erase any doubt about what your setup and boot process really looks like.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

