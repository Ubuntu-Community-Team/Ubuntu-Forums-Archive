---
title: "Install 7.04 onto Netserver LH3"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by theApemani on 2007-05-24
Hi,

I need help installing 7.04 onto an old server
LH3 ...  I have reconfigured the Disks through Netraid and initialised the disks
As far as I know it is 3SI SCSI
I have booted up to the install screen and when go to install it says loading kernel
and then the machine reboots

Is there any boot parameter to enter to get it to work??

Thanks

---

### Post by ybn1197 on 2007-06-15
Any luck with this? The IT department of the company I work for is excessing one of these servers and giving it to me. I was going to install the server version of 7.04 on it. If you were successful, is there anything I should look out for?

---

### Post by ybn1197 on 2007-06-29
Its been almost two weeks since I setup Ubuntu 7.04 server on the LH3. Everything is working fine. The only change I had to make was to go into the SCSI configuration and change the RAID to a megaRAID configuration. Once I did that, everything started working fine.

---

### Post by ironlizard on 2007-08-19
If only they were all that simple. If anyone else has this problem with the 1M and 2M, the solution is to [edit the megaraid.h and megaraic.c]("http://ironlizard.blogspot.com/2007/08/hp-netraid-and-modern-linux-kernels.html") files in the SCSI driver directory, then recompile the kernel with only the legacy driver as a module. This is for debian, but Ubuntu should be almost exactly the same. This took me two days to figure out and the answer wasn't anywhere in here. Had to piece it together form several places. I did it on the machine itself by installing an older 2.4 kernel first, then compiling. With luck this patch will be included in future versions so I don't have to recompile the kernel for every upgrade.

---

