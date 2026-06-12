---
title: "Compaq Presario V2000 w/Ubuntu 6.10"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by ricardovich on 2007-01-13
I've been using linux for many years and was blown away by my Ubuntu 6.10 installation on my Compaq V2000 laptop. Granted, I haven't installed a new version of any linux distro on any of my computers in a few years, but none the less I've been converted to Ubuntu. Everything I expected not to work, worked perfectly!!! If you're new to linux then you may not remember what a pain thumb drives, usb mouses, wifi, and tons of cheap hardware have been for linux users. I was blown away because even my [Fn] keys worked without any configuration. I use a usb mouse w/my laptop when I'm at home and even it works no matter how many times I plug it in and out (I like to move around a bit). My thumb drive worked immediately without any painful configuration as well. 

But alas, I knew well beforehand that my wifi would need some work, So here we go...

My specs:
Presario V2000 w/ AMD Sempron (Not Pentium M, and not the Intel wireless chipset that also ships w/V2000)

```
lspci
```

returns:

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```


```
sudo gedit /etc/modprobe.d/blacklist
```

Add 'blacklist bcm43xx' to the bottom, save, and exit.

Install ndiswrapper 1.33

I'm dual booting with a windows partition so to install my wifi drivers:

```
ndiswrapper -i /media/hda1/SWSetup/WLAN/bcmwl5a.inf
```

worked fine for me. Otherwise add "bcmwl5a.inf" and "bcmwl5.sys" to your desktop and change '/media/hda1/SWSetup/WLAN/' from above accordingly. 

Then of course:

```
ndiswrapper -l
```

returns:

Installed drivers:
bcmwl5a         driver installed, hardware present 

else you've got a problem.

```
ndiswrapper -m
```


restart for good measure

```
sudo iwlist scan
```
If you're in range then there should be something under wlan0.

```
sudo gedit /etc/network/interfaces
```

My working wifi interface looks thusly:



auto lo
iface lo inet loopback
#iface eth0 inet dhcp
#auto eth1
#iface eth1 inet dhcp
#auto eth2
#iface eth2 inet dhcp
#auto ath0
#iface ath0 inet dhcp

mapping hotplug
        script grep
        map eth0

iface wlan0 inet dhcp
wireless_keymode open
wireless_mode managed
wireless_nick home
wireless-essid XXXXXXX
wireless-key XXXXXXX

auto wlan0




Fill in the X's with your essid and wep key. Note the wep key in this form will/can have letters and numbers b/c it is in HEX. If you're using an open wireless switch 'wireless-key XXXXXXX' to 'wireless-key open'. Also note the difference between the -'s and the _'s.

restart for good measure

Open network selector.

Apps -> Internet -> Network Selector

It should put an icon (small red X) on your gnome panel. Click and select wlan0.

And that did it for me. Except for 

```
sudo gedit /etc/apt/sources.list
```

and uncomment the two lines for the universe.

However, I wrote this after the fact and may have left something off, etc.

Rant: When I use the volume keys on my laptop, Ubuntu shows what the current system volume is. Windows does not do this. My touchpad was automatically configured for speed sensitivity, but not on Windows. On and on it goes.

---

### Post by durkhaima on 2007-02-25
I followed your steps however, each time I run 'ndiswrapper -l' bcmwl5 and bcmwl5a are listed as invalid driver.  I was wondering if this is because I have a 64 bit processor on my Compaq Presario V2000 .

---

### Post by ricardovich on 2007-02-28
I don't think the processor would come into play unless there's driver process interference "some how". Make sure that the wireless card is the same as mine and that you "ndiswrapper -i bcmwl5a.inf" from the same folder that contains the bcmwl5.sys file - meaning that the two files are in the same location.

The two files themselves could be a problem. On other wireless cards I have configured, downloading the drivers from the internet at DriverGuide.com or somewhere else was required as oppose to using the drivers off the "Windows install hardware disk". 
```
wget http://biginoz.free.fr/linux/bcmwl5.sys
wget http://biginoz.free.fr/linux/bcmwl5a.inf
```
This will download the two files into your home directory.
```
sudo ndiswrapper -i bcmwl5a.inf
```

---

### Post by emodro on 2007-03-08
i successfully install the driver, however when i type sudo iwlist scan
i get 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

then when i go to system- networking, my wireless adapter isn't there anymore
i'm getting
Installed drivers:
bcmwl5          driver installed, hardware present

i'm stumped, i've restarted a bunch, un black listed it, put it back, and i still cant get it, i have the same pc as you, but i have a turion 64 processor... same wireless card though.

---

### Post by ricardovich on 2007-03-08
Check the file: /etc/network/interfaces
You may need to manually add wlan0. If so:

```
sudo gedit /etc/network/interfaces
```
add:
```
iface wlan0 inet dhcp
auto wlan0
```
Has the blue wireless light above the keyboard come on? Press it and restart.

---

### Post by emodro on 2007-03-09
i went to the file and it was already there... i took it out saved it put it back saved, still nothing... the blue light has never come on

---

### Post by ricardovich on 2007-03-11
Go to Applications -> Internet -> Networking and make sure that only Wireless connection has a check next to it. Anything else should have dashes.

---

### Post by arke on 2007-04-09
I

've got the same problem (except that I'm on Kubuntu, not Ubuntu). I did some digging and tried 

```
sudo /etc/rcS.d/S40networking restart
```

...and got the following:

```
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

Of course, ndiswrapper -l says everything is fine, and I blacklisted, etc.etc.etc...:( 

I'll probably do some more digging today, but any ideas what it could be?

---

### Post by ricardovich on 2007-04-15
```
sudo modprobe ndiswrapper 
```
Should allow wlan0 to boot with start-up if you have ndiswrapper configured properly.

---

### Post by ricardovich on 2007-04-30
I decided to kill my Windows partition and reinstall Ubuntu Feisty 7.04 on the entire hard drive b/c Windows was just taking up space. I hooked up my wired ethernet cable and Feisty connected automatically. Then:

```
sudo aptitude update && sudo aptitude install bcm43xx-fwcutter
```

Reboot

Press Wireless button on laptop. Light came on. Used the nm-applet to connect to my router.
That's it!

The signal strength meter now works. Yeah, I guess.

---

### Post by ricardovich on 2007-05-04
For some reason the wireless card and network-manager occasionally act flaky. 
Its an easy fix with Wifi-radar as I describe on this post:
[http://ubuntuforums.org/showthread.php?t=432933]("http://ubuntuforums.org/showthread.php?t=432933")

---

