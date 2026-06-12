---
title: "Installtion hung up"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by awuwish on 2008-02-06
While installing from DVD boot, the installer goes through all its checks: hardware, etc. It can't find any driver for my graphics card, so I tell it to run in 800x600 and it continues. It then proceeds to a screen where it says 
*Checking battery state...    OK
*Running local boot scripts (etc/rc.local)     OK

then after this there is a blinking cursor and the system does nothing. I'm new to Ubuntu and linux, so I'm probably just missing a command or something, but I have looked all over for this same issue or any support files for installation, but have not found anything. Any help or redirection would be appreciated.

Thanks.

---

### Post by bwtranch on 2008-02-06
It's a driver problem. Gonna have to go into the command line and post some output. Type in lspci and you should get something like this:

jim@jim-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
jim@jim-desktop:~$ 

The video controller is the one of interest. You'll notice that on this machine it is an ATI. This is the place to start.

---

### Post by awuwish on 2008-02-06
Either I'm not at the command line, or the command isn't working; I think its the before, there is just a blank cursor, nothing with ~$ . it just has the battery state, and the local boot scripts line. I think I'm going to make a different disk with the earlier version of ubuntu as I am seeing that there are other people that are having problems with their laptops (Compaq Presario F700 series, which is what I have). Hopefully that will work, if not, I will come back here :)

---

### Post by bwtranch on 2008-02-06
You can boot from the CD and get into recovery mode.

---

### Post by awuwish on 2008-02-06
OK, I did get it to install, or at least run from the DVD. I'm on the desktop in Terminal. lspci gives:

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus:  nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory:  nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor:  nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller:  nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller:  nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller:  nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller:  nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface:  nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00.18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02.05.0 Generic system peripheral [0805]: Richos Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02.05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02.05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02.05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03.00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


and that is the end. I've noticed that there have been multiple problems with this series of laptop and nVidia chipsets, as well as the Atheros WiFi card ( [http://ubuntuforums.org/showthread.php?t=656756&highlight=f700](http://ubuntuforums.org/showthread.php?t=656756&highlight=f700) ) 

Anyway, obviously there is a problem with the chipset, and the wireless card also, seeing as I can't find an internet connection yet. I'll keep searching that thread to see if I can't figure it out, but any other information on either subject would definitely help.

Thanks again.

---

### Post by bwtranch on 2008-02-06
Here's the problem

00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)

Driver. Oh, I hate driver problems. Glad it's yours and not mine:) Sorry. Well, we have to get a driver loaded. How good are you at the CLI? and then you could try envy, but I don't like that very much. The trouble with envy is that it might get it to work, but not that well. Maybe you don't care at this point. If you got it to at least work, then you can look around and find the real fix. or maybe something, I don't know. It's up to you. If you can get your monitor to work outside of a shell, then we have more options. Can you use a command line browser, like links?

---

### Post by awuwish on 2008-02-06
Well like I said, I'm brand new to linux. The closest I've used to any command line systems is MSDOS :(   I have an old Unix book from about 1985 (not sure how different everything is from then to now). I know that when I hit "run in Terminal" it comes up saying "installer must be run as root" ...after that I'm lost. Tell me if I'm more lost than can be helped or point me in the direction of somewhere I can actually learn linux. I have the basic idea of how it works, but after that, its Greek to me. (i do have both the files for the nvidia driver and the driver for my network card though, so its a start :) )

---

### Post by bwtranch on 2008-02-06
Hey, it's OK. I remember those old DOS prompts. I still try to use 'em in bash. Doesn't work most of the time! Ha! Well, you seem like a nice person and I will tell you about Linux.

1. It is based on Unix and that was the OS that was designed by the military for security on what would later be called the internet.

2. Linux/Unix uses a hierachal tree that comes down from root (/) and branches out into different folders.

3. Unlike other OS's , Linux treats all things as folders, even devices such as CD roms, floppys (what are they?), USB devices, etc. All are treated as files. (Weird, I know, but you get used to it)

4. Unlike Windows, files can reside in multiple folders. That is, the same file can be in many places.

5. Going back to 4, you can put your files wherever you want. But there are certain conventions that are adhered to. To wit: / is root, and you can't change that, but, let me open a terminal and that will be easier. (And save me some typing)

Oh, btw, I got Firefox 3.0 today!

jim@jim-desktop:~$ sudo su
[sudo] password for jim:
root@jim-desktop:/home/jim# ls
AFMSC Web Pages  Incomplete                My GCompris             Templates
Desktop          LimeWire Saved            nautilus-debug-log.txt  Videos
Documents        LimeWire Shared           nvidia-bug-report.log
Examples         LimeWire Store Purchased  Pictures
gedit            Music                     Public
root@jim-desktop:/home/jim# cd /
root@jim-desktop:/# ls
backups                              etc             media  sys
bin                                  home            mnt    tmp
boot                                 initrd          opt    usr
cdrom                                initrd.img      proc   var
cupswrapperdcp1000_1.0.2-1_i386.deb  initrd.img.old  root   vmlinuz
cupswrapperDCP1000-1.0.2-1.i386.rpm  lib             sbin   vmlinuz.old
dev                                  lost+found      srv
root@jim-desktop:/# exit
exit
jim@jim-desktop:~$ 

The # means I was root. You don't want to stay there too long. It is also called superuser (i.e. the master) Well, that's about it for now. There is more. You can do everything you want from the command line (CLI) but we love those GUI's don't we?

---

### Post by awuwish on 2008-02-06
Hey thanks for all the help. I know I'm a newbie, but I love to learn all this new stuff. That's really the main reason I wanted to try linux, and maybe get away from windows (ugh) and osx (eh). I'll just keep fiddling around with it and see what I can come up with...I actually got the wireless card drivers to install and i rebooted the computer, but then remembered I had not actually installed linux yet :(   oh well...something else for me to play with. And ya, I know not to use sudo very much if I don't have to...I'll probably mess something up anyway, knowing my luck.

Thanks again!

---

### Post by Partyboi2 on 2008-02-07
Try using the 2nd option at the live cd main menu screen I think its called "install with safe graphics mode" If that does not work you could trywhen you get to this point:
>  *Checking battery state...    OK
*Running local boot scripts (etc/rc.local)     OK press Ctrl+Alt+F2 this should get you to a terminal
then run this command
```
sudo dpkg-reconfigure xserver-xorg
``` and choose nv for the graphics driver and answer all the questions, if unsure then choose the default answers which are displayed on screen.
then type
```
startx
```(If nv does not work then try again with vesa)
If that does not work then I suggest trying the [alternate cd]("http://releases.ubuntu.com/releases/7.10/")
which is a text based installer. Its what worked for me when I was trying to install on a Compaq Presario

---

