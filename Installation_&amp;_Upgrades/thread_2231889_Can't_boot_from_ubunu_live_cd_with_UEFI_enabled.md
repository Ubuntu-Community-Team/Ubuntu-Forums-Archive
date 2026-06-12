---
title: "Can't boot from ubunu live cd with UEFI enabled"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by path_finder on 2014-06-28
Hi all,

My laptop is Dell inspiron 14z 5423.
I disabled secure boot and integrated NIC, but still can't boot in to Ubuntu with UEFI enabled. So with desperate need I enabled legacy mode and installed Ubuntu. Succeeded in installing but can't boot to the installed Ubuntu version.
I tried to this in 2013 and gave up. But now I want to install Ubuntu so badly.

P.S. I tried this with both 13.04 and 14.04.

Any help is appreciated greatly...!
Naya

---

### Post by katriel on 2014-06-28
Hi Naya,

Have you tried booting into the LiveCD and using Boot Repair to set up UEFI booting? Do you have a /boot/efi partition?

---

### Post by path_finder on 2014-06-28
I just tried Boot repair. 
Still its same. I don't have a separate boot partition so I don't think I have /boot/efi partition.

---

### Post by ubfan1 on 2014-06-28
Is the EFI partition (small 300M FAT bootable) mounted in /boot/efi?  You may check with the df command in a terminal to see what's mounted where.  The contents of /boot/efi should be the EFI directory containing directories Boot, Microsoft, ..., and ubuntu.  The /boot/efi/EFI/ubuntu directory should contain the grub.cfg file (just a 3 line stub to pull in the maintained copy from /boot/grub) and the bootloader(s) grubx64.efi and maybe shimx64.efi for secure boot.  boot-repair might have set this up, but you should have run it back in UEFI mode.

---

### Post by katriel on 2014-06-28
First, for other readers, some context: Naya messaged me because I have the exact same computer model, and after a little back and forth, I suggested Naya post here.

I was able to successfully boot from my old LiveCD with the following settings (I didn't try all permutations, so less than this may be necessary):
- Turn off Intel Rapid Start
- Turn off Integrated NIC
- Switch SATA from Intel Rapid Start to ATA (maybe AHCI would be a better first try?)

If you're willing to install all of Ubuntu again, you may then be able to turn Smart Response back on. If doing so breaks Grub, hopefully you can fix it with boot-repair.

---

### Post by katriel on 2014-06-28
Furthermore, I was able to boot fine when I set SATA Operation to AHCI and ATA, so I don't think you'll have trouble booting up if you install with the ATA set.

---

### Post by oldfred on 2014-07-01
Some additional threads

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

Not just precision models, but some issues also all Intel chips:

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

