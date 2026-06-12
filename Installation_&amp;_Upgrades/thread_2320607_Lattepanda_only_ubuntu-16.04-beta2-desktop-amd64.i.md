---
title: "Lattepanda only ubuntu-16.04-beta2-desktop-amd64.iso live works on it"
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2016-04-15
Can boot though the USB 3.0 ubuntu-16.04-beta2-desktop-amd64.iso try or live and then go to install it say reboot and it just stays there with the Ubuntu logo and the dots going right over and over. If I reset or pull the power it starts to boot from the eMMC it install on. But never gets to the desktop.

It's something the live works good on it but can't install it.

Other Ubuntu before 16.04 will not even run the live on it.

The Ubuntu 16.04 bata2 of the server will not load on it. It locks up when it list language.

I guess because it's still in beta2 is why it don't install on this Lattepanda.

It came with windows 10 and worked on there good. I DD backed it up with the Ubuntu 16.04 live.

Any one know what could do to install this on it's eMMC?

-Raymond Day

---

### Post by mörgæs on 2016-04-16
Have you tried Lubuntu 16.04?
Better to use the daily build than beta 2, though I don't think the difference is big.

---

### Post by Bucky Ball on 2016-04-16
*Thread moved to **Installation & Upgrades**.*

Yep. I'd go for Lubuntu or Xubuntu. Both do a -core version which is even lighter. Unsure you will get a full Ubuntu 16.04 LTS running on that, but curious.

---

### Post by Raymond Day on 2016-04-16
Tested both Lubuntu and Xubuntu loading the try they start but lockup after about 10 sec.

The only one that works is the live of **ubuntu-16.04-beta2-desktop-amd64** But it don't work for installing it.

-Raymond Day

---

### Post by grahammechanical on 2016-04-16
I do not understand why the Ubuntu live session loads but the Xubuntu & Lubuntu live sessions do not load as all Ubuntu flavours use the same software for running a live session and for installing the distribution.

I do wonder about the graphic adapter on this device. I see no reference to it on various web sites other than it is an integrated GPU. So, I think this is an issue of video drivers with a Windows driver being provided but there not being a Linux driver for this particular GPU.

And yet you say that the Ubuntu live session loads. Well, the Ubuntu live session uses an open source video driver. But when we install and tick the box "Install third party software" the installer will install some third party audio & video codecs and also a proprietary video driver. Or, in your case, attempt to install a proprietary video driver. But one might not be available.

I suggest that you try installing again and this time do not tick the box "Install third party software." That is, if you did in fact tick that box in your attempts to install.

Regards.

---

### Post by Bucky Ball on 2016-04-16
As above. Don't tick third-party drivers, don't tick 'Update during install' or whatever that one's called. Do that once you're installed.

---

### Post by Raymond Day on 2016-04-16
I did try it with checking the "install third party software" and with out. I guess did it in other ways 10 times.

Installed Webmin on it and seen it has the same CPU as the new Intel compute stick that has a USB 3.0 port too. But I think can't install Linux with the USB 3.0 port have to use the USB 2.0 port on the stick. But USB 3.0 install works on this Lattepanda. Webmin shows the CPU like this on both systems: **Intel(R) Atom(TM) x5-Z8300 CPU @ 1.44GHz, 4 cores**

I think it my have something to do with how they have the power on this Lattepanda. This Xenial Desktop still can't power off. If I say reboot it turns the screen black in like a sec. Then just locks up. I have to press reset or pull the power.

On thing with the power on this. The CPU has a red LED and it's the 1st that lights when plugging power in. Have to wait for that and then the power LED lights and the CPU one goes off and stays off. Then can press the power to turn it on.

So it my be the power or the display.

I am just using it as a server. But I guess the server code don't know how to install the boot on EFI type.

Have not tested the Xenial server. Maybe it would work.

Here is some info on both of them on the command line:

Intel compute stick:

system         Computer
/0                                            bus            Motherboard
/0/0                                          memory         1930MiB System memory
/0/1                                          processor      Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz
/0/100                                        bridge         Intel Corporation
/0/100/2                                      display        Intel Corporation
/0/100/14                                     bus            Intel Corporation
/0/100/14/0                  usb2             bus            xHCI Host Controller
/0/100/14/0/1                                 bus            USB3.0 Hub
/0/100/14/0/1/2                               bus            USB3.0 Hub

lshw -short on the Lattepanda:

root@Lattepanda:~# lshw -short
H/W path         Device           Class          Description
============================================================
                                  system         Computer
/0                                bus            Motherboard
/0/0                              memory         3876MiB System memory
/0/1                              processor      Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz
/0/100                            bridge         Intel Corporation
/0/100/2                          display        Intel Corporation
/0/100/3                          multimedia     Intel Corporation
/0/100/b                          generic        Intel Corporation
/0/100/14                         bus            Intel Corporation
/0/100/14/0      usb2             bus            xHCI Host Controller
/0/100/14/1      usb1             bus            xHCI Host Controller
/0/100/14/1/3                     bus            USB2.0 Hub
/0/100/14/1/3/1                   communication  Arduino Leonardo
/0/100/14/1/3/3                   input          USB Receiver
/0/100/14/1/4                     generic        USB 10/100 LAN
/0/100/1a                         generic        Intel Corporation
/0/100/1f                         bridge         Intel Corporation
/1               enx00e04c36408f  network        Ethernet interface
root@Lattepanda:~#

---

