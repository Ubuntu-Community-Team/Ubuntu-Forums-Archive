---
title: "upgrade 16.04 to 16.04.2"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by koaung2 on 2017-02-23
how to upgrade 16.04 to 16.04.2 without boot error.

---

### Post by QIII on 2017-02-23
Hello!

Have you already upgraded and encountered an error, or are you asking before you upgrade?

---

### Post by bearlake on 2017-02-23
> **koaung2 said:**
> how to upgrade 16.04 to 16.04.2 without boot error.

If you been updating all along, then you are likely at 16.04.02

In terminal type:

```
lsb_release -a
```

Please post your results.

Edit: darn he's fast

---

### Post by koaung2 on 2017-02-23
i mean i want to upgrade 16.04 to 16.04.2. when i upgrade 16.04 to 16.10 i go the boot error.So how to prepare before upgrade 16.04.2 and i want to know "[COLOR=#ff0000]dist-upgrade[/COLOR]" is enought to upgrade or i should use "[COLOR=#ff0000]do-release-upgrade -d[/COLOR]" ?What should i do and what kind of command can i use ?

---

### Post by deadflowr on 2017-02-23
There is no upgrade from 16.04 to 16.04.2, only simply updates; that you should be doing anyway.
16.04 = 16/04.2, they are one and the same.
The sole difference being 16.04.2 has all the updates from the initial release (In this case April 2016) already applied (as of Feb 2017).

If the goal is to get to 16.10 then you can do that with do-release-upgrade.
no need for the development flag (the -d ), it's not in development.

And it should not matter if the upgrade is done with a fresh install of 16.04 or a fully updated install of 16.04.2.
(I've done a few upgrades directly from a fresh installation of one LTS release into another LTS release, simply because there is no point installing updates for a system that will have all those updates wiped out with a completely new set up updates. The release-upgrader installs updates for all packages that would be currently in the new version's archives.)

If you are getting some booting error caused by trying to upgrade releases from 16.04 to 16.10 then that should be addressed in it's own thread, perhaps.
With details.

Or explain better what booting error you have.

---

### Post by koaung2 on 2017-02-23
> **deadflowr said:**
> There is no upgrade from 16.04 to 16.04.2, only simply updates; that you should be doing anyway.
16.04 = 16/04.2, they are one and the same.
The sole difference being 16.04.2 has all the updates from the initial release (In this case April 2016) already applied (as of Feb 2017).

If the goal is to get to 16.10 then you can do that with do-release-upgrade.
no need for the development flag (the -d ), it's not in development.

And it should not matter if the upgrade is done with a fresh install of 16.04 or a fully updated install of 16.04.2.
(I've done a few upgrades directly from a fresh installation of one LTS release into another LTS release, simply because there is no point installing updates for a system that will have all those updates wiped out with a completely new set up updates. The release-upgrader installs updates for all packages that would be currently in the new version's archives.)

If you are getting some booting error caused by trying to upgrade releases from 16.04 to 16.10 then that should be addressed in it's own thread, perhaps.
With details.

Or explain better what booting error you have.

Do you mean i can't upgrade 16.04 to 16.04.2 or 16.04.1 ? If i want to upgrade,do i need fresh install ?

---

### Post by deadflowr on 2017-02-23
> Do you mean i can't upgrade 16.04 to 16.04.2 or 16.04.1 ? If i want to upgrade,do i need fresh install ?
?
Did you read what I posted?

Or is this not actually about updating to 16.04.2 but rather updating the hardware stack from the original hardware stack to the newer 16.10 stack.
(Like upgrading from the original 4.4 kernel series to the 16.10 4.8 kernel series)
If that's the case please read :
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by DuckHook on 2017-02-23
I take it that you installed Xenial when it first came out, are now running the 4.4.x kernel and would like to upgrade to the 4.8.x kernel as well as its associated new X-related apps and services? If so, then what you are looking to do is to upgrade to the new hardware enablement stack:```
sudo apt install -s --install-recommends xserver-xorg-hwe-16.04
```The write-up for this is here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus)

Make sure that you back everything of value up first.

---

### Post by koaung2 on 2017-02-23
Thank you for all.Now i am clear and know what should i do.

---

### Post by ajgreeny on 2017-02-23
Be warned that if you upgrade the hardware enablement stack now to the 16.10 version, you will start chasing your tail and have to do the same thing again in a few months time when the 16.10 HWE loses its support.

I often wonder why users rush to update the HWE when the original versions in the OSs are supported for 5 years, or 3 years in the case of the other DE versions.  If you need better hardware support as you have, for example, very new graphics and must use the newest xorg and kernel, it may be worthwhile, but generally it is best to stick with the default in an LTS and get the stability that comes with the system.

---

### Post by howefield on 2017-02-23
> **ajgreeny said:**
> Be warned that if you upgrade the hardware enablement stack now to the 16.10 version, you will start chasing your tail and have to do the same thing again in a few months time when the 16.10 HWE loses its support.

Not anymore, as I understand it, from 16.04.2 the upgrade through the HWE stacks will be automatic as opposed to having to manually upgrade as was the case in previous LTS installs.

> I often wonder why users rush to update the HWE when the original versions in the OSs are supported for 5 years, or 3 years in the case of the other DE versions.  If you need better hardware support as you have, for example, very new graphics and must use the newest xorg and kernel, it may be worthwhile, but generally it is best to stick with the default in an LTS and get the stability that comes with the system.

I think much of the time people didn't realise the 5 years didn't apply in those cases and ended up being burned, which is why it's a moot point now, at least for the current LTS :)

---

### Post by ajgreeny on 2017-02-23
Ah! I admit I had read that but forgotten about the change, so thanks for the reminder howefield.

I stick with LTS versions only for my main system, and do not bother with the HWE updates, as my hardware versions are not brand new, and weren't even when I purchased the machine so I have never needed the upgrades for hardware support.

---

### Post by howefield on 2017-02-23
> **ajgreeny said:**
> I stick with LTS versions only for my main system, and do not bother with the HWE updates, as my hardware versions are not brand new, and weren't even when I purchased the machine so I have never needed the upgrades for hardware support.

You're right, if hardware works then there is no *need* to upgrade. Must admit I generally prefer new bugs to old bugs so usually follow the HWE and glad it won't be so onerous this time around with 16.04. I labour under the belief that newer (probably) means performance gains :)

---

### Post by Keith_Helms on 2017-02-23
> **ajgreeny said:**
> Ah! I admit I had read that but forgotten about the change, so thanks for the reminder howefield.

I stick with LTS versions only for my main system, and do not bother with the HWE updates, as my hardware versions are not brand new, and weren't even when I purchased the machine so I have never needed the upgrades for hardware support.

The thing is, once 16.04.2 came out, you have to hunt for 16.04 and 16.04.1 in order to avoid automatically getting on the HWE treadmill.  16.04.2 is what the download page points you to as the latest LTS release.

---

### Post by DuckHook on 2017-02-23
But starting with the Yaketty kernel in 16.04.2, won't the HWE upgrade process simply feel like another regular kernel upgrade? If it gets installed automagically, it will hardly feel like a treadmill&#8212;just another kernel upgrade with a few more associated dependencies. New users who start out now with the 16.04.2 ISO will think that's the way it's always been. For the rest of us, installing the latest HWE stack will be the last time we will have to specifically do so.

I've upgraded all of my machines including servers and VMs to the latest HWE. Everything went smoothly and no problems so far (knock-on-wood). I've even purged the old linux-generic-image from a few of them, but I admit that's getting rather cheeky and I'm not recommending it to others.

I'm expecting future HWE upgrades to be transparent. We'll see.

---

