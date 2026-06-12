---
title: "Problems with Network on Intel PRO/Wireless 3945ABG"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by flowbot on 2008-09-30
I've recently installed Intrepid Ibex Alpha 6, and have applied all updates. My problem is with my wireless card, Intel Pro/Wireless 3945ABG, using driver iwl3945, which has a VERY UNRELIABLE connection. It can take minutes for a website to load properly, if it loads at all. Ubuntu Forums seems to be mostly okay, if a bit slow, while sites such as [www.smh.com.au](www.smh.com.au) are apt not to load at all. Speaking of apt - Synaptic will take *ages* to refresh the repositories and/or download packages. Basically, anything requiring a network connection is slow and intermittent.

To test if it was a problem with my network or Ibex, I fired up a Hardy Heron live cd - no problems at all ... all webpages and repositories load as quickly as they should. I also tested wired and wireless connections from other systems on my network - all worked fine.

Have any other users of the iwl3945 driver run into similar problems, and are there any workarounds?

---

### Post by jfernyhough on 2008-09-30
I'm not sure this is anything to do with the Intel chipset - I have the same card and it seems to work fine. I am, however, using the NetworkManager 0.7 PPA. I'd put this down to NM0.7.

---

### Post by ketk on 2008-09-30
For me is working much better since I'm on intrepid.
NetworkManager 0.7.0
Driver iwl3945
Much better means that connexions are faster (connecting) than hardy and can connect further.

---

### Post by klange on 2008-09-30
iwl3945 sucks. Period.
It is a bit better on Intrepid than on Hardy, though, as various bugs have been fixed, however, overall, it still sucks.

The list of problems is everything from poor connection quality to complete system crashes while on WiFi. I constantly get system freezes that will last until I supply some form of input (poke my touchpad, press a key, etc.), but I've also had complete lockups.

And you know what? I never had a single issue back with the old IPW drivers.

---

### Post by flowbot on 2008-10-12
adding the ppa repo did it for me, cheers ... though there's been quite a few updates to network-manager since then, so i'm not sure if it's still necessary.

---

### Post by MacUntu on 2008-10-12
> **WindowsSucks said:**
> I never had a single issue back with the old IPW drivers.

I never had a single issue with the new iwl drivers. Period. ;)

Maybe this shows that it's not as trivial as many think to make networking work flawlessly.

---

### Post by mykrob on 2008-10-13
> **flowbot said:**
> adding the ppa repo did it for me, cheers ... though there's been quite a few updates to network-manager since then, so i'm not sure if it's still necessary.

what is the ppa repository that you added? My intel 3945abg will connect fine, but it "hiccups" regularly, at which point my mouse and keyboard stall for a few seconds, then kick back in. Very annoying. If i use my Belkin USB wifi, this problem doesnt occur.

---

### Post by pedrogfrancisco on 2008-10-21
I'd say its NetworkManager's fault... Though I 'only' had 3 crashes, they all were while using NetworkManager; using wpa_supplicant yelds absolutely no issues...

---

### Post by jfernyhough on 2008-10-21
> **mykrob said:**
> what is the ppa repository that you added? 

## NM 0.7
deb [http://ppa.launchpad.net/network-manager/ubuntu/](http://ppa.launchpad.net/network-manager/ubuntu/) intrepid main
# deb-src [http://ppa.launchpad.net/network-manager/ubuntu/](http://ppa.launchpad.net/network-manager/ubuntu/) intrepid main

Though I warn you, this will most likely bork your install.

It hasn't had any ill effects on mine (recently), but if you go in thinking you'll need to reinstall you should be in the right frame of mind for using NM0.7 from SVN builds. :D

---

