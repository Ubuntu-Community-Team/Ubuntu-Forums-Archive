---
title: "I do not know how to install my drivers"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by badboy1234 on 2008-02-29
Hi,
I have just installed ubuntu 7.10 on my computer and i am new to linux operating systems. I guess i dont have any driver installed on my computer. i have searched for commands that would help. i found a command called 'lspci'. i wrote in the terminal. then here is what came out:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:02.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)
_______________________________________________________________________________
Please guys, give me a detailed way to install them coz i almost know nothing about linux generally and ubuntu especially. Plz answer me as soon as possible. Thanks for ur time.

---

### Post by overdrank on 2008-02-29
> **badboy1234 said:**
> Hi,
I have just installed ubuntu 7.10 on my computer and i am new to linux operating systems. I guess i dont have any driver installed on my computer. i have searched for commands that would help. i found a command called 'lspci'. i wrote in the terminal. then here is what came out:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:02.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)
_______________________________________________________________________________
Please guys, give me a detailed way to install them coz i almost know nothing about linux generally and ubuntu especially. Plz answer me as soon as possible. Thanks for ur time.

HI and what drivers are you trying to install? The graphics driver would be located under system, administration, restricted drivers.

---

### Post by banewman on 2008-02-29
Ubuntu has good support for most hardware - if something isn't working on your system to your satisfaction that is when you need to worry about drivers.
:)

---

### Post by badboy1234 on 2008-02-29
i cant install the network card, nor the graphics card. thanks for ur help

---

### Post by banewman on 2008-02-29
In the menu is a "restricted drivers" entry - click that to install the vid card drivers.
Your network card seems to be a fake realtek card
[http://vishalmanohar.wordpress.com/2007/07/03/trouble-with-fake-lan-card/](http://vishalmanohar.wordpress.com/2007/07/03/trouble-with-fake-lan-card/)
so no support in linux - sorry

---

### Post by dstew on 2008-02-29
If that card works in XP, you can probably get it to work using [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/"). Read the page carefully, and you will see that although ndiswrapper is used mostly for wireless cards, it can work for ethernet LAN cards too. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") is a HowTo. You can install ndiswrapper using synaptic if it is not already installed.

---

### Post by badboy1234 on 2008-02-29
I have tried using the restricted drivers to install my graphics card driver and here's what appeared to me.


Step 1: It told me that the VGA card was not in use and that I have to enable it to be able to use it
Step 2: I made a tick which opened me a window saying "Enable the Driver?" and describing how enabling the driver will help 2 b able 2 use the card in 3D applications such as games.
Step 3: It gave me an error saying :   the software source for the package  nvidia-glx is not enabled.
I really dont know what to do about it.

Regarding the network card, here is what happened when i tried installing the ndiswrapper software:
I opened a terminal and typed the following code but it still didnt work:

mr@mr-desktop:~$ sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb
dpkg: error processing ndiswrapper-common_1.43-1ubuntu2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-common_1.43-1ubuntu2_all.deb


Thus, i need ur help. thank for ur help

---

### Post by oldos2er on 2008-02-29
Go to System, Administration, Software Sources, and make sure all the boxes under 'Ubuntu Software' are checked.

 If you downloaded ndiswrapper to your desktop, you'll need to run "cd Desktop" before installing it.

---

### Post by dstew on 2008-02-29
> Regarding the network card, here is what happened when i tried installing the ndiswrapper software:
I opened a terminal and typed the following code but it still didnt work:

mr@mr-desktop:~$ sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb
dpkg: error processing ndiswrapper-common_1.43-1ubuntu2_all.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
ndiswrapper-common_1.43-1ubuntu2_all.debDid you download the package file first?

---

### Post by badboy1234 on 2008-02-29
what do u mean by 'cd desktop' oldos2er?

---

### Post by oldos2er on 2008-03-01
When you're in the terminal, type "cd Desktop", then try running the command "sudo dpkg -i ndiswrapper-common_1.43-1ubuntu2_all.deb"

---

