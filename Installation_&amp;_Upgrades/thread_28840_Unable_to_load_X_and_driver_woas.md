---
title: "Unable to load X and driver woas"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by IAmNotPhillip on 2005-04-21
After many a failed attempts to get Hoary to work on my newer computer, I decided it was time to actually post and maybe get some help.

1) Right at the begging of the installation when the kernel is being uncompressed, my system rebooted and then went back to the main Ubuntu install screen.
**FIXED: linux apci=off**

2) While booting up linux during the Hotplug part, my system freezes.
**FIXED: [ctrl] + [c] just before Hotplug during bootup (temporary fix)**

3) At login, Ubuntu says it is unable to load X and I am stuck at console. I figured this was due to my graphics card (see specs below) and tried to get the drivers through the console which leads to my next problem...
[B]FIXED:
1) got name of GFX card and PCI slot through "lspci -X"
2) edited xorg.conf and changed Section "Device" to match my GFX card's name and slot
2b) also in xorg.conf, changed the Default view to match my GFX card's name
3) startx[/B]

4) Following instructions from ubuntuguide.org, after trying the command "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907", it errors with "Can't get key from keyserver: Connection refused"
*Connected to problem #6 & #7*

5) While trying to "sudo apt-get update" many errors are returned and Ubuntu helpfully suggests that I should "apt-get update in order to fix the problem"  >.<
*Connected to problem #6 & #7*

6) Ubuntu unable to detect PCI Ethernet card - is listed under device manager, but not network manager

7) Ubuntu unable to detect PCI 802.11g wireless card - same as problem #6


**System Specs:**
hp pavilon a705w
1st HDD - 2 partitions (35 GB for WinXP Home & 5 GB for backup)
2nd HDD - Maxtor 7200 RPM 120GB - 2 partitions (100 GB for windows storage & 20 GB for Ubuntu)
2.93 GHz Intel Celeron Processor
Intel Extreme [integrated] Graphics (currently disabled)
XFX GeForce FX5200 256MB
768MB DDR333 RAM - 512(x1) & 256(x1)

---

### Post by runt on 2005-04-21
[QUOTE=IAmNotPhillip]After many a failed attempts to get Hoary to work on my newer computer, I decided it was time to actually post and maybe get some help.

1) Right at the begging of the installation when the kernel is being uncompressed, my system rebooted and then went back to the main Ubuntu install screen. I was able to bypass this with "linux apci=off" (found via these forums).

2) While booting up linux during the Hotplug part, my system freezes. I was also able to bypass this problem by hitting [ctrl] + [c] multiple right before the Hotplug section (also found via these forums). While only a temporary fix, it has let me continue to some degree.

3) At login, Ubuntu says it is unable to load X (or whatever the GUI is called) and I am stuck at console. I figured this was due to my graphics card (see specs below) and tried to get the drivers through the console which leads to my next problem...

4) After following instructions from ubuntuguide.org, after trying the command "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907", it errors with "Can't get key from keyserver: Connection refused"

5) While trying to "sudo apt-get update" many errors are returned and Ubuntu helpfully suggests that I should "apt-get update in order to fix the problem"  >.<

**System Specs:**
hp pavilon a705w
2nd HDD - Maxtor 7200 RPM 120GB - 2 partitions (100 GB & 20 GB)
2.93 GHz Intel Celeron Processor
Intel Extreme [integrated] Graphics (currently disabled)
XFX GeForce FX5200 256MB
768MB DDR333 RAM - 512(x1) & 256(x1)[/QUOTE]
 while i am not a ubuntu god, i will try to help.

what do you have for an Internet connection?  i know that ```
sudo apt-get update
``` and ```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
``` require a working Internet connection to work.

---

### Post by IAmNotPhillip on 2005-04-21
[QUOTE=runt]while i am not a ubuntu god, i will try to help.

what do you have for an Internet connection?  i know that ```
sudo apt-get update
``` and ```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
``` require a working Internet connection to work.[/QUOTE]
 I am on a low end DSL connection (256k). I also set up the network during installation so it should work.

---

### Post by runt on 2005-04-21
[QUOTE=IAmNotPhillip]I am on a low end DSL connection (256k). I also set up the network during installation so it should work.[/QUOTE]

if you open up firefox, are you able to browse the Internet?

---

### Post by IAmNotPhillip on 2005-04-21
[QUOTE=runt]if you open up firefox, are you able to browse the Internet?[/QUOTE]
 On my windows partition? Yes.

But I somehow doubt that's what you meant. As stated above in problem #3 (and in my thread title) X (the GUI) won't load. I thought that maybe it had something to do with my graphics card, so that's why I've been trying to get the drivers.

BTW - I apreciate you trying to help me. A good community is always a good sign. =)

---

### Post by runt on 2005-04-21
s[QUOTE=IAmNotPhillip]On my windows partition? Yes.

But I somehow doubt that's what you meant. As stated above in problem #3 (and in my thread title) X (the GUI) won't load. I thought that maybe it had something to do with my graphics card, so that's why I've been trying to get the drivers.

BTW - I apreciate you trying to help me. A good community is always a good sign. =)[/QUOTE]

sorry, had a brain fart. boot into ubuntu, put in the cd, and then type ```
sudo apt-get install lynx
``` and then type ```
lynx www.google.com
``` lynx is a CLI text browser that is useful for testing network connections. also, type ifconfig and if you don't have an ip address, that is your problem.

---

### Post by heimo on 2005-04-21
1. Xorg problems

You should check /var/log/Xorg.0.log for any warnings and errors. Is there an error with "no screen found" or similar?
```
less /var/log/Xorg.0.log
``` 

Try editing xorg.conf and check that you have nv as a Driver in Device section

 ```
sudo nano /etc/X11/xorg.conf
```

Device section on my xorg.conf (I've XFX FX5200 with 128MB):
```

Section "Device"
		Identifier	  "NVIDIA Corporation NV34 [GeForce FX 5200]"
		Driver		  "nv"
		BusID		   "PCI:1:0:0"
	 Option		 "RenderAccel"		 "true"
		Option		  "NoLogo"
EndSection

``` 
Only change Driver, if neccessary.

Try restarting X.
 ```
sudo /etc/init.d/gdm restart
``` 
or
```
startx
```

2. Networking problems
Try restarting your network connection:
 ```
/etc/init.d/networking restart
``` 
and check /var/log/messages for any errors:
 ```
less /var/log/messages
``` 

If you're using DHCP, run
 ```
sudo /sbin/dhclient
``` 

Check /etc/resolv.conf - you should have your nameservers there. If you're using static ip addresses, check the interface configuration in /etc/network/interfaces.

Maybe these will give you some error messages to help get a better picture of what's going on. Post your observations, errors and warning and we'll be more than glad to help you.

And please, post output of commands 
[list]
[*]*lspci*   
[*] *ifconfig*   
[*]route -n 
[/list]

---

### Post by IAmNotPhillip on 2005-04-22
I would like to thank you both for all your help. Because of your suggestions, I was able to find the problem and fix it. X is now working wonderfully.

The problem was Ubuntu was trying to use my intel integrated graphics (which was disabled) while looking in the PCI slot that my nVidia card was in. I simply changed my xorg.conf to look more like yours and also had to change references to nVidia in a few more places.

I will gladly post the full (more detailed) solution for anyone else having this problem as soon as I get home in about 3-4 hours.

---

### Post by runt on 2005-04-22
[QUOTE=IAmNotPhillip]I would like to thank you both for all your help. Because of your suggestions, I was able to find the problem and fix it. X is now working wonderfully.

The problem was Ubuntu was trying to use my intel integrated graphics (which was disabled) while looking in the PCI slot that my nVidia card was in. I simply changed my xorg.conf to look more like yours and also had to change references to nVidia in a few more places.

I will gladly post the full (more detailed) solution for anyone else having this problem as soon as I get home in about 3-4 hours.[/QUOTE]

glad it works for you now.

---

### Post by heimo on 2005-04-22
[QUOTE=IAmNotPhillip]
I will gladly post the full (more detailed) solution for anyone else having this problem as soon as I get home in about 3-4 hours.[/QUOTE]
 
Great. I appreciate it highly. There's rarely unique problems, so someone will eventually see this thread and find a solution for his/her problem.

---

### Post by IAmNotPhillip on 2005-04-22
Well, X is working, and it is working rather well. But, alas, I have run into a few more problems:

1) Freeze up at Hotplug - this hasn't changed since before I got X working

2) PCI Ethernet - Ubuntu seems unable to detect my Ethernet card. Under the networking settings, all that's listed is my modem. I also have a wireless 802.11g card installed, but I wasn't really expecting that to show up in the first place. At least, not yet. But I would like to get my Ethernet working since I am currently plugged directly into my router.

And that's about it from what I can tell. Much better than it was before. Just a few more kinks to work out.

---

### Post by runt on 2005-04-22
[QUOTE=IAmNotPhillip]Well, X is working, and it is working rather well. But, alas, I have run into a few more problems:

1) Freeze up at Hotplug - this hasn't changed since before I got X working

2) PCI Ethernet - Ubuntu seems unable to detect my Ethernet card. Under the networking settings, all that's listed is my modem. I also have a wireless 802.11g card installed, but I wasn't really expecting that to show up in the first place. At least, not yet. But I would like to get my Ethernet working since I am currently plugged directly into my router.

And that's about it from what I can tell. Much better than it was before. Just a few more kinks to work out.[/QUOTE]

what do you have for a wifi card?

---

### Post by IAmNotPhillip on 2005-04-22
A Belkin Wireless 54Mbps Desktop Adapter.

---

### Post by IAmNotPhillip on 2005-04-23
Okay. Still haven't gotten the internet to work on Ubuntu. I feel that this thread:

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

would help me in getting my wireless card to work, but it requires an internet connection >.<

I was thinking, is there a way to configure my xorg.conf file to manually add my PCI ethernet card? It is listed in my device manager, but not in the networking settings.

---

### Post by IAmNotPhillip on 2005-04-23
Or another thought, is there a way to download all files needed from the thread mentioned above under windows and then simply copy them over to my Ubuntu partition? (I have mounted windows partitions)

---

### Post by runt on 2005-04-24
[QUOTE=IAmNotPhillip]Or another thought, is there a way to download all files needed from the thread mentioned above under windows and then simply copy them over to my Ubuntu partition? (I have mounted windows partitions)[/QUOTE]

that would work, and probably be easier

---

### Post by IAmNotPhillip on 2005-04-24
It worked!
[this message was posted from within Ubuntu over a wireless connection ;)]

---

### Post by snapper on 2005-06-10
This helped me as well.

Just installed Hoary, and couldn't get X to work. I've an agp and an PCi nvidia mx4000.

Chaged the device to match the one listed here (1:0:0) and removed the framebuffer support, and the I managed to get into X  O:) 

Thanks.

Gareth

---

