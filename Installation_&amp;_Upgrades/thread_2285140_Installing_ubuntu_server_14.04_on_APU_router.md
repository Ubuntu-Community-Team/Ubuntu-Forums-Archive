---
title: "Installing ubuntu server 14.04 on APU router"
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by michael302 on 2015-07-03
Hi there,

I am trying to install Ubuntu server 14.04 on my APU router but I encounter a weird behavior in which the installation screen is entirely made up by strange characters (see image attached).
I connect to the router via serial tty 115200n8 using a serial to usb connector and screen on a Mac.

Here are my configuration files (I am booting from USB, created with unetbootin):

#)txt.cfg:
default install
label install
  menu label ^Install Ubuntu Server
  kernel /install/vmlinuz
  append  file=/preseed/ubuntu-server.seed \
          vga=788 initrd=/install/initrd.gz -- \
      console=ttyS0,115200n8 quiet &#8211;

#)syslinux.cfg:
# D-I config version 2.0
CONSOLE 0
SERIAL 0 115200 0

default menu.c32
prompt 0
menu title UNetbootin
timeout 100
label unetbootindefault
kernel /install/netboot/ubuntu-installer/amd64/linux
append initrd=/install/netboot/ubuntu-installer/amd64/initrd.gz \
       tasks=standard pkgsel/language-pack-patterns= \
   pkgsel/install-language-support=false vga=788 -- \
   console=ttyS0,115200n8 --

isolinux.cfg:
CONSOLE 0
SERIAL 0 115200 0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0

Any help would be greatly appreciated.

Thanks

---

### Post by tgalati4 on 2015-07-03
Since you turned off language pack support, you have no language set.  I presume that you turned off language support because of limited resources?

---

### Post by michael302 on 2015-07-03
I have also tried with specific language packs selected and without this line but no change.
What would you put syslinux.cfg?
Thx

---

### Post by tgalati4 on 2015-07-03
What is the hardware?

---

### Post by michael302 on 2015-07-04
an apu1d4

---

### Post by tgalati4 on 2015-07-04
The [hardware]("http://www.pcengines.ch/apu1d4.htm") looks decent and should be able to run Ubuntu 14.04 server out of the box.  However, if your serial terminal is using a USB-to-serial adapter (like a PL2303) there are some known bugs that display strange characters.  Boot with TinyCore Linux as described in the flash update instructions.  Use that to troubleshoot.

First, try 9600 baud and describe the behavior.  115K may be too fast.  If 9600 works, then try 38400.

Make sure the Coreboot firmware is the latest (9/8/14).

The vendor provides no software support, but mentions *pfsense*, which implies a BSD flavor of linux.

---

