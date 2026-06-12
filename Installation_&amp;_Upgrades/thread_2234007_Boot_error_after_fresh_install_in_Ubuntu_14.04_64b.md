---
title: "Boot error after fresh install in Ubuntu 14.04 64bit"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by tears of the river on 2014-07-11
I have a lenovo b570e laptop. I just installed Ubuntu 14.04. It is a fresh install that I perform on the laptop when it was in EFI mode. the installation went perfectly fine but then when it restarted I got the error:

```
[COLOR=#000000][FONT=Ubuntu Mono]Intel UNDI, PXE-2.1 (build 083)[/FONT][/COLOR]Copyright (C) 1997-2000 Intel Corporation

This Product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776 and US6,327,625

Realtek PCIe GBE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media test failure, check cable [COLOR=#000000][FONT=Ubuntu Mono]PXE-M0F: Exiting PXE ROM.[/FONT][/COLOR]
```

Any help would be really appreciated.
Thanks in advanced

---

### Post by oldfred on 2014-07-11
That looks like it is trying to do a network boot. 

Check boot device order in UEFI. You should have Ubuntu first in boot order. And network usually as last.

Post this from live installer's terminal to see UEFI boot order. Is Ubuntu installed in UEFI mode?
       sudo efibootmgr -v
    

Now old obsolete version of Ubuntu. I would expect newer to install easier.
 How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

---

### Post by tears of the river on 2014-07-12
> **oldfred said:**
> 
Post this from live installer's terminal to see UEFI boot order. Is Ubuntu installed in UEFI mode?
       sudo efibootmgr -v


I tried it and this is the result:

```
sudo: efibootmgr: command not found
```

To be noted when I installed it the loading screen that came was like such:

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

---

### Post by tears of the river on 2014-07-12
Not sure if this helps but I tried a boot-repair and it gave me an error with the following paste:

[http://paste.ubuntu.com/7784345/](http://paste.ubuntu.com/7784345/)

---

### Post by oldfred on 2014-07-12
Boot-Repair ran it fine:

 BootOrder: 0009,0004,0002,0003,0005,0006,0007,0008
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:
Boot0003* ATA SSD:
Boot0004* ATA HDD: HITACHI HTS547550A9E384
Boot0005* ATAPI CD: SlimtypeDVD A  DS8A5SH
Boot0006* USB HDD:
Boot0007* USB CD:
Boot0008* PCI LAN: Realtek PXE B03 D00
Boot0009* ubuntu,BootCurrent: 0005

Can you not select entry 9 or ubuntu as it should be shown in UEFI menu?

Or are you booting but do not get grub as you only have one install. Then it may be a video issue?

Some Lenovo's need work arounds.


 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

You are not showing a /EFI/Boot/bootx64.efi which I thought was installed by default.
But you can just create a /efi/boot folder and copy grubx64.efi into it.

---

### Post by tears of the river on 2014-07-13
> **oldfred said:**
> 
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)


From this the following worked:
```
[COLOR=#000000][FONT=courier new]mount /dev/sda1 /mnt[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cd /mnt/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cp -rfv ubuntu boot[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]cd boot[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]mv grubx64.efi bootx64.efi[/FONT][/COLOR]
```

Thanks a lot for your helped it was really appreciated

---

