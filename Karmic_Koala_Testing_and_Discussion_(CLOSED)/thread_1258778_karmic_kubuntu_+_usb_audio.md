---
title: "karmic kubuntu + usb audio"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-09-05
i am running karmic kubuntu and have
```
Bus 003 Device 002: ID 0d8c:0001 C-Media Electronics, Inc. Audio Device

```
and in system settings/multimedia I can set prefer for usb to be used.  Also when i hit the 'test' button i get great sound.

it's the only sound/speaker configuration I have at the moment.  i disabled the onboard sound for no speakers to connect to it.  plugged in the usb sound and it configured it self and with the 'test' button it's definately working.

my dilema is that sound doesnt' work for anything else.  amarok, vlc, firefox, etc has no sound.

i found a thread that mentioned ```
sudo asoundconf list
sudo asoundconf setdefaultcard
```
but it seems to longer be on the current kde/kubuntu setup.
```
buzzmandt@buzzmandt-desktop:~$ sudo asoundconf list
sudo: asoundconf: command not found

```

how can i set kubuntu to use the usb speakers?

edit:  oh yeah, I've also made sure already that it's in the kmix volume app, which it is, and that it's not muted, which it isn't.

---

### Post by buzzmandt on 2009-09-05
update
it's working with amarok, vlc, internal apps.

but still no sound through firefox

any suggestions?

---

### Post by buzzmandt on 2009-09-05
anyone?

---

### Post by rbmorse on 2009-09-05
I don't have a solution, but I can confirm the behavior.

---

### Post by buzzmandt on 2009-09-06
I found to install libflashsupport which refered to another package.
> buzzmandt@buzzmandt-desktop:~$ sudo apt-get install libflashsupport
[sudo] password for buzzmandt:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree-extrasound
E: Package libflashsupport has no installation candidate

so i installed flashplugin-nonfree-extrasound but it still doesn't work for firefox.

is there no fix for this?

---

### Post by buzzmandt on 2009-09-06
couple more tests
> buzzmandt@buzzmandt-desktop:~$ lsmod | grep snd
snd_wavefront          37332  0
snd_cs4236             29620  0
snd_usb_audio          84224  3
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75264  4 snd_cs4236,snd_usb_audio,snd_wss_lib,snd_pcm_oss
snd_mpu401              7016  0
snd_mpu401_uart         6940  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_page_alloc          9156  2 snd_wss_lib,snd_pcm
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  3 snd_wavefront,snd_usb_audio,snd_opl3_lib
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  4 snd_wavefront,snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  22 snd_wavefront,snd_cs4236,snd_usb_audio,snd_wss_lib,snd_opl3_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd


and 

> buzzmandt@buzzmandt-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


the last one is saying it's card 2.  do i need to change it to be card 1?  if so, how?

---

### Post by Asraniel on 2009-09-06
the only "help" i can give you is this:

amarok and kde use phonon, which then uses gstreamer to play the sound. through kde you can configure phonon, and then all your phonon using applications should work. for all other applications you have to setup that manualy, how, i don't know. (pulseaudio?)

---

### Post by buzzmandt on 2009-09-06
Found a fix that worked for me

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Seems when it sets up the installer finds the current sound scheme and sets this for firefox.  must be a way to change the config without purging/reinstalling.  But it worked in any case.

---

### Post by crimsun on 2009-09-07
> **buzzmandt said:**
> i found a thread that mentioned ```
sudo asoundconf list
sudo asoundconf setdefaultcard
```
but it seems to longer be on the current kde/kubuntu setup.
```
buzzmandt@buzzmandt-desktop:~$ sudo asoundconf list
sudo: asoundconf: command not found

```

We no longer ship asoundconf as part of alsa-utils (we removed it from Debian, too), as it was only useful while the hal/udev detect bits in PA were less mature.

If you have a pressing need for asoundconf (but in reading this thread, I can say definitively that you don't), I still maintain it.

---

### Post by crimsun on 2009-09-07
> **buzzmandt said:**
> Found a fix that worked for me

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Seems when it sets up the installer finds the current sound scheme and sets this for firefox.  must be a way to change the config without purging/reinstalling.  But it worked in any case.

Are you on a 32-bit or 64-bit install? If the former, you probably want adobe-flashplugin from the Canonical partner repo instead of flashplugin-nonfree from the Ubuntu multiverse repo.

---

### Post by buzzmandt on 2009-09-07
thank you crimsun. i'm on 32 bit.  and no need for asoundconf.  purging then reinstalling flash worked.

---

### Post by jbernardo on 2009-09-07
> **crimsun said:**
> We no longer ship asoundconf as part of alsa-utils (we removed it from Debian, too), as it was only useful while the hal/udev detect bits in PA were less mature.

If you have a pressing need for asoundconf (but in reading this thread, I can say definitively that you don't), I still maintain it.

Maybe you could keep it available for kubuntu users? I still try to steer away from pulseaudio while I can, and possibly I'm not the only one.

---

### Post by Zorael on 2009-09-07
> **jbernardo said:**
> Maybe you could keep it available for kubuntu users? I still try to steer away from pulseaudio while I can, and possibly I'm not the only one.
+1

What would be the recommended way to change default alsa output device in Kubuntu Karmic, on the fly, *without* PA? I had to download the Jaunty alsa-base package and extract asoundconf from there.

My usercase is that I have a netbook with a USB soundcard that I sometimes have connected, that I further sometimes want to route default output through.

As an example, I have a video-conferencing app that I manually tell to use the USB device (since sound gets garbled if I use the internal Intel HDA chipset for some reason), while letting Firefox and everything else still use the Intel chipset.

At other times, I output video to a bigger monitor a few metres away, and then I want the USB device to be the default (to get Firefox to output there) so I don't get the oddities of the Intel chipset when I connect headphones or speakers.

If I had HAL/udev make the USB device hijack being the default card upon connecting, I'd get all sound output through there except if I tell an app not to - if the app even supports that, and Firefox and Flash don't. On a session-wide basis I can tell Phonon (and xine) what the default device should be, but only KDE apps would honor the change.

'**asoundconf set-default-card MP3**' was enough up until Karmic, and now with the script removed there plain isn't a way of doing it. Except creating my own ~/.asoundrc.asoundconf by hand and changing its contents when I want to manage the default.

Please advise. I don't see why the environment-independent terminal script had to be removed to give way for a PA (and likely GTK) solution. Unless a new HAL/udev-based script/tool to provide the same functionality in a neater fashion is on the way, this seems destructive to non-GNOME non-PA installations.

I don't want alsamixer to be removed in favor of some PA app either, just as I imagine people don't want nano removed when Kwrite gets an upgrade.

---

