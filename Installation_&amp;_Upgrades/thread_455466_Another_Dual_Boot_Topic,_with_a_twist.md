---
title: "Another Dual Boot Topic, with a twist"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by zhowen on 2007-05-26
Hey everyone.  I'm trying to configure my PC for dual boot with Windows XP Pro and Ubuntu 7.04 Feisty.  I'm running into a similar problem as all the ones I've seen, however, unlike most, the windows partition isn't the one taking over and booting.  Here's what I did:

I repartitioned my SATA, formatted NTFS and installed a new installation of WinXP Pro.  Once done, I rebooted off of the Ubuntu alternative Feisty CD, and repartitioned and formatted my other HD, the IDE and installed Ubuntu.  Bam, Ubuntu boots and works like a charm, however, when I go into the BIOS to try and boot windows, it just hangs, and eventually says DISK BOOT FAILURE.  I Can only boot off of my IDE, not the SATA.  I went into the Ubuntu cd and went into RESCUE mode, reinstalled the GRUB loader onto the IDE, and then went into my menu.lst and added this code:

```
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

Still, no luck.  Any Ideas guys?

P.S. Sorry if this exact situation has been answered before, it's a little bit tedious to search for things like this, so just post me the page if it has.  Thanks in advance.

---

### Post by logos34 on 2007-05-26
> I repartitioned my SATA, formatted NTFS and installed a new installation of WinXP Pro. Once done, I rebooted off of the Ubuntu alternative Feisty CD, and repartitioned and formatted my other HD, the IDE and installed Ubuntu. Bam, Ubuntu boots and works like a charm, however, when I go into the BIOS to try and boot windows, it just hangs, and eventually says DISK BOOT FAILURE. I Can only boot off of my IDE, not the SATA. I went into the Ubuntu cd and went into RESCUE mode, reinstalled the GRUB loader onto the IDE, and then went into my menu.lst and added this code...

Windows NTLDR bootloader probably didn't install correctly on the sata drive, which is why Grub can't chainload it either.   

Run **sudo fdisk -l** and post it.

You can try restoring ntldr to the sata MBR.  Boot the winxp cd, type 'r' to enter the recovery console and do 'fixmbr' to reinstall.  If this allows you to boot directly into windows from the bios, then try it via grub on the ubuntu disk.

---

