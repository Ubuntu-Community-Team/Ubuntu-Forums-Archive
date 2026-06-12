---
title: "Ubuntu update has killed my triple-boot."
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by kev717 on 2010-09-18
After installing ubuntu 10.04 updates just now (including updates to the kernel), update-grub seems to have seriously messed up my triple boot.  
It used to go: Ubuntu, Fedora (listed as 3 fedora kernels for /dev/logVol, and 3 kernels for /dev/sda2), and Sabayon (edited in my /etc/grub.d/40_custom because ubuntu wouldn't detect Sabayon).  
Now, it's pretty much all sabayon and my Fedora 13 kernels are listed as sabayon as well :confused: (and it tries to boot sabayon to a fedora kernel).  
I have attached a copy of my /boot/grub/grub.cfg in case it can help, as well as the output from my messages.log that seem to correspond with the updating of grub (first the installer updated my grub.cfg, then I ran update-grub after noticing the problem, so there are two blocks of data at two different times corresponding with update-grub).  

I would really like to have this fixed within the next 12 hours because I will be having company over and I was hoping to show off my linux triple-boot.

Thank-you in advance for any assistance that can be offered.
-kev717

EDIT: Also, it would appear that on a separate partition there is another grub bootloader that is inactive because Ubuntu's bootloader overwrote the MBR.  There are the Fedora and Sabayon boot kernels in that partition as well as the grub.cfg within that partition which also contains the entries for Fedora and Sabayon (but not ubuntu).  Don't know if this will help with a solution, but it is worth knowing that a temporary solution can be made by modifying Ubuntu's grub.cfg to include the necessary entries (but it will still be problematic as ubuntu regenerates the grub.cfg)

---

### Post by kev717 on 2010-09-19
*bump*
Searched around and still can't find anything.

---

