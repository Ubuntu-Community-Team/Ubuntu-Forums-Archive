---
title: "Problems with booting (Ubuntu 13.10 on Sony Vaio Pro 13)"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by ChiVampir on 2013-10-23
Hi!
I've been working for two days now without really arriving  anywhere which is starting to get really frustrating. The problem is  that I've just got my Sony Vaio Pro 13 that I hoped to use for my  studies. But unfortunately I can't use it for anything right now as  neither Ubuntu 13.10 or Linux Mint 15 will boot on this machine. 

I've  disabled secure boot and switched to Legacy mode as well as disabled  Intel(R) AT Support System. The whole disk is formated into msdos and  gpt. I've also tried with UEFI and gpt, and all other combinations, but  still get the same result. I've also tried  Installation and running my  live-USB for both distros works like a charm without any problems. The  problems start when the system is restarted, and tries to boot. I've run  boot-repair which makes me able to boot into the operating system very  slowly after minutes of booting. But when I'm starting my system for the  second time after rebooting I run into this screen: [http://i41.tinypic.com/29zr6ua.jpg](http://i41.tinypic.com/29zr6ua.jpg)

I've  also tried to upgrade into kernel 3.12 and still run into the same  problem. I've also tried to try to click [ESC] at the splash screen, but  don't get any information. It is also impossible to go into the command  window. I've tried different USB-drives and don't know how many times  I've tried to reinstall now. 

I've tried to google for more information but can't really find anything useful for my problem.

So now I really really hope that some of you are able to help me!
I'm  not that good at more complex stuff than simple installing and updating  from the command line, so more detailed explanations are really  appreciated :)

---

### Post by ubfan1 on 2013-10-23
I'd suggest searching here and at askubuntu.com for your machine model for specific suggestions.  Just to get some more info so anyone else who sees this has a better starting place:  Are you trying to dual boot Windows 8?  Does your hard disk have a gpt or msdos partition table?  Any special video hardware?  Just a hard disk or also a solid state device?  At boot time, start rapidly typing the  key (ESC? F12?, ...) which offers you the boot options, sometimes the timing is hard to get right.  What choices do you get, (maybe after selecting the hard disk, you get more choices).  Do any work?

---

### Post by ChiVampir on 2013-10-24
Hi and thank you for the answer ubfan1!
I see that I was a little bit too frustrated to explain myself when I posted yesterday. And since I'm not an native English speaker I now see that it is really difficult to decode my message.

The problem is that the computer will rarely boot and will give the message in the picture link above. Sometimes (very rare) however it will boot but uses over 10 min on the process, but when it do it seems to run okey. Running from a live USB runs very smooth however.  

I've now run another fresh install so it should be a bit easier to help me. The only things I have done after this install is to upgrade the kernel, run boot-repair and install updates with:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```


More information about my computer and set-up:

[B]Kernel, os and other
[/B]Distro: Ubuntu 13.10 (found out that this worked best with my wifi device right now)
Kernel: 3.11.0-12-generic
Partition table: msdos
Dualboot with windows: No


**Changes I have done in bios:**
Intel(R) AT Support System	[Disabled]
Secure Boot			[Disabled]
External Device Boot		[Enabled]
Select 1st Boot Priority	[External Device]
Boot Mode			[Legacy] 

**About the hardware from Sony:**
Processor: Intel&#9415; CoreTM i3-4010U, 1.7GHZ
Storage: 256 GB PCIe Flash SSD
Memory: 4 GB 16000 MT/s DDR3L-SDRAM
Graphics: Intel&#9415; HD Graphics 4400
Wireless: Wireless LAN (IEEE 802.11abgn)

But that really dosen't say much so here is the output from lshw -short:
```
H/W path        Device     Class          Description
=====================================================
                           system         SVP1321C5E (54671160)
/0                         bus            VAIO
/0/0                       memory         64KiB BIOS
/0/7                       processor      Intel(R) Core(TM) i3-4010U CPU @ 1.70G
/0/7/8                     memory         128KiB L1 cache
/0/7/9                     memory         512KiB L2 cache
/0/7/a                     memory         3MiB L3 cache
/0/b                       memory         4GiB System Memory
/0/b/0                     memory         2GiB SODIMM DDR3
/0/b/1                     memory         2GiB SODIMM DDR3
/0/100                     bridge         Haswell-ULT DRAM Controller
/0/100/2                   display        Haswell-ULT Integrated Graphics Contro
/0/100/3                   multimedia     Intel Corporation
/0/100/14                  bus            Lynx Point-LP USB xHCI HC
/0/100/16                  communication  Lynx Point-LP HECI #0
/0/100/1b                  multimedia     Lynx Point-LP HD Audio Controller
/0/100/1c                  bridge         Lynx Point-LP PCI Express Root Port 3
/0/100/1c/0     wlan0      network        Wireless 7260
/0/100/1c.3                bridge         Lynx Point-LP PCI Express Root Port 4
/0/100/1c.4                bridge         Lynx Point-LP PCI Express Root Port 6
/0/100/1c.4/0              storage        Samsung Electronics Co Ltd
/0/100/1d                  bus            Lynx Point-LP USB EHCI #1
/0/100/1f                  bridge         Lynx Point-LP LPC Controller
/0/100/1f.3                bus            Lynx Point-LP SMBus Controller
/0/1            scsi0      storage        
/0/1/0.0.0      /dev/sda   disk           256GB SAMSUNG MZHPU256
/0/1/0.0.0/1    /dev/sda1  volume         234GiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2  volume         4002MiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5  volume         4002MiB Linux swap / Solaris partition
```

**And here is my latest boot-repair URL**: [http://paste.ubuntu.com/6293415/](http://paste.ubuntu.com/6293415/)

[B]What I have tried so far:
[/B]
[LIST]
[*]Searched the internett and forums for information about this problem, apperantly there are some problems with the sony vaio pro series, but I could not find anyone strugeling with the same problem as I have, even though I have tried some of the solutions that solved other peoples booting problems with this hardware.
[*]Tried to start the system in recovery mode (hope it's the correct english word, as both my grub and install is in Norwegian), but still end up with the same problems.
[*]Tried to use gpt partision table instead of msdos when installing, installed with enabled uefi and all different combinations of uefi and legacy as well as the the different partision tables msdos and gpt.
[*]Tried to enter the "command window" from boot, and I'm able to enter it but is not allowed to type in anything
[*]Tried to click [esc] when when ubuntu (or linux mint) is trying to boot to try and find some information about what's wrong. The only result is that I end up with a black screen.
[*]Tried to install Linux Mint 15 instead of Ubuntu 13.10, but I still end up with the same booting problems
[LIST]
[*]But found out that this computer's hardware seems to be better supported by Ubuntu 13.10 at the moment
[/LIST]
[/LIST]

Hope this makes a bit more sense than my previous post, and if you need some more information please tell me.

---

### Post by ChiVampir on 2013-10-24
After the reinstall I'm only getting this screen: [IMG]http://i44.tinypic.com/2zsnr51.jpg[/IMG]

---

### Post by ChiVampir on 2013-10-24
Yay! I've managed to fix the problem by myself :D

To fix the problem the kernel have to be edited a bit. To do this press "**e**" when entering grub. 

Boot the slow boot problem and the problem with not booting at all is fixed by this method. 

Then add this to the line starting with** linux**:
```
libata.force=noncq
```
Then press **"F10"** too boot into the operating system

To make this change permanent grub has to be edited:
```
sudo nano /etc/default/grub
```

Then change the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

into:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq"
```

Save and run:
```
update-grub
```

And then problem solved! 

Hope this can help other frustrated people as well :)

---

