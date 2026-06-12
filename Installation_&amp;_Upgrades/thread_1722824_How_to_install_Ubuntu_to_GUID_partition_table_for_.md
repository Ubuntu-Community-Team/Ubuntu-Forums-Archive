---
title: "How to install Ubuntu to GUID partition table for UEFI booting on a non-Mac?"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by SniperSlap on 2011-04-06
I have a PC that supports UEFI booting and I've got Windows set up with it's EFI boot loader all fine.  I tried installing the latest beta image of 11.04, but it didn't boot after install.

Grub seemed to not install correctly, despite me choosing to install it to my primary EFI system partition.  My guess is that it installed itself the old BIOS way.

So, what exactly is the trick to getting Ubuntu installed with full UEFI support?

Shouldn't the installer have said "Oh, you have a GPT partition table and an EFI System partition, let me install an EFI bootloader for you!"

??

---

### Post by psusi on 2011-04-06
Did you boot the install cd in uefi mode, or bios mode?

---

### Post by SniperSlap on 2011-04-06
UEFI.  The disc drive had two entires in my EFI boot menu and I selected the non-BIOS mode one.

---

### Post by srs5694 on 2011-04-06
The alpha-2 release worked fine when I tested it this way on an EFI system (using an Intel motherboard), but I don't recall the details, and it was only a test installation, so I can't go and check how it was installed.

One thing I do recall is that EFI includes its own boot loader. Thus, you may need to add a file called grub.efi to your EFI's boot loader in order to launch GRUB, and from that Linux. I recommend you use your EFI to look for that file, which should be on the EFI System Partition, probably in a subdirectory of the EFI directory (as in EFI/ubuntu or EFI/grub). My Intel board has an option to set an EFI booting mode, and to add items to the EFI menu, I had to use an option in the CMOS menus to change the boot order to set which .efi file was used as the default boot item. The latest generation of UEFI boards seem to have flashy GUI firmware interfaces, and I don't know how you'd adjust their built-in boot loaders.

If you can't find such a file, you could boot the Ubuntu installer in "live CD" mode and examine the EFI System Partition's and Linux /boot directory's contents in more detail. Look for a file called grub.efi, and if it's present, copy it to the EFI System Partition, in a subdirectory of EFI, and try adding it to the EFI's boot loader. You might also need to create an EFI/grub directory and copy your GRUB files there. More generally, [this page](http://grub.enbug.org/TestingOnMacbook) describes setting up EFI booting; however, it assumes you've got a working installation to compile GRUB and prepare the files. You should be able to use another Linux installation for this, if you've got one, but you'd need to copy the files over (via network, USB flash drive, or whatever).

---

### Post by SniperSlap on 2011-04-06
EFI can have multiple bootloaders if I recall correctly.  The System partition is where all of them are stored.

So I guess this is more an issue of Ubuntu not installing grub to it correctly.

I don't really have an option in my bios to "edit the efi menu".  EFI generates the list of boot options based on what it finds in the system partition as per a standard...

---

### Post by psusi on 2011-04-06
I don't think the efi version of grub is on the livecd or that the installer knows to use it.  You will have to install it manually.

---

### Post by SniperSlap on 2011-04-06
Strange.  This needs to be addressed by Ubuntu ASAP.  Lots of new EFI boards coming out and Windows makes it a cinch.

---

### Post by the-ridikulus-rat on 2011-04-06
You can use efibootmgr to add grub-efi-amd64 to the efi boot manager. See [https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems) , although it is slightly specific to Archlinux, it may be useful. See [https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369](https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369) on how to use efibootmgr.

---

### Post by psusi on 2011-04-06
Windows really finally has support for EFI?  Wow.

I have a brand new board that supports EFI, but it works just fine in bios mode too.

---

### Post by the-ridikulus-rat on 2011-04-06
> **psusi said:**
> Windows really finally has support for EFI?  Wow.

I have a brand new board that supports EFI, but it works just fine in bios mode too.

[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)

---

### Post by oldfred on 2011-04-06
The old version of boot info script does not parse gpt partitions and the new does. Not sure if it works with efi. You could try testing it.

Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

Old version is here.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V56 has improved formating and requires code tags to make it legible.

---

### Post by srs5694 on 2011-04-06
> **psusi said:**
> Windows really finally has support for EFI?  Wow.

I have a brand new board that supports EFI, but it works just fine in bios mode too.

Windows has supported EFI for a long time, but this is true only of certain versions of Windows. IIRC, the x86-64 version of Windows Vista and 7 can boot using EFI, and the Itanium version of Windows XP and later can boot using EFI. AFAIK, no 32-bit version of Windows can boot using EFI, but that's not a big problem, since AFAIK, the only 32-bit (x86) EFI systems are some of the earliest Intel-based Macs, and Microsoft doesn't support the version of EFI that Apple uses even on its 64-bit Intel Macs.

There are some more details in [Microsoft's GPT FAQ,](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx) although that document is focused on GPT rather than EFI.

---

### Post by rijnsma on 2011-10-25
I hope not, but I think Linux is going to lose a lot of people this way, while it has never been very 'big'. Grub2, ext4, Unity, Gnome3 were problems for the user, this is worse. It cumulates.
And this in a time of much bought smartphone and tablet...

I think there will have to be a solution or more then one, which make(s) install (or install of more systems on partitions: multiboot) as 'simple' or 'easy' as it was. Or else we can forget it I am afraid.
Ubuntu was always easy installing and it has payed off.
I hope I'm too pessimistic.

---

