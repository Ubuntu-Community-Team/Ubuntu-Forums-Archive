---
title: "Ubuntu 22.04 Live USB not Connecting to Wifi"
date: 2022-08-21
forum: Installation &amp; Upgrades
---

### Post by eMshsWE on 2022-08-21
Hello,

I have a Dell G15 Ryzen Edition Gaming Laptop. with Windows 11 installed , and trying to dual boot this with Ubuntu 22.04.
After shrinking my C drive, and creating the live USB, I booted into the USB and reached the "Try Ubuntu without Installing section".
Here when I try connecting to Wi-fi it refuses inspite of typing the Wi-fi password correctly.
Have restarted the laptop multiple times but still same problem persists.

Then I tried connecting live Ubuntu to my Mobile Phone's Hotspot using its Data Connection. Now, Ubuntu was able to connect.
But then when I switched back to Wi-fi it refuses to connect

Have checked for typos while typing the Wi-fi Password on Laptop, but am not making any mistake there.

Could someone please help me out?
Regards,
ajayram198

---

### Post by sudodus on 2022-08-21
It is possible that your computer has a wifi system, that is not yet supported with a Linux kernel driver, but it is also possible, that there is a proprietary driver to be downloaded and installed.

Please tell us about the wifi hardware (brand name and model) in your Dell G15 Ryzen Edition Gaming Laptop. If Ubuntu cannot see it, boot into Windows which should be able to identify it.

---

### Post by eMshsWE on 2022-08-22
So I checked in Windows Under Device Manager -> Network Adapters 

Killer(R) Wi-Fi 6 AX1650x 160MHz Wireless Network Adapter (200 NGW)


Just another doubt, if I use a LAN (Ethernet) Cable, I wont be prompted to type in any Password right??

---

### Post by sudodus on 2022-08-22
According to [this link](https://www.reddit.com/r/linuxquestions/comments/d893wa/no_wifi_with_killerr_wifi_6_ax1650x_160mhz/), it should work with new Linux kernels, and maybe your kernel is new enough to come with a driver for your wifi hardware.

- One answer states that 5.1+ kernels can manage it. If this is correct, you should be able to make your wifi work in Ubuntu 22.04 LTS.

- One answer states that you should install kernel 5.3.1, and there are further instructions. Anyway, it seems that the problems were solved for the person who asked for help (by switching to Manjaro). If I understand correctly, Ubuntu 22.04 LTS uses Linux 5.15 now. Also the developing version ('Kinetic Kudu' to be released as Ubuntu 22.10 in October) has a Linux kernel in the 5.15 series now. The kernel of Kinetic Kudu will probably be upgraded before the release, but anyway, it should be new enough.

[hr][/hr]
My experience of ethernet is that it just works (also with live systems and other test systems), I need no password (but I guess it depends on the router, so I don't know what will happen in your case).

---

### Post by eMshsWE on 2022-08-22
I chceked the Linux Kernel version by using the uname -f command. It gives 5.15.0-25-generic

And in you have mentioned that in 5.1+ version kernels, Wi-fi connectivity should work. However, thats not happening. Repeatedly asking for Wi-fi password even though I'm typing it correctly.

Never faced this kind of situation while installing Ubuntu, ever. :( !!

---

### Post by eMshsWE on 2022-08-23
Was wondering .. when I connect to the mobile Hotspot using its Data Connection even that is a Wifi connection only. How does it work there but is unable to connect to the Home Wi-fi?

Then I tried connecting to the Office Wi-fi network (yes, our organization hasn't provided Office laptops). It connected to the Office Wi-fi network in a jiffy :).
Lemme check this once again in the evening at home Wifi.

---

### Post by eMshsWE on 2022-08-27
At home, I booted into Windows and checked the Wifi password. It is exactly the SAME password that I have been typing into Ubuntu and inspite of this, Ubuntu refuses to connect to network.
So using the Office Wifi, I installed Ubuntu from live USB. And it works perfectly there. It was able to connect to Office Wifi after that as well.
But it refuses to connect to the home Wifi network even after typing the correct password.
Whereas Windows and all other devices (like my Ipad and mobile Phone) connect there.
Really strange !!

---

### Post by sudodus on 2022-08-27
Does your password contain one or more non-ascii characters, that are interpreted differently by Windows and Ubuntu? 

You can install a small tool
```

sudo apt update
sudo apt install ascii

```
and run it to see which characters are ascii.
```

$ ascii
Usage: ascii [-adxohv] [-t] [char-alias...]
   -t = one-line output  -a = vertical format
   -d = Decimal table  -o = octal table  -x = hex table  -b binary table
   -h = This help screen -v = version information
Prints all aliases of an ASCII character. Args may be chars, C \-escapes,
English names, ^-escapes, ASCII mnemonics, or numerics in decimal/octal/hex.

Dec Hex    Dec Hex    Dec Hex  Dec Hex  Dec Hex  Dec Hex   Dec Hex   Dec Hex  
  0 00 NUL  16 10 DLE  32 20    48 30 0  64 40 @  80 50 P   96 60 `  112 70 p
  1 01 SOH  17 11 DC1  33 21 !  49 31 1  65 41 A  81 51 Q   97 61 a  113 71 q
  2 02 STX  18 12 DC2  34 22 "  50 32 2  66 42 B  82 52 R   98 62 b  114 72 r
  3 03 ETX  19 13 DC3  35 23 #  51 33 3  67 43 C  83 53 S   99 63 c  115 73 s
  4 04 EOT  20 14 DC4  36 24 $  52 34 4  68 44 D  84 54 T  100 64 d  116 74 t
  5 05 ENQ  21 15 NAK  37 25 %  53 35 5  69 45 E  85 55 U  101 65 e  117 75 u
  6 06 ACK  22 16 SYN  38 26 &  54 36 6  70 46 F  86 56 V  102 66 f  118 76 v
  7 07 BEL  23 17 ETB  39 27 '  55 37 7  71 47 G  87 57 W  103 67 g  119 77 w
  8 08 BS   24 18 CAN  40 28 (  56 38 8  72 48 H  88 58 X  104 68 h  120 78 x
  9 09 HT   25 19 EM   41 29 )  57 39 9  73 49 I  89 59 Y  105 69 i  121 79 y
 10 0A LF   26 1A SUB  42 2A *  58 3A :  74 4A J  90 5A Z  106 6A j  122 7A z
 11 0B VT   27 1B ESC  43 2B +  59 3B ;  75 4B K  91 5B [  107 6B k  123 7B {
 12 0C FF   28 1C FS   44 2C ,  60 3C <  76 4C L  92 5C \  108 6C l  124 7C |
 13 0D CR   29 1D GS   45 2D -  61 3D =  77 4D M  93 5D ]  109 6D m  125 7D }
 14 0E SO   30 1E RS   46 2E .  62 3E >  78 4E N  94 5E ^  110 6E n  126 7E ~
 15 0F SI   31 1F US   47 2F /  63 3F ?  79 4F O  95 5F _  111 6F o  127 7F DEL

```
The printable characters that you should use start with '!' and end with '~'.

Some password managers might have stricter or looser rules. Anyway, you have a password that works with Windows, so you can check if all characters in your password at home are included in this list of ascii characters.

Please notice that some of the characters might activate shell actions (for example '*' might be expanded to a list of the file names in the current directory), and for that reason should be avoided.

---

### Post by ActionParsnip on 2022-08-27
What is the output of
```

sudo lshw -C network

```

---

### Post by eMshsWE on 2022-08-30
No, my Home Wifi-password contains only ASCII characters. So what else could be the problem?
Another thing I notice is, if I connect with mobile hotspot & mobile is using Home Wi-fi then Ubuntu automatically connects to the Home Wi-fi through phone.

---

### Post by eMshsWE on 2022-08-30
ajayram198@ajayram198-Dell-G15-5515:$ sudo lshw -C network
 *-network                 
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 05
       serial: b4:45:06:9b:f0:72
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-46-generic firmware=rtl8125b-2_0.0.2 07/13/20 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 ioport:2000(size=256) memory:d1700000-d170ffff memory:d1710000-d1713fff
  *-network
       description: Wireless interface
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 1a
       serial: ac:74:b1:42:43:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-46-generic firmware=66.f1c864e0.0 cc-a0-66.ucode latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:84 memory:d1600000-d1603fff

---

### Post by eMshsWE on 2022-12-07
Hello,

I had to shift my house. And had to surrender the old Internet connection. I purchaed a new Internet connection with a modem. And now am able to connect smoothly to Internet on Ubuntu.
So looks like there was some Router setting in the old router which was allowing Windows 11 to connect to Internet but not Ubuntu inspite of typing correct password.

So the issue has been resolved.
I will mark this thread as solved.

Regards,

---

