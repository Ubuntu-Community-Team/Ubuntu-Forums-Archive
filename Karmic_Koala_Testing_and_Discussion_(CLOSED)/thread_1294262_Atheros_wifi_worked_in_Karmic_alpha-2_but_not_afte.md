---
title: "Atheros wifi worked in Karmic alpha-2 but not after that."
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moma on 2009-10-18
Hello,

I have Fujitsu Siemens AMILO Li 1718 laptop with Atheros AR5001 wireless network adapter. It worked very well and out-of-the-box (first time ever !) in Karmic 9.10 alpha-2, but stopped working after subsequent upgrades.

The network-manager's "Enable Wireless" option is disabled and the wireless list is completely empty.

See this bug report.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565)
---

System information:
$ uname -a
Linux karmic32 2.6.31-14-generic #47-Ubuntu SMP Thu Oct 15 02:08:08 UTC 2009 i686 GNU/Linux
--

$ lsb_release -a
Distributor ID: Ubuntu
Description: Ubuntu karmic (development branch)
Release: 9.10
Codename: karmic
--

$ lspci -vnvn
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
 Subsystem: Atheros Communications Inc. Device [168c:3067]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 32 bytes
 Interrupt: pin A routed to IRQ 16
 Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=64K]
 Capabilities: <access denied>
 Kernel driver in use: ath5k
 Kernel modules: ath5k
--
Other information:
$ lspci -vnvn
[http://www.edbl.no/tmp/karmic/lspci.txt](http://www.edbl.no/tmp/karmic/lspci.txt)

$ uname -a
[http://www.edbl.no/tmp/karmic/uname.txt](http://www.edbl.no/tmp/karmic/uname.txt)

$ dmesg
[http://www.edbl.no/tmp/karmic/dmesg.txt](http://www.edbl.no/tmp/karmic/dmesg.txt)

$ lsmod
[http://www.edbl.no/tmp/karmic/lsmod.txt](http://www.edbl.no/tmp/karmic/lsmod.txt)

---

### Post by oldrocker99 on 2009-10-18
I just installed from disk and updated, and got my Atheros wifi working after that. Before, I was getting an error when I tried to config the connection properties.

:guitar:

---

### Post by IanW on 2009-10-19
AFAIK, Karmic defaults to "WiFi OFF" at first boot.
If you have a hardware switch on your laptop for wifi, try it?

---

### Post by moma on 2009-10-19
Hello and thanks for your input,

I will make a new fresh installation and try with that.

Yes, this laptop has a hotkey/button to switch the wireless on/off. It has also a green led indicator that shows the status. Unfortunately the button and led-light do not work in Karmic as is.

In jaunty, I had to install acerhk.ko software driver that manages the button and led-light. I used this guide in Jaunty: [http://futuredesktop.org/jaunty/amilo_1718_wireless_in_linux.txt](http://futuredesktop.org/jaunty/amilo_1718_wireless_in_linux.txt). Some Fujitsu Siemens AMILO laptops use the acer's keyboard circuitry, therefore the the driver works on them too.

My preliminary test shows that the guide will not work in Karmic. Compiling the acerhk driver (if it is needed?) may also be a challenge.

The question is how to switch the wifi on.

See also: 
1) [http://www.amilo-forum.com/topic,2750,-LI-2732-Wlan-Ubuntu-9-10.html](http://www.amilo-forum.com/topic,2750,-LI-2732-Wlan-Ubuntu-9-10.html)
2) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425620)
---
Anyway, I'll be back after fresh installment.

---

### Post by moma on 2009-10-19
Re-hello,

Ok, I got it working.
The WLAN-driver itself is loaded and well, but it (the driver or hardware) is simply switched off.

So I downloaded source code for the [acerhk...]("http://www.cakey.de/acerhk/") hotkey driver and managed, after some hackery, to compile it on Karmic. Now the hotkey (function key) **Fn** + **((o))** works and allows me to switch the WLAN on. The led turns green and wifi access points appear in the network manager. 

Picture: 
[[img]http://bildr.no/thumb/509975.jpeg[/img]](http://bildr.no/view/509975)

I will later release patched source code for the acerhk hotkey-driver so other people may also use it. It will be available here.

[COLOR="Red"]EDIT:[/COLOR] The following bug report in Debian concerns the compilation problem of acerhk.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=533341](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=533341)

[COLOR="Red"]EDIT:[/COLOR] Very good news. Debian's people has already fixed and patched the acerhk-0.5.35.tgz source so it should now compile in Karmic. And the source is in the Ubuntu's repository.
$ apt-cache search acerhk-source

[COLOR="Red"]EDIT:[/COLOR] Bad news.
The source code from Ubuntu's repo does not compile!
See bug report: [https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)

[COLOR="SeaGreen"]The solution: [/COLOR]Here is a temporary solution and guide
[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt](http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt)

-- case closed --

---

### Post by umberstark on 2009-10-21
Moma,

Thanks so much for this, the guide worked like a charm!

---

### Post by karesz on 2009-10-23
> **moma said:**
> 
[COLOR="SeaGreen"]The solution: [/COLOR]Here is a temporary solution and guide
[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt](http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt)

-- case closed --

Hi!
I still can't get this working... at the 

"$ sudo /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1"

part it says 

"WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting acerhk (/lib/modules/2.6.31-14-generic/extra/acerhk.ko): Unknown symbol in module, or unknown parameter (see dmesg)"

In the /etc/modprobe.d/ directory there aren't any options.conf, only options, so I tried copying it to options.conf, but still the same error message :( I don't know what to do... :(

dmesg | egrep -i "acer" says acerhk: Unknown parameter 'force'

---

### Post by moma on 2009-10-24
What type of AMILO laptop do you have?

In steps 3) and 4) you test the module loading and usage manually.
Many AMILO models do not understand or match the "force_series=6805" option. Try without it.

$ sudo /sbin/modprobe acerhk autowlan=1
---

Tell me what options work in your laptop model. I will then update the document.

---

### Post by karesz on 2009-10-24
I've got an Amilo Li1718, Model: MS2212

I have already tried modprobe acerhk autowlan=1, and the modprobe acerhk, both give back the same error :( 
Still no action... Are there any way to switch the wlan on by software?

---

### Post by moma on 2009-10-24
Hello,

Ok, check the /etc/modprobe.d/ directory. Maybe you have erroneous, old files there. Delete them. What is this /etc/modprobe.d/options file? I think it is remnant of Jaunty Jackalope?

I have Fujitsu Siemens AMILO Li 1718 with Ubuntu 9.10 (karmic) and /etc/modprobe.d/ has these files.
$ [COLOR="SeaGreen"]ls -l /etc/modprobe.d/[/COLOR]

```
-rw-r--r-- 1 root root   47 2009-10-20 15:14 acerhk.conf
-rw-r--r-- 1 root root 2497 2009-10-12 00:07 alsa-base.conf
-rw-r--r-- 1 root root  325 2009-09-15 23:46 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2009-09-15 23:46 blacklist.conf
-rw-r--r-- 1 root root  213 2009-09-15 23:46 blacklist-firewire.conf
-rw-r--r-- 1 root root  662 2009-09-15 23:46 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2009-05-26 23:02 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2009-10-19 20:28 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2009-09-15 23:46 blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2009-08-26 11:49 libpisock9.conf
```

And /etc/modprobe.d/acerhk.conf contains one line:
$ [COLOR="SeaGreen"]cat /etc/modprobe.d/acerhk.conf[/COLOR]

```
options acerhk force_series=6805 autowlan=1
```

And /etc/modules file has this 
$ [COLOR="SeaGreen"]cat /etc/modules[/COLOR]
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
acerhk

```

And of course, the acerhk.ko driver must be in /lib/modules/$(uname -r)/extra/

My recommendation is;-)
Do a ny fresh installation. Do not upgrade from Jaunty.

I hope to have upgraded this [http://www.futuredesktop.org](http://www.futuredesktop.org) guide till Karmic is out.

---

### Post by regne v on 2009-10-24
> **umberstark said:**
> Moma,

Thanks so much for this, the guide worked like a charm!

Same here with Acer Aspire One 110 and UNR Karmic RC

Thanks a lot!

---

### Post by karesz on 2009-10-24
I' ve deleted the options file, works like a charm. I don't know how it got there, because it was a fresh install of karmic, and this was the first thing i wanted to do... Not a single clue... but, it doesn't matter after all :)

Thank you very much for your help!
:)

---

### Post by moma on 2009-10-24
Hello,

Good to hear that the guide worked for you, but the original compilation problem remains. See this bug-report: [https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)

Ubuntu has its own "acerhk-source" package. Read more about it at the bottom of the [guide...]("http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt")

---

