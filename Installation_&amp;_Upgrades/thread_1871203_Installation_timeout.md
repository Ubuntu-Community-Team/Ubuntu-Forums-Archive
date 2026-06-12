---
title: "Installation timeout"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Saphyy on 2011-10-28
So i've been trying all day to get ubuntu on my MSI ge620 dx laptop.

I've tried 32bit as well as 64bit on a pendrive and a dvd.

this seems to be the error i get. I cannot figure out what is wrong myself.

udevd[105]: timeout: killing '/sbin/modprobe -bv pci:v00008086d00000116sv0000146sd0000108Dbc03sc00i00' [209]

screenshot:
[http://imageshack.us/photo/my-images/696/fotofot.jpg/]("http://imageshack.us/photo/my-images/696/fotofot.jpg/")

Please help

---

### Post by deloquencia on 2011-10-28
Did you try any parameters at the boot prompt? With the tab key you can submit some, try around, because it's difficult to determine the exact pci device which blocks. Perhaps, try to install without ACPI or may be in the text mode only.

Here is an overview about different options at boot time: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Stating from the manufacture's datasheet ([http://www.msi.com/product/nb/GE620.html#/?div=Specification](http://www.msi.com/product/nb/GE620.html#/?div=Specification)) you definitively have to go with 64-Bit.

I hope you'll find your way with some boot options, after the installation you can fix this issue.

---

### Post by Saphyy on 2011-10-28
nvm i just got into livecd! i will report back when i have ubuntu installed

---

### Post by deloquencia on 2011-10-28
Great, I'll stay tuned... :)

---

### Post by Saphyy on 2011-10-28
Okay, so i got ubuntu installed. i now have dual boot option with Windows 7. Selecting normal ubuntu doesnt work, using fail safe mode work does work though. What should i do?

---

### Post by Saphyy on 2011-10-29
Im sorry, i meant recovery mode. I've no idea what to do or google. Any hints

---

### Post by lisati on 2011-10-29
> **Saphyy said:**
> Im sorry, i meant recovery mode. I've no idea what to do or google. Any hints

Are you able to get a command prompt and login?

---

### Post by Saphyy on 2011-10-29
> **lisati said:**
> Are you able to get a command prompt and login?

Yes i am indeed.

---

### Post by deloquencia on 2011-10-29
When you get to the login and a prompt, go ahead and check the **syslog** and **kern.log** in /var/log/. Search there for a failed boot process and please forward us this parts of this files. 

dmesg won't do the job - it logs only kernel messages from the last boot - the boot which brought you into recovery mode.

Also you could run **lspci** and **lsusb** just to give us some more information about devices in your system.

When it's the kernel which stops the boot process you'll go with boot options in the short and a new kernel in the long run. When it's some daemon which stops the boot process, you'll tweak it's configuration.
I really hope it'll be that easy...

---

### Post by Saphyy on 2011-10-29
> **deloquencia said:**
> When you get to the login and a prompt, go ahead and check the **syslog** and **kern.log** in /var/log/. Search there for a failed boot process and please forward us this parts of this files. 

dmesg won't do the job - it logs only kernel messages from the last boot - the boot which brought you into recovery mode.

Also you could run **lspci** and **lsusb** just to give us some more information about devices in your system.

When it's the kernel which stops the boot process you'll go with boot options in the short and a new kernel in the long run. When it's some daemon which stops the boot process, you'll tweak it's configuration.
I really hope it'll be that easy...

When looking in both logs im not able to find any information. It's like it stops even before this.

When i run the ubuntu without recovery mode it gets purple for 15 secs and then black and that's it.


lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 5986:0262 Acer, Inc 

```

lspci:
```
mikkel@WoodenPC:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 124d (rev a1)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)

```

I hope you can help me!

---

### Post by deloquencia on 2011-10-29
> When i run the ubuntu without recovery mode it gets purple for 15 secs and then black and that's it.

This sounds like a problem with your video card. From the output of lspci you've got two video cards, one Intel onBoard and one nVidia. 

How do you switch between them? In the BIOS, perhaps? When you're able to switch via BIOS, switch to the onBoard one. When you're not able to switch like that, crawl down and remove the nVidia card from the slot and then boot.

After booting a regular system you can prepare for using the nVidia card.

I hope this helps you a little bit, but I confess I don't know too much about this new graphic cards of ATI/AMD and nVidia and how do you configure them in Ubuntu. But I'm sure folks in here know how to do it.

Good luck :)

---

### Post by Saphyy on 2011-10-29
> **deloquencia said:**
> This sounds like a problem with your video card. From the output of lspci you've got two video cards, one Intel onBoard and one nVidia. 

How do you switch between them? In the BIOS, perhaps? When you're able to switch via BIOS, switch to the onBoard one. When you're not able to switch like that, crawl down and remove the nVidia card from the slot and then boot.

After booting a regular system you can prepare for using the nVidia card.

I hope this helps you a little bit, but I confess I don't know too much about this new graphic cards of ATI/AMD and nVidia and how do you configure them in Ubuntu. But I'm sure folks in here know how to do it.

Good luck :)

i cant switch in the bios :/ Do you want me to plug out the external nvidia card or? How will this resolve the problem?

---

### Post by deloquencia on 2011-10-29
It won't solve it, but we'll get to know what the problem is. At the moment it's only a hunch...

---

### Post by MadeR on 2011-12-17
> **Saphyy said:**
> So i've been trying all day to get ubuntu on my MSI ge620 dx laptop.

I've tried 32bit as well as 64bit on a pendrive and a dvd.

this seems to be the error i get. I cannot figure out what is wrong myself.

udevd[105]: timeout: killing '/sbin/modprobe -bv pci:v00008086d00000116sv0000146sd0000108Dbc03sc00i00' [209]

screenshot:
[http://imageshack.us/photo/my-images/696/fotofot.jpg/](http://imageshack.us/photo/my-images/696/fotofot.jpg/)

Please help


I solved the same problem.
At boot, when ubuntu lets you set some options, press F6 and disable the "modesetting" option.

---

### Post by DevonHartigan on 2012-02-21
> **Saphyy said:**
> So i've been trying all day to get ubuntu on my MSI ge620 dx laptop.

I've tried 32bit as well as 64bit on a pendrive and a dvd.

this seems to be the error i get. I cannot figure out what is wrong myself.

udevd[105]: timeout: killing '/sbin/modprobe -bv pci:v00008086d00000116sv0000146sd0000108Dbc03sc00i00' [209]

screenshot:
[http://imageshack.us/photo/my-images/696/fotofot.jpg/](http://imageshack.us/photo/my-images/696/fotofot.jpg/)

Please help

I had the EXACT same problem...

> **MadeR said:**
> I solved the same problem.
At boot, when ubuntu lets you set some options, press F6 and disable the "modesetting" option.

This solved it for me too (i.e. I was able to get to the install guide), but I'm going to be a bit more precise. When you press F6, you move down to select the "**nomodeset**" and not modesetting (nitpicking I know, but for novice user, every bit of help is sometimes needed), and press enter so a little "X" appears to the left (yes this guide is for dummies).

Btw I have a notebook MSI GE620 DX too (this is both for info and search engines so other users can't find the same problem easier).

---

### Post by rollingthunderb on 2012-04-24
Thank you so much!!! This worked for my attempts at installing Lubuntu 11.10 and I will shortly try Kubuntu before Ubuntu 12.4 comes out. I'm Soooo thankful!!! I was about to remove sata cables from other drives to isolate as my 790i Ultra SLI has 4 drives in it. Windows is on sda and nothing would install in sdb. The setting you described got me back into the install since I have 2 Nvidia 550 Ti cards and it is working. Awesome.

Kubuntu loaded. had to use the grub edit as well. All worked. I'm so excited. Thanks again.

B

---

