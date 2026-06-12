---
title: "PXE boot with Unbuntu and Winodws Server 2003"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by kapellen421 on 2009-12-16
OK here is my problem.
I am trying to setup a pxe boot server using Ubuntu 9.10. I have read a fair amount of documentation out their about setting up a server. My problem is that they all want the pxe server to also serve as the dhcp server. This I can't do. I have a windows server 2003 box that is the dhcp server. What i need to know is if it is what if anything do I need to do to have a Windows dhcp box and an Ubuntu pxe box to coexists in some unholy union so that I can have the awesome power of pxe boot.

Thanks in advanced

---

### Post by kapellen421 on 2009-12-17
bump

---

### Post by mdshann on 2009-12-18
You need to have the dhcp server tell the client where the PXE / TFTP server is. I had to do this on my tomato router by adding ```
dhcp-boot=pxelinux.0,,192.168.1.150
``` to the dhcp section. Unfortunately I don't know exactly how to do the same on server 2003.

Looking at my server here I would imagine that if you went to Administrative Tools > DHCP, clicked on Scope Options, and the right clicked in the main window and selected Configure Options that options 066 and 067 would be what you are looking for. Try putting the PXE servers IP address as the string value for 066 and the name of the boot file (probably pxelinux.0) in the string field for option 067.]

I have never done this but it looks to me like it may work. You may need to restart the DHCP service or the 2003 machine to see results.

---

