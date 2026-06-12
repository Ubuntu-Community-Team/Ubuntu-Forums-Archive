---
title: "Unable to get Orinoco Classic Gold in Monitor Mode"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by mbh on 2005-04-09
I get no help in the Kismet forum, so I try here:

My drivers report monitor mode available (iwpriv) but refuse to enter monitor mode.

I am running kernel 2.6.10-5-686 on an IBM Thinkpad T41 
the build-in Atheros based 802.11g adapter is working perfectly in monitor mode, but my (Proxim) Orinoco Classic Gold card is not. 

When i run iwconfig eth1 mode monitor I get the following message: 

Error for wireless request "Set Mode" (8B06) : 
SET failed on device eth1 ; Invalid argument. 

iwpriv displays monitor mode as an option: 

eth1 Available private ioctl : 
force_reset (8BE0) : set 0 & get 0 
card_reset (8BE1) : set 0 & get 0 
set_port3 (8BE2) : set 1 int & get 0 
get_port3 (8BE3) : set 0 & get 1 int 
set_preamble (8BE4) : set 1 int & get 0 
get_preamble (8BE5) : set 0 & get 1 int 
set_ibssport (8BE6) : set 1 int & get 0 
get_ibssport (8BE7) : set 0 & get 1 int 
monitor (8BE8) : set 2 int & get 0 
dump_recs (8BFF) : set 0 & get 0 

iwpriv monitor 1 1 runs without error message, but when I check with iwconfig or run Kismet, I am not in monitor mode. 

I have tried both the stand-alone drivers and patched the 2.6.10-5-686 source with orinoco-2.6.9-rfmon-dragorn-1.diff , compiled it and copied the orinoco*.ko and hermes.ko files to /lib/modules/version/kernel/drivers/net/wireless (forgive any misspellings here). 

For compiling, I have tried make, make_modules and make modules_install (not quite understanding the difference). 

I also checked that there are no other orinoco drivers present in the /lib/modules tree). 

dmesg says: 

eth1: Station identity 001f:0001:0008:0048 
eth1: Looks like a Lucent/Agere firmware version 8.72 
eth1: Ad-hoc demo mode supported 
eth1: IEEE standard IBSS ad-hoc mode supported 
eth1: WEP supported, 104-bit key 
eth1: MAC address 00:02:2D:AA:06:95 
eth1: Station name "HERMES I" 
eth1: ready 
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f 


This appear to be a genue Hermes based card. I tried temporarily to downgrade to firmware 6.06, but this gave the same result. 

Can anyone please help me - Is it correct, that the drivers are the .ko modules and loaded from the wireless direcory under /lib/modules/... ? 

The new drivers appear loaded, as there were NO monitor mode listed when running iwpriv before the update. 

I am unable to compile the v15 drivers - I get lots of 'Pointer from Integer' errors during make, so I have only tried the 0.13 drivers.

Any help would be greatly appreciated, I have searched google and the various forums for days in vain.

Regards 
Michael

---

### Post by jshein on 2005-04-09
see my previous post

[http://ubuntuforums.org/showthread.php?t=23596](http://ubuntuforums.org/showthread.php?t=23596)

---

### Post by mbh on 2005-04-10
Thanks for your reply

I did what you listed - except using -686 rather than -383 as I am running the 686 kernel.

I have NOT installed kismet and ethereal yet - the apt-get ethereal-common does not work: "Couldn't find package ethereal-common" apt-cache search does not list any ethereal hits either.

After completing your instructions, I rebooted but I am stuck at the same response from iwconfig: Invalid argument..

Are you running the 8.72 firmware ? I belive I have seen reports of users doing so with success, but possible not on Ubuntu (if it matters).

Regards
Michael

---

### Post by mbh on 2005-04-10
Hmm - I think it is working, I am seeing traffic from the router to my second laptop on the Ethereal console, which must mean that I am in monitor mode.

iwconfig still refuses to set or display eth1 in monitor mode, so so far my conclusion is that iwconfig is broken, but that kismet and ethereal manage to set the interface in monitor mode anyway.

Regards
Michael

---

### Post by jshein on 2005-04-10
I am using a dell true mobile 1150 ( re badged orinoco )

Make sure that you have uncommented universe in /etc/apt/sources.conf

I am using kubuntu, but that should make no difference at all, because it the same repositories as ubuntu. 

Other than that all I can say is that on my 2 laptops it works fine.

Toshiba Satellite 1900
Dell Lattitude C600

---

