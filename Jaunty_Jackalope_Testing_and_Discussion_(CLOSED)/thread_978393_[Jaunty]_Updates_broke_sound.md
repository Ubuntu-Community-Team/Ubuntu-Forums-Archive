---
title: "[Jaunty] Updates broke sound"
date: 2008-11-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-11
It seems last nights updates have broken sound on my PC. If I click on the speaker icon I get "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured."  If I then go to Sound settings top three settings are set to autodetect and capture is set to ALSA. If I clcik on Test I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument".
After that I can't close the Sound Preferences Window (have to do a reboot).
Audio is nVidia Corporation CK804 AC'97 Audio Controller (rev a2).

---

### Post by ronacc on 2008-11-11
file a bug on it and I'll confirm , I have the same situation here except that I can close the sound prefs window without reboot.

---

### Post by Kevbert on 2008-11-11
Thanks ronacc. The bug report is [#296738]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/296738").  Since the initial error occurred something has been changed (in this mornings' updates), but still no sound. It's looks like someone is working on sound drivers...

---

### Post by ronacc on 2008-11-11
confirmed and added comment . I wouldn't worry too much they borked sound early on in intrepid too .

---

### Post by Kevbert on 2008-11-11
Sound is now working again. Found sound settings in volume control set to minimum (after update ?) Set to mid-range and they're working again.

---

### Post by danf_1979 on 2008-11-11
Maybe "hal" was guilty?

---

### Post by ronacc on 2008-11-11
just updated a few minutes ago ( 15:30 eastcoast US ) and my sound is still fubar .

---

### Post by MaX on 2008-11-22
My sound works for like 30 minutes at a time, then I have to starte pulseaudio again...

This is what happens:
```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
N: module-alsa-sink.c: Increasing wakeup watermark to 36,75 ms
N: module-alsa-sink.c: Increasing wakeup watermark to 73,50 ms
N: module-alsa-sink.c: Increasing wakeup watermark to 147,00 ms
N: module-alsa-sink.c: Increasing wakeup watermark to 177,00 ms
Soft CPU time limit exhausted, terminating.
E: cpulimit.c: Recevied request to terminate due to CPU overload.

```

---

### Post by BwackNinja on 2008-11-23
Yup, mine dies like that too.

---

### Post by plun on 2008-11-23
From PAs mailing list:

> If you are using 0.9.13 please make sure you are using:

  1) All the patches included in the Fedora package (all backports from git master)

  2) The latest alsa-plugins package (and alsa-lib and drivers too!)

If things are still wrong, please let us know :)

Col

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-November/002632.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-November/002632.html)



Luke must have seen this....:confused:

(GIT works perfect now)  

I filed bugs during Intrepid but it was no interrest about it...

---

### Post by theozzlives on 2008-11-23
just upgraded my laptop with 64... no sound and Amarok will not load

---

### Post by ronacc on 2008-11-23
open your volume control and unmute your side , center and front they muter at every reboot that should get you sound , if not check the threads in this fourum about sound pulse is having problems right now , run amorok from a term to see why its not loading .

---

### Post by jmdsdf on 2008-11-23
Try running the command "amarokapp" from the terminal... and you may find a bug like this: 

amarokapp: symbol lookup error: /usr/lib/libkhtml.so.4: undefined symbol: _ZN3KJS9ObjectImp4markEv

Which is reported here:

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/301109](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/301109)

Apparently rolling back kdelibs to Intrepid's version is the solution for now, but I am lost as to how to do that...

---

### Post by ronacc on 2008-11-23
if you updated from intrepid you may have the deb for the intrepid version still in /var/cache/apt/archives .

---

### Post by jmdsdf on 2008-11-24
I only have kdelibs_4%3a3.5.10.dfsg.1-1ubuntu4_all.deb in /var/cache/apt/archives/ (the Jaunty version), I installed Intrepid off of CD, so they're not cached. I figure I need kdelibs_3.5.10-0ubuntu6_all.deb. I downloaded it from here:

[http://packages.ubuntu.com/intrepid/all/kdelibs/download](http://packages.ubuntu.com/intrepid/all/kdelibs/download)

but... dpkg -i kdelibs_3.5.10-0ubuntu6_all.deb doesn't downgrade the dependencies... what really obvious thing am I missing? :)

**SOLVED:**

The needed dependency to fix the problem is kdelibs4c2a_3.5.10-0ubuntu6_i386.deb

[http://packages.ubuntu.com/intrepid/i386/kdelibs4c2a/download](http://packages.ubuntu.com/intrepid/i386/kdelibs4c2a/download)

Once installed, Amarok will work again. Now I understand the term "dependency hell".

---

### Post by theozzlives on 2008-11-24
After the wireless NIC probs I had with the Intrepid Alphas, I swore I'd wait til April.... hmmmmmmm

---

### Post by theozzlives on 2008-11-24
> **ronacc said:**
> open your volume control and unmute your side , center and front they muter at every reboot that should get you sound , if not check the threads in this fourum about sound pulse is having problems right now , run amorok from a term to see why its not loading .

That's not good, my laptop is the only computer I shutdown.

---

