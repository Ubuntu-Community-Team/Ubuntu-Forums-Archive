---
title: "Intel Centrino Advanced-N 6230, and Ralink RT5390 - Can Not Connect"
date: 2017-08-24
forum: MINT
---

### Post by nicholaswogan on 2017-08-24
Hi, 

I have install Linux Mint Cinnamon installed on a HP Pavilion Dv6t Laptop. I can not get my wireless internet to work at all. I have two cards I can use: Intel Corporation Centrino Advanced-N 6230, or a Ralink RT5390. I have tried to get wireless to work with both of the cards by following instructions on various forum posts, but with no success.

Attached is my wireless-info.txt

Thanks!

---

### Post by ajgreeny on 2017-08-24
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by chili555 on 2017-08-24
This suggests that the switch or key combination is set to disable wireless:> ##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yesAnd we notice this:> [/etc/modprobe.d/hp-wmi.conf]
blacklist hp_wmi
Why did you blacklist the apparent helper module that should translate key presses into action? Anything to confess??

---

### Post by nicholaswogan on 2017-08-24
There is a switch on the laptop to enable/disable wireless. toggling the switch does seem to do anything.

I am fairly inexperienced. I am not sure what the following means. I may have accidentally done this??? 

[COLOR=#000000]*[/etc/modprobe.d/hp-wmi.conf]*[/COLOR]
[COLOR=#000000]*blacklist hp_wmi*[/COLOR]

Do you have any suggestions for enabling this switch or key combination?[COLOR=#000000][I]
[/I][/COLOR]

---

### Post by chili555 on 2017-08-24
Usually, people don't "accidentally" blacklist a needed module. 

Let's try an experiment. From the terminal:```
sudo modprobe hp_wmi
```Now does the wireless switch work? If so, we'll make a simple change and fix it.

---

### Post by nicholaswogan on 2017-08-24
Thanks for the reply!,

The switch still does not work. The switch is a key on my keyboard that is lit amber when it is disabled and green when it is enabled. Still (after running the command you gave) the key it lit amber after toggled.

---

### Post by chili555 on 2017-08-24
Please see: [https://forums.linuxmint.com/viewtopic.php?t=185561](https://forums.linuxmint.com/viewtopic.php?t=185561)> I just booted into BIOS and pressed F9 (Reset setup defaults). After that I pressed F10 to Save and exit, and my WLAN now works like a charm.Please try it and post back the result. You will probably need to repeat:```
sudo modprobe hp_wmi
```

---

### Post by nicholaswogan on 2017-08-28
Hi,

I reset my bios to defaults, and the wifi still refused to turn on. In the link you provided I tried the series of commands suggested

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list
sudo modprobe -r hp_wireless
sudo rfkill unblock all
rfkill list
```

This result was
```
0: phy0: Wireless LAN    
    Soft blocked: no
    Hard blocked: yes
```

Do you have other suggestions?

---

### Post by chili555 on 2017-08-29
Since the module is blacklisted in your system. it is not helpful to remove (-r) it:> sudo modprobe[COLOR="#FF0000"] -r[/COLOR] hp_wmi
sudo rfkill unblock all
rfkill list
sudo modprobe[COLOR="#FF0000"] -r[/COLOR] hp_wireless
sudo rfkill unblock all
rfkill listPlease try again:```
sudo modprobe hp_wmi
sudo rfkill unblock all
rfkill list all
```

---

### Post by nicholaswogan on 2017-08-29
Here is the result:

```
0: phy0: Wireless LAN    
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by chili555 on 2017-08-30
Other than taking the card out and taping off the pin that looks for the kill switch, I have no other suggestions:

[https://forums.opensuse.org/showthread.php/477982-Hard-blocked-WiFi-SuSE-12-2/page3](https://forums.opensuse.org/showthread.php/477982-Hard-blocked-WiFi-SuSE-12-2/page3)

> Masking pin 20 WORKS! 

I found this to be insanely difficult, but worth the effort. Wash your hands before starting. The cheapest cellophane tape (think dollar store) works best. Put a larger-than-needed piece of tape over the pin 20 finger and then carefully cut away the excess with an exacto knife.It may be another pin on your card.

You might also try simply removing the internal card and trying the USB.

---

