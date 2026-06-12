---
title: "[SOLVED] gutsy-&amp;gt;hardy lost sound"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by wazo2k on 2008-05-12
Hi,
I have upgraded to Hardy Heron 8.04 from 7.10 using the automated upgrade in kubuntu. I had sound, I don't have anymore. I tried to follow [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and couldn't get anywhere.

**find /lib/modules/`uname -r` | grep snd**
gives 161 lines (see attached modules.txt)

**aplay -l**
gives
```

**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC662 Analog [ALC662 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC662 Digital [ALC662 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```

**lspci -v**
gives
```

[...]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8290
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at dbdf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
[...]

```

**sudo modprobe snd-hda-intel**
doesn't give anything

[B]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils[/B]
fails to do anything

**alsamixer**
Everything is up, nothing muted

**cat /proc/asound/cards**
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdbdf8000 irq 20

```

I am part of the **"audio" group**

**sudo bash aadebug**
see attached aadebug.txt

What should I look for next?

---

### Post by hermes0710 on 2008-05-13
Have you tried installing the backport modules?

---

### Post by wazo2k on 2008-05-13
> **hermes0710 said:**
> Have you tried installing the backport modules?
Thanks for the tip, I didn't know about backport modules. I'll read [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) and try that tonight.

---

### Post by hermes0710 on 2008-05-13
I had a similar problem with my sound on an hp and couldn't make it work until i installed the backport modules. Just be careful to install those matching your kernel. Good luck!

---

### Post by WebWatch on 2008-05-13
I had the sound working fine for a couple of weeks and then it stopped. Tried all the above and nothing fixed. Soundcard is found in lspci -v but aplay -l shows the driver is not loading. With 7.10  I managed to get 2 soundcards and 1 onboard all working at the same time. Please report if your having similar problems and maybe the next update could fix it.

---

### Post by wazo2k on 2008-05-13
> **hermes0710 said:**
> Have you tried installing the backport modules?
Sorry but I probably din't get your point, backports available to hardy don't seem to have any sound related package (looking at [http://packages.ubuntu.com/hardy-backports/allpackages](http://packages.ubuntu.com/hardy-backports/allpackages) )

---

### Post by wazo2k on 2008-05-13
Another thing, I have been looking at bug

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/223061](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/223061) (upgraded to hardy heron from gutsy and now sound card does not work, no sound is being emmited)

In it, someone mentions "I started running the "Hardware Test" utility. The test sound didn't play. During the video test, something strange happened, and I cycled the power. When the laptop came back on, sound was working." 

What could that hardware test utility be?

---

### Post by hermes0710 on 2008-05-14
I was talking about modules, not packages. Actually the package you need is something like: linux-restricted-modules-???? where ???? stand for your kernel version

---

### Post by Dubolomov on 2008-05-14
I had this problem after upgrading to Hardy. It was fixed by using ALSA (Advanced Linux Sound Architecture) instead of "Autodetect" that used by default.

---

### Post by wazo2k on 2008-05-14
> **hermes0710 said:**
> I was talking about modules, not packages. Actually the package you need is something like: linux-restricted-modules-???? where ???? stand for your kernel version

Thanks, I'll try that tonight if I have the time

> **Dubolomov said:**
> I had this problem after upgrading to Hardy. It was fixed by using ALSA (Advanced Linux Sound Architecture) instead of "Autodetect" that used by default.

Thanks for the tip, but unfortunately it didn't work (tried within the control panel and within xine engine's audio setup in kaffeine.


I have tested the live kubuntu 8.04 CD this morning, and using it I heard the KDE login/logout sounds (this at least proves that my speakers are well connected). Unfortunately I didn't have time to test a lot more, especially since neither "amarok", "kaffeine" nor "top" were able to launch. I'll investigate more as soon as I get some time.

---

### Post by hermes0710 on 2008-05-14
The package you need is linux-backports-modules-???? where ??? matches your kernel version (Search with synaptic package manager). Check this out and let me know

---

### Post by wazo2k on 2008-05-15
I installed linux-backports-modules-2.6.14-17-generic (via linux-backports-modules-hardy), did a reboot, still no sound :(

but thanks again for the suggestion :|

---

### Post by HangukMiguk on 2008-05-15
Have you checked in the sound configurations to see if ALSA is being used to handle sounds?  ALSA is no longer default in Hardy, Pulse Audio is.

I don't remember where the config GUI is for audio in KDE though, but KDE's pretty easy when it comes to finding this stuff.

---

### Post by wazo2k on 2008-05-15
> **HangukMiguk said:**
> Have you checked in the sound configurations to see if ALSA is being used to handle sounds?  ALSA is no longer default in Hardy, Pulse Audio is.

Using the livecd (where sound is actually working), **system settings > sound system > hardware > select the audio device**  is set to autodetect. If I change it to **Advanced Linux Sound Architecture**, sound still works. There is no choice for Pulse Audio. (Altough I vaguely remember having that setting available in my normal installation... I'll inspect in that direction)

In any case, thanks for the tip :KS

---

### Post by wazo2k on 2008-05-15
no such thing as a Pulse Audio in the KDE control panel, but....

SOLVED!! :guitar:

For those interested, I noticed in the live cd that some channels in alsamixer were muted ("Front Mi", "Line", "Mic" and "IEC958"). So I tried to mute them on my installed system, and this gave me sound!

The weird thing is that I can re-unmute them without affecting sound.

---

