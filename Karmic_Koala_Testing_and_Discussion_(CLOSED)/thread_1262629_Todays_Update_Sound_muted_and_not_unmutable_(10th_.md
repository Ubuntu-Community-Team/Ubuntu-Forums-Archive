---
title: "Todays Update: Sound muted and not unmutable (10th September 2009)"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lprofil on 2009-09-10
Hello,

i didn't check the list of updates proper which might have prevented me from running into a system without sound. 
My system starts with a muted sound device and i cannot use the slider to unmute the device.
Clicking on it: nothing. 
Opening the Sound Preferences menue: i click the mute hock away but when i try to adjust the "Output volume" the slider goes nuts and does not let me adjust it.


lspci output of my sound device:

```
01:09.0 Multimedia video controller: C-Media Electronics Inc CM8338A (rev ff)
```



/var/log/user.log shows:```
Sep 10 09:46:44 leaf-garden pulseaudio[3619]: ratelimit.c: 67 events suppressed
Sep 10 09:49:05 leaf-garden pulseaudio[3798]: module-alsa-card.c: Failed to find a working profile.
Sep 10 09:49:05 leaf-garden pulseaudio[3798]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 10 10:09:07 leaf-garden pulseaudio[3798]: ratelimit.c: 5 events suppressed
Sep 10 10:10:52 leaf-garden pulseaudio[3503]: module-alsa-card.c: Failed to find a working profile.
Sep 10 10:10:52 leaf-garden pulseaudio[3503]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 10 10:10:57 leaf-garden pulseaudio[3503]: ratelimit.c: 19 events suppressed

```


```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8338 [C-Media CMI8338], device 0: CMI8338 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8338 [C-Media CMI8338], device 1: CMI8338 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
cat /proc/asound/cards
 0 [CMI8338        ]: CMI8338 - C-Media CMI8338
                      C-Media CMI8338 (model 0) at 0xff00, irq 17
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

```


I tried [this suggestion]("http://ubuntuforums.org/showpost.php?p=7338739&postcount=10"),
but it did not work for me.


I will try to downgrade the package which might have caused this trouble.
Any help is very welcome though.

/lprofil

---

### Post by Robin Nixon on 2009-09-10
I got the same. I fixed it by right clicking and clicking mon the Mute check box a few times until it eventually cleared.

---

