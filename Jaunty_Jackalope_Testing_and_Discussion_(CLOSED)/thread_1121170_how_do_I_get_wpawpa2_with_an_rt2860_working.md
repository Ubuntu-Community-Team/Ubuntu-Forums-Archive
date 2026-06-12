---
title: "how do I get wpa/wpa2 with an rt2860 working?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-04-09
without encryption I can connect to a wireless network,
but not with wpa/wpa2.

Is it working for anybody?

I also tried manually installing the driver but no luck either.

---

### Post by Confuseling on 2009-04-09
This may not be entirely helpful, but just in case... On Zenwalk I had to install the kernel source, then in [driver]/os/linux/config.mk change

```

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```

Then just make / make install.

[http://support.zenwalk.org/viewtopic.php?f=28&t=21362&start=15](http://support.zenwalk.org/viewtopic.php?f=28&t=21362&start=15)

---

### Post by excogitation on 2009-04-09
thanks, tried that already.

Also shouldn't the module come with wpa_supplicant support support to not be useless? (may be a bug)

---

### Post by Confuseling on 2009-04-13
I agree, it is a strange way to default a configuration. Oh well.

Afraid to say it's working fine here on WEP on the LPIA Jaunty. It took a little bit of jigging - I had to compile the driver before it saw anything, and when I tried to set up my own entry in 'Wireless Networks' it didn't seem to like it, but the 'Auto wireless' one works.

Good luck.

---

### Post by dirtylobster on 2009-04-14
Unsecured and WEP working fine here but still no WPA (Eee PC 1000H).

---

### Post by Kobalt on 2009-04-14
I'm unfortunately stuck out of my wireless network as well, eeePC 901 using Jaunty: not working with WPA2...

---

### Post by excogitation on 2009-04-14
This is how I dot it working:
> **Akita said:**
> WPA/WPA2 are broken in every module everybody has tried (AFAIK) since Adam's 1.7.1.1 DKMS driver. Downgrade like so:

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

2) Go to terminal, and move the pre-installed driver so it won't get loaded.

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak


3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

Launchpad bug report:
> **Akita said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022")

There's a few that overlap, but that one seems to be the best fit.

---

### Post by synthaxx on 2009-04-14
Excogitation's method above worked for me (eee pc 901 20gb).


/edit: Also checking out the launchpad message.

---

### Post by Kobalt on 2009-04-14
Thanks excogitation, your method worked. 
I had tried to revert to the ancient driver used in the array custom kernel, but never quite managed to do it...

---

### Post by acreda on 2009-04-21
the 1.8.0.0 driver does work for me from source and from a dkms deb file on WPA only (TKIP)......... i think the problem is with supplicant rather than the actual driver

---

### Post by HankB on 2009-04-21
I set my router (Linksys WRT150N running DD-WRT) to AES vs. AES/TKIP and find I can get a connection. I also have the security mode set to WPA2 Personal Mixed if that matters. This is on an Eee PC 901.

HTH,
hank

---

