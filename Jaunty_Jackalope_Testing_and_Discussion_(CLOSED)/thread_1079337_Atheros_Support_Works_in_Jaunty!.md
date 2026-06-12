---
title: "Atheros Support Works in Jaunty!"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by darksideforge on 2009-02-24
First of all, I upgraded 8.10 to 9.04 on a lark...I'm really not good enough with Linux to be a tester or to know what to report or how. But here are two major observations I have:

1) After 5 months of trying every "fix" known to mankind, all to no avail, to get my Atheros wifi to work in Intrepid, imagine my surprise and delight when I upgraded to Jaunty and disconnected my CAT5 cable last night in preparation to shut down and VOILA! my Toshiba Satellite auto-connected to my open wireless three rooms away!!!  I delayed shutting down for another hour while I played around and surfed the 'net. GREAT JOB DEVELOPERS!!!

2) Jaunty is S----L----O----W!!!!!!!   I'm not sure why; I don't know if it's something I'm doing wrong or if maybe I've got too many apps/programs running at the same time or what, but browsing my files and running firefox at the same time is like being back on a bad trip with Micro$hit Winslows.

If someone would like to forward this to the developers, feel free.

---

### Post by TrueTom on 2009-02-24
> **darksideforge said:**
> 2) Jaunty is S----L----O----W!!!!!!!

Do you have an Intel graphics card?

---

### Post by jbernardo on 2009-02-24
For me the atheros support is worst than in Intrepid. The ath_pci (madwifi) drivers won't work on my aspire one, and I have to blacklist acer_wmi before the ath5k drivers will even start working. And these disconnect frequently on a area with various APs with the same SSID, as the one I have at work.

Also, since cgd80211 no longer allows to configure the region, iw isn't yet in jaunty, and the version of wpa_supplicant that supports [CRDA ]("http://wireless.kernel.org/en/developers/Regulatory/CRDA")is also only in git and not in jaunty yet, I've lost channels 12 & 13. So, another regression... :(

---

### Post by Eclipse. on 2009-02-24
> **jbernardo said:**
> For me the atheros support is worst than in Intrepid. The ath_pci (madwifi) drivers won't work on my aspire one, and I have to blacklist acer_wmi before the ath5k drivers will even start working. And these disconnect frequently on a area with various APs with the same SSID, as the one I have at work.

Also, since cgd80211 no longer allows to configure the region, iw isn't yet in jaunty, and the version of wpa_supplicant that supports [CRDA ]("http://wireless.kernel.org/en/developers/Regulatory/CRDA")is also only in git and not in jaunty yet, I've lost channels 12 & 13. So, another regression... :(

Have you bothered reporting it on launchpad? Regressions are very bad.

---

### Post by jbernardo on 2009-02-24
Haven't yet - just tested it at work, and also tested with mandriva and the instability, which hadn't shown before in mandriva, is now also present, so it might also be the APs playing up.

But the CRDA regression is there. And it is a conscious decision by the 80211 stack developers, to appease the regulatory bodies. I found there is a proposal to add the iw package from debian to universe, but by my (very short) tests it alone won't bring back the missing 2 channels. It seems we need another netowrkmanager update together with wpa_supplicant.

---

### Post by darksideforge on 2009-02-24
> **TrueTom said:**
> Do you have an Intel graphics card?

Yes, although I don't think it's in use...I think a generic is in use instead.

Here's a partial listing of lspci -v:

```
@darkside:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff40
	Flags: bus master, fast devsel, latency 0
	Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

```

Does that help?

---

### Post by stricte on 2009-02-24
in subject Atheros support, i needed turn off this standard driver from kernel in jaunty (13% packets loss). Madwifi-hal works perfect.

Second, yes jaunty is slow and yes i have intel 4500. Is this a reason?

---

### Post by Sand &amp; Mercury on 2009-02-24
No good for me, as always has been the case. Starting with Intrepid though it got particularly bad; my wifi light would be off even when the switch was on. If I turn it off and on again, the light will flicker on and then off again. No wireless at all.

---

### Post by jbernardo on 2009-02-25
To have something close to the (already slow) intel X performance in intrepid, you have to turn on UXA. There is already a uxa intel thread [here]("http://ubuntuforums.org/showthread.php?p=6668996"). But intel developers seem to have thrown out the baby with the bathwater - deprecated a working architecture in favor of one that doesn't work properly yet and has yet to reach the same level of performance, let alone surpass it.

---

### Post by cl333r on 2009-02-25
> **jbernardo said:**
> To have something close to the (already slow) intel X performance in intrepid, you have to turn on UXA. There is already a uxa intel thread [here]("http://ubuntuforums.org/showthread.php?p=6668996"). But intel developers seem to have thrown out the baby with the bathwater - deprecated a working architecture in favor of one that doesn't work properly yet and has yet to reach the same level of performance, let alone surpass it.

The Intel GPU speed on Linux is very bad and has always been afaik. A year ago I had my computer at work dual booting ubuntu feisty and xp, I have to say XP felt like 500% snappier, no joking and no overreacting, really. Since then I have remembered the golden rule: if you have Linux you better have a nvidia card, yes it's the most closed source one, but it gives you least head aches (if any at all).

---

### Post by darksideforge on 2009-02-25
I don't know if it's my xorg or my video card or what, but my new install of Ultimate Edition 2.0 on top of Jaunty isn't working very well. :(  I haven't had a chance to do much debugging, but right now I've switched to an xfce session just so i can access my email and the web.

---

### Post by jamaisvu on 2009-02-27
> **darksideforge said:**
> First of all, I upgraded 8.10 to 9.04 on a lark...I'm really not good enough with Linux to be a tester or to know what to report or how. But here are two major observations I have:

1) After 5 months of trying every "fix" known to mankind, all to no avail, to get my Atheros wifi to work in Intrepid, imagine my surprise and delight when I upgraded to Jaunty and disconnected my CAT5 cable last night in preparation to shut down and VOILA! my Toshiba Satellite auto-connected to my open wireless three rooms away!!!  I delayed shutting down for another hour while I played around and surfed the 'net. GREAT JOB DEVELOPERS!!!

Thank you! +1 :D:D:D (Maybe it was a kernel thing -- 2.6.27.10 and 11 seemed to be disasters for me...)

---

### Post by mariner09 on 2009-02-28
Define slow???

I have the Intel chipset on my T61 and I've not seem any performance issues.  Jaunty is the fastest thing I've tried yet.  I'm not a gamer at all, so if it's 3D you're talking about, I wouldn't know...

---

### Post by jbernardo on 2009-03-02
3D is awfully slow and has been slowing since Hardy. I'm not that much of a gamer too, but I noticed first with compiz and now with kde 4.2 that the driver is slower every new release.

---

### Post by scaine on 2009-03-02
I'm really surprised to hear these views on Intel.  I'm using a Toshiba U400 with Intel (GMA4500 I think) and the compiz effects on this laptop are superb.  Jaunty is easily the snappiest, most responsive O/S I've used yet.  Faster, even, than my main PC up the stairs which uses a Raptor hard disk and Nvidia 6800GTX.

Even Docky is ultra smooth.  The whole experience is ultra smooth.  The laptop boots from grub count down to fully working (auto-logged in) desktop in around 40 seconds.  USplash is onscreen for only about 10 seconds...

I haven't changed any configurations, such as UXA - all I've done is what I always do : turn on compiz, install Thunderbird, install Shiki theme and restore my firefox extensions/history/bookmarks with FEBE.  Certainly no low-level stuff, that's for sure.

---

