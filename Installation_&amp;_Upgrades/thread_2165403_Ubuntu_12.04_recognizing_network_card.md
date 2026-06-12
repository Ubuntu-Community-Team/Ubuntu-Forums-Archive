---
title: "Ubuntu 12.04 recognizing network card"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by WrERPYT on 2013-08-04
Hello, I have an acer Aspire r7. I installed Ubuntu 12.04 alongside Windows 8, following all the instructions, disabling UEFI, and did it from a USB drive. Now I can get into Ubuntu, but I cannot connect to the internet using wifi. I guess the network card that this laptop uses is not recognized by the operating system. Is there any updates, or any drivers I could download and install within the Ubuntu OS so that it can recognize it? I should be able to download it from Windows though, as my Ubuntu OS cannot connect to the internet. Thank you very much for your help.

---

### Post by thespirit3 on 2013-08-05
If you post details of your wifi device someone may be able to offer advice.

Personally, I'd connect the laptop via a wired ethernet cable and at least then download all updates.

edit: lspci and lsusb from the command line should list the wifi card - amongst all other devices.

---

### Post by WrERPYT on 2013-08-06
Hello, the details are below. I thought of connecting the a wired Ethernet cable, but this acer Aspire R7 does not has an Ethernet port, therefore it is impossible. The only thing I could do is download the required drivers using windows, and then transfer the files to Ubuntu (I can access my windows files from Ubuntu).

[EMAIL="yfkv@YFKV:~$"]yfkv@YFKV:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
03:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

[EMAIL="yfkv@YFKV:~$"]yfkv@YFKV:~$[/EMAIL] lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04ca:2004 Lite-On Technology Corp. 
Bus 001 Device 004: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
Bus 001 Device 005: ID 04f3:005a Elan Microelectronics Corp. 
Bus 001 Device 006: ID 0483:91d1 SGS Thomson Microelectronics

---

### Post by WrERPYT on 2013-08-06
Hello! I need help, my computer has this NC:

Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n

I want to install the required driver so that I can use wireless internet, now, of course I should follow what was previously exposed however... I am using an acer Aspire R7, which does NOT have an Ethernet port to have wired internet. The only option for me would be to download the installation program while using windows 8, store it on C:// and then access it through UBUNTU OS and install it. Can someone help me with that? Thank you.

---

### Post by WrERPYT on 2013-08-06
Good day, 
                   I own an acer Aspire R7, where I installed UBUNTU 12.04 along Windows 8. However, when I use Ubuntu, it does not recognize the network card. I know I need to install a driver (which driver, I do not know). However, there is a further problem. The Aspire R7 does not have an Ethernet port for wired internet, therefore the only option I have is to download the drivers I need through windows 8, and then open it through Ubuntu. Could someone please help me how to do it? Thank you very much. 

Below you have some information you might find useful. 


 yfkv@YFKV:~$ lspci
 00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
 00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
 00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
 00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
 00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
 00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
 00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
 00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
 00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
 00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
 00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
 00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
 00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
 03:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
 04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

 yfkv@YFKV:~$ lsusb
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 003: ID 04ca:2004 Lite-On Technology Corp. 
 Bus 001 Device 004: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
 Bus 001 Device 005: ID 04f3:005a Elan Microelectronics Corp. 
 Bus 001 Device 006: ID 0483:91d1 SGS Thomson Microelectronics

---

### Post by varunendra on 2013-08-07
> **WrERPYT said:**
> 
03:00.0 Network controller: Broadcom Corporation **BCM43228 802.11a/b/g/n**

Please do -
```
apt-get install --print-uris bcmwl-kernel-source
```
The above command may ask you to confirm the download/installation. If so, just answer 'y' > press 'Enter'.

Instead of actually downloading the required package(s), it will return their download URIs at the bottom of the output. You can then use (copy-paste) these URI(s) to download the required packages on a system where internet is working.

Once ALL the packages are downloaded, copy them to a new empty folder on your Ubuntu desktop > cd to it in the terminal > install them with "sudo dpkg -i *".

For example, if you copied ALL the downloaded packages to a new empty folder called "**driver**" on your desktop, then in a terminal, do -
```
cd ~/Desktop/driver
sudo dpkg -i *

```

This will install the "wl" driver which is the only linux driver that your card works with. Let us know if you have any problems understanding or following the above steps or if there are any errors in the process. Hope it goes well and works well for you. :)

---

### Post by bapoumba on 2013-08-07
Threads merged.

---

### Post by WrERPYT on 2013-08-07
Thank you for the help varunendra! This happened when I tried to follow though:

[EMAIL="yfkv@YFKV:~$"]yfkv@YFKV:~$[/EMAIL] apt-get install --print-uris bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source

Did I do something wrong?
Thanks

---

### Post by varunendra on 2013-08-08
You did it right, maybe you also need to enable "restricted" repository in "Software Sources" *(Ubuntu Software Center > Edit > Software Sources)*, or do an update (which would be impossible without a connection).

Anyway, let's try the official method now. First, please try adding the installation CD as software source and make sure that the "restricted" repository is enabled : [https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD)

Then try-
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Make sure the CD has been inserted and detected by the system while doing above, and ignore the errors regarding online repositories that occur during the update.

It will install the packages from the CD. However, if the installation source is a USB device, this won't work so easily and the next easiest way would be to follow the manual installation instructions here (steps 1 to 4, you may skip step 2 regarding installation of "patch" if that package is not available on the CD) : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

Let us know if there are further problems, although I hope there shouldn't be any.

---

