---
title: "Install on OEM 500 GB drive won't boot, now Windows 7 problems"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Songfellow on 2012-05-15
I recently upgraded my PC with a new ASUS M5 A88-V EVO motherboard, 8 gb of memory and an unformatted 500 GB Western Digital SATA hard drive.  I installed Ubuntu but couldn't get the drive to boot. It jusy hanged.  So, I ordered Windows 7 64-bit (OEM) with the idea of dual-booting Windows and Ubuntu.  Before the Windows install, I deleted all of the drive partitions and thought that I once again had a pristine hard drive.

Well, Windows seemed to install okay but when it re-started, the system hanged at boot.  I have re-installed Windows about 5 times now but it always hangs.  Finally, after accidentally leaving the Windows install disc in my DVD drive, I saw an ISOLinux message to press enter if I wanted to boot from the disc in the dvd reader!  I waited and the system booted normally into Windows.

I then got the brilliant idea of re-installing Ubunto.  The installation seemed to go well  but it alsohangs unless I leave a bootable DVD in the dvd reader.

How do I get rid of that old ISOLinux boot code?  It's obviously hiding somewhere and I am clueless about what to do next.

Thank you!

Songfellow

---

### Post by darkod on 2012-05-15
Run the boot info script from the link in my signature. Post the results as explained there. That will show many details about your system.

You can do all that from ubuntu live mode.

---

### Post by Songfellow on 2012-05-15
Thank you so much for your quick reply!

I've attached the gzipped output for your review.  

Your help is very much appreciated.

---

### Post by darkod on 2012-05-15
The results look normal. I can't see anything wrong.

Go into the BIOS and make sure the HDD is recognized correctly, and try with the boot device order of: cd-rom, usb-hdd, hdd...

That should boot from cd or usb stick if any are present, and after that from hdd. That is sort of default setup.

Look in the boot order devices if anything doesn't look right.

I don't see any stray ISOLINUX code anywhere. You have grub2 on the MBR after the latest uubntu install, which is correct.

The grub.cfg file looks correct with entries for ubuntu and win7.

You could have given ubuntu more space on the HDD but apart from that, it looks OK.

---

### Post by Songfellow on 2012-05-16
Thank you. Yes, my bios boot order is  correct.  I'll just keep a bootable dvd in my drive.  If you think of anything else let me know.

---

### Post by Songfellow on 2012-05-16
Thanks to your assistance I have gotten my system to boot from the SATA hard drive. 

I unplugged my 2 legacy  IDE DVD writers from the motherboard. They were set to master/slave.  I tried cable select on both but that also failed.

I might have to upgrade to a SATA dvd reader/writer.

Thanks for your help!

---

### Post by darkod on 2012-05-16
When there is a mix of IDE and SATA devices, some boards would give priority to IDE even though in this case it's only a DVD drive, not a HDD.

---

