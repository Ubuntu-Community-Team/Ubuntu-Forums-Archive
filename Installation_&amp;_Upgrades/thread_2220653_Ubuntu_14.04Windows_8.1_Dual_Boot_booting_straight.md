---
title: "Ubuntu 14.04/Windows 8.1 Dual Boot booting straight to Windows"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by deigan91 on 2014-04-28
Hi,

I'm trying to install Ubuntu 14.04 alongside Windows 8.1 on my Sony Vaio Pro (which came with Windows 8 preinstalled). I followed the instructions at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450), and completed an installation, but when I restarted my computer, it booted straight to Windows. So I ran Boot-Repair (following the second option here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), but my computer is still booting straight into Windows. Here is the pastebin from the boot repair: [http://paste.ubuntu.com/7355864/](http://paste.ubuntu.com/7355864/).

I'd really appreciate any help. Let me know if there's any more information that I could provide that might be useful.

Thanks,
Mike

---

### Post by oldfred on 2014-04-29
I do not think Sony's are Ubuntu friendly.

Can you boot the ubuntu entry from UEFI? With either secure boot on or secure boot off, but still UEFI?
Not sure how or why you have so many Windows entries?
Soon info on cleaning up UEFI, is in link in my signature.

```
BootOrder: 0000,000C,0005,0007,0008,0009,0001,000B,000A
Boot0001* Windows Boot Manager
Boot0005* Sony Original
Boot0007* Windows Boot Manager
Boot0008* Windows Boot Manager
Boot0009* Windows Boot Manager
Boot000A* Windows Boot Manager
Boot000B* Windows Boot Manager
Boot000C* UEFI: IntegralCourier PMAP
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR].
```

Other Sony, seemed like file rename required as Sony has modified UEFI to only boot Windows. Work around is to rename Windows efi file to be grub or shim and UEFI thinks it is booting Windows but really boots grub menu. But then you can only boot Windows from grub menu.

 With encryption but you do not have to
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
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

Some have found they can rename bootx64.efi and boot hard drive.

 Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
The booting device or hard drive works also.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

