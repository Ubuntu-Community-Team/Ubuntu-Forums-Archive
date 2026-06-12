---
title: "[SOLVED] Kubuntu Gutsy Gibbon doesn't boot on Siemens Amilo Pro V2030"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by fitlad on 2007-12-03
Hi there,

I checked the forum for existing threads which may solve my problem, but I couldn't find any useful solution :(. I successfully installed Kubuntu Gutsy Gibbon on my Fujitsu Siemens Amilo Pro V2030. Unfortunately, the system didn't boot properly due to
[LIST]
[*]X server (it asks me to set the screen resolution)
[*]BCM43XX (the built-in wireless adapter)
[/LIST]

I cannot install the wlan driver unless Kubuntu is booting and the system is working. I only get error messages over and over and over related to BCM43XX :confused:

Please help me at least to get Kubuntu to start. I cannot run the system at all.

Thanks :confused:

---

### Post by paul.matthijsse on 2007-12-03
Hello, I am running Xubuntu on the same type of laptop. To solve the X problem, type the following from the commandline:
# dpkg-reconfigure -phigh xserver-xorg
when done, type startx.

To get the bcm43xx working, go to the following page and do step 1, 2b and 3. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Perhaps your bcm43 has another revision number, but that's easy to find out. As far as I know, you *do* need an internet connection for this to set it up, 

Succes.

---

### Post by fitlad on 2007-12-03
> **paul.matthijsse said:**
> Hello, I am running Xubuntu on the same type of laptop. To solve the X problem, type the following from the commandline:
# dpkg-reconfigure -phigh xserver-xorg
when done, type startx.

To get the bcm43xx working, go to the following page and do step 1, 2b and 3. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Perhaps your bcm43 has another revision number, but that's easy to find out. As far as I know, you *do* need an internet connection for this to set it up, 

Succes.

Thanks paul.matthijsse for your quick respond,
I still have a difficulty to get Kubuntu to start. Gutsy can install BCM43XX with the "restricted drivers" tool but the system should be running in the first place. Can you kindly provide me with clear instructions on how you managed to install and run Xubuntu in your machine? Amilo Pro V2030 is not (K)(X)Ubuntu friendly at all :confused:.

---

### Post by paul.matthijsse on 2007-12-03
Ah, if I remember well I used the alternate install cd, not the regular one because that resulted in problems (again, if I remember well). So download (or get otherwise) the Alternate cd for Kubuntu.

---

### Post by fitlad on 2007-12-03
> **paul.matthijsse said:**
> Ah, if I remember well I used the alternate install cd, not the regular one because that resulted in problems (again, if I remember well). So download (or get otherwise) the Alternate cd for Kubuntu.

Hi Paul,

I already installed Kubuntu on my notebook using the alternate cd (I don't like the live cd version). Any, other suggestion please? :confused: Thanks

---

### Post by fitlad on 2007-12-03
Hi there,

Just to be more precise, I'd like to include the error message I receive every time I restart my Kubuntu machine.

Starting K display
[LIST]
[*]Starting Common Unix Printing System: cupsd
[*]Starting Powernowd................. /etc/rc2.d/S20 powernowd. 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling.governor: Directory nonexistent
[*]CPU frequency scaling not supported
[*]Starting Avahi mDVS/DNS-SD Daemon avahi-daemon
[*]Starting DHCP D-Bus daemon dhcdbd
[*]Starting Bluetooth Services
[*]Starting anac(h)ronistic cron anacron
[*]Starting defferred execution scheduler atd
[*]Starting periodic command scheduler crond[/LIST]
Checking battery state
[LIST]
[66.356000] bcm43xx:
[*]Running local boot scripts (/etc/rc.local)
[/LIST]
Error: Microcode "bcm32xx_microcode5.fw. "not available or load failed".

Can anyone figure out how to sort out this mess and get Kubuntu to start? Thanks

---

### Post by paul.matthijsse on 2007-12-04
what happens after the last error? system hangs or...?

---

### Post by fitlad on 2007-12-04
I have downgraded my Kubuntu from Gutsy Gibbon to Feisty Fawn and my Amilo Pro V2030 machine is working at last. I successfully managed to install BCM43XX driver for my WLAN but the display unit doesn't work properly; the resolution is kept as VGA rather than 1024x768! The size of icons is big and colours are not appealing. Any support given by other Kubuntu users is appreciated. After sorting out the display driver issue, is it safe to upgrade my Kubuntu to Gutsy Gibbon via the "Adept Manager"? Thanks for help.

---

### Post by paul.matthijsse on 2007-12-04
I also had only VGA, I worked around that (in Xubu) by choosing small system and application fonts, the smallest window decorations I could find, and having no icons on te desktop, etc. No problem for me as it was only a machine to play music and surf the web. But it is annoying indeed. Happily my V2030 laptop is half broken now (fan stopped working due to my own stupidness), so I bought a cheap desktop instead! :-)

---

### Post by fitlad on 2007-12-15
Finally it's solved, with the support provided by this thread [http://ubuntuforums.org/s howthread.php?p=3956021#post3956021]("http://ubuntuforums.org/showthread.php?p=3956021#post3956021") The graphic card is working as charm and I decided to keep Kubuntu Feisty (Gutsy is not "Amilo" Friendly") :lolflag:

---

