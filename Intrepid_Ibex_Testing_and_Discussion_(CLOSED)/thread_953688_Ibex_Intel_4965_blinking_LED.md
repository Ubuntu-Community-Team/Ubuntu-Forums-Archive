---
title: "Ibex Intel 4965 blinking LED"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TBKDan on 2008-10-20
I'm running the Ibex beta (x64) on my Dell M1730 laptop with an Intel 4965 wireless card. On Hardy, the wireless LED did not light up whatsoever. When I first installed Ibex (very shortly after the beta was released), the wireless LED just stayed on when the card was enabled with the switch (exactly what I wanted). A recent update now causes the LED to blink with wireless activity which can get very annoying... some searching yielded no results (mostly people requesting the feature). Anybody have any ideas of how to set the LED to just stay on solid when the card is enabled and not blink on activity? Thanks!

---

### Post by zoomy942 on 2008-10-20
do you have an embedded data card?

---

### Post by Saneless on 2008-10-20
That's how it's (unfortunately) supposed to act.  Pretty stupid, huh?  I curse anyone who ever wanted the stupid thing on in the first place.

My "fix" was a sharpie.  I had no other choice.

---

### Post by zoomy942 on 2008-10-20
for me, it used to do that when my embedded data card was deactivated in the Bios.  I rutned it back on and now it's solid all the time.  :)

---

### Post by TBKDan on 2008-10-20
@zoomy: If by embedded you mean internal (Mini PCI-Express), then yes it is. Unfortunately I don't think the BIOS disable/enable will do the trick since it was a new feature added by the developers.

@Saneless: Yeah... very stupid >_<  Although I would imagine there would be *some* way to disable it..  I don't want to completely cover it because I would like to know when the hardware is active :(

---

### Post by Mr. Picklesworth on 2008-10-20
That's strange. TBKDan, I have the exact same wireless card on my Asus F8SV!

However, the WiFi LED worked for me with Hardy final and works for me at the moment with Intrepid. May be an upcoming update (which you have) that does this, since it constantly gets broken and unbroken during development.

For me, though, the only persistent problem with my WiFi LED has been that it stops working after sleep mode; when the computer wakes up the light is not lit even though wifi works fine. If I really want that extra bit of green light, I can happily press the WiFi hardware switch twice to turn it back on. Perhaps Intel has a few different versions of the same card.

I don't want to highjack your thread, but while we're both here, what speed does NM report your connection at? (Right click on network manager applet, go to Connection Information). Mine is 60 Mb/s with a good wireless N router (should be *way* more than that!).

---

### Post by Muflon on 2008-10-20
TBKDan

I agree with you when the Wifi LED first started flashing, it was really annoying, a bit like the hard disk LED.  Now I have got used to it and it doesn't bother me any more.  It would be nice to be given the choice to have it flashing or not though.

Muflon

---

### Post by Mr. Picklesworth on 2008-10-20
Flashing suggests an error or otherwise notable state that requires the user's attention, like "still connecting". The fact that it is connected is not notable. The behaviour definitely is a bug, intended or not.

---

### Post by TBKDan on 2008-10-20
Has your wireless LED always worked in Hardy or just recently?  Could also be some differences in how the rest of the hardware communicates... dunno.

As for wireless speeds, I don't have an N router to test with, but in my wireless class we pretty much never saw the advertised speeds mainly because there were other B/G AP's in the area bumping the speed down.  Also, is your router a true N with 2.4 and 5Ghz radios with all the N speed capabilities enabled? (Block ACK, channel bonding, etc)  Unfortunately, way too many factors can bring down your speeds :(

---

### Post by TBKDan on 2008-10-20
> **Mr. Picklesworth said:**
> Flashing suggests an error or otherwise notable state that requires the user's attention, like "still connecting". The fact that it is connected is not notable. The behaviour definitely is a bug, intended or not.

Gah, should have quoted your first post on my previous one.  What may be one man's bug could be another man's feature :P   Regardless, I would think they would have left an option for it considering it does get pretty friggin annoying.  I checked the module and didn't see any options for turning it off...

```

# modinfo iwlagn
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
srcversion:     D2AECFCE21BDB49D6298264
alias:          pci:v00008086d0000423Asv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```

---

### Post by argoo on 2008-10-22
Check out the following fix...

[http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html](http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html)

---

### Post by iggames on 2008-10-22
I believe this is the *correct* behavior, as this is what the LED does under Windows. That said, I agree that it is distracting, and wish there was a more user-friendly way to control the behavior.

---

### Post by TBKDan on 2008-10-22
> **argoo said:**
> Check out the following fix...

[http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html](http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html)

Thanks, that seems to have done the trick :)  I may disable the auth blinking as well.

> **iggames said:**
> I believe this is the *correct* behavior, as this is what the LED does under Windows. That said, I agree that it is distracting, and wish there was a more user-friendly way to control the behavior.

Since when is the Windows behavior the end-all *correct* behavior?:lolflag:  While the drivers direct from Intel do this (blinking), the drivers I obtained from the Dell site for this card do not.

---

### Post by FuturePilot on 2008-10-22
> **iggames said:**
> I believe this is the *correct* behavior, as this is what the LED does under Windows. That said, I agree that it is distracting, and wish there was a more user-friendly way to control the behavior.

Not for me. I have an Intel 3945 and in Windows the LED is orange until you connect to a network, then it turns blue and it stays blue. This is how it worked in Linux too with the ipw driver until they switched to the iwl driver. Since then the LED has never worked the same. It's orange until NM starts during bootup, then it turns blue even though it's not connected to anything. Now in Intrepid it's added this quirky blinking thing where it blinks blue and orange. Not a huge deal but I would like the old functionality back so it would change state depending on the connection status, not depending on whether NM was running.

---

