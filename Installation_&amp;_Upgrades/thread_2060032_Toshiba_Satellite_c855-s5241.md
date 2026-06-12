---
title: "Toshiba Satellite c855-s5241"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by OneirictheOcelot on 2012-09-19
When I try to install this the install usually detects the wired connection on other computers but this particular computer it doesn't detect the wired connection or the wireless.

So I was wondering is it a compatibility problem, driver problem or a setting preventing net access to download updates?

---

### Post by youngunix on 2012-09-19
10hrs since you posted and no1 replied cuz your question is hard to understand (at least for me). Can you give detailed explanation of the issue and what it is exactly you are trying to accomplish.

---

### Post by Old_Grey_Wolf on 2012-09-19
Are you saying that when you try to install Ubuntu on a Toshiba Satellite C855-S5241, 15.6" Laptop with Intel Pentium B970 Processor, 4GB DDR3, 500GB HDD, it doesn't detect the wired network?

What version/release of Ubuntu are you installing?

---

### Post by uRock on 2012-09-19
Hello and welcome to the forums,

What exactly are you trying to install? [s]If you are trying to install ubuntu 12.10, then let me know and I will move the thread to the proper sub-forum. Ubuntu 12.10 is not due to release until later next month.[/s]

Please create thread with a purposeful title, which will be more likely to gt the proper attention.

---

### Post by Old_Grey_Wolf on 2012-09-19
> **uRock said:**
> ...What exactly are you trying to install? If you are trying to install ubuntu 12.10, then let me know and I will move the thread to the proper sub-forum. ...

Three responses in 20 minutes all basically asking the same question.

From the user name I am guessing they are installing 11.10; however, I don't know for sure or what DE specific version they are using.

---

### Post by youngunix on 2012-09-19
> **Old_Gray_Wolf said:**
> Are you saying that when you try to install Ubuntu on a Toshiba Satellite C855-S5241, 15.6" Laptop with Intel Pentium B970 Processor, 4GB DDR3, 500GB HDD, it doesn't detect the wired network?

What version/release of Ubuntu are you installing?

You forgot to list the rest of the information on the back label of the laptop, such as: Serial#, US, IC, SCT, etc...

:guitar:

---

### Post by Old_Grey_Wolf on 2012-09-20
> **youngunix said:**
> [QUOTE=Old_Gray_Wolf;12249086]Are you saying that when you try to install Ubuntu on a Toshiba Satellite C855-S5241, 15.6" Laptop with Intel Pentium B970 Processor, 4GB DDR3, 500GB HDD, it doesn't detect the wired network?

What version/release of Ubuntu are you installing?
You forgot to list the rest of the information on the back label of the laptop, such as: Serial#, US, IC, SCT, etc...

:guitar:[/QUOTE]

I think you meant that post for someone other than me. :)

However, in response:
[INDENT]The model, part number, and serial number are usually listed on the laptop label. I have looked at the laptops on my desk, and that is all they have on the label except for the Dell laptops with an express service code.[/INDENT]

---

### Post by OneirictheOcelot on 2012-09-22
It's a Toshiba Satilite of that model number and it doesn't detect the network on ubuntu 12.04 when I try to install.

---

### Post by uRock on 2012-09-22
> **OneirictheOcelot said:**
> It's a Toshiba Satilite of that model number and it doesn't detect the network on ubuntu 12.04 when I try to install.

can you type ```
lspci
``` in a terminal, then copy and paste the output here?

---

### Post by OneirictheOcelot on 2012-09-23
> **uRock said:**
> can you type ```
lspci
``` in a terminal, then copy and paste the output here?


ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) 
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) 
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) 
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) 
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04) 
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10) 
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev ff) 
ubuntu@ubuntu:~$

---

### Post by amboxer21 on 2012-09-23
Nvm

---

### Post by uRock on 2012-09-23
The fellow in the thread seems to have gotten his identical networking hardware working by following this advice, [http://ubuntuforums.org/showpost.php?p=12206899&postcount=6](http://ubuntuforums.org/showpost.php?p=12206899&postcount=6)

> **chili555 said:**
> That's too bad. Installing the driver alx will be challenging without it. If you can download the packages to your Windows partition and then transfer them on a USB key, CD or similar, then we can get the job done. First, let's get build-essential: [http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential) 

Download the package as appropriate to your architecture; either i386 (32-bit) or amd64 (64-bit). Find out which you have with this command:```
arch
```32-bit will report as i686 and 64-bit as x86_64.

The red dots indicate that the package build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev and make. Download those packages also.

Now for linux-headers: [http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=linux-headers-generic&searchon=names&suite=precise&section=all)  As you can see, you can download linux-headers-generic or linux-headers-generic-pae. Find out which you need with:```
uname -r
```This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' or generic-pae' package, you'll also need linux-headers for your kernel. For example, if the uname -r command shows that you are running *3.2.0-23-generic*, you will need linux-headers-*3.2.0-23-generic. *

Once you have all these on a USB key or CD, drag and drop these on to the desktop of your Ubuntu installation. Open a terminal and do:```
cd Desktop
sudo dpkg -i *.deb
```The wildcard * means to install every .deb package on your desktop. We hope there are no missing dependencies, but if so, go here, download and install them, too: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Now for compat-wireless. Download this package and transfer it to your Ubuntu desktop. [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2)

Then install it:```
cd Desktop
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Post back any errors or problems; I'll be glad to help.

We are many timezones apart, so I will look for your post early tomorrow morning.

---

