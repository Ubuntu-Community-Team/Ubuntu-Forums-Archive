---
title: "ubuntu 14.04 server install blank screen"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by pkoukoulis-r on 2014-07-22
I'm attempting to install ubuntu 14.04 server on a somewhat dated pc workstation. After selecting the keyboard and country a purple blank screen appears and nothing appears to happen.

Workstation specs:
cpu: dual opteron cpu
ram: 16gb
hard disk: maxtor 350gb x 4
video card: radeon 4850

Could anybody suggest what might be the reason as to the installation appearing to stall?

Thanks
Peter

---

### Post by Bashing-om on 2014-07-22
pkoukoulis-r; Hi ! Welcome to the forum;

Maybe a graphics driver issue:
> 
video card: radeon 4850


AMD no longer supports that card, so you must use the open source driver. If in the 'server' install you have the options to install 3rd party software and install updates during the install, don't .
And try to install with the boot parameter "nomodeset".
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[INDENT][INDENT]hey, it is a thouhgt
[/INDENT][/INDENT]

---

### Post by pkoukoulis-r on 2014-07-22
Hi

thanks for replying. Tried the installation with the "nomodeset" option, but still the same outcome. Just a blank purple screen.
I'm tempted to buy a new video card and see if that makes a difference.
Can anybody else suggest a way around the blank screen?

Thanks
Peter

---

### Post by sudodus on 2014-07-23
Welcome to the Ubuntu Forums :-)

I suppose that you are trying to run Ubuntu Server in text mode.

You should try to modify the file **/etc/default/grub** (uncomment the GRUB_TERMINAL line) to the following

```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

```

and run

```
sudo update-grub
```

But with a blank terminal it is not easy, so at first, modify the target file of **sudo update-grub** from a live drive:

```
sudo mount /dev/sdxy /mnt
``` where x is the drive letter and y is the partition number, so something like **/dev/sda1**

```
sudo nano /mnt/boot/grub/grub.cfg
```

and modify the corresponding entry at the end of the first part of the file "00_header"

```

[COLOR=#ff8c00]if [ x$feature ... ]
...
...
...
fi[/COLOR]
[COLOR=#ff0000]terminal_output gfxterm[/COLOR]
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###
```

In a system Lubuntu 14.04 LTS, where I tested, it was changed to

```

[COLOR=#ff0000]terminal_input console[/COLOR]
[COLOR=#ff0000]terminal_output console
[/COLOR]if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###
```

This will be overwritten, so I suggest that you change **/etc/default/grub** too (if the tweak works).

---

### Post by pkoukoulis-r on 2015-01-08
Hi

I modified file as follows:
ubuntu@ubuntu:~$ pwd
/home/ubuntu
ubuntu@ubuntu:~$ cd /media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/boot/grub
ubuntu@ubuntu:/media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/boot/grub$ sudo vi grub.cfg

The file modifications are as follows:
terminal_input console
terminal_output console
as suggested

further down I also removed the queit splash from the following line:
linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=a5f3a1fe-32a0-434b-992a-ed8966e5c84e ro nomodeset text

I restarted the laptop hoping to see a text install, but I still only see a blank screen with a blinking cursor!

Does anybody know of any place I can go to/call in London for some help, that can deal with these sorts of issues?

The full hardware list is:

Laptop hardware specs:
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3 1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio Device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB Controller: Intel Corporation 8 series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication Controller: Intel Corporation 8 series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 8 series/C220 Series Chipset Family EHCI #2 (rev 05)
00:1b.0 Audio Device: Intel Corporation 8 series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI Bridge: Intel Corporation 8 series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 880M] (rev a1)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
04:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)

---

### Post by sudodus on 2015-01-08
Did you remember also this command

```
sudo nano /mnt/boot/grub/grub.cfg
```

and modify the corresponding entry at the end of the first part of the file "00_header"?

-o-

I hope someone living there can give you a tip about who can help you in London.

---

### Post by MAFoElffen on 2015-01-08
> **sudodus said:**
> Did you remember also this command

```
sudo nano /mnt/boot/grub/grub.cfg
```

and modify the corresponding entry at the end of the first part of the file "00_header"?

-o-

I hope someone living there can give you a tip about who can help you in London.
sudodus and the OP--

Server Edition is VGA mode graphics. It is a low-graphics mode. This problem started when they implemented Kermel Mode Switching (KMS) around Ubuntu Version 11.04, abut the same time I started my sticky here (link in my signature line). If you look on post #2, there are several fixes there that include server edition.

The logic suggested is like hitting that with a 2x4 and will disable some things in server that use the VGA palette. Turning the terminal into a complete text mode does turn off that graphical mode, but that will effect anything that uses the VGA palette, such as aptitude and byobu. Besides, then when even doing a list directory, ls command, the text has no color hinting... that is boring.

Editting the 00_header file is only a temp fix. That file gets replaced in Grub2 updates... then the OP is going to be broke again. I only suggest that is they are having a specific hardware problem where an upstream fix should be on the way (have such a patched header_00 from GNU for lvm and mdadm that has not hit Debain yet). Editting /boot/grub/grub.cfg is even more temp, it gets rebuilt on almost every upgrade...

The basics of my work-around-- 
Do a temp boot in text -- Temporarily edit the grub boot menu and append the line starting with "linux' (the kernel boot line) with the kernel boot option "text"... then boot (link for detailed instructions from post #2 of my sticky).

Once booted, edit /etc/default/grub with favorite text-mode editor. I use VI, but nano is easier for the uninitiated. 
```

sudo nano /etc/default/grub

```
Once into that file, look for this line:
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
Change it to this:
```

GRUB_CMDLINE_LINUX_DEFAULT="radeon.mode=0"

```
Most server iron uses a radeon chipset, as this OP's server is. This turns off KMS for his server. 

Since I like to see what I'm doing, while in that file, before saving and exiting, I change the menu timeout  from 2 to 4 seconds, then uncomment this line
```

#GRUB_GFXMODE=640x480

```
And I change that to 
```

GRUB_GFXMODE=1024x768x16

```
Which also fixes some out-of-range erros fromsome server consoles that don't play well with mode probes...

Save the file and exit.
```

sudo update-grub

```
... to pickup and save those changes to grub and the intrafs image.

That file is persistent and will stay during upgrades and release upgrades. That is a long-term fix.

After over 4000 installs, with about 1/3rd of those of servers, I've only had to use 
```

GRUB_TERMINAL=console

```
...on 6 "old" servers, and that didn't work on those. Timing was between Ubuntu Server 11.10 and 12.04 LTS. I ended up appending that same /etc/default/grub file with 
```

GRUB_GFXPAYLOAD_LINUX=text

```
As the last line, as a temporary fix until I could debug what was going on...

---

