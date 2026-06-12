---
title: "Boot problem on Sony Vaio Pro with win8"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by filaruina on 2016-01-02
Hi,

I got tired of windows on my ultrabook and since I'll be doing some work on it decided to install the new ubuntu version.
I'm not new to the process. Built an 64-bit Ubuntu 15.10 bootable stick, booted from it and did a clean installation, removing windows at all.
All was installed in UEFI mode and worked really well.
Problem is that the PC won't boot into ubuntu, even after an apparently perfect installation.
It goes to the "windows couldn't be booted" vaio rescue screen. I tried disabling safe boot, reinstalling and etc.
I've done the Boot-Repair recommended repair and didn't work either. Here is the output [http://paste.ubuntu.com/14368110/](http://paste.ubuntu.com/14368110/)
Here is efibootmgr output (not sure it is contained in the repair output)
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0006,0005
Boot0005* Windows Boot Manager
Boot0006* UEFI: KingstonDataTraveler 2.01.00

The notebook is a Sony Vaio [FONT=Arial][COLOR=#000000]SVP13215PXB
[/COLOR][/FONT]
Any ideas? Thanks for any help!

---

### Post by oldfred on 2016-01-03
One Sony user who was dual booting:
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

And if only booting Ubuntu change UEFI descption from ubuntu to Windows for the shim boot file.
      
 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)

    
More details on editing UEFI boot entries in link in my signature.

---

### Post by filaruina on 2016-01-05
Thanks a lot, that solved the problem!
Everything is working as expected.
Maybe that could go in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) ?
A troubleshooting section or something like that, just like the one in your thread.

Thanks again!

---

