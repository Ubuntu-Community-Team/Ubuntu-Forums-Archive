---
title: "Intel 8260 Wireless Card + iwlwifi driver troubles + USB-to-Ethernet adapter."
date: 2015-12-02
forum: MINT
---

### Post by adelie2 on 2015-12-02
*Disclaimer:* I don't run Ubuntu, but Mint is essentially a derivative of Ubuntu and their official forums are down. I'm at the end of my rope and urgently need to get my Linux installation up and running. I'm sorry. :<

tl;dr -
I'm dualbooting Mint with Windows, have no wired connection, and Mint refuses to set up a wireless connection. I have an ethernet-to-USB adapter (Gigaware) but it also refuses to work, and apparently people with the same adapter have given up on it ever working.

Here's what I've tried so far:
- Updated my kernel to 4.3.0. This should at least make my kernel compatible with the iwlwifi version needed for my Intel 8260 wireless card.
- Downloaded the [iwlmvm firmware]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi") from the relevant website and moved the files into my /lib/firmware directory.
- Used *modprobe iwlwifi* and *modprobe* *iwlmvm* multiple times.
- Tried the fix [given here]("http://askubuntu.com/questions/693109/intel-wireless-8260-unclaimed-network") where you compile the driver yourself. I am on the same subsystem and pci.id as the poster, but after following the instructions exactly, the backport refuses to compile because it can't find locale.h. Apart from this file having something to do with operating system innards I'm loath to touch, I have no idea what any of that means.
- Drawn a summoning hexagram and stood in it while doing the 'Please Give Me Wifi Signal' dance.

Here's a few relevant outputs that may be helpful.

I've done a lot of the steps I've found and haven't saved all the information. My results for running grep on dmesg and checking other points are [about the same as this person's]("https://www.reddit.com/r/linux4noobs/comments/2kagi6/how_to_install_intel_wireless_drivers_without/cljir6y"). If you have anything you'd like me to run and post, please tell me. Thank you very much for any potential help you can give me!

```
$ lshw -c network

  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d2a00000-d2a01fff

// some stuff about my ethernet network omitted since it seems irrelevant

$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

// it seems suspicious that my wireless doesn't even show up at all here

$ inxi -Nn
Network:   Card-1: Intel Wireless 8260 
           IF: N/A state: N/A mac: N/A
           Card-2: Intel Device 1570 driver: e1000e 
           IF: eth0 state: down mac: 54:ee:75:79:a6:10

$ mintwifi
-------------------------
* I. scanning WIFI PCI devices...
  -- Intel Corporation Wireless 8260 (rev 3a)
      ==> PCI ID = 8086:24f3 (rev 3a)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
eth0      no wireless extensions.

lo        no wireless extensions.

// some other stuff that i believe is irrelevant

```

---

### Post by Hadaka on 2015-12-03
Hi please COPY and paste to a terminal..
```
lspci -nnk | grep 0280 -A2
uname -r
```
thanks

---

### Post by adelie2 on 2015-12-03
Here's the results - the kernel was updated by me by downloading the kernel to a USB.

```
$ lspci -nnk | grep 0280 -A2
03:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1130]
06:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1347] (rev a2)

$ uname -r
4.3.0-040300-generic


```

---

### Post by Hadaka on 2015-12-03
ok, lets take a look at the modinfo...info
please do and post,,
```
modinfo iwlwifi | grep 1130
```
thanks

---

### Post by adelie2 on 2015-12-03
Got this:

```
$ modinfo iwlwifi | grep 1130
alias:          pci:v00008086d000024F4sv*sd00001130bc*sc*i*
```

---

### Post by howefield on 2015-12-03
Thread moved to the "*MINT*" sub forum.

---

### Post by jeremy31 on 2015-12-03
See if a different version of backports will compile
```
[FONT=Consolas][COLOR=#111111]wget [/COLOR][/FONT]https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
[COLOR=#111111][FONT=Consolas]tar -zxvf backports-20151120.tar.gz
[/FONT][/COLOR]cd backports-20151120
make defconfig-wifi
make
sudo make install
```

This version doesn't have to be patched for your wifi, reboot

---

### Post by adelie2 on 2015-12-03
No luck - same issue as with other backports.

```
$ make clean
Generating local configuration database from kernel ... done.

$ make defconfig-iwlwifi
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
conf.c:6:20: fatal error: locale.h: No such file or directory
 #include <locale.h>
                    ^
compilation terminated.
make[2]: *** [conf.o] Error 1
make[1]: *** [defconfig-iwlwifi] Error 2
make: *** [defconfig-iwlwifi] Error 2
```

I remember there were a few little complaints about localization when I updated the kernel to begin with, but nothing that actually seemed to impact anything. :< I know literally nothing about operating systems so I'm not even sure where locale.h is supposed to be, much less what should be in there.

---

### Post by jeremy31 on 2015-12-04
Can you boot into an old kernel?  Hold the Shift key during boot until the Grub Menu appears, then select Previous Linux Versions and choose a 3.13, 3.16, or 3.19 kernel to boot from
Then
```
sudo apt-get install build-essential linux-headers-$(uname -r)
cd backports-20151120
make clean
make defconfig-wifi
sudo make install
```

Reboot and use the grub menu to select the same previous kernel

---

### Post by adelie2 on 2015-12-05
Same issue with locale.h missing on 3.16.

EDIT: Forgot to install build headers, but same result. Here's the message for that line.

```
$ sudo apt-get install build-essential linux-headers-3.16.0-38-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.16.0-38-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by jeremy31 on 2015-12-05
Open Synaptic Package Manager and see if you can search for and install
libc6-dev
libc-dev
g++
dpkg-dev

The Synaptic Package Manager has a Fix Broken Packages option in the Edit menu that might be able to fix things

---

### Post by faldiin on 2016-09-27
> **jeremy31 said:**
> Can you boot into an old kernel?  Hold the Shift key during boot until the Grub Menu appears, then select Previous Linux Versions and choose a 3.13, 3.16, or 3.19 kernel to boot from
Then
```
sudo apt-get install build-essential linux-headers-$(uname -r)
cd backports-20151120
make clean
make defconfig-wifi
sudo make install
```

Reboot and use the grub menu to select the same previous kernel

Good day,
        I am using LMDE 2 (Betsy) and was having issues with the Wireless Card. These instructions helped me fix my issue. I thank you for the walk through. 

Faldiin

---

