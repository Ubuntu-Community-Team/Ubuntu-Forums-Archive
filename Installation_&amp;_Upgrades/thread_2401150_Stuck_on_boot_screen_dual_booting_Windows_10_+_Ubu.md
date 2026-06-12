---
title: "Stuck on boot screen dual booting Windows 10 + Ubuntu 18.04"
date: 2018-09-14
forum: Installation &amp; Upgrades
---

### Post by coldcamo on 2018-09-14
I'm following the process [here]("https://askubuntu.com/a/484456"), and everything was going smoothly until I realized I was stuck on the purple Ubuntu boot screen. I pressed the escape key and saw the output below.

[IMG]https://i.imgur.com/ocrfnsv.png[/IMG]

Those lines towards the bottom repeat over and over again. My specs are x64 Windows 10 8GB, FX-6300 processor, NVIDIA GeForce 970, and an MSI 7641 motherboard.

Any help is appreciated. Would like to get away from windows as soon as possible.

---

### Post by oldfred on 2018-09-14
Is this from live installer or after install?
 
Your nVidia typically needs nomodeset.
Most systems require UEFI updates, and if SSD firmware update to SSD.
Some MSI need boot parameters or UEFI settings. Note if you update UEFI, you have to redo settings you changed. My Asus has 5 to 7 settings, some requried & some optional that I have to redo.

See also:
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by coldcamo on 2018-09-14
> **oldfred said:**
> Is this from live installer or after install?
 
Your nVidia typically needs nomodeset.
Most systems require UEFI updates, and if SSD firmware update to SSD.
Some MSI need boot parameters or UEFI settings. Note if you update UEFI, you have to redo settings you changed. My Asus has 5 to 7 settings, some requried & some optional that I have to redo.

See also:
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
This is from the initial install process. My bios is legacy and not UEFI. I think those are different things. Maybe I'm wrong, sorry. I don't have an SSD either. I updated my graphics drivers to the latest version and replaced "quiet splash" with "nomodeset". The result is pretty much the same, unfortunately. I don't see any other boot parameters on those pages that would solve this.

[IMG]https://i.imgur.com/nXMvn3c.png[/IMG]

Do I need to update/flash my bios?

---

### Post by oldfred on 2018-09-14
I would update BIOS, that may be part or all of issue.

Are drives set for AHCI, not RAID nor some Intel SRT type setting?
If RAID Windows will need AHCI driver first. And if RAID 0 that should not be changed, but a separate issue.

---

### Post by coldcamo on 2018-09-15
I solved this by just using a USB instead of unetbootin. Thanks for the help anyways, I appreciate it.

---

