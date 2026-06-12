---
title: "FSC Esprimo Mobile U9200 and Linux (and WinXP)."
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Melkekartong on 2008-01-23
Hi there.

I'm about to purchase a new laptop and I was thinking about a Fujitsu Siemens Esprimo U9200.
This laptop has both 3G modem and Fingerprint control and I'm curious on how this will work with ubuntu linux. Like with drivers and such..

It would be great if anyone of you had any experience with this model.

In advance, thanks!

---

### Post by size_XXM on 2008-02-06
HI. Any news on compatibilty?
The only thing I found was a link to contents of a german linux magazine: [http://www.linux-user.de/ausgabe/2008/02](http://www.linux-user.de/ausgabe/2008/02) (a recent issue, it seems). Anyone out there with the mag?

I'm not very keen on the 3G/fingerprint stuff - I'm more curios about non-replaceable components that could prove as show-stoppers: ACPI/chipset/graphics. If the laptop can do suspend/hibernate with (at least) 2D accelerated drivers, I'm in.

---

### Post by Melkekartong on 2008-02-12
Hi.
I've got the computer running Ubuntu now :) The worst part so far has been removing vista off the HDD. That thing has claws.

So far.. The graphic card (Intel X3100) seems to be blacklisted by compiz, but commenting out a line in the config makes it work like a charm. It's probably blacklisted because that you can't run any video applications while having fancy desktop effects turned on, but this issue is solved by switching the visual effects on/off.

I haven't tried the 3G modem yet, but rest of the functions work fine with no need to install  the drivers.

So.. I'm very satisfied with the U9200, except that the integrated speakers is the WORST EVER. Headset is a must.

---

### Post by size_XXM on 2008-02-13
Hi.
That's great news...
So the ACPI, suspend/hibernate work too?

---

### Post by Melkekartong on 2008-02-13
Hmm.. I'm not sure about the ACPI..I have no clue what ACPI is :P Hibernate works great..

How can I "test" the ACPI? :S

---

### Post by size_XXM on 2008-02-13
ACPI is responsible for modern PC's power management - if hibernate works, it means ACPI (should) work - I haven't yet tried hibernate on my desktop (no point), but suspend (to RAM) occasionally causes trouble.
ACPI in linux has been known to cause various hardware conflicts (random hangs, hardware not working, resource conflicts)... (adding 'noacpi' to bootline was a common solution I think). 
If ACPI is enabled, there will be acpi/ directory under /proc/; Type ```
cat /proc/acpi/info
```in terminal - you should get a version date or something. As to whether it works, well - if you're not having hardware/resource problems, then it obviously works ;)

Even better would be if you actually had access to thermal sensors, buttons, lid sense etc...  For example, does the screen turn off/laptop suspend when you close the lid, CPU frequency throttling when idle - this is the kind of thing that ACPI makes possible :) You may want to check what's in the acpi/ directory - some of the files can be read although only using cat in terminal (when I open them in a text editor, they are empty :( ) Where there are 'info' files, it generally means the buttton/fan whatever is recognized and supported.

---

### Post by Melkekartong on 2008-02-14
Aha. Well, the screen turns off when I close the lid, but I don't know whether this is an OS feature or integrated into the laptop.when 
Other than that, hibernate works flawlessly, BUT the computer is not always aware that it runs on batteries. The battery icon in the "tray" top right on the screen occasionally disappear, thus the computer has no idea that it runs on battery. 
I'm also not quite sure that it throttles the CPU when idle as I've experienced a shorter battery lifetime running Linux, compared to Windows XP. 


I'm very new on Linux and have no idea how to monitor CPU freq etc. \o: But I'm more than willing to learn ;)

---

### Post by size_XXM on 2008-02-14
Monitoring CPU freq> isn't there a Gnome applet for that? (I'm a KDE  user, so I wouldn't know.)
As far as you're OK with commandline, I remember numerous articles about this Intel utility that monitors which processes make the CPU switch to higher frequency - powerTOP. And hey, it appears to be in ubuntu repository:
[quote=package description]PowerTOP is a Linux tool that finds the software component(s) that make your laptop use more power than necessary while it is idle. As of Linux kernel version 2.6.21, the kernel no longer has a fixed 1000Hz timer tick. This will (in theory) give a huge power savings because the CPU stays in low power mode for longer periods of time during system idle.
However... there are many things that can ruin the party, both inside the kernel and in userspace. PowerTOP combines various sources of information from the kernel into one convenient screen so that you can see how well your system is doing, and which components are the biggest problem.
Homepage: [http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)[/quote]
You can try that if you want.
Anyway - AFAIK this is kernel/driver related stuff, and so should be somewhere in /proc. See what you get when you [cat](http://en.wiktionary.org/wiki/cat#Verb_2) the following```
cd /proc/acpi/processor/CPU#
cat ... (fill in one of the following)
>power
>limit
>throttling
>info
 
```
note: those are 4 separate commands and # is the number of core ;)

---

### Post by Melkekartong on 2008-02-14
Thanks :) The results are pretty much the same for both CPUs.
I'll give PowerTOP a try :-D

These are my results:
```

POWER:
active state:            C3
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[001] usage[00015310] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00241737] duration[00000000000923156262]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[02932932] duration[00000000017770543116]

LIMIT:
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0

THROTTLING
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

INFO
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

```


edit: > Currently, only 32-bit kernels have support for tickless idle; 64-bit kernels are expected to gain this feature in version 2.6.23. oh well, seems like I have to wait a while \o: But I'll make a note of it.

---

### Post by size_XXM on 2008-02-17
Oh, almost forgot - do you have the model with the camera? If so, does it work?

---

### Post by Melkekartong on 2008-02-18
I have the model with the camera, but I haven't found out how to make it work. However, when using the camera in Windows XP,' I'm quite disappointed with the quality (need a very good light source).

The sound is another issue. I haven't figured out how to make the headphone connector to work properly. When plugging in headphones, the speaker keep playing with no sound on the phones.

The MMC/SD reader is very easy to access. It adds as an own sdb* which can be mounted either auto/man. No drivers required.

The blueetoth appears in the systray, but I haven't made it work yet. Probably because of bad software.


Ar thing I'm very disappointed with in ubuntu is the network manager-applet. It exits randomly/unstable, very limited settings (can't specify wep key index), etc.

---

### Post by size_XXM on 2008-02-19
> I have the model with the camera, but I haven't found out how to make it work.
Hm, what did you try? Does it show up in some list? Try *lspci* or (more likely) *lsusb*. Or *lshw* - I think that one needs to be installed (the package is called lshw). If you see it in the list, try to find out if there's a /dev/video# (# being a number, usually 0) device and open it with something that handles video streaming devices - VLC, *mplayer, skype, whatever...

> The sound is another issue. I haven't figured out how to make the headphone connector to work properly.
Hmm, I'd check what soundcard you have and if there's anything mentioned about it in the forums - it could be a (yet) unsupported card or a simple switch in *alsamixer*.

---

### Post by bobishh on 2008-03-28
I've got this laptop. 'Bout webcam - i use linux-uvc drivers, laptop have foxlink webcam, it uses  v4l2. The problem is that I don't know how can I configure resolution of my webcam. Cheese makes photos 640x320, instead of cam is 1.3 mpx.

'Bout sound - work out of box, to turn off sound from front speakers you should enable "front" track in mixer, and turn the sound off. I always use headphones, so it solves the problem.
Also there were some problems with sound capture, but you should properly set parameters in mixer, and the problem will be solved.

p.s. sorry for my english, i'm russian. ;)

---

### Post by Melkekartong on 2008-04-19
I've installed Ubuntu 32bit instead of 64bit. Seems like it's working far more better than amd64!! :D

About the webcam, I haven't got it to work though I can see it in lsusb:
*05c8:0103 Cheng Uei Precision Industry Co., Ltd (Foxlink)*

How can I use the linux-uvc / v4l2 drivers? Any howto on this?
I've tried loading the stream in VLC, using the videoforlinux-tab. It doesn't give any error, nor any video.

---

### Post by bobishh on 2008-05-06
For the Foxlink webcam look here:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
And here's the howto:
[http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

P.s. after upgrade to hardy Cheese started making pics in 1280x960

---

### Post by Anton_A on 2008-06-17
Hi!
I by this nout today and install Ubuntu 8.04.
All work successful, but I don`t know, how can I check the web-camera work.

---

### Post by patrickfromspain on 2008-07-12
If you have problems with the speaker not muting when pluging in the headphones, here's the solution: [http://ubuntuforums.org/showpost.php?p=5366917&postcount=3](http://ubuntuforums.org/showpost.php?p=5366917&postcount=3)

---

