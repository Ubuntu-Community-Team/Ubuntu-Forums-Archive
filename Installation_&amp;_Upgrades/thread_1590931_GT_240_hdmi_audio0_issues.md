---
title: "GT 240 hdmi audio0 issues"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by ICANSEEYOU7687 on 2010-10-08
I have seen a lot of these threads and have followed a few guides and I cannot get it to work correctly, maybe I need some more guidance bcause I am lost.

But I have followed

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller)
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

None of these work and now if I try aplay -l in the terminal, I now get

> 
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:594get_char_skip_comments) Cannot access file <EOF
ALSA lib conf.c:1645snd_config_load1) _toplevel_:1:15:No such file or directory
ALSA lib conf.c:3425snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3671snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (0): No such file or directory
ALSA lib conf.c:594get_char_skip_comments) Cannot access file <EOF
ALSA lib conf.c:1645snd_config_load1) _toplevel_:1:15:No such file or directory
ALSA lib conf.c:3425snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286snd_config_hooks_call) function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3671snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (1): No such file or directory
Thanks

---

### Post by ICANSEEYOU7687 on 2010-10-09
So, I installed ubuntu 10.10 and now it can see the HDMI as an audio device but no sounds comes out of it still.

I have tried messing with the ALSA mixer with the terminal and the gui but nothing yet....

I also tried following the above guides and adding all the lines to the configs.

If anyone has any ideas I would greatly appreciate them, thanks!

---

### Post by ICANSEEYOU7687 on 2010-10-10
SOLVED! Took a while and tried a few things (these I think are unimportant but might have had an effect)

-Removed old ATI drivers
-Disabled integrated audio

So then I replaced my alsa conf file and the HDA intel one with the ones found here
[http://ubuntuforums.org/showthread.php?t=1565479&page=2](http://ubuntuforums.org/showthread.php?t=1565479&page=2)

and rebooted and everything seems working now.  Although im not sure if it is currently stereo or 5.1 but defenately an improvement!

This was also done with a EVGA GT 240 512mb DDR5

---

