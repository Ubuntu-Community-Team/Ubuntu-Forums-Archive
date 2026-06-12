---
title: "Disabling onboard video?"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by pclancy on 2006-06-14
I'm trying to install Ubuntu on a new computer, it's got an Asus P5RD2-VM motherboard with onboard video.  I wanted to disable it in the BIOS, but there doesn't appear to be an option for totally disabling it.  I have a Nvidia graphics card I'd like to use instead, but each time I try to install Ubuntu it configures xorg.conf to look for the Ati x200 express onboard graphics.

Here are my choices in the bios: 
> Boot Graphics Adapter Priority: [IGD], [PEG/IGD], [PCI/IGD]

I chose [PCI/IGD], but that doesn't seem to do anything.  Can I get Ubuntu to ignore the onboard graphics completely?  Can I do this from the installation DVD?  I tried to configure my xorg.conf manually using a nvidia driver, but it said that the module needs to be loaded.

Thanks.

---

### Post by pclancy on 2006-06-14
I should mention that I can get graphics working by running a ```
dpkg-reconfigure xserver-xorg
```

---

### Post by az on 2006-06-14
[QUOTE=pclancy]I should mention that I can get graphics working by running a ```
dpkg-reconfigure xserver-xorg
```[/QUOTE]
Well, that should fix it permanently, no?

---

### Post by pclancy on 2006-06-15
That solves it from the Linux side, but now it's just a question of completely disabling it in the BIOS.  It steals 32 MB of the RAM for the onboard video, even though I'm not using it.  Also, it complains about not allocating device region 3 with the address 0000:00.00.  If I run lspci -v I can see that address corresponds to the onboard video.  Any ideas?

---

### Post by jrd on 2006-06-15
If it uses a pci slot just select PCI/IGD. It will look for a device on the pci slot first, if it finds one it will use it, if not it will use the other, not both.

---

### Post by pclancy on 2006-06-15
I am using PCI/IGD, but that does explain why it always selects the onboard video by default. lspci -v tells me that onboard video is the first address, and my video card is at 02:00.00.

---

### Post by pclancy on 2006-06-15
Here are the error messages I see when I boot into Ubuntu.
```
[17179571.316000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[17179570.948000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
```

Any ideas?

---

### Post by emelpy on 2006-07-27
> **pclancy said:**
> Here are the error messages I see when I boot into Ubuntu.
```
[17179571.316000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[17179570.948000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
```


I have the same motherboard with a Pentium D 930 chip and I am getting that same message when I try to install ubuntu.  I would really like to try it out on my new comp so any help would be appreciated.

---

