---
title: "no sound!! installed ubuntu 10.04 on toshiba satellite p105-s6024"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by jeff464 on 2010-05-12
All,

Please help. I just installed 10.04 on my laptop (p105-s6024) and now the sounds doesn't work. I searched and tried a number of things, but no luck, I'm very new to this, so anyone that help would really be appreciated!!!


"aplay -l " returns:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


"cat /proc/asound/version" returns:

Advanced Linux Sound Architecture Driver Version 1.0.21.


"head -n 1 /proc/asound/card*/codec#*"  returns:

Codec: Conexant CX20551 (Waikiki)


Once again, any help / guidance would be very appreciated!!!!

Thanks in advance.

---

### Post by jeff464 on 2010-05-12
bump......

can someone help??

---

### Post by efflandt on 2010-05-13
Not sure what all that means.  My A105 has different devices, but is otherwise somewhat similar, and sound works:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC861

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054

Since a Winmodem appears to be a sound device, that can sometimes interfere.

Did you by chance leave your sound muted?  In the sound applet, see if it says **Mute All**, or **Unmute**.  And in Sound Preferences what shows for Hardware and Output.

---

### Post by raygj on 2010-05-13
> **jeff464 said:**
> All,

Please help. I just installed 10.04 on my laptop (p105-s6024) and now the sounds doesn't work. I searched and tried a number of things, but no luck, I'm very new to this, so anyone that help would really be appreciated!!!


"aplay -l " returns:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


"cat /proc/asound/version" returns:

Advanced Linux Sound Architecture Driver Version 1.0.21.


"head -n 1 /proc/asound/card*/codec#*"  returns:

Codec: Conexant CX20551 (Waikiki)


Once again, any help / guidance would be very appreciated!!!!

Thanks in advance.

give this a go
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")

---

### Post by dino99 on 2010-05-13
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/66426](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/66426)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

---

### Post by gabak on 2010-11-28
i saw in other forum they solved it just upgrading the bios. and reinstalling all again.
did u fix urs?

---

### Post by gabak on 2010-11-28
I FIXED IT
IT WORKS NOW !!!!!!!!!!1

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1364120&rpn=PSPA0U&modelFilter=P105-S6024&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1364120&rpn=PSPA0U&modelFilter=P105-S6024&selCategory=2756709&selFamily=1073768663)

JUST UPDATE YOUR BIOS TO THE LAST ONE

---

