---
title: "grub not working - bootrepair error"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by bagels89 on 2013-01-03
Hi all,

I'm relatively inexperienced with ubuntu.

In case  the preamble isn't useful, my current problem is that I can only enter  grub rescue when starting up my computer. Running bootrepair using a  live copy of ubuntu 12.10 results in an error and this report:  [http://paste.ubuntu.com/1491845/](http://paste.ubuntu.com/1491845/)

Any advice on what to do? Would  re-installing ubuntu, setting the partition with a (partial)  installation of Ubuntu on it already (sda7) as root and also setting  sda7 as the device for bootloader installation work? 

Thanks in advance!

Here is the aforementioned preamble (or is it now a postamble?):

I'd got lazy with upgrades and started an upgrade from 11.04 (I think) to 11.10. 

During the upgrade, some packages were not installed.

After  the upgrade, the boot menu appeared upon starting up my computer.  Selecting ubuntu led to the loading screen ("ubuntu" logo with orange  dots beneath) and here it got stuck. Windows 7 did load successfully.

I  created a live bootable USB stick with ubuntu 12.10 on it and tried to  install from this. The installation encountered a "critical error" and  had to abort.

After this, the boot menu does not appear on startup and instead I enter grub rescue. I have tried using the following help: 

[http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)

However, there seem to be some files missing so that when I try to load modules, I receive the message

error: symbol not found grub_divmod64 if trying to load modules using "insmod ntfs"

Apologies for the fragmented and likely nonsensical nature of this informaiton - I have no idea what most of it means.

---

### Post by darkod on 2013-01-03
First, you have grub1 on the MBR of the disk. It seems you were running it all this time. Ubuntu stopped coming with grub1 since 9.10 so if you were doing upgrades all the time but never upgraded grub1 as recommended, it remained grub1.

Second, it seems there is some issue with the sda5 swap partition. If you can boot your 12.10 cd/usb in live mode, do it, open Gparted and try to delete sda5. If it has a keys symbol next to it, you need to unmount it first with right-click, Swapoff.
After deleting it in Gparted click the green button to execute the changes. Only after that you can exit Gparted.

Deleting sda5 will not solve everything but it might solve the critical error. Grub2 in your 12.10 did not install completely, so you will either need to reinstall grub2, or reinstall ubuntu again. If reinstalling ubuntu note that it doesn't use the same partitions automatically. You have to tell it manually to use them, or delete them rom live mode too and then let the auto instaler use all that unallocated space.

As for the bootloader destination, it needs to be the MBR of the disk which is /dev/sda. Not /dev/sda7. sda7 is the ubuntu root partition and the bootloader always gos to the MBR, not to a partition. Except in some special cases, but in general it is always on the MBR.

If you decide to try only reinstalling grub2, just ask and we can provide the exact commands.

---

### Post by bagels89 on 2013-01-03
Thanks - I tried a variation on what you suggested (patience is not one of my virtues, so I took a gamble and tried this).

Reinstalled Ubunutu 12.10 from my live USB. I set /dev/sda as the destination for the bootloader (and you have now explained why that was necessary!). I set sda7 as root (because I knew it was)  and set sda5 as a swap partition. I formatted both sda5 and sda7.

This seems to have fixed the grub problem, though it is perhaps a bit of an intrusive way of doing it?

Everything seems to be working ok now.

Thanks for your help - you've explained to me why what I ended up doing worked. I suspect if I'd just asked for help sooner and had some more patience I would have solved it far more easily!

---

### Post by darkod on 2013-01-03
Reinstalling is fine, especially since it was also a new install that had no personal data inside yet.

It seems to be working fine, so good job. :)

---

### Post by scottmcon on 2013-01-03
Have been trying to avoid the **GRUB** since I began a try-out of Ubuntu.  Have loaded Ubuntu 12.10 by Windows Installer - which is fast and averts **grub**.  When selection of OS via a thumb-drive load or another install process with the ISO, the **grub** returns.  Have found the tab for COMMANDS in **grub**, but the kernal won't load -- at least not from a thumb drive.   The system will partition and perform per the PC's space in the HD --- 5gb recommended - it stores at 2.7 gb; 1GB RAM available. Hence   ...   If it is the purpose, the Windows UBUNTU installer - WUBI is immensely friendly for a try-out.  Load and pair it in the Hard Drive or an external Drive.  Unless the selection of OS from a Menu (after WUBI install) fails, the **grub** issue is avoided. Only grief with that is the smaller HD of many systems - cannot say yet whether the space margins or accomodation of a graphics card - including a Matrox dual head 450 AGP affects the graphics display speed.  It performs as if a slow dissolve slide show at 2.6ghz on local.  Would assume some speed up after more performance.  The WWW browser (Firefox) performs quickly (to speed expectations with COMCAST xfinity broadband) and wireless connects with Apple style menu/graphics quickly and performs well after install.  Drop down menus are slow -but may improve.

---

