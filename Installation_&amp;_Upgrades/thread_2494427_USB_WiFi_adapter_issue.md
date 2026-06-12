---
title: "USB WiFi adapter issue"
date: 2024-01-16
forum: Installation &amp; Upgrades
---

### Post by paul_red2 on 2024-01-16
Hello.

I'm trying to use a USB WiFi adapter (Linksys WUSB6300 V2) on a freshly installed Lubuntu.
I've already used it when I did some tests on this same computer running Kali.
The problem is I don't remember why that time the drivers I installed worked and this time, don't.
When I give "lsusb" in terminal, it lists the Linksys WUSB6300 V2 (so it's there)
But when I disable the computers own LAN and WLAN, I can't connect to anything (WiFi)

For this model they say to use this driver here: [https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)
I installed this driver and when I give "inxi -N" in terminal, it says that the Linksys WUSB6300 V2 has driver installed.

I'm not very good with linux.. I tried googling this for a couple of days.. trying all I could find, but I reached the limit of what I can do. So please help me guys :?

---

### Post by MAFoElffen on 2024-01-16
Here is the instructions for that, that were on AskUbuntu: [https://askubuntu.com/a/1358400/138255](https://askubuntu.com/a/1358400/138255)

I'm thinking that after that script, you will find the module with this
```

find /lib/modules -name 8812au*

```
and the script says it is installed into /lib/modules/${KVER}/kernel/drivers/net/wireless/

While the module and options file will be placed into /etc/modprobe.d/${OPTIONS_FILE}

I do see some notes about SecureBoot being disabled...

There were no errors returned during the build right?

---

### Post by paul_red2 on 2024-01-16
Thanks for the help.
In that link there are two answers: The first is maybe for V2 of this adapter?
I've tried answer 2 (and didn't work).

Also right now after lots of trying I've done smth wrong bcs now my internal WLAN doesn't work
So I have no way to connect with this computer. I'm using another one to post here.

Is there any way to kinda reset or smth to make the Wireless of the computer work again?

---

### Post by MAFoElffen on 2024-01-16
Lost you on that. I am not familiar with the term 'smth'... Please explain.

Was 'smth wrong bcs' short for "something wrong because"?

---

### Post by MAFoElffen on 2024-01-16
Please post the output of this wrapped within CODE Tags: 
```

sudo lshw -C network | grep -E 'description|product|configuration'

```

---

### Post by paul_red2 on 2024-01-16
```
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       configuration: broadcast=yes driver=ath9k driverversion=6.5.0-14-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.5.0-14-generic latency=0 link=no multicast=yes port=twisted pair


```

Looks like it's not there

---

### Post by MAFoElffen on 2024-01-16
Because it's a USB device...

Please post the output of this wrapped within CODE Tags: 
```

lsusb -vvv

```
But just copy the piece that pertains to the adapter...

---

### Post by paul_red2 on 2024-01-16
```
Bus 005 Device 004: ID 13b1:0045 Linksys WUSB6300 V2
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13b1 Linksys
  idProduct          0x0045 
  bcdDevice            2.10
  iManufacturer           1 Linksys
  iProduct                2 WUSB6300 V2
  iSerial                 3 123456
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0035
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               3
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

---

### Post by MAFoElffen on 2024-01-16
On resetting your adapter, if Desktop:
```

rfkill block wifi
rfkill list
killall nm-applet
rfkill unblock wifi
nm-applet

```
But what we really need is a look to see if the modules built, and if it is loaded in the kernel
```

ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
find /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ -name *88x2bu.ko
lsmod | grep '88x2bu'

```

---

### Post by paul_red2 on 2024-01-16
> **MAFoElffen said:**
> On resetting your adapter, if Desktop:
```

rfkill block wifi
rfkill list
killall nm-applet
rfkill unblock wifi
nm-applet

```

From this code, I got this (at the end with the last one just hangs there.. does nothing):

```


m@m-n51vg:~$ rfkill block wifi
m@m-n51vg:~$ rfkill block list
rfkill: invalid identifier: list                                                                                                      
m@m-n51vg:~$ rfkill list                                                                                                        
1: phy0: Wireless LAN                                                                                                                 
        Soft blocked: yes                                                                                                             
        Hard blocked: yes                                                                                                             
m@m-n51vg:~$ killall nm-applet
nm-applet: no process found
m@m-n51vg:~$ rfkill unblock wifi
m@m-n51vg:~$ nm-applet


```

From the second codes, I got this: (the second and third line did nothing):

```


m@m-n51vg:~$ ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
admtek  atmel     cisco  intersil  marvell   microchip  quantenna  realtek  silabs  ti       zydas
ath     broadcom  intel  legacy    mediatek  purelifi   ralink     rsi      st      virtual
m@m-n51vg:~$ find /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ -name *88x2bu.ko
m@m-n51vg:~$ lsmod | grep '88x2bu'
m@m-n51vg:~$ 

```

---

### Post by MAFoElffen on 2024-01-16
Well... According to this: [https://github.com/morrownr/88x2bu/issues/63#issue-875944827](https://github.com/morrownr/88x2bu/issues/63#issue-875944827)

The kernel module that should have built and been added to the kernel is: 88x2bu

What is in this output?
```

ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/realtek
sudo dmesg | grep '88x2bu'

```

---

### Post by paul_red2 on 2024-01-17
I got this (at the end asked for pass and did nothing):

```
m@m-n51vg:~$ ls /lib/modules/$(uname -r)/kernel/drivers/net/wireless/realtek
sudo dmesg | grep '88x2bu'
rtl818x  rtl8xxxu  rtlwifi  rtw88  rtw89
[sudo] password for m: 
m@m-n51vg:~$ 

```

I wanted to add also that I did other things that maybe better I tell..
In the hope of making this thing work I installed some kind of a driver called "compat-wireless" I remember I used them when I was (on this same machine and wifi adapter) on Kali. There are these commands you give "make unload" and "make load" wich kinda resets the network.

Also I've installed aircrack-ng drivers (don't ask me why, I'm ignorant) So there's a mess now in this computer (maybe there's conflicting drivers.. who knows).

---

### Post by MAFoElffen on 2024-01-17
I think maybe you are right... I messaged someone I think might be better suited to figure that out. Waiting for his response to see if he can come and help.

---

### Post by paul_red2 on 2024-01-17
thanks!

---

### Post by paul_red2 on 2024-01-18
While waiting I tried using another USB adapter I have (another model)
I managed to install the drivers.. the thing is being recognized by the system
When I do inxi -N now it says it has a working driver.

So I put the physical wireless internal PCI card switch (that the laptop has in the front) to OFF (in the hope that I would be able to use just the USB adapter wireless to connect) but I don't see it.

I also made a new Wifi connection and choose the other device that was available (named like wlxe84..................:3F) the one of the internal wifi card was named wlp3s0 ...............:96

So my question is: How can I choose with what wifi device I can use internet?

---

### Post by paul_red2 on 2024-01-18
update:
For the moment looks like I solved this by using this comand:

```
sudo ifconfig wlp3s0 down
```

Now only the adapter is working and the internal wifi antenna is not.
Thanks for the help MAFoElffen ; )

---

### Post by paul_red2 on 2024-01-23
I'm trying to install this same USB adapter drivers to another old laptop with Xubuntu and I get this error:

```
Starting installation.
Installing 8821au.conf to /etc/modprobe.d
The non-dkms installation routines are in use.
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/6.5.0-14-generic/build M=/home/m/8821au-20210708  modules
make[1]: Entering directory '/usr/src/linux-headers-6.5.0-14-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  You are using:           
/bin/sh: 1: gcc-12: not found
(standard_in) 1: syntax error
  CC [M]  /home/m/8821au-20210708/core/rtw_cmd.o
/bin/sh: 1: gcc-12: not found
make[3]: *** [scripts/Makefile.build:251: /home/m/8821au-20210708/core/rtw_cmd.o] Error 127
make[2]: *** [/usr/src/linux-headers-6.5.0-14-generic/Makefile:2037: /home/m/8821au-20210708] Error 2
make[1]: *** [Makefile:234: __sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-14-generic'
make: *** [Makefile:2497: modules] Error 2
An error occurred:  2
Please report this error.
Please copy all screen output and paste it into the problem report.
You will need to run the following before reattempting installation.
$ sudo ./remove-driver.sh
root@mv:/home/m/8821au-20210708#
```

It's been hours trying to install just a freaking driver... Why is so hard in Linux to do a simple thing like this.. hours and hours of pain to do such a simple thing.. I thought I had to do the same thing I did to the other laptop (that has Lubuntu).
Please help me guys.. I'm stuck at this point.. it's driving me crazy.

edit: the drivers in question are these: [https://github.com/morrownr/8821au-20210708.git](https://github.com/morrownr/8821au-20210708.git)

---

### Post by him610 on 2024-01-23
>  Why is so hard in Linux to do a simple thing like this..
Some hardware manufacturers do not provide drivers to the open source community which means a certain amount of reverse engineering, ie: skills, knowledge, and time.

---

### Post by paul_red2 on 2024-01-23
@him610 Thanks.. I know.. I was boiling with rage :D
I found out where issue was.. I hadn't installed dkms
Now everything works!:KS

---

### Post by MAFoElffen on 2024-01-24
Dang. What an adventure. LOL. Glad everything is working now.

---

### Post by paul_red2 on 2024-01-25
If it wasn't for Google, I would not be able to do anything with linux.
As for Xubuntu.. it's not running smooth as Lubuntu. ofc.. but has this cool zoom that I like.. Anyway for the moment my only huge problem is with Telegram:
When I call someone it hangs there with "exchanging encryption keys"
This is a issue I have only in linux.. on mac and windows I can call w/o any problems.
Apparently it has smth to do with security.. being linux more strict on that.
If anyone has anything about this, it would be great.. I googled for the solution to death and still no luck.

---

### Post by MAFoElffen on 2024-01-25
File a bug here at launchpad...

Tell them it is a know problem, not just in Ubuntu, where you refer to this bug report at arch, where they found there were upstream bugs: [https://bugs.archlinux.org/task/76789](https://bugs.archlinux.org/task/76789)

That in that bug, there was a patchset to fix it: [https://github.com/telegramdesktop/tdesktop/issues/25780#issuecomment-1402796924](https://github.com/telegramdesktop/tdesktop/issues/25780#issuecomment-1402796924)

The patchset was applied in this build: [https://github.com/desktop-app/patches/tree/master/qtbase_6_4_2](https://github.com/desktop-app/patches/tree/master/qtbase_6_4_2)
and cam out in these builds:
[https://github.com/telegramdesktop/tdesktop/blob/de11987312798bda5dea716ea5210adf807e20aa/Telegram/build/prepare/prepare.py#L1303](https://github.com/telegramdesktop/tdesktop/blob/de11987312798bda5dea716ea5210adf807e20aa/Telegram/build/prepare/prepare.py#L1303)
[https://github.com/telegramdesktop/tdesktop/blob/cd85c4911c7ad39754b7c343ae60a0369ee03dc6/Telegram/build/docker/centos_env/Dockerfile#L695](https://github.com/telegramdesktop/tdesktop/blob/cd85c4911c7ad39754b7c343ae60a0369ee03dc6/Telegram/build/docker/centos_env/Dockerfile#L695)

BUT... The last 3 posts reported that the problem was STILL ongoing.

Hmmm. Might take looking at the pen issues at [https://bugs.telegram.org/](https://bugs.telegram.org/). You would think with as many people hitting this problem, that there will be an open bug report there on this. I just do not have the time this morning to look through that.

---

### Post by paul_red2 on 2024-01-25
@MAFoElffen 
Wow.. thanks man you already did so much by telling me it's not just me.
Now I'll take a look at these links and hopefully I can understand and help if I can reporting my issue.

Thanks again!!

---

### Post by MAFoElffen on 2024-01-26
Oh, by the way, you probably just didn't know... But if we open a thread, we, the person who opened it is responsible for marking it as "Solved" when we decide it should be.

You can mark this a Solved by selecting the "Thread Tools" link at the upper right of the first page of the thread, and then select "Mark as Solved". That helps other find answers to their similar problems when they search the Forums.

---

