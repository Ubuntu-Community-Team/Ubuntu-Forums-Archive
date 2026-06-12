---
title: "Restore files in /boot partition"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2017-10-27
An update failed with the familiar "/boot partition full?" error. To clean up the boot partition, I executed the following commands
>uname -a
Linux cavu 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

>dpkg -l linux-{image,headers}-\* | grep ^ii
```
ii  linux-headers-4.4.0-93             4.4.0-93.116 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-93-generic     4.4.0-93.116 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-96             4.4.0-96.119 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic     4.4.0-96.119 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-97             4.4.0-97.120 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic     4.4.0-97.120 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.97.102 amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-92-generic       4.4.0-92.115 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generic       4.4.0-93.116 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic       4.4.0-96.119 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic       4.4.0-97.120 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-93-generic 4.4.0-93.116 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic 4.4.0-96.119 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic 4.4.0-97.120 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.97.102 amd64        Generic Linux kernel image
```

>sudo apt-get purge linux-{image,headers}-4.4.0-{92,93,96}* 


>dpkg -l linux-{image,headers}-\* | grep ^ii
```
ii  linux-headers-4.4.0-97             4.4.0-97.120 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic     4.4.0-97.120 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              4.4.0.97.102 amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-97-generic       4.4.0-97.120 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic 4.4.0-97.120 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.97.102 amd64        Generic Linux kernel image
```



I usually keep the two most recent images and headers, but this time I kept only the most recent (97). Unfortunately, 97 had not been installed yet (I was still running 96).  

I then ran the updater.  It gave an error message about "software not found in repositories", but then proceeded with an update. When it prompted me to reboot, I pushed the "reboot later" button because I was afraid it would not boot.  

What should I do?  How can I make sure the new kernel is loaded and the system will boot when I restart?

---

### Post by ian-weisser on 2017-10-27
Your output says 97 IS installed. It's just not the running kernel currently.
The install includes adding the kernel to GRUB.

Let's check to see it it's true and -97 really is a current grub option:
```
cat /boot/grub/grub.cfg | grep "Ubuntu, with Linux 4.4.0-97-generic"
```
If you get NO OUTPUT, then -97 is not installed, run 'sudo update-grub', then look again.
If you get two or three lines of output, then -97 is indeed installed and bootable. Go ahead and reboot.

If there is a problem during reboot, you might need to press ESC to reach the grub menu and the option to boot into -97.

---

### Post by asb3 on 2017-10-27
Thank you.  I will reboot as soon as my currently running jobs finish.

---

