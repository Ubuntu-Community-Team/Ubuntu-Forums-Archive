---
title: "Wireless Inconsistency (wl Driver w/ BC4312) - Jaunty and now Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sanskaras on 2009-10-26
My wireless tends to stall or hang often.  During downloads it'll just stop or when I click a link the browser will just hang.  It appears to be random and happens on my wpa network at home and the encrypted wpa network at school.

It started when I upgraded to jaunty.  I tried wicd and that didn't change anything.

Now I'm running karmic beta (hoped that would fix it), but it didn't..

Heres some info:
Broadcom Corporation BCM4312 802.11b/g (rev 01) with the wl driver.

The last time this happened on karmic, the speed under network manager dropped to 1Mb/s and I had to restart networking to get my Internet working again.  It's been getting annoying, especially when doing research for papers.

Anyone have any ideas besides downgrading to hardy or windows 7? lol

---

### Post by sanskaras on 2009-10-27
Bump! Just did the good ole stall while a couple times today already, this time connection speed has remained unchanged though.

---

### Post by sanskaras on 2009-10-28
Daily bump.

I've read this can be fixed by the use of something called backports?  Or this might be a dns resolution problem?

---

### Post by Saghaulor on 2009-10-28
Have you tried checking ```
dmesg
``` for any clues? I was having issues with the driver to my wifi card and network manager. I had to uninstall network mananger and create startup scripts to automatically connect. 

I discovered the problem with ```
dmesg
```as there were references listed that indicated the driver module was not loading.

It's a thought.

Also,what do you mean, an unencrypted WPA connection? WPA is encryption. Have you had issues while connected to any unencrypted wireless?

Also, you could try checking your logs for issues. However, I'm not sure what you should be explicitly looking for. I'd start by trying to find any references to your wifi drivers.

---

### Post by sanskaras on 2009-10-28
Well I found a bunch of this in dmesg -

```
Oct 28 16:11:43 nick-laptop kernel: [77147.170029] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:44 nick-laptop kernel: [77148.024238] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:45 nick-laptop kernel: [77149.217887] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:46 nick-laptop kernel: [77150.139690] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:49 nick-laptop kernel: [77153.007733] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:50 nick-laptop kernel: [77154.030777] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:51 nick-laptop kernel: [77154.952582] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:52 nick-laptop kernel: [77155.976185] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:11:54 nick-laptop kernel: [77158.024176] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:12:06 nick-laptop kernel: [77169.902635] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:12:07 nick-laptop kernel: [77170.926521] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:07 nick-laptop kernel: [77231.136741] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:08 nick-laptop kernel: [77232.161091] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:09 nick-laptop kernel: [77233.185442] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:10 nick-laptop kernel: [77234.209054] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:11 nick-laptop kernel: [77235.130647] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:12 nick-laptop kernel: [77236.154395] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:19 nick-laptop kernel: [77242.650261] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:20 nick-laptop kernel: [77243.649980] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:21 nick-laptop kernel: [77244.650088] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:22 nick-laptop kernel: [77245.779864] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:23 nick-laptop kernel: [77246.649717] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:24 nick-laptop kernel: [77247.827935] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:25 nick-laptop kernel: [77248.852167] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:26 nick-laptop kernel: [77249.773398] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:27 nick-laptop kernel: [77250.797399] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:28 nick-laptop kernel: [77251.663098] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:29 nick-laptop kernel: [77252.845465] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:30 nick-laptop kernel: [77253.767214] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:32 nick-laptop kernel: [77256.533607] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:33 nick-laptop kernel: [77257.556208] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:34 nick-laptop kernel: [77258.477577] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:35 nick-laptop kernel: [77259.351564] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 16:13:36 nick-laptop kernel: [77260.351385] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
```

I don't have time to google what TKIP means at the moment, have to run to class.  But, I guess by encrypted wpa I meant secured wpa, and I've only used wpa networks.

How to I check the logs?

---

### Post by Saghaulor on 2009-10-28
In Ubuntu (gnome) go to System->Administration->Log File Viewer

I'm not sure if I stated it clearly though, you should check dmesg when the connection is crapping out on you.

---

### Post by nanog on 2009-10-28
[http://www.google.com/products?q=3945ABG&hl=en&aq=f](http://www.google.com/products?q=3945ABG&hl=en&aq=f)

---

### Post by Saghaulor on 2009-10-28
> **nanog said:**
> [http://www.google.com/products?q=3945ABG&hl=en&aq=f](http://www.google.com/products?q=3945ABG&hl=en&aq=f)

I'm not sure how that is useful.

---

### Post by sanskaras on 2009-10-28
K so I watched the syslog while the connection craps out -

It repeats the 
```
Oct 28 18:05:19 nick-laptop kernel: [83963.126777] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
```
over and over while I'm waiting for a page to load.  This error never comes up when the connection is working and stops once I finally get a page to load.  It's pretty random many times the error shows up before the connection works again.  Oh and once in awhile a
```
Oct 28 18:09:19 nick-laptop wpa_supplicant[1323]: CTRL-EVENT-SCAN-RESULTS 
``` is thrown in there

---------------------

For example:

I click a link -
The syslog goes through these
```
Oct 28 18:11:07 nick-laptop kernel: [84311.282110] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:08 nick-laptop kernel: [84312.305711] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:09 nick-laptop kernel: [84313.325053] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:10 nick-laptop kernel: [84314.353683] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:11 nick-laptop kernel: [84315.275275] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:12 nick-laptop kernel: [84316.299369] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:16 nick-laptop kernel: [84319.576291] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:17 nick-laptop kernel: [84320.600026] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:18 nick-laptop kernel: [84321.623995] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:18 nick-laptop kernel: [84322.546019] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:19 nick-laptop wpa_supplicant[1323]: CTRL-EVENT-SCAN-RESULTS 
Oct 28 18:11:19 nick-laptop kernel: [84323.570580] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:23 nick-laptop kernel: [84326.816184] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:24 nick-laptop kernel: [84327.768038] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:25 nick-laptop kernel: [84328.792022] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:26 nick-laptop kernel: [84329.816075] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:27 nick-laptop kernel: [84330.839994] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:28 nick-laptop kernel: [84331.662867] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:31 nick-laptop kernel: [84335.345517] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:32 nick-laptop kernel: [84336.369391] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:33 nick-laptop kernel: [84337.393652] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:34 nick-laptop kernel: [84338.417585] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:35 nick-laptop kernel: [84339.339073] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:36 nick-laptop kernel: [84340.363059] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:38 nick-laptop kernel: [84342.308711] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:39 nick-laptop kernel: [84343.332623] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:40 nick-laptop kernel: [84344.356615] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:41 nick-laptop kernel: [84345.278183] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:42 nick-laptop kernel: [84346.302215] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:43 nick-laptop kernel: [84347.326161] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:48 nick-laptop kernel: [84352.548375] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:49 nick-laptop kernel: [84353.572331] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:50 nick-laptop kernel: [84354.494140] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:51 nick-laptop kernel: [84355.518564] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:52 nick-laptop kernel: [84356.542034] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
```

Then after the last error the page started to load - I had to wait from 18:11:07 to 18:11:52.  Sometimes it's only a couple seconds and sometimes it's long enough to make the browser timeout.

Guess I'll look into what TKIP means.  Is there anyway to find out what program/module er whatever writes that error to the log?  Or is that a driver error?  Not quite sure how to read these.
.

---

### Post by Saghaulor on 2009-10-28
> **sanskaras said:**
> K so I watched the syslog while the connection craps out -

It repeats the 
```
Oct 28 18:05:19 nick-laptop kernel: [83963.126777] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
```
over and over while I'm waiting for a page to load.  This error never comes up when the connection is working and stops once I finally get a page to load.  It's pretty random many times the error shows up before the connection works again.  Oh and once in awhile a
```
Oct 28 18:09:19 nick-laptop wpa_supplicant[1323]: CTRL-EVENT-SCAN-RESULTS 
``` is thrown in there

---------------------

For example:

I click a link -
The syslog goes through these
```
Oct 28 18:11:07 nick-laptop kernel: [84311.282110] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:08 nick-laptop kernel: [84312.305711] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:09 nick-laptop kernel: [84313.325053] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:10 nick-laptop kernel: [84314.353683] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:11 nick-laptop kernel: [84315.275275] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:12 nick-laptop kernel: [84316.299369] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:16 nick-laptop kernel: [84319.576291] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:17 nick-laptop kernel: [84320.600026] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:18 nick-laptop kernel: [84321.623995] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:18 nick-laptop kernel: [84322.546019] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:19 nick-laptop wpa_supplicant[1323]: CTRL-EVENT-SCAN-RESULTS 
Oct 28 18:11:19 nick-laptop kernel: [84323.570580] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:23 nick-laptop kernel: [84326.816184] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:24 nick-laptop kernel: [84327.768038] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:25 nick-laptop kernel: [84328.792022] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:26 nick-laptop kernel: [84329.816075] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:27 nick-laptop kernel: [84330.839994] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:28 nick-laptop kernel: [84331.662867] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:31 nick-laptop kernel: [84335.345517] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:32 nick-laptop kernel: [84336.369391] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:33 nick-laptop kernel: [84337.393652] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:34 nick-laptop kernel: [84338.417585] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:35 nick-laptop kernel: [84339.339073] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:36 nick-laptop kernel: [84340.363059] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:38 nick-laptop kernel: [84342.308711] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:39 nick-laptop kernel: [84343.332623] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:40 nick-laptop kernel: [84344.356615] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:41 nick-laptop kernel: [84345.278183] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:42 nick-laptop kernel: [84346.302215] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:43 nick-laptop kernel: [84347.326161] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:48 nick-laptop kernel: [84352.548375] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:49 nick-laptop kernel: [84353.572331] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:50 nick-laptop kernel: [84354.494140] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:51 nick-laptop kernel: [84355.518564] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
Oct 28 18:11:52 nick-laptop kernel: [84356.542034] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f3d52000
```

Then after the last error the page started to load - I had to wait from 18:11:07 to 18:11:52.  Sometimes it's only a couple seconds and sometimes it's long enough to make the browser timeout.

Guess I'll look into what TKIP means.  Is there anyway to find out what program/module er whatever writes that error to the log?  Or is that a driver error?  Not quite sure how to read these.
.

TKIP is the encryption type in WPA.

One would assume that's a message indicating a key exchange.

Do you have this issue on networks that are unencrypted or on WEP networks?

---

