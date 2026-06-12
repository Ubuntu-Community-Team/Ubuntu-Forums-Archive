---
title: "Installing Ubuntu 12.04 w/ USB issue"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by zhengalanzheng on 2013-09-15
[COLOR=#333333][FONT=UbuntuRegular]Motherboard: ASRock Z77 Extreme4 ATX
 LGA1155 Motherboard Video Card: Sapphire Radeon HD 7970 3GB 
OS: Windows 7 64 bit 
 Hi, I'm a windows user trying to convert to linux. But there were problems when I try to [/FONT][/COLOR][install]("http://askubuntu.com/questions/345718/installing-ubuntu-12-04-w-usb-issue#")[COLOR=#333333][FONT=UbuntuRegular] ubuntu. So I found out that I installed windows 7 from the BIOS way and I know that I have to install it the same way as windows which I have no idea about. So, I created the bootable [/FONT][/COLOR][usb drive]("http://askubuntu.com/questions/345718/installing-ubuntu-12-04-w-usb-issue#")[COLOR=#333333][FONT=UbuntuRegular] as listed in the instructions on the main ubuntu website. I created the bootable usb from the 12.04 [/FONT][/COLOR][desktop]("http://askubuntu.com/questions/345718/installing-ubuntu-12-04-w-usb-issue#")[COLOR=#333333][FONT=UbuntuRegular] amd64 which is the 64 bit version. So, I turned off my computer and turned it back on, pressed f11, and it shows me that I can boot from 4 places. One of them was the USB and one of them said something about the UEFI USB. I tried the UEFI but when I got to the screen where it said install ubuntu, 5 seconds later, it just turned into a black screen for like 10 minutes and just stayed there. Then I tried the USB option, booting from it, it asked me if I wanted to run it or install it. I chose install but after the initializing log, it froze at another initializing log: [/FONT][/COLOR][http://i.imgur.com/iqGHCOJ.jpg](http://i.imgur.com/iqGHCOJ.jpg)[COLOR=#333333][FONT=UbuntuRegular] Any help will be appreciated. Thanks.[/FONT][/COLOR]

---

### Post by sudodus on 2013-09-15
Welcome to the Ubuntu Forums :-)

It is hard to tell for sure, but I think from the information I have, that

- you should *not* run Ubuntu in UEFI mode, since Windows 7 is installed the BIOS way.

- you have an ATI/AMD/Radeon graphics card (from the screenshot)

There are often issues with the graphics drivers, and the first step is to add a boot option. The first boot option to try is ***nomodeset***. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Furthermore, it is always a good idea to check if the download was successful, so that the iso file is correct. Use ***md5sum*** with data from

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by zhengalanzheng on 2013-09-15
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

It is hard to tell for sure, but I think from the information I have, that

- you should *not* run Ubuntu in UEFI mode, since Windows 7 is installed the BIOS way.

- you have an ATI/AMD/Radeon graphics card (from the screenshot)

There are often issues with the graphics drivers, and the first step is to add a boot option. The first boot option to try is ***nomodeset***. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Furthermore, it is always a good idea to check if the download was successful, so that the iso file is correct. Use ***md5sum*** with data from

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I solved the problem by referring to this: [http://ubuntuforums.org/showthread.php?t=2038227](http://ubuntuforums.org/showthread.php?t=2038227)
Thanks for trying to help.

---

