---
title: "Install windows 8 after Ubuntu 12.10"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by erik1001 on 2012-12-29
Hello guys.
It's the first time I install Ubuntu before windows and thats why I failed so much so I need your help.
I have 64bit Ubuntu 12.10 and I left some space to add Windows 8 later. The time for Windows came and I put the bootable USB stick to install it, but get stuck - choosing any partition, including ntfs one, return this message: 
```
"windows cannot be installed on this disk. The selected disk is of the GPT partition style."
```
I've googled it for some info, but all I understand is that I have partition table that Windows does not like and support. One solution would be to backup entire data, install Windows and then restore my Ubuntu, but I think there should be easier way.
There is my partition table:
[IMG]http://screencloud.net/img/screenshots/7990971d4aa1ff4df2ab9892c36badcf.png[/IMG]
Thanks in advance.

---

### Post by ronparent on 2012-12-29
Have you tried installing to what is now sda6 ntfs with it as unallocated space (ie delete the sda6 partition)? This would allow Windows to partition its own space as it pleases.

---

### Post by erik1001 on 2012-12-29
Yes, I have. And I had the same result. The problem seems to be the type of partition table. I have GPT, windows wants MBR, but I have no idea how to change it without data-loss.

---

### Post by ronparent on 2012-12-29
Windows 8 will probably prefer GPT system but may insist on setting it up itself. We need to get the attention of someone who knows the uefi specifics as it relates to Windows..

---

### Post by erik1001 on 2012-12-29
Actually you are right, I've switched GPT with MBR. To be honest, I've learned about them this evening and I'm little confused in this situation. :D

---

### Post by oldfred on 2012-12-29
I see an efi partition, so is Ubuntu in UEFI mode. Then you need to install Windows in UEFI mode.

Windows needs some extra partitions, but should use same efi partition. I think someone posted that DVD does not work, you have to use flash drive and boot installer in UEFI mode, not BIOS.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
       You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

