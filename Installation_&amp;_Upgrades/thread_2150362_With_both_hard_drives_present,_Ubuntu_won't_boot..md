---
title: "With both hard drives present, Ubuntu won't boot."
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by PhantamaroK on 2013-05-31
I have a Lenovo IdeaPad Y500 with 2 drives: a 256GB mSATA SSD and a 1TB SATA HDD.  I want to be able to dual boot (Windows 8 on the SSD, Ubuntu on the HDD), with an 800GB partition on the HDD for my data.

I don't want either operating system rewriting the bootloader of the other, so I installed each operating system with only one hard drive present (removed the other).  The BIOS is set to legacy mode only (I think this is necessary for the mSATA install).  Now that both operating systems are installed, I inserted both drives, and I can boot from the Windows drive, and not from the Ubuntu drive.  Ubuntu boots if the SSD is removed.  Windows can see the 800GB data partition on Ubuntu's HDD.  When I select the Ubuntu HDD drive from the boot menu, the screen goes black and the computer stays on.

Can anyone tell me what is stopping Ubuntu from booting?  Why is it bothered by the presence of another drive?

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by grahammechanical on 2013-05-31
What you have done is fine as far as it goes but the Windows boot loader does not know that Ubuntu is there and the Ubuntu boot loader does not know Windows is there.

The BIOS/EFI will look for an operating system in order of priority set by you. When it cannot find an OS on the SSD (it is removed) it looks elsewhere and finds an OS on the Sata drive. That is what is happening.

One thing you can do is to change the boot priority in BIOS/EFI when you want to boot Ubuntu.

Also with both the SSD and the Sata HD in place and Ubuntu loaded you run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That will update the grub menu on the Sata HD which should now show an option for Windows. Be careful make sure that sda is the Sata HD the SSD. Otherwise you will do the very thing that you wish to avoid - mess up the Windows boot loader. 

You could also modify the Windows boot loader to include Ubuntu in its menu. I have no idea on how to do that.

Regards.

---

