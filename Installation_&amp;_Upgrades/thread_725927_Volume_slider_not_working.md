---
title: "Volume slider not working"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Dai777 on 2008-03-16
I seem to have lost the ability to adjust the sound using the slider for volume icon. When I go into open volume control to check on things I see there is no master volume, even under edit preferences there is no master control. My volume control is:
HDA Intel (Alsa Mixer)

I used to have control over the volume before but can't remember if master was in there.
One thing I have noticed is when the mixer panel is open the volume slider operates the microphone slider.

How do I get the volume slider to work again?

dai@dai-desktop:~$ ls -la /dev/snd
total 0
drwxr-xr-x  2 root root     180 2008-03-16 10:45 .
drwxr-xr-x 14 root root   14280 2008-03-16 11:08 ..
crw-rw----  1 root audio 116, 8 2008-03-16 10:45 controlC0
crw-rw----  1 root audio 116, 7 2008-03-16 10:45 pcmC0D0c
crw-rw----  1 root audio 116, 6 2008-03-16 10:45 pcmC0D0p
crw-rw----  1 root audio 116, 5 2008-03-16 10:45 pcmC0D1p
crw-rw----  1 root audio 116, 4 2008-03-16 10:45 pcmC0D2c
crw-rw----  1 root audio 116, 3 2008-03-16 10:45 seq
crw-rw----  1 root audio 116, 2 2008-03-16 10:45 timer


dai@dai-desktop:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Unknown device 2936
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Thanks in advance
Dai

---

### Post by Pumalite on 2008-03-16
What happens when you type 'alsamixer' in your Terminal?

---

### Post by Dai777 on 2008-03-16
> **Pumalite said:**
> What happens when you type 'alsamixer' in your Terminal?

see it in the terminal but no master volume.
pcm, front, front mic, surround, center, lfe, side, headphone

---

### Post by Dai777 on 2008-03-16
got it sorted wrong device was selected in preferences.

---

### Post by Pumalite on 2008-03-16
Maybe compiling the new alsa driver is your answer.

---

