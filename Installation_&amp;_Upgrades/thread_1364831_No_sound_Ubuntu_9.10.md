---
title: "No sound Ubuntu 9.10"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by dvdbosch on 2009-12-26
Hello,

Im kinda new on Ubuntu:-).

I have just installed Ubuntu 9.1, but im getting no sound.

I tried all kind of things (all ideas posted in these forums) but nothing helped.

Can someone help me with this issue?

Thanks in advance.

---

### Post by raymondh on 2009-12-26
> **dvdbosch said:**
> Hello,

Im kinda new on Ubuntu:-).

I have just installed Ubuntu 9.1, but im getting no sound.

I tried all kind of things (all ideas posted in these forums) but nothing helped.

Can someone help me with this issue?

Thanks in advance.

[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Just maybe... in case you have not seen this yet ....

---

### Post by dvdbosch on 2009-12-27
> **raymondh said:**
> [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Just maybe... in case you have not seen this yet ....

Thx, can someone translate this in newbie language :-)

---

### Post by spiky001 on 2009-12-27
Hi I know this might soud silly but is the volume turned on & up ?

---

### Post by dvdbosch on 2009-12-27
> **spiky001 said:**
> Hi I know this might soud silly but is the volume turned on & up ?

Yeah it is :-)

Tried everything, adjustmens on alsa etc. Im now thinking of downgrading to 9.04. Hopefully this will help.

And in the mean time, just waiting for an update :-)

---

### Post by SecretCode on 2009-12-27
Did you install any proprietary drivers (under System > Admin > Hardware drivers) - in particular for a software modem? I had no sound at all; tried lots of things; but removing the proprietary software modem driver sorted it out. (Modems and sound cards often run off common chips, at least in laptops.)

---

### Post by dvdbosch on 2009-12-28
> **SecretCode said:**
> Did you install any proprietary drivers (under System > Admin > Hardware drivers) - in particular for a software modem? I had no sound at all; tried lots of things; but removing the proprietary software modem driver sorted it out. (Modems and sound cards often run off common chips, at least in laptops.)
 
I've installed NVIDIA drivers, thats the only driver thats is activated. What is a software modem (sorry for the noobisch question).

---

### Post by SecretCode on 2009-12-28
If there's no software modem detected then it's not a problem!
(Cheap modem chips often used in Windows.)

---

### Post by dvdbosch on 2009-12-28
> **SecretCode said:**
> If there's no software modem detected then it's not a problem!
(Cheap modem chips often used in Windows.)

Mmm so thats not the solution. I think im going to downgrade.

---

### Post by phillw on 2009-12-28
Have you installed the restricted drivers - required for mp3 etc ?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Head for the Section ..
> **Playing Restricted Formats**

  
Follow these steps to play and record most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages. 
 
**Ubuntu 9.04 (Jaunty Jackalope) and 9.10 (Karmic Koala)**

 

And click on the link that says 'click here' - That'll put the drivers on for you.

Regards,
Phill.

---

### Post by dvdbosch on 2009-12-28
> **dvdbosch said:**
> Mmm so thats not the solution. I think im going to downgrade.

After downgrading to 9.04 same problems. Can someone help me with this?

---

### Post by dvdbosch on 2009-12-29
> **dvdbosch said:**
> After downgrading to 9.04 same problems. Can someone help me with this?


PhillW, thanks for the tip, but that didnt work.

Im using realtek onboard soundcard, i think that will be the issue.

---

### Post by dvdbosch on 2009-12-30
> **dvdbosch said:**
> PhillW, thanks for the tip, but that didnt work.

Im using realtek onboard soundcard, i think that will be the issue.


So i think i upgraded everything.

Ive got the following config:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is this correct?

---

### Post by dvdbosch on 2009-12-31
> **dvdbosch said:**
> So i think i upgraded everything.

Ive got the following config:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Is this correct?

Guys!

I've got the sound working!

Ive donwloaded the latest driver (alsa) from the realtek site, compiled and installed!

Great!!

Thanks for the help and tips.

---

