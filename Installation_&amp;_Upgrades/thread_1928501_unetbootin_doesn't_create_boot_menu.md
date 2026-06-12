---
title: "unetbootin doesn't create boot menu?"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by th1 on 2012-02-20
Can't use a cd drive and can't boot from usb..

So, I was trying to install xubuntu using the hdd 'as an usb stick'

I have:
xubuntu-11.10-desktop-i386.iso
unetbootin-windows-568.exe

I run unetbootin select the iso, install, A message in unetbootin says that I should reboot and select unetbootinin the boot menu. I  reboot

My C: drive has a new name: '(C:) Install Xubuntu' and a red cirle as the icon. 

I reboot and XP starts normally, no boot menu... treid F8 but 'windows xp professional' is the only OS option

am I missing something?

c: drive has windows installed. I have a E:\ drive (which is a partition from the main drive, where I wanto to install xubuntu)

my specs are:
1.66 ghz amd
756mb ram
nvidia geforce4 64mb :D


EDIT:

boot.ini, before unebootin:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

[spybotsd]
timeout.old=30

```AFTER:
```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

[spybotsd]
timeout.old=30

C:\ubnldr.mbr="UNetbootin"

```EDIT":

I found this, as it seems everything should be working -_-

> 
**Hard Disk (frugal) install mode**

  On Windows, UNetbootin modifies boot.ini (on 2000/XP), or uses bcdedit  (on Vista/7) to add a boot menu option titled UNetbootin. This loads the  GRUB4DOS bootloader, which is installed at /ubnldr and /ubnldr.mbr, and  this in turn reads boot menu entries from /unetbtin/menu.lst. The  installation .exe file is copied to /unetbtin.exe, and this is added to  autorun upon the next bootup. When run, this will uninstall UNetbootin  by deleting the extracted files (which is recorded using /ubnfilel.txt  and /ubnpathl.txt) and removing the UNetbootin boot menu entry. 



---

