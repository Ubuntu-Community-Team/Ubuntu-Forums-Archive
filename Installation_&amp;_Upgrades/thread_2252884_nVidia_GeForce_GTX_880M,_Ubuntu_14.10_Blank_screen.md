---
title: "nVidia GeForce GTX 880M, Ubuntu 14.10: Blank screen with blinking cursor"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by pkoukoulis-r on 2014-11-15
Hi 

I attempted to install 14.10 on a new laptop with the following spec:
CPU: Intel i7  4810MQ
Graphis: nVidia GeForce GTX 880M
Samsung SSD 84 500GB

The installation runs fine from my live USB stick. I got the folowing error:* "gfxboot,c32: not a COM32R image*" however, but after entering TAB and then typing in "live" ubuntu started fine.

I then started "install ubuntu", which took about 15 minutes and seem to run without any problems.
It then came to the restart, at which point I took the USB stick out, after hitting restart.

The screen appears as blank, with just a blinking cursor showing. 
Could anyone suggest any keystrokes I could press and what to do?
Any help would be much appreciated!


Peter

---

### Post by sudodus on 2014-11-15
I think you have problems with the nvidia graphics. Try with the boot option ***nomodeset*** (and maybe also other boot options, you can have more than one at the same time). See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then, with the help of nomodeset, I think you have a system running that can install a proprietary driver for nvidia.

---

### Post by pkoukoulis-r on 2014-11-27
Hi

I cannot get the F6 set of options to appear with the 14.10 install. So I've reverted to trying to install 14.04 64 bit.
The same outcome occurs however, which is a blinking cursor on a blank screen, even though "**nomodeset**" was selected.

The initial install for 14.04 was successful as was the case for 14.10, but the blinking cursor appears once the restart has happened.

Does anyone have any other ideas?
Any help would be appreciated.

Thanks
Peter

---

### Post by sudodus on 2014-11-28
Try with the boot option **text** in the installed system's file** /etc/default/grub**

```
sudo nano /etc/default/grub
```

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

This  line imports any entries to the end of the 'linux' line (GRUB legacy's  "kernel" line). The entries are appended to the end of the normal mode  only. To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


Enter it after **quiet splash**, or even better, remove quiet splash and use the boot option **text** instead.

according to the description in this link

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

after that you must run

sudo update-grub

to make the change active, and then reboot.

Alternative:

It is also possible to enter the boot option text (or any other boot option) temporarily by pressing [SIZE=3]**e**[/SIZE] at the grub menu and edit the 'linux line' containing quite splash.

-o-

Then, if the computer boots into text mode, you should be able to install nvidia graphics drivers. Type

```
sudo apt-get install nvidia-TAB
```

TAB means that you press the TAB key (not that you type the three letters TAB). You should get a list of available nvidia drivers. Then make the command complete by adding the missing characters and press enter to start the command. Reboot after the installation has finished. If still no go, remove that driver and install another one.

I use nvidia-304 for my nvidia GeForce GT 430 card.

```
sudo apt-get install nvidia-304
```

Try the available drivers - let us hope that you find one driver, that works well for you, [s]probably[/s] maybe another one than what works for me.

---

### Post by pkoukoulis-r on 2015-01-04
Hi

I started the laptop with a USB stick. I used the "Startup Disk Creator" to install Ubuntu desktop 14.10 64 bit. 

The grub file on the SSD is at the following location: 
[FONT=courier new]ubuntu@ubuntu:/media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/etc/default$[/FONT]

 I modified the "grub" file to the following

[FONT=courier new]GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX="text"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
[/FONT]

I used "sudo vi grub" to modify the file and then :wq! to save the changes.

I then ran sudo update-grub as you suggested, but get the following error:
[FONT=courier new]ubuntu@ubuntu:/media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/etc/default$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

[FONT=arial]Not sure what to do next? Any ideas anyone?

Peter
[/FONT][/FONT]

---

### Post by sudodus on 2015-01-04
You are running ***update-grub*** in the live system (which does not work).

Either do it when running the installed system, or do the corresponding edits of

```
/media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/boot/grub/grub.cfg
```

Add **text** to the 'linux lines' after **quiet splash** ---> 

```
... quiet splash **text**
```

(save it and reboot into text mode)

This is actually what update-grub would do (carry the modifications from **etc/default/grub** to **boot/grub/grub.cfg**)

---

### Post by pkoukoulis-r on 2015-01-08
[COLOR=#000000]Hi[/COLOR]

[COLOR=#000000]I modified file as follows:[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ pwd[/COLOR]
[COLOR=#000000]/home/ubuntu[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ cd /media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/boot/grub[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:/media/ubuntu/a5f3a1fe-32a0-434b-992a-ed8966e5c84e/boot/grub$ sudo vi grub.cfg[/COLOR]

[COLOR=#000000]linux /boot/vmlinuz-3.16.0-23-generic root=UUID=a5f3a1fe-32a0-434b-992a-ed8966e5c84e ro nomodeset text
[/COLOR]Found the text in two places so I modified both.

[COLOR=#000000]I restarted the laptop hoping to see a text install, but I still only see a blank screen with a blinking cursor![/COLOR]

[COLOR=#000000]Does anybody know of any place I can go to/call in London for some help, that can deal with these sorts of issues?[/COLOR]

[COLOR=#000000]The full hardware list is:[/COLOR]

[COLOR=#000000]Laptop hardware specs:[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ lspci[/COLOR]
[COLOR=#000000]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)[/COLOR]
[COLOR=#000000]00:01.0 PCI bridge: Intel Corporation Xeon E3 1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)[/COLOR]
[COLOR=#000000]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)[/COLOR]
[COLOR=#000000]00:03.0 Audio Device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)[/COLOR]
[COLOR=#000000]00:14.0 USB Controller: Intel Corporation 8 series/C220 Series Chipset Family USB xHCI (rev 05)[/COLOR]
[COLOR=#000000]00:16.0 Communication Controller: Intel Corporation 8 series/C220 Series Chipset Family MEI Controller #1 (rev 04)[/COLOR]
[COLOR=#000000]00:1a.0 USB Controller: Intel Corporation 8 series/C220 Series Chipset Family EHCI #2 (rev 05)[/COLOR]
[COLOR=#000000]00:1b.0 Audio Device: Intel Corporation 8 series/C220 Series Chipset High Definition Audio Controller (rev 05)[/COLOR]
[COLOR=#000000]00:1c.0 PCI Bridge: Intel Corporation 8 series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)[/COLOR]
[COLOR=#000000]00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)[/COLOR]
[COLOR=#000000]00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)[/COLOR]
[COLOR=#000000]00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)[/COLOR]
[COLOR=#000000]00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)[/COLOR]
[COLOR=#000000]00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 05)[/COLOR]
[COLOR=#000000]00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)[/COLOR]
[COLOR=#000000]01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 880M] (rev a1)[/COLOR]
[COLOR=#000000]03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)[/COLOR]
[COLOR=#000000]03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)[/COLOR]
[COLOR=#000000]04:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)[/COLOR]

---

