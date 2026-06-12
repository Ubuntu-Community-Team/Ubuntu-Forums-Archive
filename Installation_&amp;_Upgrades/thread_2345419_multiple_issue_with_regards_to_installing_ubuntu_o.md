---
title: "multiple issue with regards to installing ubuntu on Alienware 15 R3"
date: 2016-12-04
forum: Installation &amp; Upgrades
---

### Post by hb4ch on 2016-12-04
Hi!I just got a new Alienware 15 R3 computer and tried to install a ubuntu 16.04 LTS alongside with my factory-installed Windows 10 with my live usb created in Rufus. And There seem to be some troublesome issues.

The hardware specs involved: 
      CPU:i7-6700HQ
      Harddrive: 1TB HDD(AHCI controller) + 256GB SSD(NVM controller)
      Graphic: Intel embedded + Nvidia GTX 1070

The computer is pre-installed with a Windows 10. I assume it's installed in UEFI mode since it's a relatively new model. However, the ubuntu installer can't recognize the installed Windows(on SSD), and can only recognize the HDD. Because the ubuntu installer can't read my SSD, it pops up a warning, saying that I should reconsider sticking to UEFI mode if I am still willing to boot my installed system(How weird? How did it see the EFI partition? The EFI partition is on my NVM SSD).

 I was hoping that it could create a EFI partition on the HDD and the bios could read it. But that's not the case here. After installation, the computer went directly to Windows. I tried to change the BIOS boot options several times, switching from UEFI to Legacy, with secure boot on and off...It booted for once, but there shows a software lock up bug, saying that the CPU#4 is not responding(not exact word, transcribed from memory).

I did some googling. I upgrade my BIOS firmware to the latest version. I tried the newest Ubuntu 16.10, and the installation just can't work. It went to a black screen, saying some nouveau error. (I assume that's the Nvidia graphic problem?).

So in brief, How can I make ubuntu recognize my SSD? I think that can solve more that half of the issue.

Thanks!

---

