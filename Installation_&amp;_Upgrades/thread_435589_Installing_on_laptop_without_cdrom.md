---
title: "Installing on laptop without cdrom"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by smdeep on 2007-05-07
Hi

I have Ubuntu Hoary already installed on the laptop. I have formatted the Windows partition as ext3 (/dev/sda1). The cdrom does not work on the laptop nor can I boot via usb pendrive. Hoary works on the laptop. Is there any way I can mount a Feisty iso in Hoary and install to /dev/sda1 ?

Thanks in advance.

---

### Post by Stephen Howard on 2007-05-07
[This thread]("http://ubuntuforums.org/showthread.php?t=430669") has a method to install via an ISO mounted from a partition.  Don't know if it works, but it seems sensible.

---

### Post by smdeep on 2007-05-07
Thanks Stephen
Will try it out and see how it goes.

---

### Post by smdeep on 2007-05-12
Hi
I have managed to install via PXE boot. The above link posted by Stephen did not help. There is a vital omission about installing and configuring netkit-inetd to get tftp server going. After spending more than 24 hours on this problem I came across a couple of howtos in the net, among them :
[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

Finally I have Feisty installed on the laptop.

:)

---

