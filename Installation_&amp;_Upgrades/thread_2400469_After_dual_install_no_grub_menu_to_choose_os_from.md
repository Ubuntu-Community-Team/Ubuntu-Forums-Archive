---
title: "After dual install no grub menu to choose os from"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2018-09-06
I had an old system which contained one SSD with only windows 10.Today  I bought an extra SSD and installed ubuntu 18.04/mate on it. When I reboot it starts windows 10 immediately without giving me the option to choose an os. I can boot from the USB stick that contains the live ubuntu system that I used to install ubuntu. When I run GParted I see both SSD's are recognized and the new SSD contains the partitions I created fro Ubuntu during install.

This is an old system from 2010. There are no UEFI things and such.

Could someone advise me on how to solve this problem?

Thank you for your time.

---

### Post by dsstorefile1 on 2018-09-06
Which disk did GRUB install to? If the BIOS is configured to boot from the SSD containing Windows and GRUB resides on the extra SSD, then Linux won't boot.

---

### Post by nocom2 on 2018-09-06
This is exactly the situation I have. There is no workaround for this?

---

### Post by oldfred on 2018-09-06
You want to install grub to Ubuntu SSD and set BIOS to boot that SSD by default.
And which drive is first or sda is defined by BIOS and that is defined by which SATA port you used. 
Generally SATA0 is sda, SATA1 is sdb etc.
And grub default install will install grub to drive seen as first. Grub/BIOS calls it hd0, before Ubuntu loads and makes it sda.

I would reinstall grub to Ubuntu drive, Windows boot loader to Windows drive and set BIOS to boot from Ubuntu drive.

If Windows 10 you really want Windows boot loader on Windows drive. Grub only boots working Windows. And that is Windows that does not need chkdsk, nor is hibernated. And Windows fast start up is hibernation. Even after you turn hibernation/fast start up off, Windows updates will turn it back on. So when grub fails to boot Windows do not blame grub, but use BIOS to boot Windows drive and repair it.

You can use Boot-Repair's advanced mode to install boot loaders. Or use your Windows repair disk or installer if it has repair console for installing Windows boot loader. 
Do not use Boot-Repairs auto-fix as that just installs grub to all drives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nocom2 on 2018-09-06
So i shrunk the windows partition and with 30GB and reinstalled ubuntu on free space. still not a trace of grub. How can I remedy this situation?

---

