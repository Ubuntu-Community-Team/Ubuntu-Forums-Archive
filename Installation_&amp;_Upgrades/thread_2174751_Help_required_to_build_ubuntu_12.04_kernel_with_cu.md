---
title: "Help required to build ubuntu 12.04 kernel with custom requirements"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by anilmaguluri on 2013-09-16
Hi,

I am new to the Linux Kernel and have custom requirements to build the kernel (12.04).
The changes are regarding the New Socket in networking (mainly on socket.h)...like AF_INET, i have to add new socket AF_CUSTOM.

I am able to download the source using "sudo apt-get source linux-image-$(uname -r)", which has downloaded "linux-lts-quantal-3.5.0" on /usr/src dir.
Then i have modified the socket.h file using sudo vim linux-lts-quantal-3.5.0/include/linux/socket.h and i have followed the below link to build the kernel.

URL: [http://mitchtech.net/compile-linux-kernel-on-ubuntu-12-04-lts-detailed/](http://mitchtech.net/compile-linux-kernel-on-ubuntu-12-04-lts-detailed/)

With the help of above link, i am able to build the kernel and install the deb packages and also updated the grub using "sudo update-grub" command and rebooted the sysem.

After reboot, i am able to select the new kernel. Till this point i am happy that i didnt face any problem.

[B]_Now, when i checked the socket.h file for my changes in /usr/include/sys/socket.h and /usr/include/bits/socket.h, the changes which i made is not updated._
Then i cross verified the path usr/src/linux-lts-quantal-3.5.0/include/linux/socket.h, the chages were present and also i have chekecd the selected kernel image using "uname -r", that also giving custom verion only.[/B]

So, please help me to resolve this.

Thanks & Regards,
Anil Kumar Maguluri

---

