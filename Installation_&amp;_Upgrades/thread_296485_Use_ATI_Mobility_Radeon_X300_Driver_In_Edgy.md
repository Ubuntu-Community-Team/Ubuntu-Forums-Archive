---
title: "Use ATI Mobility Radeon X300 Driver In Edgy"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by macsmister on 2006-11-09
Wow this is my first post in Ubuntu forums. After trying anything I could to enable the ATI driver for my ATI Mobility Radeon X300 I thought I might post a message here and see if someone could help a lost cause :D 

The latest ATI drivers are installed on the system. I followed the instructions given in [THIS WIKI]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

Upon reboot, when I type **fglrxinfo** in the terminal I get:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Here is the output of **dmesg | grep fglrx**:
> [17179596.136000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179596.140000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179596.140000] [fglrx] module loaded - fglrx 8.30.3 [Oct 26 2006] on minor 0
[17179609.536000] [fglrx] total      GART = 134217728
[17179609.536000] [fglrx] free       GART = 118226944
[17179609.536000] [fglrx] max single GART = 118226944
[17179609.536000] [fglrx] total      LFB  = 61730816
[17179609.536000] [fglrx] free       LFB  = 52293632
[17179609.536000] [fglrx] max single LFB  = 52293632
[17179609.536000] [fglrx] total      Inv  = 0
[17179609.536000] [fglrx] free       Inv  = 0
[17179609.536000] [fglrx] max single Inv  = 0
[17179609.536000] [fglrx] total      TIM  = 0

Also I noticed when I boot up my laptop it shows something strange in the post. I don't know if it could have anything to do with me not being able to enable to ATI driver. Here it is:
>     Booting 'Ubuntu, kernel 2.6.17-10-386'
root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=55e6afd4-751f-4aeb-86fc-f36637d2f
beb ro quiet splash
  [linux-bzImage, setup=0x1c00, size=0x17e851]
initrd /boot/initrd.img-2.6.17-10-386
  [Linux-initrd @ 0x1f976000, 0x67934e bytes]
savedefault
boot
[17179574.340000] PCI: Cannot allocate resource region 7 of the bridge 0000:00:1c.1
[17179574.340000] PCI: Cannot allocate resource region 8 of the bridge 0000:00:1c.1
[17179574.340000] PCI: Cannot allocate resource region 9 of the bridge 0000:00:1c.1
Ubuntu 6.10 TNLAPTOP tty1

Any clue why I can't enable ATI drivers for my card which I know is compatible? Any help would be apreciated! I would just love to be able to install Compiz/XGL on my machine :)

---

