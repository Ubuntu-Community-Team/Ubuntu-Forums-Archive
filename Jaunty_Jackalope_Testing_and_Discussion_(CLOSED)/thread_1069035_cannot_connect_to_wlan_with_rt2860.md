---
title: "cannot connect to wlan with rt2860"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by loddi on 2009-02-13
Hi everybody!

I try to use jaunty with my eeepc 901.

this has a built-in wlan card ralink rt2860. The driver must be in the kernel now, as far as i know. 
It finds my personal network, but i cannot connect to it. it uses a wpa2 key. it asked for the key when it tries to connect, i enter the key and after that nothing happens. it tries to connect for a time, and than it asks for the key again. 
i'm sure it is the right key.
has anybody similar problems or knows how to fix this?

---

### Post by Kobalt on 2009-03-16
I'm bringing this back up, I have an eeePC 901 and it uses a Ralink 2860 chipset. I have the exact same issue. Using Juanty with the latest updates, I can browse wireless networks, access a WPA network, but not a WPA2.
Any updates?

---

### Post by Skeorx13 on 2009-03-17
eee pc 1000 does this as well. (they use the same wifi card) Something with the way the driver handles wpa2 IIRC. What driver and what kernel are you running? I haven't tried it in jaunty but in intrepid I'm using adam's kernel and the latest driver in synaptic. (The number scheme is messed up, the higher number isn't the latest version. Check what synaptic says for latest version and use that one.)

---

### Post by nyarnon on 2009-03-17
Great to know I will hold back updates on my eeepc but it seems not to be only the rt2860 I just had my desktop rebooting without the wireless coming up after restarting network connections it went smooth again. Probably just the devs at work.

---

### Post by Kobalt on 2009-03-18
I'm running Jaunty with kernel 2.6.28-10.

---

### Post by taavikko on 2009-03-18
Is the driver loaded for the wlan chip, **lsmod**

Have tried **linux-backports-modules-jaunty-generic** pkg
For provided maybe better working drivers?

---

### Post by nyarnon on 2009-03-18
@kobalt

My eepc 1000h is running just fine on 28-10 and wireless is up, but indeed there is an issue with wpa2 this has nothing to do with the kernel or its modules but with the authentications used by the networkmanager. Most likely with wpasupplicant. Currently reading
[http://ubuntuforums.org/showthread.php?t=1032489](http://ubuntuforums.org/showthread.php?t=1032489)

---

### Post by Kobalt on 2009-03-18
> **nyarnon said:**
> @kobalt

My eepc 1000h is running just fine on 28-10 and wireless is up, but indeed there is an issue with wpa2 this has nothing to do with the kernel or its modules but with the authentications used by the networkmanager. Most likely with wpasupplicant. Currently reading
[http://ubuntuforums.org/showthread.php?t=1032489](http://ubuntuforums.org/showthread.php?t=1032489)

I don't know about that, using Intrepid and the Array custom kernel for eeePC, I managed to connect to my network just fine.

---

### Post by nyarnon on 2009-03-18
> **Kobalt said:**
> I don't know about that, using Intrepid and the Array custom kernel for eeePC, I managed to connect to my network just fine.

That might be but we are talking Jaunty and not Intrepid.

---

### Post by SushiR on 2009-03-18
On my 901 its working without problem. Only strange thing: I have to start a GNOME (or KDE) session to get the network starting.

---

### Post by scaine on 2009-03-19
Think this bug might be relevant - I researched this when looking into WIFI transfers gradually slowing down :
[http://ubuntuforums.org/showthread.php?t=1099916](http://ubuntuforums.org/showthread.php?t=1099916)

---

### Post by nyarnon on 2009-03-19
> **SushiR said:**
> On my 901 its working without problem. Only strange thing: I have to start a GNOME (or KDE) session to get the network starting.

Thats becouse networkmanager doesn't start before that. Under another windowmanager you have to hardcode it.

---

### Post by SushiR on 2009-03-19
> **nyarnon said:**
> Thats becouse networkmanager doesn't start before that. Under another windowmanager you have to hardcode it.

Well, I thought networking would start when the system boots, no matter if I log into a graphical session or cli. Seems that I was wrong... ;-)

---

### Post by nyarnon on 2009-03-19
Yes and I'm not in the camp of those who are supporting this setup. It's a drag if you want f.i. ssh access on a homecomputer that sometimes restart :-(

---

### Post by dirtylobster on 2009-03-27
Confirmed. I have an Eee PC 1000H and can connect to unsecured networks but not WEP or WPA. This is with Jaunty Beta. With Jaunty Alpha6 I could connect to unsecured and WEP but not WPA.

---

### Post by excogitation on 2009-04-03
same problem on a Wind U100 with RT2860

btw does bluetooth work for you?

---

### Post by tawmas on 2009-04-03
> **nyarnon said:**
> @kobalt

My eepc 1000h is running just fine on 28-10 and wireless is up, but indeed there is an issue with wpa2 this has nothing to do with the kernel or its modules but with the authentications used by the networkmanager. Most likely with wpasupplicant. Currently reading
[http://ubuntuforums.org/showthread.php?t=1032489](http://ubuntuforums.org/showthread.php?t=1032489)

I wish I could tell the same. Neither my eee 900 (which has now become my new home server) nor my eee 1000h can do wifi much well if at all. Right now, for example, my 1000h is sitting in from of the router, reporting 100% field, and still can't connect -- all with encryption disabled on the router.

I don't know if there's a bug open for that, but it surely needs to be!

---

### Post by scaine on 2009-04-03
> **excogitation said:**
> same problem on a Wind U100 with RT2860

btw does bluetooth work for you?

Is your bluetooth built-in with your Eee?  If this is the case, please confirm and add to :
[https://bugs.launchpad.net/ubuntu/+bug/347512](https://bugs.launchpad.net/ubuntu/+bug/347512)

Thanks.

---

### Post by excogitation on 2009-04-03
> **scaine said:**
> Is your bluetooth built-in with your Eee?  If this is the case, please confirm and add to :
[https://bugs.launchpad.net/ubuntu/+bug/347512](https://bugs.launchpad.net/ubuntu/+bug/347512)

Thanks.

Yes, I have bluetooth built in - but from what I see I don't have this bug.
Just found out that Fn+F11 does switch
bt & wlan on
bt & wlan off
bt off & wlan on
bt on & wlan off.
no status messages so I didn't notice before (that could be improved)

Just connecting to a WPA/WPA2 personal network doesn't work

---

### Post by tlois on 2009-04-05
Well, I can log on to my WPA encrypted network with my eee 701, but not with my eee box with rt2860 (I don't know off hand what is in the 701).  I did at first have a problem with the 701, but think by switching my router to g only from mixed it solved that one's problem.  

Still, cannot get on on the eee box with the internal wireless. Stole my husband's Linksys usb dongle for now and am able to get online, so can work...but he is going to want that back!

---

### Post by xyverz on 2009-04-06
I'm having this same problem with my MacBook Pro.  Every time I input my key, it ponders for a few seconds, then prompts again.

Sometimes I'll cancel and it'll eventually connect, but more and more it just seems to taunt me and continue prompting for a key.

I'm using Jaunty with the latest updates.

---

### Post by dtoronto on 2009-04-06
you might need to ndiswrapper your wireless card.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Reiger on 2009-04-06
No there is an open source ralink driver available. [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Anyways if the issue is not with the driver, you can always try to see if a different network management app `fixes' it? I've found network manager to be too unreliable in the past, even though they use the 'same' wpa_supplicant WICD seems to do a much better job at wireless connections.

[If it is the driver, be sure to check that your hardware signature is listed among those defined in the relevant header files: it would not be the first time Ralink drivers were a bit behind.]("http://ubuntuforums.org/showthread.php?t=1079015")

---

### Post by excogitation on 2009-04-10
> **Reiger said:**
> No there is an open source ralink driver available. [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Anyways if the issue is not with the driver, you can always try to see if a different network management app `fixes' it? I've found network manager to be too unreliable in the past, even though they use the 'same' wpa_supplicant WICD seems to do a much better job at wireless connections.

[If it is the driver, be sure to check that your hardware signature is listed among those defined in the relevant header files: it would not be the first time Ralink drivers were a bit behind.]("http://ubuntuforums.org/showthread.php?t=1079015")

The rt2680sta module comes with 9.04 (>= 2.6.28.10 I think) so you don't have to compile it from source.

Also I tried wicd but that doesn't work either.

Wireless works without encryption, but I can't connect to wpa/wpa2 secured networks.

---

### Post by Akita on 2009-04-10
WPA/WPA2 are broken in every module everybody has tried (AFAIK) since Adam's 1.7.1.1 DKMS driver. Downgrade like so:

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

2) Go to terminal, and move the pre-installed driver so it won't get loaded.

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak


3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically.

---

### Post by tawmas on 2009-04-11
> **nyarnon said:**
> Yes and I'm not in the camp of those who are supporting this setup. It's a drag if you want f.i. ssh access on a homecomputer that sometimes restart :-(

If you configure a system connection in NetworkManager, it should just work. I used to SSH a lot from my laptop to my desktop while not logged in on my desktop when I still had wireless on my laptop (EDIT: while not logged in on my desktop, I mean).

---

### Post by tawmas on 2009-04-11
> **Akita said:**
> WPA/WPA2 are broken in every module everybody has tried (AFAIK) since Adam's 1.7.1.1 DKMS driver. Downgrade like so:

Been there, done that. Didn't help much. :-(

---

### Post by excogitation on 2009-04-11
> **Akita said:**
> 
1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

4) Restart. The new driver should work automatically.
Yes it does. Nice.

Is there already a bug filed about that problem?

---

### Post by Akita on 2009-04-11
> **excogitation said:**
> Yes it does. Nice.

Is there already a bug filed about that problem?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344022")

There's a few that overlap, but that one seems to be the best fit.

---

### Post by Akita on 2009-04-11
> **tawmas said:**
> Been there, done that. Didn't help much. :-(

Are you sure that's the driver being used?

```
sudo modinfo rt2860sta
```

Should show a version of 1.7.1.1.

---

### Post by gunnar123 on 2009-04-20
This works to connect my 1000H with WPA.

But I only get 802.11g speeds.  What could cause the n performance to be lost ?  On XP I can download at an effective 50 Mbit/s (on a 100 Mbit/s internet connection) but on this driver and jaunty it's around 20 Mbit/s.

---

