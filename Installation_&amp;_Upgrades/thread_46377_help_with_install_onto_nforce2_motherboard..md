---
title: "help with install onto nforce2 motherboard."
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by darkpark on 2005-07-04
i can successfully install ubuntu 5.04 onto my system which has the nforce2 chipset (abit nf7-s2)  but upon the completion of the installation i have no connectivity.  when i run ifconfig eth0 up or down i get no errors but i can't get an ip via dhcp.  
so i install the kernel headers and build-essentials, download the nforce2 drivers from nvidia (using another machine to download) and install them.  
after the nvidia installer does it's thing i still have no connectivity.  if i do modprobe nvnet i get a connection but it only lasts until i reboot.  i added 'nvnet' to /etc/modules but that doesn't help.   what am i doing wrong?   
oh yeah, i also tried "alias nvnet eth0" or vise versa.  but again that didn't help.  (yes, i did reboot) :)  

please help.

---

### Post by nudicles on 2005-09-19
[QUOTE=darkpark]i can successfully install ubuntu 5.04 onto my system which has the nforce2 chipset (abit nf7-s2)  but upon the completion of the installation i have no connectivity.  when i run ifconfig eth0 up or down i get no errors but i can't get an ip via dhcp.  
so i install the kernel headers and build-essentials, download the nforce2 drivers from nvidia (using another machine to download) and install them.  
after the nvidia installer does it's thing i still have no connectivity.  if i do modprobe nvnet i get a connection but it only lasts until i reboot.  i added 'nvnet' to /etc/modules but that doesn't help.   what am i doing wrong?   
oh yeah, i also tried "alias nvnet eth0" or vise versa.  but again that didn't help.  (yes, i did reboot) :)  

please help.[/QUOTE]
 Sorry to dig up an old thread but...

I just got this new motherboard, and reinstalled Ubuntu on it. I'm having similar issues... I can't get Ubuntu to recognize my IC Plus IP100 onboard ethernet adapter; it doesn't show up at all in the network settings. I downloaded and installed the nvidia drivers, and that didn't do anything either.

Then I realized that the nvidia chipset drivers don't install the ethernet driver for this motherboard, even in windows. I had to use a special driver that came with the mobo cd to get it working in windows. So I think the solution may lie in finding the driver from IC Plus, but I couldn't find anything so far.

Does anyone else out there have this mobo and rurnning any distro of Linux?

---

### Post by Nikusan on 2005-12-02
nudicles, I have an ABIT UL8 (ULI chipset, socket 939) here and I'm experiencing the same problem. Everything works fine with the Breezy live CD except the onboard NIC.
Windows XP identifies it as "IC Plus IP100 10/100 Fast Ethernet".
A Google search turns up almost nothing. Can anyone help?

---

