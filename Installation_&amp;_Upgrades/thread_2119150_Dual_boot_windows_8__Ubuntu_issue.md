---
title: "Dual boot windows 8 / Ubuntu issue"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by _guybrush_ on 2013-02-23
Dear Ubuntu community,

I have the following issue with my computer on which Windows 8 was pre-installed.
I installed kubuntu 12.10 to get a dual boot system. There was already a few partitions on the hard drive, and I re-sized the main windows partition, and crated partitions for linux, with a separate partition for /boot.
My problem is as follows: When I start the computer the grub menu comes (in BIOS, first boot says UEFI:Ubuntu) and if I choose the ubuntu entry in the grub menu, then kubuntu boots as expected, and everything works fine. If I choose the entry for windows, (Windows UEFI bootmgfw.efi), then windows boots.
And now the problem shows up: when I shut down from windows, and starts the computer again, I get a "no boot device" message, and the grub menu is not shown. The bios is set to UEFI:Windows boot manager, and the UEFI:Ubuntu possibility is not shown in the possible choices. My only solution is to boot linux from a USB stick and run boot-repair ([http://paste.ubuntu.com/5556312/]("http://paste.ubuntu.com/5556312/"))

Then grub menu is back, but as soon as I boot windows 8, then I cannot restart the computer and must use a live disc and run boot repair.

It seems that there is a sort of conflict between windows and Grub. Can someone help me resolve this issue?

Many thanks in advance!

---

### Post by oldfred on 2013-02-23
Are you booting Windows from UEFI menu or from grub menu.

UEFI shows this (line 1029 in pastebin):

> BootOrder: 0002,0000,0001
Boot0000* Windows Boot Manager
Boot0001* UEFI: SanDisk U3 Titanium 3.27
Boot0002* ubuntuSo that indicates that ubuntu should be the default.

Dells do seem to be one of the UEFI systems that work better than some others. But some systems only boot from Windows so Boot-Repair renames files so UEFI thinks it is booting Windows. Others work so then you should not use the rename. I think Boot-Repair either renames or un-renames  depending on which advanced options you choose.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

Other Dell systems that worked.
       Dell XPS14
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by _guybrush_ on 2013-02-23
Thanks for your answer oldfred.

Windows was booting from grub, but this worked only once because when I restarted the computer after booting windows, the computer refused to boot.

But I solved the issue, even though I don't really know what the problem was/is: I re-installed kubuntu and now it seems to be working.

However, I still observed something strange: for this re-install, my intention was to use the windows boot loader with easy BCD to boot kubuntu. So I chose my ext2 boot partition for where I wanted to locate the boot loader. After the installation, I was expecting to see windows boot because the EFI partition should not have been changed. However, kubuntu booted without asking me anything. No possibility to boot windows. So I ran boot-repair, and I can now boot either windows or linux via grub. The problem I was having before does not appear anymore: after booting windows and restarting the computer, I get the grub menu as expected.

---

### Post by oldfred on 2013-02-23
I have no idea how EasyBCD works with UEFI. It did not before as it used grub4dos which was based on grub legacy. And grub legacy never supported UEFI.

But all systems with UEFI boot from efi partition not any place else. Grub2's os-prober still has a bug that creates chain load entries to the Windows partition like a BIOS boot which does not work. The chain entry has to be back to the efi entry in the efi partition.

If you installed in the same partition, grub in the efi may still be the one working? Grub is not hard coded and uses search to find its install.

---

### Post by _guybrush_ on 2013-02-24
I unfortunately have no knowledge about the boot process and this appears a bit obscure to me.
So I don't know what happened, or why it didn't work the first time, but then worked after I re-installed Kubuntu with exactly the same options.

I also don't know what are the actions performed by boot-repair, but it did its job perfectly, as right after Kubuntu installation I didn't get the option of booting windows. But after running boot-repair, the grub menu was restored, and I can boot Windows or Linux!

---

### Post by oldfred on 2013-02-24
Glad you got it working. :)

The reinstall probably just refreshed grub in the efi partition and you do need Boot-Repair to fix the issues of chain loading to the correct Windows efi entry.

---

