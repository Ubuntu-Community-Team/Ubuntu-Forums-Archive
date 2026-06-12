---
title: "grub won't come up when I restart after installing."
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by markhoeft on 2018-01-19
I just installed 16.04.03 and when I restart it boots directly into windows 8.1

Standard defaults for install.
Installed a second time, same problem.
Ran powercfg /h off in windows.

From the USB try ubuntu stick:
Ran boot-repair [http://paste.ubuntu.com/26419590/](http://paste.ubuntu.com/26419590/)
It says:
[COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]5.00 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

Still doesn't work. What do you suggest?
-Mark

---

### Post by markhoeft on 2018-01-19
I had gotten a message about turning off secure boot, and had tried that, but my bios won't let me.
I then hit continue and boot-repair seemed to work, but nothing happened.
I found out I have to set a bios password to disable secure boot, so I did that and reran boot-repair.

No msg this time paste.ubuntu.com/26420047
but it did not work.  Still says no boot loaded installed in MBR.

Anymore Ideas -Mark

---

### Post by markhoeft on 2018-01-19
[https://paste.ubuntu.com/26420047/](https://paste.ubuntu.com/26420047/) (here is the link from the previous reply)
ran bcdedit in windows and it says one bootmgr and one bootloader.
no path with EFI in it.
-Mark

---

### Post by markhoeft on 2018-01-19
I tried to do a bcdedit path before but got an error.
I just tried again after disabling secure boot, then running boot-repair, and bcdedit worked.
But windows 8.1 on a ACER still boots automatically.
I've tried to have boot order of Windows boot mgr first, and HDD first.

All well, I'll keep trying. Should doing an default install be this hard?

-Mark

---

### Post by oldfred on 2018-01-20
You have an Acer.

Acer has a unique requirement of setting "trust" on the Ubuntu/grub .efi boot files from within UEFI.
Actually better than some other brands that require major work arounds.
Also make sure you have newest UEFI from Acer. Some older threads may mention downgrading UEFI, but newer ones say upgrade works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by markhoeft on 2018-01-20
Well I removed the password from the bios, reinstalled, ran boot-repair and bcdedit.
Still not working.

---

### Post by oldfred on 2018-01-20
It is set password and enable trust as other threads report with more details.

---

### Post by markhoeft on 2018-01-20
Thanks Oldfred!

[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)

did the trick. Clear step by step. Just a lot of bios work. No need to reflash.

Thanks again!

-Mark

---

