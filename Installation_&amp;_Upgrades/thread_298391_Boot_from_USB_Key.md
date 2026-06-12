---
title: "Boot from USB Key?"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Infamous Flame on 2006-11-12
Hey,

First time using Linux, followed the instructions in [this guide]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29") but when I reboot, it just doesn't seem to notice any difference and loads windows normally. There's no "problem" apart from the fact that there's no sign of ubuntu lol.

Anyone done this before or know of an obvious problem I've missed?

Many thanks in advance :)

---

### Post by jd65pl on 2006-11-12
Is your system set to boot off the usb drive before the hard drive?

---

### Post by Infamous Flame on 2006-11-12
Would I have had to changed that in BIOS? If so, then no heh. Last time I entered the BIOS, the computer died. Badly. That's why I didn't want to mess with it unless I had to.

---

### Post by emdeem on 2006-11-12
Most BIOS's have an option to select the boot device without entering the BIOS setup menu.  When the PC powers on, look for a message that says "Press XX to selct boot device" (or something similar).

---

### Post by jd65pl on 2006-11-12
[SIZE=3]In the bios there should be a section which says "1st boot device, 2nd boot device, 3rd boot device" This is the order in which your computer will try to load an operating system, by changing the order nothing bad will happen to your system, only it will try to boot an OS from the first device then the second etc...[/SIZE]

---

### Post by Infamous Flame on 2006-11-14
Sorry for the delay in replying.

I ended up getting ubuntu working from usb key, after changing the boot priorities in BIOS (thankyou j lol) and entering some boot switch (something=disabled:yes) because if i ran the default boot, it didn't work, just hung during the boot process.

Anyways, I ended up (long story, it didn't work properly from USB key) installing from an install CD someone gave me. Which is Drake, but I can sync it later.

It worked, except I couldn't get on the net, and it wouldn't boot windows anymore, so I ended up doing a hard restore to windows only *sigh*. So when I go home, I'm gonna try the install CD again, pay more attention, and try to get online.

Edit: The firmware-extractor is for installing firmware for my Speedtouch USB ADSL modem (sucky i know but meh).

My other question is:

When entering this terminal line:

chmod +x firmware-extractor &&

The terminal just printed a ">" on the next line. If i pressed return, it'd just print another one on a new line, and so on. If i entered any characters then pressed return, it'd say bash command not recognised or something. Not sure what I'm supposed to do here.

Thanks for your help, and thanks for help with this latest question heh.

Edit: The firmware-extractor is for installing firmware for my Speedtouch USB ADSL modem (sucky i know but meh, i don't have a router)

---

### Post by jd65pl on 2006-11-14
>  When entering this terminal line:

chmod +x firmware-extractor &&

The terminal just printed a ">" on the next line

The characters && indicate another command is anticipated therefore it is waiting for another command. Try using

```
chmod +x firmware-extractor
```

---

### Post by Infamous Flame on 2006-11-15
Thankyou everyone for your help. I've succesfully installed linux and gotten online. Now trying to get onto my MSN, gaim keeps throwing connection/switchboard errors.

---

### Post by Step on 2006-11-15
> **Infamous Flame said:**
> Thankyou everyone for your help. I've succesfully installed linux and gotten online. Now trying to get onto my MSN, gaim keeps throwing connection/switchboard errors.

This is not your fault, everyone on MSN has that problem. Probably because they are converting hotmail into live. I'm new here but I thought I should let you know!;)

I'm running Dapper Drake for a while now without much problems, my friend Heliode is helping me too. So far an excellent operating system, it's definitely a stay for me!

---

### Post by Infamous Flame on 2006-11-16
I much prefer it over Windows, but I don't like the whole dependcies thing, everything is dependent on something which i dont have lol. And when trying to upgrade to Dapper Drake from Breezy Badger, it does something but says it kept forty odd packages back :(

---

### Post by jd65pl on 2006-11-16
> **Infamous Flame said:**
> I much prefer it over Windows, but I don't like the whole dependcies thing, everything is dependent on something which i dont have lol. And when trying to upgrade to Dapper Drake from Breezy Badger, it does something but says it kept forty odd packages back :(

How are you installing things if you are using apt, aptitude or synaptic you should not be having these "dependency issues"

---

### Post by Infamous Flame on 2006-11-16
I mostly use apt, synaptic never works, but I'm also using configur"ers" within stuff I've downloaded, which keeps throwing up C Compiler not found in $PATH errors. So I'm looking for a decent C Compiler, which I'm having trouble with.

Edit: Upon running System>Admin>Update Software, i get the following

Message about Edgy Eft

"It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

The following packages are not upgraded:

gstreamer0.8-alsa
gstreamer0.8-audiofile
gstreamer0.8-cdparanoia
gstreamer0.8-dv
gstreamer0.8-dvd
gstreamer0.8-esd
gstreamer0.8-flac
gstreamer0.8-gnomevfs
gstreamer0.8-gsm
gstreamer0.8-hermes
gstreamer0.8-jpeg
gstreamer0.8-misc
gstreamer0.8-musepack
gstreamer0.8-oss
gstreamer0.8-plugin-apps
gstreamer0.8-sdl
gstreamer0.8-speex
gstreamer0.8-theora
gstreamer0.8-tools
gstreamer0.8-vorbis
gstreamer0.8-x
ifrename
libgnutls11
libgstreamer-gconf0.8-0
libgstreamer-plugins0.8-0
libgstreamer0.8-0
libmysqlclient14
libneon24
libopenal0
libreadline4
python-gst
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-calcomp
xserver-xorg-input-digitaledge
xserver-xorg-input-dmc
xserver-xorg-input-dynapro
xserver-xorg-input-fpit
xserver-xorg-input-hyperpen
xserver-xorg-input-magellan
xserver-xorg-input-microtouch
xserver-xorg-input-mutouch
xserver-xorg-input-palmax
xserver-xorg-input-penmount
xserver-xorg-input-spaceorb
xserver-xorg-input-summa
xserver-xorg-input-tek4957
xserver-xorg-input-void"

---

### Post by Step on 2006-11-16
> **Infamous Flame said:**
> I much prefer it over Windows, but I don't like the whole dependcies thing, everything is dependent on something which i dont have lol. And when trying to upgrade to Dapper Drake from Breezy Badger, it does something but says it kept forty odd packages back :(

Well Windows depends on codecs and programs as well, but they cannot always fully show what they install and how they work. (I don't know everything either but Unix systems show me a lot more than simply an installer.

Maybe you should consider looking at upgrading problem topics from breezy badger to dapper drake, I'd look for you but I'm at work and I'm not fully known with Unix either, the only thing I miss is playing games lol, good luck man..I'm just trying to help as much as I can!

/Edit: kinda late post and a late quote, sorry.

---

### Post by Infamous Flame on 2006-11-16
Lol, thanks for the reply, and I'm currently updating to DD, then I'll update to EE, so that should *hopefully* fix most of my problems.

---

