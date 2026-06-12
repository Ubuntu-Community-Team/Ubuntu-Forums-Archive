---
title: "Sagem fast 800 installation in Ubuntu 7.10"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by xanthigior on 2007-10-21
[FONT="Arial"]Hello to everyone. I 'm a new Greek user of Ubuntu. I downloaded it yesterday and I was very happy when I made it working in my pc.

The only problem I have is that I cannot install my usb modem. I have read various solutions but nothing help me. Please, give me a quide to install Sagem Fast 800 in Ubuntu 7.10. I know that it's a stupid modem but this is the one I have and I want to make it work in ubuntu. I don't want to use anymore windows.

And two last things: which is the best driver for my ati 9600 pro card and should I use nvidia drivers for my sound card or Realtek?

Thank's in advance! :)[/FONT]

---

### Post by dimis2410 on 2007-10-22
i've done that using the previous Kernel...

(file mallon den exei vgei akoma module gia to pirina tou gutsy)

I just finished the destruction of my loyal Feisty with an upgrade to Gutsy
****!

I could give you my sister if it was possible to have my Feisty back... :p
Damn Online Upgrade and shits...
Now i remeber when i've upgraded MAC OS without a ******* problem ...

---

### Post by ippokratis on 2007-10-23
I have exactly the same problem!  **Please, all you Linux experts, help us!  We just want to really USE Linux, not return to Windows!  If we cannot connect to the Internet, how will we stay in the Linux community?**:confused::confused::confused::(

---

### Post by darkazurka on 2007-10-23
Hi fellow ubuntu user. I followed the "3." step in this guide for my Sagem fast 840 on an ISDN connection. It's worked in both 7.04 and 7.10! I hope this helps!

[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm) (help with Sagem Fast 800 , Sagem Fast 840 and other modems)

It was a little pain to get it working for my modem actually, but after some hours it worked. :)

---

### Post by xanthigior on 2007-10-24
Part of the solution:
I manage to install sagem fast 800 (IV or E4) in ubuntu 7.10 but I cannot connect yet.
Anyway, go to ***_[http://eagleedgy.c-webhosting.org/deb/](http://eagleedgy.c-webhosting.org/deb/)_***
and download the files your need.
I downloaded and run the files *ueagle4firmware* & *ueagle4-gutsy-2.6.22-14-generic*.
Sagem can now synchronize with the line but I receive an error:
error loading '/lib/firmware/ueagle-atm/DSP4i.bin' for device '/class/firmware/2-1' with driver 'usb'
kernel: [ 2526.073566] usb 2-1: [ueagle-atm] sending DSP page 0
kernel: [ 2526.076201] usb 2-1: [UEAGLE-ATM] requesting firmware ueagle-atm/DSP4i.bin failed with error -2
I don't know what this is.
Maybe the solution is very easy now but I am a new user in linux. Sorry. Start learning

---

### Post by Nikos.Alexandris on 2007-10-24
Well,

many Greek users have the same problem with Sagem usb modems. Including me (with the Sagem 800 E2T). 

The solution will come sooner or later ;)

Greetings to all!

---

### Post by Nikos.Alexandris on 2007-10-27
I have a silly question:

How the heck can one execute the command **$ sudo apt-get install build-essential linux-headers-$(uname -r)** and install with it the headers if there is no internet connection?

**[COLOR="Red"]Impossible![/COLOR]**

Then** how can one**, for example,** install the headers in order to compile and install packages for the SAGEM usb modem?**

**Is it possible to download them** with another machine (any kind of) **and copy them into the ubuntu system?** Or will this attempt lead to an endless search for dependencies?

---

### Post by aatiis on 2007-10-27
Sure, dude. Go to packages.ubuntu.com and find the package you need (on a system with internet connection, of course.) copy the .deb files to your ubuntu system (usp/cd/whatever) and execute:```
sudo dpkg -i file.deb
```for example ```
sudo dpkg -i ueagle4-gutsy-2.6.22-14-generic.deb
```
Hope it helped.
Actually there's a nice tutorial on the serbian ubuntu wiki for the E4 sagem f@st, if you know serbian, it will help you:
[http://ubuntu-rs.org/wiki/Sagem_F%40st_800](http://ubuntu-rs.org/wiki/Sagem_F%40st_800)

---

### Post by Nikos.Alexandris on 2007-10-28
Thanks a lot. I will try to follow up.

I just need packages for **SAGEM F@st 800 [COLOR="Red"]E2T[/COLOR]** (used in France!).

---

### Post by Nikos.Alexandris on 2007-10-28
I got it! Thanks for the hint aatis.

I am on-line with my box.

Credits go mainly to Valente (in ubuntu-fr): [COLOR="Blue"]http://eagleedgy.c-webhosting.org/[/COLOR]

**1**. Download for SAGEM E2T ueaglefirmware.deb from [COLOR="Blue"]http://eagleedgy.c-webhosting.org.nyud.net:8080/debian/ueaglefirmware.deb[/COLOR]

    * For SAGEM E IV devices I suppose it is **[COLOR="Blue"]http://eagleedgy.c-webhosting.org.nyud.net:8080/debian/ueagle4firmware.deb[/COLOR]**

**2**. Install it: **sudo dpkg -i ueaglefirmware.deb**

**3**. Check if **sudo cat /etc/network/interface** prints out:
    [B]auto ppp0
    iface pppà inet ppp
    provider dsl-provider
[/B]

**4**. Configure with: **sudo sh /usr/bin/config-ueagle.sh [COLOR="Red"]KEY[/COLOR]**
    * (Replace [COLOR="Red"]**KEY**[/COLOR] with the respective code as seen in [COLOR="Blue"][http://eagleedgy.c-webhosting.org](http://eagleedgy.c-webhosting.org))[/COLOR]

    * *It is FR07 for France, Region Haut Savoie with a Tiscali ISP and GR02 for Greece*

**5**. Start it with: **pon ueagle-atm**

**6**. If it doesn't work try to: **sudo /etc/init.d/networking restart**

**7**. Try again!

+. You might want/ need to add also this... : **sudo route del default** & **sudo route add default ppp0**

---

### Post by darkazurka on 2007-10-31
I also connect using pon ueagle-atm.

---

### Post by myle on 2007-11-18
> **Nikos.Alexandris said:**
> auto ppp0
    iface pppà inet ppp
    provider dsl-provider
[/B]


It prints:
> myle@myle-desktop:~$ sudo cat /etc/network/interface
cat: /etc/network/interface: No such file or directory


What have I to do? The internet connection works, but I have to try a lot of times to get access on the Internet.

---

### Post by Nikos.Alexandris on 2007-11-19
Check in this page... [http://eagleedgy.c-webhosting.org/](http://eagleedgy.c-webhosting.org/)
Do all steps one-by-one as I posted before.

It should work...

P.S. Important is also to know the exact model of your modem!

---

### Post by Grizli on 2008-05-22
People try this:
```
http://www.ubudsl.com/en/download.php
```
It works!:guitar:

---

### Post by valiexo on 2008-05-22
> **Grizli said:**
> People try this:
```
http://www.ubudsl.com/en/download.php
```
It works!:guitar:
I have tried, i have done exactly everything the instructions said but there is no connection.
Both lights in my sagem flashes right but nothing.

---

