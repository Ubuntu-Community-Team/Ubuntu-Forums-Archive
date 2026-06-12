---
title: "Edgy kernels and linux-restricted-modules for nvidia driver"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by tommcd on 2006-10-27
I did a clean install of Edgy using the alternate install CD. After the install I did 'uname -r' and got '2.6.17-10-generic' as kernel. After installing the nvidia driver like this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
I had to use the CD to install kernel-common. Upon reboot 'uname -r' gave 2.6.17-10-386.
I understand the 686 and k7 kernels are not being offered anymore, is that correct?
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)
Anyway, my question is: Should I be booting the 386 or the 'generic' kernel by default? And does it matter? I have an AMD 64 CPU.
Any advice appreciated, thanks.

---

### Post by TKBuisan on 2006-10-27
I understand the the "generic" kernal/image/restricted... has all the SMP and K7 stuff. I updated my laptop to edgy... For the most part, it is okay. I am not able to use the nvidia drivers, and I have to boot into recovery mode before going to X/gui.

---

### Post by tommcd on 2006-10-27
OK, thanks. I just found this by nvidia guru tseliot:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
I guess I will go back to the generic kernel. Hope it goes OK.

---

### Post by tommcd on 2006-10-27
Well, it went ok! I am now back on the generic kernel. I had to edit /boot/grub/menu.lst to get the generic kernel to boot by default though. Glad I didn't screw that up. I don't know if either kernel makes any real difference. I never saw any performance boost on the k7 kernel in dapper. I did notice that the 386 kernel in edgy can address more than 1GB RAM (I have 2GB). If I remember corrrectly, the 386 kernel in dapper could only address 1GB RAM. Thanks again.
EDIT: forgot to mention I am using 32bit ubuntu, not 64bit.

---

