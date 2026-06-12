---
title: "need to clear /boot to upgrade to 10.10"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by RuRat on 2010-12-11
I have searched high an low for weeks now and have been unsuccessful in finding a solution, any pointers i have been given i have tried and it has not cleared my boot directory to be able to upgrade.

i know i need to use synaptic but what do i look for in synaptic, i already tried &#347;udo apt-get clean, without success, please help!
Below is the error i get when i try to upgrade along with the contents of my /boot



Not enough free disk space

The upgrade has aborted. The upgrade needs a total of 39.8M free space on disk '/boot'. Please free at least an additional 19.0M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

this is the contents of my boot directory what do i need to delete out of it to be able to upgrade to 10.10;

/boot/abi-2.6.22-14-server
/boot/abi-2.6.22-16-server
/boot/abi-2.6.24-28-server
/boot/abi-2.6.27-17-server
/boot/abi-2.6.28-19-server
/boot/abi-2.6.31-22-generic
/boot/abi-2.6.31-22-generic-pae
/boot/abi-2.6.32-22-generic
/boot/abi-2.6.32-22-generic-pae
/boot/abi-2.6.32-23-generic
/boot/abi-2.6.32-23-generic-pae
/boot/abi-2.6.32-24-generic
/boot/abi-2.6.32-24-generic-pae
/boot/config-2.6.22-14-server
/boot/config-2.6.22-16-server
/boot/config-2.6.24-28-server
/boot/config-2.6.27-17-server
/boot/config-2.6.28-19-server
/boot/config-2.6.31-22-generic
/boot/config-2.6.31-22-generic-pae
/boot/config-2.6.32-22-generic
/boot/config-2.6.32-22-generic-pae
/boot/config-2.6.32-23-generic
/boot/config-2.6.32-23-generic-pae
/boot/config-2.6.32-24-generic
/boot/config-2.6.32-24-generic-pae
/boot/initrd.img-2.6.22-14-server
/boot/initrd.img-2.6.22-14-server.bak
/boot/initrd.img-2.6.22-16-server
/boot/initrd.img-2.6.22-16-server.bak
/boot/initrd.img-2.6.24-28-server
/boot/initrd.img-2.6.24-28-server.bak
/boot/initrd.img-2.6.27-17-server
/boot/initrd.img-2.6.28-19-server
/boot/initrd.img-2.6.31-22-generic
/boot/initrd.img-2.6.31-22-generic-pae
/boot/initrd.img-2.6.32-22-generic
/boot/initrd.img-2.6.32-22-generic-pae
/boot/initrd.img-2.6.32-23-generic
/boot/initrd.img-2.6.32-23-generic-pae
/boot/initrd.img-2.6.32-24-generic
/boot/initrd.img-2.6.32-24-generic-pae
/boot/memtest86+.bin
/boot/System.map-2.6.22-14-server
/boot/System.map-2.6.22-16-server
/boot/System.map-2.6.24-28-server
/boot/System.map-2.6.27-17-server
/boot/System.map-2.6.28-19-server
/boot/System.map-2.6.31-22-generic
/boot/System.map-2.6.31-22-generic-pae
/boot/System.map-2.6.32-22-generic
/boot/System.map-2.6.32-22-generic-pae
/boot/System.map-2.6.32-23-generic
/boot/System.map-2.6.32-23-generic-pae
/boot/System.map-2.6.32-24-generic
/boot/System.map-2.6.32-24-generic-pae
/boot/vmcoreinfo-2.6.27-17-server
/boot/vmcoreinfo-2.6.28-19-server
/boot/vmcoreinfo-2.6.31-22-generic
/boot/vmcoreinfo-2.6.31-22-generic-pae
/boot/vmcoreinfo-2.6.32-22-generic
/boot/vmcoreinfo-2.6.32-22-generic-pae
/boot/vmcoreinfo-2.6.32-23-generic
/boot/vmcoreinfo-2.6.32-23-generic-pae
/boot/vmcoreinfo-2.6.32-24-generic
/boot/vmcoreinfo-2.6.32-24-generic-pae
/boot/vmlinuz-2.6.22-14-server
/boot/vmlinuz-2.6.22-16-server
/boot/vmlinuz-2.6.24-28-server
/boot/vmlinuz-2.6.27-17-server
/boot/vmlinuz-2.6.28-19-server
/boot/vmlinuz-2.6.31-22-generic
/boot/vmlinuz-2.6.31-22-generic-pae
/boot/vmlinuz-2.6.32-22-generic
/boot/vmlinuz-2.6.32-22-generic-pae
/boot/vmlinuz-2.6.32-23-generic
/boot/vmlinuz-2.6.32-23-generic-pae
/boot/vmlinuz-2.6.32-24-generic
/boot/vmlinuz-2.6.32-24-generic-pae

---

### Post by cipherboy_loc on 2010-12-11
Do you really have 14 different kernel version? Open up synaptic and remove all but 2.6.32-24 and 2.6.32-24-pae.

That should free up a lot of space.




Cipherboy

---

### Post by drs305 on 2010-12-11
Install Ubuntu Tweak. It's a GUI app that can easily remove older kernels. Here is a link on how to install and use it, as well as other ways to remove older kernels:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by RuRat on 2010-12-12
> **drs305 said:**
> Install Ubuntu Tweak. It's a GUI app that can easily remove older kernels. Here is a link on how to install and use it, as well as other ways to remove older kernels:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")


thanks that helped a great deal i am now using 10.10 

i had to disable the nouveau display driver as i have an nvidia graphics card but after i figured that out, i was and am golden

thanks so much Ubuntu Tweak was the answer

---

