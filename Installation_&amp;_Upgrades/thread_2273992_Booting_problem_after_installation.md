---
title: "Booting problem after installation"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-04-16
Hi all,

I have 2 SSDs installed on this PC, a new PC.

SS1 120G
SS2 1TB

First I installed Ubuntu 14.04 on SSD1 taking up the entire SSD1 without partition.  Then I installed Ubuntu 14.04 on SSD2 also on the entire SSD2 with LVM partitioning

The motherboard BIOS (Asus M5A97 LE R2.0) detects both SSDs.

Boot Option setting
===================
1st boot - SSD2
2nd boot - SSD1

On booting the bootloader displays both OSs of SSDs allowing to select either SSD (SSD1 or SSD2) to boot.  It is quite convenient.  But after booting SSD2 I couldn't mount SSD1 to read its content.

Then I reinstall Ubuntu 14.04 on SSD1 with LVM partitioning.  For safety reason I disconnected the cable of SSD2 before installation.  The installation went throught without problem.  On reboot I can boot SSD1

After reconnecting the cable to SSD2, on booting the motherboard BIOS detects both SSDs and the bootloader also displays the OS on both SSDs.  But I can only boot SSD2.

On choosing SSD1 to boot it fails and then after a while it boots SSD2 automatically.  Restart PC and on BIOS select to boot SSD1.  It fails and automatically boot SSD2.

To boot SSD1 I must disconnect the cable to SSD2.  It is very strange to me unable to sort out the problem after struggling several hours.  Is it only ONE LVM system allowed on ONE PC?

Please help.  Thanks

Regards
satimis

---

### Post by oldfred on 2015-04-17
If you reinstalled then UUIDs were updated, you need to run this in your other install.
sudo update-grub

Your install without LVM, did not have LVM drivers, so that may have been an issue. But boot is usually a separate /boot partition that should have been seen.

Post link to Summary report, do not run auto repair as that installs one grub to all MBRs.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by satimis on 2015-04-17
> **oldfred said:**
> If you reinstalled then UUIDs were updated, you need to run this in your other install.
sudo update-grub

Hi,

Thanks for your advice and link.  Please advise on which SSD Ubuntu to run "sudo update-grub".  On SSD2 Ubuntu?

> 
Your install without LVM, did not have LVM drivers, so that may have been an issue. But boot is usually a separate /boot partition that should have been seen.

Noted.

> 
Post link to Summary report, do not run auto repair as that installs one grub to all MBRs.

Please explain in more detail.  Thanks.

Regards
satimis

---

### Post by yancek on 2015-04-17
If you reinstalled on ssd1, the UUID numbers will have changed so that the menuentry for the ssd1 install in the Grub boot menu from ssd2 will still have the old uuid.  Remember, you had ssd2 disconnected when you reinstalled on ssd1, thence no way for its boot loader to know the new uuid.  update-grub on ssd2.  If they are both detected in the BIOS, you might be able to select either on boot and boot that way.

oldfred was also asking that you post a link to the output of the "Create Boot Info Summary" option from the boot repair software from the link in his post.

---

### Post by satimis on 2015-04-17
> **yancek said:**
> If you reinstalled on ssd1, the UUID numbers will have changed so that the menuentry for the ssd1 install in the Grub boot menu from ssd2 will still have the old uuid.  Remember, you had ssd2 disconnected when you reinstalled on ssd1, thence no way for its boot loader to know the new uuid.  update-grub on ssd2.  If they are both detected in the BIOS, you might be able to select either on boot and boot that way.
Hi,

No.  A new boot loader is already displayed on booting SSD2.  I couldn't boot SSD1 there.  Neither is its kernel displayed there.

The strange thing is neither can I boot SSD1 on motherboard BIOS without disconnecting the cable to SSD2.  After disconnecting the cable to SSD2 then I can boot SSD1 on BIOS.  I can't resolve?

On SSD2
$ sudo update-grub```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin

```

Remark:
```

/boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic

```
It is the old kernel of SSD2 before running update and upgrade

Reboot PC but the problem still remains.  SSD1 kernel is NOT detected/displayed on the boot loader.

> 
oldfred was also asking that you post a link to the output of the "Create Boot Info Summary" option from the boot repair software from the link in his post.
I have clicked the link but have no idea whether it has taken effect?

I'm prepared reinstall Ubuntu 14.04 on both SSDs.  This is a new box not much work has been put on it.  This time I would connect both SSDs.

Would it be better without creating LVM just let the OS taking up the entire SSD?  So that I can transfer data between them in future?

This time I'll install SSD2 first so;
SSD2 will become SSD1 (1TB)
and
SSD1 will become SSD2 (120G)

Thanks

Regards
satimis

---

### Post by oldfred on 2015-04-17
The link is to the instructions on installing Boot-Repair either to a live installer or to any of your working installs. Did you look at link.
Another link with more detail on the summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Without more details we cannot be sure what your configuration is.

---

### Post by satimis on 2015-04-17
> **oldfred said:**
> The link is to the instructions on installing Boot-Repair either to a live installer or to any of your working installs. Did you look at link.
Another link with more detail on the summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Without more details we cannot be sure what your configuration is.

Hi,

Thanks for your advice.  Yes, I have read the link.

I'll not continue to fix the problem on following ground:-

The OS (Ubuntu 14.04) on SSD2 will be reinstalled because;
First I installed Virtualbox on it.  Then I un-installed Virtualbox and installed KVM on it.  Now I'm prepared to wipe out KVM and install Virtualbox on it again.  To keep the OS clean I consider it will be better to wipe out everything and make a clean installation of Ubuntu 14.04 on SSD2

I have another box also having 2 drives and dual boot
(Motherboard - ASUS M5A97 R20)
Drive-1 - SSD plus WD HDD in combination running Virtualbox on Ubuntu 12.04 as host
Drive-2 - WD HDD running KVM on Debian7 as host

Both without LVM.  The dual boot is controlled by BIOS.  Data can be shared between both drives.

I'll wipe out SSD1 and SSD2 completely and re-install Ubuntu 14.04 on them without LVM to check the result.

Hi folks.  Lot of thanks for your support to this thread.

Regards
satimis

---

