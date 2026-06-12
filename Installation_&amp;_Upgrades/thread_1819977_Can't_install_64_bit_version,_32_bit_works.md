---
title: "Can't install 64 bit version, 32 bit works"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by oliwang on 2011-08-07
Hello,

last week I bought a new laptop: Lenovo E320 with a Intel Core i3 2310M CPU, which should support 64 bit. The computer came without an OS, so I downloaded the 64 bit version of Ubuntu 11.04, put it on a thumb drive. Grub displayed 3 options for me "Try Ubuntu without Install", "Install Ubuntu" and "Check disc for errors". After selecting one of these options my screen turns blank, the hard drive spins a bit and then slows down. The only thing I can do now is to power down the laptop.
At first I thought about a issue with my graphic chip, I tried to change the grub parameters according to the sticky in this subforum but nothing worked. (I never came to the Ubuntu screen described in the sticky, but just a simple Grub loader).
Anyhow, after a lot of trying I decided to download the 32bit version and it worked right out of the box.
Well, thats nice and all, but I want to use 100% of my ram, and not around 45%.

I hope I described my problem detailed and comprehensive. Please let me know if you need further details.
Have you got any suggestions for my problem? Should I try to install another distro/Windows 64bit?

Greetings,
oliwang

---

### Post by garvinrick4 on 2011-08-07
Just a bad disk I got to assume i3 will take 64 bit, make a new one and use Try Ubuntu and see if she works before install.

---

### Post by oliwang on 2011-08-07
I tried three different thumb drives, neither of them worked with 64bit. I redownloaded the 64bit iso, md5sum was fine. The thumb drives worked with the 32bit iso.
I dont have a cd rom drive. (I could try with a extern one, but I dont have on with me at the moment)
But that makes no sense to me: Why should it work with a cdrom but not with a thumb drive?

---

### Post by garvinrick4 on 2011-08-07
> But that makes no sense to me: Why should it work with a cdrom but not with a thumb drive?You are right should work with that processor: How much Ram you have 4 gig check into
the 32 bit pae-kernel. Uses more of your Ram. 
Sure does not make sense brand new machine and will not run 64 bit though.
What does this say copy and paste here:
```
lspci -k
```

---

### Post by oliwang on 2011-08-07
Ive got 8GB of Ram (shown in Bios post, so that works.)

>  ow@e320:~$ lspci -k
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 21ee
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 21ee
    Kernel modules: i2c-i801
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
08:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
    Subsystem: Lenovo Device 21ee
    Kernel driver in use: atl1c
    Kernel modules: atl1c> 
ow@e320:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2940        767       2172          0         66        390


---

### Post by dino99 on 2011-08-07
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by goldshirt9 on 2011-08-07
have you tried with a disc and not a usb stick

---

### Post by ~!geek!~ on 2011-08-07
> **oliwang said:**
> Hello,

last week I bought a new laptop: Lenovo E320 with a Intel Core i3 2310M CPU, which should support 64 bit. The computer came without an OS, so I downloaded the 64 bit version of Ubuntu 11.04, put it on a thumb drive. Grub displayed 3 options for me "Try Ubuntu without Install", "Install Ubuntu" and "Check disc for errors". After selecting one of these options my screen turns blank, the hard drive spins a bit and then slows down. The only thing I can do now is to power down the laptop.
At first I thought about a issue with my graphic chip, I tried to change the grub parameters according to the sticky in this subforum but nothing worked. (I never came to the Ubuntu screen described in the sticky, but just a simple Grub loader).
Anyhow, after a lot of trying I decided to download the 32bit version and it worked right out of the box.
Well, thats nice and all, but I want to use 100% of my ram, and not around 45%.

I hope I described my problem detailed and comprehensive. Please let me know if you need further details.
Have you got any suggestions for my problem? Should I try to install another distro/Windows 64bit?

Greetings,
oliwang


Ok, as you mentioned that you tried to burn  64bit ubuntu iso on more than one thumbdrives (The instructions to burn iso on [www.ubuntu.com](www.ubuntu.com) are good enough and I m assuming you followed it). 
You may try to check if the iso has been correctly downloaded by checking the md5sum of the iso using the command: 
> md5sum pathtodirectorywhereyoukeptiso/ubuntu-xx.xx-yyyyyyyyyyyy.iso 
You will get a string (a long string). Match it with the corresponding md5sum available on the website you downloaded from. 
The md5sums are available at the forum link:
[http://mirrors.melbourne.co.uk/ubuntu-releases/11.04/MD5SUMS](http://mirrors.melbourne.co.uk/ubuntu-releases/11.04/MD5SUMS)
If above link don't work for u, try navigating through 
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) -> click locationnear you link and select your version-> md5sums.

---

### Post by ottosykora on 2011-08-07
@oliwang

for me it was opposite, on one of my computers, the 10.10 ubuntu was running perfect in 32bit, but 11.04 refused, did crash all the time.

Reinstalled completely , this time x64 and it works fine.

However: it makes not substantial difference, as when the 32bit install detects that you have x64 system, it will install the kernel with the -pae which should use your ram full

On x64 ubuntu, well all works for me, but there are still some .deb packages around that work on 32bit only, so some drivers etc probably.

But I would say, if your system works with 32bit, leave it and be happy with it, you are not loosing anything.

---

### Post by oliwang on 2011-08-07
> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)


thanks for the info, didn't know that. ill stick with the 32bit version with pae enabled.

btw, I checked the md5sums, they were correct.
anyway, thanks for you efforts!

---

