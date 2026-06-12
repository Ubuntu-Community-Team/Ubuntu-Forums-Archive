---
title: "Disable Creative Soundblaster Z"
date: 2016-01-09
forum: MINT
---

### Post by bullpup on 2016-01-09
Hi,

I'm using Linux as my primary OS, and dual boot  Windows for Gaming. I've been using my onboard soundcard for many years  and it worked just fine, but recently I bought SimVibe for some racing  games which needs a second soundcard. So I went ahead and bought a  Creative Soundblaster Z, since it's fine for gaming and I don't plan to  use it on Linux anyways, I just want to continue using the onboard  sound.
The problem now is that not only does the new Soundcard not  work (which I expected and don't care about), the onboard sound does not  work either anymore and everytime I try to start an application that  uses sound the application hangs or crashes.
So I'd like to make sure  that my system does not try to use the damn Soundblaster but I'm not  quite sure how. That's my sound cards:

```
&#10140;  ~  inxi -Ax
Audio:     Card-1: Creative Labs Device 0012 driver: snd_hda_intel bus-ID: 02:00.0 Sound: ALSA ver: k3.13.0-37-generic
           Card-2: NVIDIA Device 0fbb driver: snd_hda_intel bus-ID: 01:00.1
            Card-3: Intel 7 Series/C210 Series Chipset Family High  Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
```


I  cannot show you aplay output, since that command hangs as well. Card 3  is the onboard sound I want to use, card 1 is the Creative Sound Blaster  and Card 2 I guess is from the graphics card which I don't use either.  Since all of them use snd_hda_intel it's not as easy as blacklisting a  module. How can I tell the system not to use that device  (02:00.0)?

---

### Post by matt_symes on 2016-01-09
Hi

> How can I tell the system not to use that device (02:00.0)? 


Here's some ideas for you to consider.

1.

It should be possible to instruct udev not to process the device at all.

Create a rule to match on ADD and the vendor and device ID and use OPTIONS+="ignore_device".

This should stop udev adding the sound card in the first place.

2.

It's also possible to hotplug remove a device.

If you want to remove the device then try this as a *test*.

Open a terminal and type

```
echo 1 | sudo tee /sys/bus/pci/devices/0000:02:00.0/remove
```

Select your onboard sound card in the GUI and try to play some music.

Does your onboard sound device play ?
Is the add-in sound card selectable and/or does it play ?

Out of the two suggestions above, i would give the first one a try first as if you can get udev to ignore the card in the first place then the sound card will never be an issue.

I'm interested in the second case though, as i'm not sure how it will affect your other sound devices.

Kind regards

---

### Post by bullpup on 2016-01-11
Hi Matt,

thanks very much for your answer. Option 1 does not work for me since I have udev 204 and that does not support the "ignore_device" option. But what I did now is using your second option, I just put that into /etc/rc.local and that seems to work fine! Onboard audio works fine, as usual.

Regards,
Julian

---

### Post by matt_symes on 2016-01-11
Hi

> **bullpup said:**
> Option 1 does not work for me since I have udev 204 and that does not support the "ignore_device" option. 

You do need a recent version of udev for this option, as you have seen. What version of Ubuntu or other Linux are you using ?

> But what I did now is using your second option, I just put that into /etc/rc.local and that seems to work fine! Onboard audio works fine, as usual.

Thanks for posting back with this information. This is useful to know.

Kind regards

---

### Post by bullpup on 2016-01-12
I am using Linux Mint 17.1 which is based on Ubuntu 14.04. As far as my research went, this option was removed in udev 148 (see: http://superuser.com/questions/611101/udev-rules-ignore-device).<br>Best regards

---

### Post by howefield on 2016-01-12
Thread moved to the "*MINT*" forum.

---

### Post by matt_symes on 2016-01-12
Hi

> **bullpup said:**
> I am using Linux Mint 17.1 which is based on Ubuntu 14.04. As far as my research went, this option was removed in udev 148 (see: http://superuser.com/questions/611101/udev-rules-ignore-device).<br>Best regards

It was removed ? I thought it was added. Seems my information is wrong then. I'm glad you posted back and i'll have to read up on the udev docs again.

I'll take another look at udev for you when i get the time and see if i can find a solution using udev.

Kind regards

---

