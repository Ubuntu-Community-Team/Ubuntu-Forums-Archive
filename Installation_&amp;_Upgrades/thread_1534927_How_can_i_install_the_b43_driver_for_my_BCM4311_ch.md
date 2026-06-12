---
title: "How can i install the b43 driver for my BCM4311 chipset?"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by sqvelasquez on 2010-07-20
[FONT=Courier New][SIZE=2]I really need help with this. I have been working with it and i just  cant figure it out. Im a noob on working with command lines and linux in  general. I run Ubuntu 10.04 Lucid Lynx.

I get this as my lspci output:
 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN  (rev 01)

for iwconfig eth1 (which is my wlan card) i get:
          eth1      IEEE 802.11  Access Point: Not-Associated
          Link Quality:5  Signal level:215  Noise level:199
          Rx invalid nwid:0  invalid crypt:116  invalid misc:0
Can anyone help?[/SIZE][/FONT]

---

### Post by lechien73 on 2010-07-20
I had the same problem, I'm just trying to remember how I fixed it!!

In System > Preferences > Software Sources, check the box that says "Software restricted by copyright or legal issues (multiverse)" and click "Close". Your repositories will update.

Then go to Applications > Ubuntu Software Centre. Search for, and install, the package named "b43-fwcutter". On my system b43-fwcutter was already installed, but I don't know if this was by accident or design :)

Now open a terminal window and type:

```
sudo modprobe -r wl
sudo modprobe b43
```

As far as I remember, that is the procedure I used. iwconfig now reports the correct values.

---

### Post by sqvelasquez on 2010-07-20
thanks! I already had b43-fwcutter so that saved some time. But when I put in the code, there was no output and when I checked the iwconfig, my card isn't even showing up

---

### Post by JackNocturne on 2010-07-20
Ok so u have already b43 fwcutter,thats good. Are you trying to connect to your **access point**(router perhaps) or?

if that is the case then

```
iwconfig eth1 essid [Name of Access point] channel [Number of channel] key [WEP/WPA password if you have]
```then
```
dhclient eth1
``` this gives you an **IP address**

---

### Post by sqvelasquez on 2010-07-20
I guess my real question is, how can i run my broadcom card without the STA Linux Wireless driver because im trying to run aircrack-ng so i can understand the types of wireless security better

---

### Post by lechien73 on 2010-07-20
> **sqvelasquez said:**
> thanks! I already had b43-fwcutter so that saved some time. But when I put in the code, there was no output and when I checked the iwconfig, my card isn't even showing up

Try going into System > Administration > Hardware Drivers and see if the drivers are there for activation. I installed it so that I could run ettercap, so I had the same problem - I just can't quite remember the full procedure I used to get it working!!

---

### Post by JackNocturne on 2010-07-21
> **sqvelasquez said:**
> I guess my real question is, how can i run my broadcom card without the STA Linux Wireless driver because im trying to run aircrack-ng so i can understand the types of wireless security better

I have the same **chipset** as you ,and i know you can't run **Aircrack-ng **
without the [COLOR=DarkRed]wireless driver[/COLOR] (Its written in the documentation) because you'll need to set up your **wireless card **in ***monitor mode*** so it can capture packets and inject.

so If you have **every **requirement,, test if injection works, remember to test it on your wireless network;)

```
aireplay-ng -9 -e [Name of AP] -a [MAC ADDRESS of the AP] -eth1
```-9 Means Injection Test
Note: -a is optional

The system will respond with **injection is working**, then you know everything is set to go.

---

