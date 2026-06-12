---
title: "Will Intrepid Fix the Intel Wireless Bugs?"
date: 2008-06-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kernel Sanders on 2008-06-29
Hi all!

I have noticed something quite alarming accross all distro's using the latest kernel. The intel wireless drivers that were integrated in the latest kernel don't work for the Intel wireless 3945 and related intel wireless.

It allows available networks to be seen, and everything seems to work fine, but it will not connect to any network.

I have seen this problem reported in every single forum for the distro's using the latest kernel.

So I was wondering, does anyone know if this will be fixed for Intrepid? Or are we entirelly at the mercy of the kernel developers in fixing this problem?

Many thanks! :)

---

### Post by spamzilla on 2008-06-29
Intel 4965 works fine here using Wicd and I haven't tried network manager yet.

---

### Post by MacUntu on 2008-06-29
3945 working flawlessly with NM here.

---

### Post by Kernel Sanders on 2008-06-29
Seriously? Are you using the latest intrepid alpha? If so i'm delighted if this problem is now fixed! :shock:

All the latest releases, hardy, opensuse etc all have this problem as it was a recognised problem with the intel drivers that were integrated into the kernel.

---

### Post by BackwardsDown on 2008-06-29
I've got a D830 with an "Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection" and I've installed Intrepid off the cd. But the Network Manager doesn't see any wireless networks.

---

### Post by Raptor45 on 2008-06-29
This is an issue because the firmware is not installed, since l-u-m for 2.6.26 has not been released yet. If wireless is critical to you, you can grab it from a hardy install or download the firmware off intel's iwlwifi site and put it in /lib/firmware manually.

---

### Post by spamzilla on 2008-06-29
Intel wireless 4965 works ok for me using NM on a fully up-to-date Ibex alpha 1. After playing with NM / restarting to get it working, I can see various wireles networks and connect tot he internet fine. Wicd works much better, but I'm going to stick with NM to see if it works any better than on Hardy.

---

### Post by Hobbsee on 2008-07-01
Works for me, with the 3945 and nm.  Go figure...

---

### Post by caryb on 2008-07-01
It works for me as well but I cant get NM or other GUI apps to work so I just hack the /etc/network/interfaces file with my ssid settings etc & then I have absolutely no problems.


Cary

---

### Post by psyke83 on 2008-07-01
I first dist-upgraded from Hardy to Intrepid with no wireless issues. However, after trying a fresh install with Alpha 1, I had no wireless.

I found out that the CD was missing the correct package containing the firmware: linux-restricted-modules-common.

Raptor45, I think you're mistaken - this is the package that contains firmware for all the Intel wireless chipsets, and it's already built. I believe there have been some changes to the way it's packaged, since in the past these firmware files were always placed in /lib/firmware/kernelversion/, but now it's in the shared location of /lib/firmware. It' a much better decision IMHO, since the firmware files don't change due to a kernel update.

---

### Post by Raptor45 on 2008-07-01
> **psyke83 said:**
> I first dist-upgraded from Hardy to Intrepid with no wireless issues. However, after trying a fresh install with Alpha 1, I had no wireless.

I found out that the CD was missing the correct package containing the firmware: linux-restricted-modules-common.

Raptor45, I think you're mistaken - this is the package that contains firmware for all the Intel wireless chipsets, and it's already built. I believe there have been some changes to the way it's packaged, since in the past these firmware files were always placed in /lib/firmware/kernelversion/, but now it's in the shared location of /lib/firmware. It' a much better decision IMHO, since the firmware files don't change due to a kernel update.

Indeed, it seems you are correct. I was unaware that this had changed.

---

### Post by spamzilla on 2008-07-06
Oddly enough, my intel 4965 wireless has now stopped working but wired is fine.

[quote=dmesg]
[  471.903705] iwl4965: iwlwifi-4965-1.ucode firmware file req failed: Reason -2
[/quote]

Well here's the problem

edit

```

download 

http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.1.21.tgz

extract

sudo cp iwlwifi-4965-ucode-228.57.1.21/iwlwifi-4965-1.ucode /lib/firmware/

sudo ifconfig wlan0 up

```

---

### Post by psyke83 on 2008-07-06
> **spamzilla said:**
> Oddly enough, my intel 4965 wireless has now stopped working but wired is fine.



Well here's the problem

edit

```

download 

http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.1.21.tgz

extract

sudo cp iwlwifi-4965-ucode-228.57.1.21/iwlwifi-4965-1.ucode /lib/firmware/

sudo ifconfig wlan0 up

```

That's really not necessary. Look at my post earlier in the thread. If a user needs to download a firmware image, they may as well download the official .deb file that contains the proper firmware image (among many others). We don't need to encourage "fixes" that treat the symptoms rather than the disease (in this case, a vital package missing from Intrepid Alpha 1 alternative's CD).

---

### Post by stari4ek on 2008-07-07
iwl3945.
works well with my wifi spot. i use network manager.

---

### Post by mikael_h on 2008-07-08
I can confirm my wireless started working after a standard Synaptic install of package 'linux-restricted-modules-common' and a system re-boot.

I'm running a HP nw8240.

cheers

---

### Post by BUGabundo on 2008-07-09
well i havent found a way to get mine working

[https://bugs.launchpad.net/ubuntu/+bug/230844](https://bugs.launchpad.net/ubuntu/+bug/230844)

---

### Post by caryb on 2008-07-10
I rebuilt my pc a week ago, I had to download the firmware/driver from intel after installing & a reboot It worked fine. I had to do the /etc/network/interface settings but as I'm in KDE4 & working utilities are a bit thin at the moment.


Cary

---

### Post by jbernardo on 2008-07-10
The only bug I see now is a reversion. The option "ieee80211_regdom" now is used by the cfg80211 module and not the mac80211 module, but seems to have been broken with this change, as I can't see my AP on channel 13 if I don't enable that option, and scan is brokend if I enable it (either setting it to "JP" or "EU" or the older "64"), returning with a timeout error. So here I am with my AP on channel 11 once again...

---

### Post by wittelw on 2008-07-15
> **mikael_h said:**
> I can confirm my wireless started working after a standard Synaptic install of package 'linux-restricted-modules-common' and a system re-boot.

I'm running a HP nw8240.

cheers

Also confirmed this package fixes wifi on Sony VGN-CR120E. Anyone know if this is in launchpad for not getting detected / installed properly from an intrepid alpha 2 CD? I did several searched and didn't get a hit.

---

### Post by xir_ on 2008-07-15
I'm having a little war with my kernel at the moment with the drivers in the .19 kernel.

is there anyway i can install the ibex kernel into hardy? I seem to recall that people ported the development hardy kernel into gusty back in the day.

Cheers

---

### Post by psyke83 on 2008-07-15
> **xir_ said:**
> I'm having a little war with my kernel at the moment with the drivers in the .19 kernel.

is there anyway i can install the ibex kernel into hardy? I seem to recall that people ported the development hardy kernel into gusty back in the day.

Cheers

Quite frankly, don't ask for help doing that. The purpose of this part of the forum is to test Intrepid, and if you're creating a custom configuration and later here come asking for help, you'll pollute threads with misinformation (as the rest of your system is still using Hardy), preventing bugs from getting identified and/or reported properly.

Intrepid's kernel is still based on a RC release of upstream 2.6.26, so it's (obviously) not considered as finished.

---

### Post by xir_ on 2008-07-15
alright then, asked and answered. O:)

I'll just try and use and older kernel instead. 

cheers anyway

edit: The reason i did post here is because im having trouble with my intel 3945 wireless card relating to the new drivers in the .19 kernel and i was hoping they had been polished. But not to worry

---

### Post by Syke on 2008-07-16
> **mikael_h said:**
> I can confirm my wireless started working after a standard Synaptic install of package 'linux-restricted-modules-common' and a system re-boot.

I'm running a HP nw8240.

cheers

Ditto. After a clean install of Intrepid Alpha 2, installing linux-restricted-modules-common and rebooting gets Intel 3945 working.

---

