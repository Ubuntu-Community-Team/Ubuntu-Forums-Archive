---
title: "Grub killed my hd?"
date: 2014-03-13
forum: Installation &amp; Upgrades
---

### Post by Eduardo_Rivera on 2014-03-13
Hello, i'm a fairly old linux user, and now I have the strangest problem:

I cant boot from anything but grub.

See, this all stared since I reinstalled ubuntu on my dual booting Toshiba Satellite. I did so because I had installed some bad video driver for nvdia, so I though the wisest choice was to reinstall ubuntu. However, i chose the reinstall option on the setup, witch deleted all my partitions and created a single Ubuntu machine. Not really a problem since i Have most of my personal stuff backed up. Just had to resintall windows, witch i need for a couple programs, and then reinstall Ubuntu.

However, after trying 5 differente windows CDs, including a couple pendrive options, I cant format anything.

The problem? I cant boot into anything but grub. No matter what cd goes on the dvd drive or USB stick, it kind of looks like it will boot from CD, then the purple grub screen appears (without options, just the purple color) and after another couple seconds, ubuntu boots.

This is a really annoying problem. I tried removing the hard drive. Windows CD booted fine, then froze at the same moment in 3 different cd (im guessing its the part where it checks for drives, right at the black screen with the colorful windows logo moving).

Im trying my third linux distro now, but im betting it will fail again. Simply put, i cant escape from grub unless there is no hard drive.

Please, I dont want to have to buy another hard drive, but I feel like im running out of options here.

---

### Post by oldfred on 2014-03-14
Once drive is converted to ext4, Windows will not see drive. 

Or if Windows was BIOS and your new Ubuntu install installed in UEFI mode it converted to gpt partitioning. Windows then only boots in UEFI mode from gpt.

You need to use a gparted liveCD or your Ubuntu live installer and with gparted create NTFS partition(s).
Was original install of Windows BIOS or UEFI?
Windows in BIOS uses 2 primary partitions, but will install into one. Windows only boots from a primary NTFS with the boot flag.

With UEFI Windows requires several partitions. Often better to just let it do its thing and then reinstall Ubuntu. You would have to erase drive to let Windows have entire thing.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by grahammechanical on 2014-03-14
> [COLOR=#000000]No matter what cd goes on the dvd drive or USB stick, it kind of looks like it will boot from CD, then the purple grub screen appears (without options, just the purple color) and after another couple seconds, ubuntu boots.[/COLOR]

If Ubuntu is the only OS on the drive then the Grub menu will not appear unless we hold down the Shift key. You may not be seeing the "purple Grub menu" but the purple Ubuntu splash screen.

Can you confirm that the boot priority is set to the optical drive or USB port and not to the hard drive. You remove the hard drive and the Windows CD boots. That suggests to me that the boot priority is not set to the optical drive before the hard disk. I guess that the Windows CD froze because it is not a true live session and so it expects a hard drive. When it fails to see one, it freezes.

Regards.

---

