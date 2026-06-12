---
title: "Several (nice to have) things not working with Ubuntu 17.04 on HP EliteBook X360"
date: 2017-05-16
forum: Installation &amp; Upgrades
---

### Post by gnumarco on 2017-05-16
I have just installed Ubuntu 17.04 on my new EliteBook X360.
The machine has an Intel(R) Core(TM) i7-7600U CPU @ 2.80GHz, 16GB RAM, full HD touch screen, fingerprint sensor, IR camera capable of facial recognition login, WWAN...and I use it with a HP USB-C docking station (DisplayLink for the external monitor)
Out of the box, the machine is usable, and some things of the docking station are recognized, which is a good thing, but:
- the fingerprint sensor is not recognized
- the wecbam works but not the IR facial recognition functions.
- Even after installing the latest DisplayLink drivers, the external monitor doesn't work.
- No automatic rotation of the screen (this is a laptop with a 360 degrees screen that can be used as a tablet etc...)
- No multitouch gestures by default on the touchpad

What makes me sad, apart from those pieces of hardware that doesn't work, is that I do not get even remotely close to the working comfort I have using this laptop with Windows 10. Actually, without some of these functionalities (external monitor, screen rotation+tablet mode), this laptop is useless to me under Ubuntu and I just have to switch back to Windows, and I am not happy with it: I am a 20 years long Linux user...

Anyone has experience with this machine, or similar machines? Any solutions?

Thanks!

---

### Post by vasa1 on 2017-05-16
What does HP say? Did they say the features you listed would be available on when running Linux?

I would really be nice if stores at least had live USBs for customers to try out before deciding.

---

### Post by gnumarco on 2017-05-16
HP said nothing, I found no information about this laptop and Ubuntu.
Testing it in a store was not an option: this is a laptop I bought from the HP online store for work, I basically had to choose this model, and I use it mainly with Windows at work. I wanted to give a try to Ubuntu, see if I could do part of the work with it. Seems that up to now it is not really the case.
Update: after tweaking a bit, the external display works using DisplayLink.

I am just a bit disappointed that there is not that much support for the high end professional laptop from HP.

---

### Post by mörgæs on 2017-05-18
New hardware is sometimes a problem for GNU/Linux. The hardware vendors cooperate with Microsoft before release in order to get support for all functions but the free software developers don't get an early warning about which hardware is coming up. This means that support might be lagging a release. 

There are exceptions, though. The [certified hardware list]("https://certification.ubuntu.com/") shows what is expected to work from first day.

---

### Post by gnumarco on 2017-05-18
Yes, I totally understand that, and I do realize that new hardware might take some time to be supported. But, for example, for the so called "tablet mode" (touchpad and keyboard disabling) and screen rotation, my laptop isn't the only one and the newest to be able to do this, and I was not able to found any information about how Ubuntu could support this (did I miss something?)...or maybe the sensors from the display's orientation and laptop orientation actually have to work to trigger something in the OS behaviour?

---

### Post by treepleks on 2017-07-30
> **gnumarco said:**
> Yes, I totally understand that, and I do realize that new hardware might take some time to be supported. But, for example, for the so called "tablet mode" (touchpad and keyboard disabling) and screen rotation, my laptop isn't the only one and the newest to be able to do this, and I was not able to found any information about how Ubuntu could support this (did I miss something?)...or maybe the sensors from the display's orientation and laptop orientation actually have to work to trigger something in the OS behaviour?

Dear Gnumarco,

Did you made any progress here ? I just got the very same elitebook as you, same configuration (except for WWAN which I did not want). I now have the automatic screen rotation working (under gnome-shell). The problem was a bug in the default Ubuntu kernel: the hid sensors do not work (with iio-proxy, the monitor-sensor app does not show changes). I installed the latest stable kernel (4.12.3) and the problem disappeared (had to update the i915 firmware too). The fingerprint sensor is  still inaccessible and I have the wifi key (F11) that apparently generate pairs of events so that it turns off and on back immediately when I hit it. I noticed that by blacklisting the hp_wireless module it works fine but the led remains orange in all cases (even with wifi on). I would love to find what other peice of software listent o the key and generates the rfkill.

The IR camera works fine but of course, no facial recognition as in Hello in Windows 10. 

So, not perfect but quite usable and much better than my MacBook Air 2011. I love being able to annotate PDFs with the pen using xournal.

---

### Post by gnumarco on 2017-07-31
Hi Treepleks.
Unfortunately, I did not dig more into this things, as for work I had to use Windows 10.
That is quite a thing that you managed to get the automatic screen rotation!
For now, I will not spend more time on it as it is very unlikely that we manage to ge the level of integration that Windows 10 has with this laptop using Ubuntu (tablet mode, facial recognition, fingerprint sensor, very poor integration of the displaylink driver, drawing functions using the pen, etc...). This hurts my heart as I write it because I am a lifetime Linux/Ubuntu user...
Maybe in the future Ubuntu will make things work for such laptops... (professional line, so some effort should be put on this so that we could really rely on this hardware+ubuntu to work).
I do agree though that this hardware is much better than a MacBook (I have a MB Pro 13'' 16GB RAM and 500 SSD, but not the new one with the fancy oled touchbar ;) ) for the price!

---

### Post by ninthdimension on 2017-08-11
> [COLOR=#000000]it is very unlikely that we manage to ge the level of integration that Windows 10 has with this laptop using Ubuntu (tablet mode, facial recognition, fingerprint sensor, very poor integration of the displaylink driver, drawing functions using the pen, etc...)[/COLOR]

I am interested in getting a 2-in-1 laptop/tablet for work.

I currently use a Dell M3800 with Ubuntu 16.04. It's a fully loaded power beast and I like it very much. The major shortcoming is that it's large and fairly heavy to lug around every day. Also I'd like to be able to read A4 journal articles on the subway and annotate them with a stylus. I'll probably leave the Dell at home or work and only use it for heavier computing loads.

As it is, my Dell doesn't have multi touch gesture support (even though I tried to install touchegg), and since some update it hasn't been able to use DisplayLink multi monitors (although it could at one point in its life!). So I'm not terribly fussy about this functionality. I also don't care about biometric login. Auto-rotation would be nice in tablet mode.

How would you recommend the Elitebook x360 for my purposes?

---

### Post by Frogs Hair on 2017-08-11
> [COLOR=#000000]Anyone has experience with this machine, or similar machines? Any solutions?[/COLOR] I have an older EliteBook and security tools including fingerprint reader and facial recognition don't function in Linux. The software for these features is/was Windows only and when my computer was built these were known as HP tools and included drive encryption, bios, and pre-boot security  .

---

### Post by mdayan-comp on 2017-09-22
Great thread! 

I was wondering if anyone could run Ubuntu inside a virtual machine on the HP EliteBook X360 (G2 1030)?  

Also could anyone use successfully multi-touch and/or the stylus/active pen in Ubuntu?

---

### Post by tokyobadger on 2017-09-22
> **vasa1 said:**
> What does HP say? Did they say the features you listed would be available on when running Linux?

I would really be nice if stores at least had live USBs for customers to try out before deciding.

HP appears to say that NeoKylin Linux 64 is a pre-installed option [http://h20195.www2.hp.com/v2/getpdf.aspx/c05275190.pdf?ver=6](http://h20195.www2.hp.com/v2/getpdf.aspx/c05275190.pdf?ver=6) (full url for transparency) - P5 & P6

ZDNet (Australia, published 29 Apr 2017) claims > If Windows is not your bag, HP is offering the device with FreeDOS or  NeoKylin Linux preinstalled instead, either of which I find personally  intriguing. In order to test Linux compatibility, I used a Fedora 24  Live distro and found the touchscreen, Active Pen, and everything else  with the laptop worked as it should, which was a pleasant surprise.
Full url [http://www.zdnet.com/product/hp-elitebook-x360-2017/](http://www.zdnet.com/product/hp-elitebook-x360-2017/)

Given the above I'd be interested to see if 16.04.1, 16.04.2, and/or 16.04.3 LTS releases were attempted by the OP (or others with the same device).

---

