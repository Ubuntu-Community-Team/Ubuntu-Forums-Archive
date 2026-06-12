---
title: "Nvidea 2.22.1"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by glowplug61 on 2008-10-23
<You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.>

...and so...

<Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'>

It is one thing that I need to work on my Firefox themes ASAP (Arctic Glow, glowyblue etc) but another for my business.

I am really fed up to the back teeth with this kind of problem.
All was working fine and then you do an update!!!!!!!!!!!!!!!!!

---

### Post by glowplug61 on 2008-10-23
Could somebody please tell me how to fix this problem.

I need to test my Firefox themes on Linux ASAP let alone other software.

Regards,
Greg (aka glowplug)

---

### Post by DrMelon on 2008-10-23
Try downloading EnvyNG and using it to install and configure the Nvidia drivers for you. Much easier.

---

### Post by glowplug61 on 2008-10-23
> **DrMelon said:**
> Try downloading EnvyNG and using it to install and configure the Nvidia drivers for you. Much easier.

Thank you for a very quick reply - I'll reboot back to ubuntu and try that.

---

### Post by glowplug61 on 2008-10-23
No change

In my experience there have been far to many ubuntu upgrades where a number of graphic card brands and/or versions have not been given serious enough consideration.

I had 1400x900 and floppy windows a few hours ago and now 640x800 since the upgrade - well done dudes, really well done!

---

### Post by mikejaegerster on 2008-10-23
I am by no means an expert on this but I found success following this thread.

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I just upgraded from 2.6.24-19 to 2.6.24-21 using this method and drivers came up successfully.

---

### Post by glowplug61 on 2008-10-26
> **mikejaegerster said:**
> I am by no means an expert on this but I found success following this thread.

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I just upgraded from 2.6.24-19 to 2.6.24-21 using this method and drivers came up successfully.

Thank you, a very good howto etc but not quite what I need.

Regards,
Greg

---

### Post by glowplug61 on 2008-10-26
1. I downloaded the latest NVIDIA driver.
No problems installing, no errors on start/log in, no resolution above 640x480.
2. The previous 2 NVIDIA drivers I downloaded - same as point 1.
3. The ones in Synaptic - same as point 1. but some with errors/not load on start/log in.

My video card is 6800GT.
Ubuntu version 8

Most of these drivers listed above were working up until the latest Ubuntu 8 update.

I apologize for starting out rude on this thread but this situation is really annoying.
A particular Firefox on Ubuntu issue means I have an enormous amount of extension testing to do for my themes.
The simplest solution still sees this problem compounded tenfold by the low res. problem.
I can avoid cross platform testing on my main software development at this stage but this still presents a serious problem!

I have tried searching for a solution but again, it is really hard on this res.
Not only that but the Advanced Search does not seem to have a...
'Limit To Sticky'
...option which is where a solution, if any, is bound to be - surely?!

To summarize the problem...
* Latest Hardy update
* NVIDIA 6800
* Most drivers, Envy, nvidia-glx, nvidia-glx-new
* Auto-installed - don't load and/or errors and res. restricted to <=640x480
* Manually installed - load but res. restricted to <=640x480

Help on this greatly appreciated.

Regards,
Greg

---

### Post by glowplug61 on 2008-10-26
I did not want to touch xorg.conf without advice from these forums but I was all out of time.

I thought I'd be at this for days but it was less than an hour.

The xorg.conf that the Ubuntu Update is generated was a good part of the problem.
That update carelessly overwrote what was there!
Furthermore it failed to probe the monitor correctly - if at all.
It created an xorg.conf that stuffed up the nvidia installation at kernel integration let alone anything else.

The Ubuntu update is still writing Modes, Virtual and ModeLine whereas it would seem that only Option "metamodes" is required by more recent NVIDIA drivers.

It is not like it is just a few people like me with old cards.
I searched and found a stack of posts including quite a range of cards.
Quite a number of people put on generic drivers at a waste of their valuable videocards.
I will try to research to help as time etc permits!!!

In the end I still say one thing...
   The Advanced Forum Search should have included a filter to 'Limit to Sticky' 2 years ago.
...it is just one bad reason for the forums being chocked with redundant threads.
It should not take me to suggest this!!!

I can put good money on it not being fixed along with the xorg.conf writer being a problem through to the end of Hardy!!

It's the same old same old, a little work by a few at the cost of a stack of time and confusion by many!!

hmmm!

---

