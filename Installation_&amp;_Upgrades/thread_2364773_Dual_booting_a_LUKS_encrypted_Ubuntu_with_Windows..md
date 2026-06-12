---
title: "Dual booting a LUKS encrypted Ubuntu with Windows... rootkit vulnerable?"
date: 2017-06-27
forum: Installation &amp; Upgrades
---

### Post by rilkeansoul on 2017-06-27
If I install a LUKS encrypted Ubuntu dual boot over an existing Windows 10 install (on the same SSD), will the Ubuntu OS be vulnerable to rootkits or other malware from the Windows coexist? Is it possible to fully encrypt the Ubuntu side so Windows can't read or write to it at all?

More and more I don't want Windows anywhere near my Ubuntu OS.

---

### Post by TheFu on 2017-06-27
How strong is your Linux-fu?  There are no trivial methods to manually setup a dual-boot system with Linux LUKS/dm-crypt working.  On a difficulty scale, I'd put this at a solid 8/10 due to the number of steps, complexity of each step and that parts require guestimation to work.

It is impossible to prevent any OS running on a computer from having access to the disks and partitions on those disks.  The other OS can delete or corrupt the encrypted partitions, but NOT be able to make sense of the encrypted portions. 
If EFI is used, then both systems will share access to those parts and if you boot from the shared EFI storage/partition, then there is a risk - this is part of the "[evil maid]("https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html")" attack profile.  The mitigation for that attack is to carry a boot device with you always, every where and never let it out of your possession/sight.

If you don't want Windows near the system, it is best to wipe it off.

---

### Post by rilkeansoul on 2017-06-28
Thanks for the comprehensive response. I think a separate hard drive for Ubuntu in the machine is the way to go, and just manually boot either from BIOS with no common Grub. As long as it's fully encrypted and backed up nightly I'm not to worried about it getting corrupted. I remember the oldschool IDE switches that literally unplugged the inactive drive.

---

