---
title: "Kernel 2.6.27-6 - How is it working?"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ghindo on 2008-10-07
How is the new kernel working for everybody?

---

### Post by executor on 2008-10-07
so far so good

---

### Post by xebian on 2008-10-07
Not good for me.  177.78 won't install so I'm back to 27-5 which is so far  the best for KDE4

---

### Post by phoenix_snake on 2008-10-07
it works well on my laptop so far....

---

### Post by jfernyhough on 2008-10-07
Fine on my Acer, as far as I can tell. No sound issues, no Nvidia 177.76 issues, no wireless issues, no GNOME issues.

Kind of odd I haven't reinstalled since Alpha 6...

---

### Post by deadite66 on 2008-10-07
1st boot it stalled, 2nd boot it loaded fine.

---

### Post by plun on 2008-10-07
Everything seems to be up and running...:)

---

### Post by deflagmator on 2008-10-07
I had one big problem 

[https://bugs.launchpad.net/ubuntu/+bug/279693]("https://bugs.launchpad.net/ubuntu/+bug/279693")

Can anyone help me?
:(

---

### Post by gwenn on 2008-10-07
Good for me

---

### Post by dabl on 2008-10-07
> **deflagmator said:**
> I had one big problem 

[https://bugs.launchpad.net/ubuntu/+bug/279693]("https://bugs.launchpad.net/ubuntu/+bug/279693")

Can anyone help me?
:(


Prolly not  :(

But what is the model of that Maxtor drive, and what motherboard is it on?  (he asks nervously ...)

---

### Post by roberthr on 2008-10-07
Not good! It kicks me in busybox, the same as it was with 2.6.27-5

---

### Post by FuturePilot on 2008-10-07
Seems to be fine here.

---

### Post by roberthr on 2008-10-07
It looks like there is a problem if system has more than one hard drive.

---

### Post by xebian on 2008-10-07
Just got the NV 177.80 final release, and it's awesome.  :guitar:

---

### Post by ghindo on 2008-10-07
> **deadite66 said:**
> 1st boot it stalled, 2nd boot it loaded fine.Ditto for me.  All's well now, it seems :)

---

### Post by Vwracer69 on 2008-10-08
:lolflag: I also had the issue with the 2.6.27-6 update problem. My laptop does have 2 hard drives. Everything worked fine in 2.6.27-4 and -5.

what i did to be able to boot was to change my bios settings from AHCI to IDE. hope that helps. :guitar:

---

### Post by olavjunior on 2008-10-08
The kernel works like a charm here! No problems so far! (Toshiba U400)

---

### Post by crazypenguin2008 on 2008-10-08
no dice here. lost wireless and the ability to configure a wireless network. clean install on a 500gd western hdd. i did the updates as they came in. wireless worked great untill i updated yesterday. verry disapointing to say the least. if anyone knows how to get wireless back please let me know.

---

### Post by rbmorse on 2008-10-08
> **roberthr said:**
> It looks like there is a problem if system has more than one hard drive.

Has to be something else. I have four internal and two external/USB drives on this box and -27 works fine. 

Is your system SATA/IDE mixed?

---

### Post by JacquiOh on 2008-10-08
I still have to use the 2.6.24 to have wireless  working. 

I'm worried it's going to disappear and I'll be stuck having to reinstall Hardy.

---

### Post by MacUntu on 2008-10-08
No problems here (iwl3945, sata).

---

### Post by ger_macaco on 2008-10-08
Had problems here.
First, after restart using this version got this message:

"Not starting K Display Manager (kdm-kde4); it is not the default display manager"

Checked /etc/X11/default-display-manager content and it was OK: "/usr/bin/kdm"

Afterwards, I restarted using the recovery mode. Did a Xorg reconfig and could load KDE4. However, I have to adjust my monitor because the image does not cover all of it (don't know if I'm explaining myself correctly).
Also, some flashes of black horizontal lines (1px height) appear when I press a key on my keyboard.

Tried to reconfigure NVidia settings but it tells me that I am not using NVidia drivers. So I tried 'nvidia-xconfig', which led me back to kdm not starting.

I'm back to 2.6.27-5.

---

### Post by AlexBellisBrown on 2008-10-08
I got myself a "Kernel panic". Reinstalled hardy and decided to wait a little longer. :)

---

### Post by mcgoochen on 2008-10-08
works on my laptop (msi VR 201) when plugged in. when running on battery every second boot stucks during "loading hardware drivers"  :(

---

### Post by douham on 2008-10-08
> **roberthr said:**
> It looks like there is a problem if system has more than one hard drive.

Ibex ..27-6 seems to be really touchy with multiple drives if BIOS settings are not correct[QUOTE=douham;5932856] I suggest consulting your m/b manual and your current Bios with regards to the way drives are set up. DONT change things willy nilly in Bios if you are uncomfortable with doing so and stay with ..27-5 or Hardy

---

### Post by vraicovi on 2008-10-09
So far, ok.  I rebooted this morning and my machine was a bit sluggish compared to Hardy.  I updated to the new NVIDIA drivers tonight and it's night and day.

However, I have a weird issue that seemed to have developed with 2.6.27-6.  In the taskbar, it's telling me that my wired network is disabled and it's not.  When I start Firefox, it keeps coming up offline.

Other than that, I can't wait for the final...

---

### Post by ronacc on 2008-10-09
all ok here amd64 and nvidia 177.80

---

### Post by ktraub on 2008-10-09
2.6.27-6 is still slower than 2.6.24 for me and I've noticed they keep messing with the HAL. Latest HAL is better but still slower than 2.6.24.
Also, 2.6.27-6 (and .5 and .4 before it) hang 2 out of 3 times on boot when loading drivers and especially when it tries to set the clock. 
2.6.24 Boots every time BTW.

I'm running a Dell Inspiron 9400 with Intel 945GM & WUXGA video, Intel Core2 T7400 CPU,Intel 3945 Wifi with SATA WDC WD2500BEAS HDD.

-Kev
:(

---

### Post by Ub1476 on 2008-10-09
It fixed my hibernate problem with intel x4500, but the res is still 1024x768 on login, even though I fixed it myself for the desktop. Wireless is still not working, it's atheros..

---

### Post by gcday on 2008-10-09
Runs fine - still no support for my Ovation MC930D usb 3g modem - which is a bit of a deal-breaker (sadly).

---

### Post by Eddy Timmermans on 2008-10-09
Flash has no sound. Tried to reinstall flashplugin-nonfree. Didn't work. Other sound works fine. Didn't have this problem with 2.6.27-5.

---

### Post by patrickfromspain on 2008-10-09
works as fine as 27-4 and 27-5

---

### Post by Gedemins on 2008-10-09
flash has no sound, and quite often only gray screen appears.
compiz doesnt work anymore (on native video drvers), but it worked before..

---

### Post by SwornPacifist on 2008-10-09
Having compiz and Atheros issues on my laptop after updating to 6, booting into 4 and everything works fine.

---

### Post by JacquiOh on 2008-10-11
Latest Updates have fixed my wireless (broadcom)... it works better than ever! Great signal strength, quick connection.

Still waiting for new Nvidia drivers, both 177 and 173 break everything. Compiz not working either.

---

### Post by TheBigT on 2008-10-11
Kernel works for me, including compiz.
But I can't run any QT apps ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501125](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501125)), the media playback is a bit jerky and sometimes the (wired) network doesn't come up without a reboot.

---

### Post by paxmark1 on 2008-10-11
Kubuntu.  The entire screen will sometimes go to black for less than 500ms, usually when scrolling in firefox, opera, or konsole.

And after about the first 15 key strokes after rebooting, a skinny 2 or 3 mc line appears starting on the left boundary (desktop or whatever program is (It went black again, it also does it after typing a bunch) on the left margin.  It appears at random vertical positions.  

It has been this way since the update to beta.  I add Xorg.logs and kdm logs to the launchpad bug for it.  

I am also disappointed that the RT73 usb wireless does not work out of the box.  They have had source code out for a long time, and they targeted the Hawking USB with the little antenna at linux users.  I know how to fix, I have to go serial monkey web site and then do some blacklisting, etc.  Sigh.

Other than that, much slower than I like.  When it all gets sorted out, I will probably do a fresh install of ubuntu server and numerous applications of aptitude to keep a newish kernel and Xorg and good old KDE 3.5.10 on this old machine.  

But no show stoppers for me, no dpkg - configue a, hanging installations, or those sorts of things.  Works well enough except for the flashing bar whenever I type or spacebar                                

peace mark

---

### Post by caryb on 2008-10-11
For me it's not! that's because I'm running 2.6.27-7:lolflag:


Cary

---

