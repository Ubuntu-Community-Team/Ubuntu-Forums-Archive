---
title: "new laptop boot"
date: 2019-12-30
forum: Installation &amp; Upgrades
---

### Post by chpnp on 2019-12-30
Hi there,

I received a new Lenovo x390.
I want to replace the provided ssd with another ssd (from my prior laptop)
My ssd when usb connected to another PC, is able to boot.
Once connected to the x390 it does not work (it proposes only to boot W10, which sits on that same hw).

An ubuntu install ssd will not boot either.
I have disabled the secure boot, this does not suffice.

Any suggestion ?
Thanks

brgds

---

### Post by yancek on 2019-12-31
Was the original SSD with Ubuntu an EFI install?  Windows 10 is almost certainly EFI.  If Ubuntu was not an EFI install on the original drive, the you would need to access the BIOS and set it to first boot priority there and enable Legacy/CSM boot.  If the Ubuntu install was EFI, you need to make the new computer aware of it by putting the EFI files from the Ubuntu SSD on the EFI partition of the windows drive (if one exists) or install Grub EFI.  

So questions are, is Ubuntu on the SSD an EFI install and is windows on the new machine EFI?

---

### Post by oldfred on 2019-12-31
If new (old) drive has UEFI installs, you have to add an ubuntu entry to UEFI with efibootmgr. Most UEFI find Windows automatically, but do not find /EFI/ubuntu folder & its boot files.

Do you have a hard drive or fallback boot entry. That is /EFI/Bootx64.efi and originally was a copy of Windows efi boot file. But grub now installs shimx64.efi as bootx64.efi to boot Ubuntu.

man efibootmgr

sudo efibootmgr -v

       sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition default is sda and first partition, so only required if ESP not sda1
sudo efibootmgr -c -g  -w -L "ubuntu" -l '\EFI\ubuntu\shimx64.efi' -d /dev/sda -p 1

---

### Post by chpnp on 2020-01-07
Hi There,

thanks for your answers.
For the records, (and for future reference) , there were several different issues.
- Lenovo setup has a tickbox for using 'optimized os set up', or something similar. Turned out that unticking it allowed to show the (uefi) ram key for boot, which was invisible before then.
As strange as it may look like, it seems that disabling secure boot (and enabling legacy boot)  was not sufficient to disable secure boot (and enable legacy boot); to untick that other box was also required.
- my ubuntu on ssd was still not visible, and I do not know why. Reinstalling it was possible (since the ram key was visible now).
Maybe using efibootmgr may have solved this; hard to tell now because it is working after reinstall (and it may have erased/replace prior ubuntu efi entries)

Anyway, problem solved. 
I gave some details here to hope it may save some time for someone doing a web search....

---

