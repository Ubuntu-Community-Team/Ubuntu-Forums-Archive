---
title: "Dualboot not working on Sony laptop with UEFI"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by clemmy on 2014-10-06
Dear all,

just tried to install ubuntu on my friend's sony Vaio laptop model SVS13A1S9ES which comes preloaded with Windows 7, UEFI H2O bios, and GPT partition table. Ubuntu successfully installed from usb drive but grub boot-loader is not shown after reboot and only windows loads.

So, we followed the tutorial on community help website, booted ubuntu live from usb drive and run Boot-Repair software with "Recommended repair". After reboot the grub menu still is not shown and the laptop boots only windows. The output of boot-repair is here [http://paste.ubuntu.com/8506859/](http://paste.ubuntu.com/8506859/)


Can you please help us or point us in the right direction? I have long experience with linux and ubuntu, but this is the first time I deal with UEFI :(

---

### Post by oldfred on 2014-10-06
Windows 7 should not have secure boot or the always on hibernation or fast boot type issues.

But with Windows 8, Sony's only boot Windows and require a work around.

Can you boot from a one time boot key? Often f12, f10 or f8 but varies by vendor.

If not you can try one of the work arounds. Many just rename /efi/boot/bootx64.efi and copy grub into that folder and rename grub to bootx64.efi. Then boot hard drive entry from UEFI.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Some others that also worked:

 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)

---

### Post by clemmy on 2014-10-06
Dear oldfred, thanks for your reply.

Secure boot does not seem to be implemented, or at least is not mentioned anywhere in the BIOS menu. Also, the laptop came with windows 7, not 8, so AFAIK it shouldn't be a problem. Am I wrong?

Concerning a one time boot key, so far we have not found any, but will try again to doublecheck. By the way, within the boot menu in the BIOS settings, we could change the order of the different devices to boot from (main HD, USB, or DVD), but not a specific partition within the HD.

In any case, we can still load a live Linux from a USB stick. Will try one of yours workarounds..

I really didn't expect this to be so complicated :(

---

### Post by clemmy on 2014-10-06
According to this Web page [http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx) probably there isn't any keyboard shortcut for a time boot menu.. Will probably need to use a workaround

---

### Post by Vladlenin5000 on 2014-10-06
Just checked Sony VAIO SVS13A1S9ES manual and found the following notes:
```
**Booting Your VAIO Computer from External Devices**

 You can boot your VAIO computer from external  devices, such as an optical disc drive or a USB floppy disk drive, by  using the BIOS function.
 
[LIST]
[*]     Connect an external device to your VAIO computer and turn on the computer. 
[/LIST]
 
[LIST]
[*]     Press the **F11** key repeatedly until the VAIO logo disappears. 
[/LIST]
 The booting process from the external device starts. If your VAIO computer does not boot up, restart the computer and try again.
 Note
 
[LIST]
[*]     Disconnect all devices from your VAIO computer except for the  external device from which you intend to boot up. Some devices cannot be  used to boot the computer, or cannot be used with the computer. 
[/LIST]
 
[LIST]
[*]     If an AC adapter is supplied with the external device, be sure to connect it to an AC power source in advance. 
[/LIST]

```

---

### Post by clemmy on 2014-10-07
Solved it the hard way. Went back to bios settings and discovered that it was possible to completely disable UEFI and fallback to legacy boot. So we did, and get rid of the problems, no workaround needed. Bombproof dualboot like good old times.

The only downside: we had to completely wipe the HD in order to setup a msdos partition table (was GPT before). So he had to backup everything to an external HD, then so he had to reinstall both windows and Ubuntu from scratch

---

### Post by Vladlenin5000 on 2014-10-07
That's certainly one way to do it... :p

---

