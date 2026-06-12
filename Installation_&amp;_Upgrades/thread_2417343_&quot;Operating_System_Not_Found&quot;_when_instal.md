---
title: "&quot;Operating System Not Found&quot; when installing Lubuntu 19.04 on Dell Inspiron N7110"
date: 2019-04-22
forum: Installation &amp; Upgrades
---

### Post by jack9761 on 2019-04-22
I am trying to install Lubuntu 19.04 64 Bit on an old Dell Inspiron N7110, I have installed the ISO on a 16GB flash drive using multiple tools (Startup Disk Creator, Unetbootin. and Balena Etcher on my Kubuntu machine, and Rufus on my windows). The BIOS has no options to switch between UEFI and Legacy or to toggle Secure Boot. I can only boot into USB using some ports. When I do manage to boot into the USB the screen goes blank for about five seconds then says "Operating System Not Found". Windows 7 is still installed on the disk if any patches are necessary. The BIOS is Dell Phenox, version A13.

---

### Post by yancek on 2019-04-22
> The BIOS has no options to switch between UEFI and Legacy or to toggle Secure Boot  

Not surprising on an older computer.  That just means you can't use UEFI.  If you have the correct drive set to first boot priority, it should boot if writing it with the different software was successful.  To eliminate that possibility, do you have another computer you can use to test to see if it boots?

---

### Post by jack9761 on 2019-04-22
I have tried two different flash drives of the same model, and both can boot using both UEFI and Legacy on my desktop.

---

