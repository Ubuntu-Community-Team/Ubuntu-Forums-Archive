---
title: "Problems with Network Install"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by scot524 on 2007-02-09
Unfortunately, I have a PC with a dead CD-ROM. I am having trouble installing Edgy with PXE (netboot). 

I have configured the dhcp server and tftp and everything works fine. The installation candidate PC gets the PXE environment and I am able to start the installation fine. I get all the way past partitioning the disk, etc. 

However, after some progress is made installing the base system, the dreaded red screen appears. The procedure is unable to install 'linux-image-generic'. (Unable to install the selected kernel). 

Log messages are written to virtual console 4. On virtual console 4, an unmet dependency is reported. linux-image-generic depends on linux-image-2.6.17.11-generic but it is not installable. I have noticed that most of the packages installed prior to this one are related to the 2.6.17.10 kernel. 

The kernel version of my dhcp server is 2.16.17.10. My get feel is that something is borked with the repositories. But I am unsure of what to do next. 

Thanks in advance.

---

### Post by reiki on 2007-02-09
Your gut feeling is correct. There is an issue with the kernel images in the repositories. Should be fixed shortly (they are pretty good about this stuff).

---

### Post by scot524 on 2007-02-09
Yep, must admit after sending this post, I see all kinds of yak about borked repositories.  Hopefully, they will fix shortly. I am installing six ubuntus this weekend.

---

