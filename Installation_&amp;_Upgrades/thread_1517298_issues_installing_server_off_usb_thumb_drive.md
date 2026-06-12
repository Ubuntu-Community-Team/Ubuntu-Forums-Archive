---
title: "issues installing server off usb thumb drive"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by jkicak on 2010-06-24
installing ubuntu server 10.04 from USB (made with universal usb installer) fails after setting up keyboard layout.  the install fails at loading files from CD.  

is there some config file that i need to change to tell it not to look at the cd-rom but to look at the USB stick?     


error code when i hit alt-f4:
cdrom-retriever error:  unable to find 'pool/main/l/linux/fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_amd64.udeb


thanks for any help in advance!

---

### Post by jkicak on 2010-06-24
ok, so i had to rename the file from .ude to .udeb on the usb drive and it worked.   not sure why it was named different than what the installer wanted???

once i renamed the extension of the file the installer worked.....

---

### Post by newlifeform on 2010-07-14
Hi guys, 

I am getting the same error when trying to install ubuntu server 10.04 64bit on ESXi server. 
Any advice would be appreciated. 

Thanks

---

