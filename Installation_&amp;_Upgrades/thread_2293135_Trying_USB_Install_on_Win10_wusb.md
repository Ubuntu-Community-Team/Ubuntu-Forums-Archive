---
title: "Trying USB Install on Win10 w/usb"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by chris411 on 2015-09-02
I just purchased a small Asus "laptop" with a 20gb SSD, with the express purpose of deleting the OS (windows 10) and installing Ubuntu (my wife likes it, since she'll be using this as well).  So, I have a 32gb usb flash, install unetbootin, with the most recent distro of ubuntu lts, 64bit as this laptop has 2gb of ram.  For the life of me I cannot get it to boot from the usb stick.  This is such a small comp that it has no dvd drive.  It does have the ability to boot from usb.  The usb is formatted as FAT32 as per unetbootin so, any help would be much appreciated.  The laptop is a 32bit system as well.
```
OS Name:                   Microsoft Windows 10 Home
OS Version:                10.0.10240 N/A Build 10240
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
OS Build Type:             Multiprocessor Free
Registered Owner: [EMAIL="cjausmc@gmail.com"]{edited out}[/EMAIL]
Registered Organization:
Product ID:                00326-10000-00000-AA181
Original Install Date:     9/2/2015, 7:39:35 PM
System Boot Time:          9/2/2015, 10:17:11 PM
System Manufacturer:       ASUSTeK COMPUTER INC.
System Model:              X205TA
System Type:               X86-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: x64 Family 6 Model 55 Stepping 8 GenuineIntel ~
1329 Mhz
BIOS Version:              American Megatrends Inc. X205TA.208, 12/18/2014
Windows Directory:         C:\WINDOWS
System Directory:          C:\WINDOWS\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC-05:00) Eastern Time (US & Canada)
Total Physical Memory:     1,983 MB
Available Physical Memory: 981 MB
Virtual Memory: Max Size:  3,135 MB
Virtual Memory: Available: 1,631 MB
Virtual Memory: In Use:    1,504 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              \\MicrosoftAccount
Hotfix(s):                 2 Hotfix(s) Installed.
                           [01]: KB3081440
                           [02]: KB3081448
Network Card(s):           2 NIC(s) Installed.
                           [01]: Broadcom 802.11abgn Wireless SDIO Adapter
                                 Connection Name: Wi-Fi
                                 DHCP Enabled:    Yes
                                 DHCP Server:     10.0.0.1
                                 IP address(es)
                                 [01]: 10.0.0.22
                                 [02]: fe80::599f:681c:1d2a:ad61
                                 [03]: 2601:180:8100:ef1:93:1c:bf9b:edad
                                 [04]: 2601:180:8100:ef1:599f:681c:1d2a:ad61
                                 [05]: 2601:180:8100:ef1::6290
                           [02]: Bluetooth Device (Personal Area Network)
                                 Connection Name: Bluetooth Network Connection
                                 Status:          Media disconnected
Hyper-V Requirements:      VM Monitor Mode Extensions: Yes
                           Virtualization Enabled In Firmware: Yes
                           Second Level Address Translation: Yes
                           Data Execution Prevention Available: Yes


C:\WINDOWS\system32>
```

---

### Post by oldfred on 2015-09-02
Please use code tags on long text. Easy to add with # in Forum's advanced Editor.
Removed email, forum is regularly scanned, and you would get spammed.

Your 32 bit UEFI makes for a more difficult install as that is not really standard, but recently Linux & Ubuntu were updated to include it. It is a system designed to prevent Linux, by crippling the boot loader as Linux only have 64 bit version. But then Linux went and modified boot to work with 32 bit UEFi.
Many threads on same model system.

Google search: site:ubuntuforums.org X205TA

Mega-thread here:
 Asus X205TA hardware support in Ubuntu

[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)

Some details:
[http://ubuntuforums.org/showthread.php?t=2254322&page=7&p=13261807#post13261807](http://ubuntuforums.org/showthread.php?t=2254322&page=7&p=13261807#post13261807)

---

