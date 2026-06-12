---
title: "Unable to boot after clean install of 18.04"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by lucky-bloop on 2018-07-18
Dear Ubuntu community, I've been struggling to get my laptop to boot into Ubuntu 18.04 or 16.04 for several weeks now and any help would be much appreciated!

I have a simple laptop for traveling: an Acer R3-131T that shipped with Windows 10. I had been using Ubuntu 16.04 for several months when an odd problem popped up and I attempted to start fresh with a clean install of Ubuntu 18.04. After reinstalling I have been unable to get the computer to boot from it's internal drive- currently it shows the Acer logo and briefly flashes some terminal output before going black and attempting to boot again.

I have been able to boot using a USB drive with the Ubuntu Installer and also using a boot repair USB drive and I was also able to successfully restore and boot a backup of Windows 10 using Clonezilla. I was unable to boot my backup of Ubuntu 16.04 or boot after installing a fresh copy of 16.04.

For additional information - this machine uses UEFI, secure boot is turned off and my boot options menu currently shows only Linpus Lite. Here is the output from my boot repair attempt: [URL="http://pastebin.ubuntu.com/p/HWbn48Gf4t/"]http://pastebin.ubuntu.com/p/HWbn48Gf4t/
[/URL]
Many thanks!

---

### Post by lucky-bloop on 2018-07-19
Problem solved by a generous EriC^^ in the ubuntu IRC channel!

The solution was to boot from a live usb and mount the sda1 partition on my internal drive:
```
sudo mount /dev/sda1 /mnt && ls -lR /mnt/efi
```

In my /dev/sda1 partition I had efi/BOOT and efi/ubuntu directories. I added /efi/microsoft/boot, and copied copied the shimx64.efi and grubx64.efi files into /efi/microsoft/boot/:
```
sudo mkdir -p /mnt/efi/microsoft/boot && sudo cp /mnt/efi/ubuntu/shimx64.efi /mnt/efi/microsoft/boot/bootmgfw.efi && sudo cp /mnt/efi/ubuntu/grubx64.efi /mnt/efi/microsoft/boot/grubx64.efi
```

Thanks again to EriC^^ !!!

---

