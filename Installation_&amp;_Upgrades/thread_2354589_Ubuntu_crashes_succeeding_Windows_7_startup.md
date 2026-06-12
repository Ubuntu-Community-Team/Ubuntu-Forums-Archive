---
title: "Ubuntu crashes succeeding Windows 7 startup"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by geohei on 2017-03-04
Hi

I have Windows 7 together with Ubuntu 14.04 Desktop installed on a SSD.
SSD is setup as GPT.
The hardware is UEFI.
I use 2 EFI partitions for each OS (not common, but possible and allowed).
After I used Ubuntu, a succeeding W7 start crashes!
The next W7 start shows the W7 "Windows Error Recovery".
I choose "Start Windows Normally" and W7 starts normally.

Details can be found here (German).
[http://extreme.pcgameshardware.de/linux-und-sonstige-betriebssysteme/463669-dual-boot-ubuntu-14-04-windows-7-a.html](http://extreme.pcgameshardware.de/linux-und-sonstige-betriebssysteme/463669-dual-boot-ubuntu-14-04-windows-7-a.html)

I checked the sdb1 (W7 EFI partition) against MD5 checksums between crashes. No change. Hence Ubuntu doesn't touch the W7 EFI partition.

I forced Ubuntu to disregard the mounting of the W7 NTFS partition. So Ubuntu can't change anything there either.

I'm running out of ideas.

What is Ubuntu changing in order to make W7 crash upon next start?

Thanks,

---

### Post by ajgreeny on 2017-03-04
Is there any good reason for you having two EFI partitions; I assume so from your description of the setup?

However, I suspect that your problem is due to this very unusual setup, hence my query, and with my limited knowledge of UEFI, I thought the only way to get things working was with one EFI partition only.

Have you tried installing both OSs using just a single EFI partition which is very much the norm?

---

### Post by oldfred on 2017-03-04
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do you only have boot flag on Ubuntu/grub ESP or Windows ESP?
And then are you booting from UEFI boot menu or grub boot menu?

I have seen a couple of cases of 2 ESP, just to boot two Windows installs. But second ESP is just for second Windows and grub chain loads to it even if not "offical" ESP  that UEFI sees.

Do you have Windows hibernated?

---

### Post by geohei on 2017-03-04
> **ajgreeny said:**
> Is there any good reason for you having two EFI partitions; I assume so from your description of the setup?
...
Yes, there is a good reason using 2 EFI partitions (explanations OT and too lenghty).
2 EFIs are not forbidden by standards.
This can't be the reason.

Fact is, that after Ubuntu ran, W7 startup crashes. So Ubuntu must have changed something within the W7 system partition!
W7 EFI partition wasn't touched (as tested by MD5 checksums).
Might be W7 system partition was touched by Ubuntu. But how and why?
Or ... is it possible that Ubuntu changes the UEFI NVRAM values in such a way, that a succeeding W7 startup crashes?

> **oldfred said:**
> ...
Do you only have boot flag on Ubuntu/grub ESP or Windows ESP?
And then are you booting from UEFI boot menu or grub boot menu?
Do you have Windows hibernated?
Bootflag is set on W7 ESP.
You can see this on the efibootmgr stdout I posted in the link.
BootOrder: 0000,0001,0002,0003,0004,0000,0000

I'm booting Ubuntu from UEFI boot menu.
W7 doesn't need to be started out of UEFI boot menu since it boots as default.

No, W7 is completely shutdown. No hibernate.

... later ...

I installed and ran Boot-Info.
After 30 minutes, still no result ... the progress bar keeps on going ...
What would make Boot-Info keep turning around?

Even without Boot-Info data ... what are the possibilities that W7 would crash after Ubuntu ran?

... later ...

1 more test. I started W7 (after Ubuntu ran) out of grub. Same result as when using the UEFI Boot Manager. A crash while staring, followed by a "Windows Error Recovery" screen and a successful "Start Windows Normally".

---

