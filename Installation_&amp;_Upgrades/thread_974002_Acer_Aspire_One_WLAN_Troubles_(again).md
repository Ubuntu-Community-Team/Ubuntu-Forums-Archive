---
title: "Acer Aspire One: WLAN Troubles (again)"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Tk0680 on 2008-11-07
After installing 8.10 on my AAO, I've had (almost) no end of wireless troubles. These have generally consisted of either the adapter not being recognised by the OS at all (other than in lspci), or being recognised and failing to deal with my WPA2 WLAN. Currently, we're on the former situation.

I have followed all manner of tips and guides to resolve this, to no avail. The backports modules are installed, and I've previously tried the madwifi drivers. ath_pci and ath_hal are blacklisted. I've updated and upgraded via apt today.

lsmod:
> 
richard@impish:~$ lsmod | grep ath
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 acer_wmi,ath5k


lspci:
> 
richard@impish:~$ sudo lspci -vnn
--SNIP--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e008]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k, ath_pci


/etc/modprobe.d/blacklist:
> 
richard@impish:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
richard@impish:~$ sudo nano -w /etc/modprobe.d/blacklist
[sudo] password for richard: 
richard@impish:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# Atheros Drivers
blacklist ath_pci
blacklist ath_hal


There are also some interesting bits from dmesg that only appear when the adapter is recognised (but can't connect) - I'll post those next time that happens.

The first odd thing (that I've noticed) is from lspci - ath5k_pci appears to be the driver in use as opposed to plain old ath5k. Is this normal?

The wired network connection is fine, so the network stack itself seems to be alright, but I'd really love to get the wireless working and in a reliable fashion.

---

### Post by ullix on 2008-11-07
Did you try the Hardware-Driver utility (/usr/bin/jockey-gtk)? It tells you what drivers are available, and in use. On my AA1 it says:
* support for 5xxx series of Atheros 802.11 wireless LAN cards
- Support for Atheros 802.11 wireless LAN cards

The first must be activated, the last one should be inactivated. This uses the driver ath5k for wireless. As far as I know, no madwifi drivers are availeble for intrepid nor should be used. It works for me, albeit at slow speed, mostly showing 1Mb/s (versus expected 54). However, i can stream mythtv tv to this computer, which supposedly is 3 - 6 Mb/s. Maybe the reported speed is (also) wrong.

output of sudo lspci -v -s 03:00:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e008
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 35200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k

---

### Post by thor2002ro on 2008-11-08
in terminal:

sudo apt-get install linux-backports-modules-intrepid

go to System -> Administration -> Hardware Drivers and uncheck Atheros wifi(bug led not working and ath_pci doesn't compile on the new kernel)

reboot and works:popcorn:

---

### Post by Tk0680 on 2008-11-10
> **thor2002ro said:**
> in terminal:

sudo apt-get install linux-backports-modules-intrepid

go to System -> Administration -> Hardware Drivers and uncheck Atheros wifi(bug led not working and ath_pci doesn't compile on the new kernel)

reboot and works:popcorn:

> The backports modules are installed
;)

I'll double check the Hardware Drivers app, ullix, but I'm pretty sure it's already set as you suggest. Would be nice if it showed the driver name as opposed to a pair of essentially identical descriptions ..

---

### Post by thor2002ro on 2008-11-10
> **Tk0680 said:**
> ;)

I'll double check the Hardware Drivers app, ullix, but I'm pretty sure it's already set as you suggest. Would be nice if it showed the driver name as opposed to a pair of essentially identical descriptions ..

if you what to blacklist it manualy the driver is ath_pci

---

### Post by Tk0680 on 2008-11-12
> **thor2002ro said:**
> if you what to blacklist it manualy the driver is ath_pci
I don't want to be rude, but that's twice you've given me suggestions that - in my original post - I stated I'd already gone through. Could you read what I've said fully before responding to it? Thank you :)

And yep, I have the correct driver selected according to ullix's suggestion. This is all sorts of suck - does anyone know if ath5k is likely to be restored to the kernel any time soon? The removal has caused a (well documented) butt-load of problems for AAO users, although I seem to be at the worse end of them.

---

### Post by casabur on 2008-11-15
I just wanted to share what *may be* a solution for those having persistent problems with the Aspire One WLAN modules in Intrepid.

I've been dealing with actual crashes of the ath5k module (at least that's what I read the dmesg logs as saying).  This is to the extent that rsync commands would often fail with MAC errors.  I tried the madwifi route, and that is certainly faster, but I was still running into the problems.  Since I haven't noticed any of these issues in Windows XP - and I definitely do NOT see these issues when on wired lan, I was fairly sure the problem had to be driver related - so I decided to try to install a newer kernel.  I enabled pre-released updated and unsupported updates in adept (I'm running kubuntu) - and then updated sources.  I then dropped to konsole and apt-get'ed the new linux kernel and associated packages to bring in 2.6.27-8-generic.  

I rebooted with the new kernel, and enabled ath5k again.  

Surprisingly, it seems to be working now.  I've been running a rsync session pulling over a few gigabytes off of my server for over an hour, and the rsync session is still going and I haven't noticed any errors in dmesg.  Now, it IS running slower (under a megabyte/sec vs 3.4MB/sec) - ath5k definitely does not seem to be particularly optimized for the hardware and the LEDs don't work with it (though I consider that a feature - not a bug) - but it seems to be stable finally.

Of course, I could be seeing something entirely different in a few hours, and it's also quite possible my problem is wholly unique to my particular aspire one (originally the 120gb model with 1gb of ram, upgraded to 320gb and 1.5gb of ram - and yes, I've run ramtest fully).  

Anyway, doing this can obviously cause issues I haven't yet hit, but for those hitting persistent wlan issues on intrepid with the aspire one, it may be worth a shot.  Oh yeah, I ONLY installed the kernel related packages when I enabled pre-release and unsupported updates, and once they were installed, I disabled those settings in adept.

** Follow-up:

As a follow-up, I let rsync transfers run over-night (copying ~ 40gb of files).  I did in fact see evidence of issues still, though FAR fewer than before with 2.6.27-8-generic's ath5k driver.  

However, since I seem to be the only one seeing these specific issues, I have a feeling the problem is more than likely hardware related, and maybe I just haven't noticed the same issues in Windows XP by sheer chance.  I think I may try to cannibalize another netbook for its mini-pci wireless card and see if that behaves better.

Anyway, I'm updating so people aren't upset if upgrading 2.6.27-8 doesn't fix their issue.

---

### Post by ullix on 2008-11-20
@Tk0680:
I noticed that you were using WAP2 initially. You still do? I use WEP, and all works well. Could increase speed to 11M (sudo iwconfig wlan1 rate 11M) and even go up to 24M. Stable for the last hours. (Fails immediately at 54M).
Can you try WEP? I can't do WAP2 for now.

---

### Post by meditatingfrog on 2009-05-07
You've probably already checked this, but I noticed on my system I had multiple files in /etc/modprobe.d that were titled "blacklist".  Here's the important part:  One of these blacklist files was blacklisting ath5k.

I have the AR242x driver according "sudo lshw".

If this doesn't help, and you're still having trouble, let me know, or repost something.  We have the same hardware, and between the two of us should be able to get it working (assuming you have an AR242x).  

Take it easy bra.

EDIT:  And YOU DO.

---

