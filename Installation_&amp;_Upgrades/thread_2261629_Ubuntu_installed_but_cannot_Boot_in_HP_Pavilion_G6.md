---
title: "Ubuntu installed but cannot Boot in HP Pavilion G6"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by i D on 2015-01-20
Hello, 

I have HP pavilion g6, AMD A8 processor. I have UEFI boot loader set to Legacy mode and Windows 8 preinstalled in the system.

Since, yesterday I have tried to install Ubuntu 14.04, but while booting I cannot see GRUB loader. It automatically boots into Windows 8 after HP Pavilion boot screen is shown. 

Furthermore, in the boot options I can see my Hard disk named as Ubuntu HDD or something similar. 

Can you please help me installing or rather booting Ubuntu into my System. 

Thank you.

---

### Post by fantab on 2015-01-20
Windows could be hibernating, have you disabled [Faststartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")?
Did you set the UEFI bootloader to 'Legacy mode'? Is Windows8 installed in 'Legacy or UEFI mode'?

---

### Post by ajgreeny on 2015-01-20
If Windows 8 was pre-installed when you bought the machine my bet is that it is using UEFI.  As you have now installed Ubuntu in legacy BIOS mode, you will not get the system to work a dual boot as you want it.

See the instructions for using Boot-Repair in my signature, follow them to get the report and then post its pastebin link back here. At this stage do not accept the offer to repair boot as that may not be the best option.

HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.
Thanks to forum member **oldfred** for this info.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix).

If Windows 8 really is also installed in legacy mode, just ignore me, though you may learn something useful about UEFI by looking at those links.

---

### Post by Saycoda on 2016-01-07
I have a similar situation on an HP Pavilion, except I chose to erase the hard drive during the initial question of the 14.04 install wizard. Should/can I use the script method to solve this? What other utilities do I need to implement a workaround?

Thanks in advance

---

### Post by oldfred on 2016-01-07
I filed a bug report with Yann at Boot-Repair to have it automate the copy files so HP, Sony & many others will work. And he already has done that.
And Boot-Repair can convert a BIOS/CSM/Legacy boot to UEFI boot by uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI).

But be sure to always boot in UEFI boot mode. 
From Boot-Repair choose the full uninstall/reinstall of grub when booted in UEFI mode. 
And select "Use the standard EFI file". That should then be the "hard drive" or a "fallback" boot entry in UEFI.

[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

---

