---
title: "Installing Ubuntu 11.04 64bit - Error when creating partitions"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by kmsram420 on 2011-05-06
All,

I have been using Ubuntu 10.04 all this while. I also have windows in my machine. Today I wanted to try 11.04 and created a USB disk. After using the live disk I set to install 11.04 via the steps below:

1. Removed the 10.04 partition via Windows 7
2. Recovered Windows 7 just to make sure I have atleast one OS running. 
3. Used the USB disk to install 11.04. 
4. I tried to set up manual partition with swap space and a ect4 drive for "/". 
5. I also tried the default partition option to install along side Windows 7 in the 11.04 installer. 

I get the following error:

“Error: Error informing the kernel about modifications to partition /dev/ <partition name> - Device or resource busy. This means Linux won't know about any changes you made to /dev/ <partition name> until you reboot - so you shouldn't mount it or use it in any way before rebooting.”

I tried googling a lot to find a fix but nothing helpful as of now.

Can someone help me with this ?

---

### Post by hohokuji on 2011-05-06
Maybe just switch the scsi setting in BIOS to ATA?

---

