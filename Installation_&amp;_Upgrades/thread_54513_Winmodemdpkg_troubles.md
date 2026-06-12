---
title: "Winmodem/dpkg troubles"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by noobiedoo on 2005-08-04
I installed Ubuntu on an old drive on my 386 Dell that has an internal winmodem.  I found the chipset and downloaded the appropriate package hcfpcimodem_1.06full_k2.6.10_5_386_ubuntu_i386.deb.zip onto a jumpdrive.  Now what?  I don't know how to install it.  When I dpkg -i in terminal, I get "requested operation requires superuser privelege".  

Do I unzip the file, then dpkg?  Will I have to specify a directory at some point?  If so, which one?

---

### Post by evilghost on 2005-08-04
unzip *.zip
sudo dpkg -i *.deb

---

### Post by noobiedoo on 2005-08-06
Package installed:

Current parameters: ("hcfpciconfig --info")

Config for modem unit 0: /dev/ttySHCF0
        Device instance: 0-PCI-14f1:1066-122d:4033
        HW revision    : DP Part '73' Rev 'BA' Asic ID 0x95
        HW profile name: hcfpciv92smart
        Registration ID: 210B-10D2-1259
        License owner  : [email]bcleer@myexcel.com[/email]
        License key    : FREE
        License status : FREE (max 14.4kbps data only)
        Current region : USA (T.35 code: 00B5)

The /dev/modem alias (symlink) points to ttySHCF0

To enable full 56K modem and FAX functionality, enter your license information
with "hcfpciconfig --license".

License owner and key data must EXACTLY match the information respectively
provided to and by Linuxant. Otherwise, license status will remain "FREE"!

Now what?  If I do pon, I get nothing.

If I do sudo wvdial, I get:

sudo: unable to lookup  via gethostbyname()
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.


I have done a pppconfig.

Do I need to config wvdial?  If so, what is the command?

Thanks for the help.

---

### Post by noobiedoo on 2005-08-07
I've tried many things to connect, yet something is missing.  Ubuntu is not very user friendly when it comes to connecting via modem or getting help.

I may have to try a different distro.  Any recommendations?

---

