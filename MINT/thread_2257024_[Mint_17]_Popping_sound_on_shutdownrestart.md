---
title: "[Mint 17] Popping sound on shutdown/restart"
date: 2014-12-16
forum: MINT
---

### Post by gordonthegopher on 2014-12-16
Hello,

This is my first post here, but over the last couple of years I have hit the same immensely frustrating issue when trying to get Linux Mint up and running.

I have an Acer Aspire 5741a laptop as my main machine. I have tried to put Mint (Cinnamon 64 bit) on it numerous times (Mint 13 through 16), but everytime I give up because of the same issue. Everytime I reboot, come out of suspend or shutdown, the speakers make a horrible crunching popping sound. I have read loads of advice both here and elsewhere and followed the following suggestions with no result:

* Added "options snd-hda-intel power_save=0 power_save_controller=N" to the end of /etc/modprobe.d/alsa-base.conf
* Edited /usr/lib/pm-utils/power.d/intel-audio-powersave so "INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}" is commented out with a # and the line "INTEL_AUDIO_POWERSAVE=false" is added underneath
* Edited /sys/module/snd_hda_intel/parameters/power_save to persistently say "0" (i.e. change is preserved on reboot)
* Edited /sys/module/snd_hda_intel/parameters/power_save_controller to persistently say "N" (i.e. change is preserved on reboot)
* Fully purged Pulse on the Vaio to let ALSA take over using the instructions here: [http://www.johndscomputers.com/2014/multimedia/geek-friday-why-and-how-i-finally-removed-pulseaudio-in-favor-of-alsa-and-alternate-notification-icon-because-it-interfered-with-skype-in-ubuntu-13-10/](http://www.johndscomputers.com/2014/multimedia/geek-friday-why-and-how-i-finally-removed-pulseaudio-in-favor-of-alsa-and-alternate-notification-icon-because-it-interfered-with-skype-in-ubuntu-13-10/)
* I came across a post on the Arch Linux forums suggesting to comment out the line "aplay -d 1 /dev/zero" in /etc/pm/sleep.d/90alsa. However, this file doesn't exist in Mint. I tried manually adding this file but it causes a shutdown hang. If I run the command "aplay -d 1 /dev/zero" in a terminal, it makes the same sound as I'm having the problem with. There is a /etc/apm/scripts.d/alsa file that seems to be about resume and suspend, but no 'aplay' in mine.
* updating to the 3.18 stable kernel
* updating ALSA to the latest daily
* installing TLP and turning off power saving and power save controller in the configuration file. 
* Deleted ~/.config/pulse and rebooted
*  edited /etc/apm/scripts.d/alsa so it looks like this:

```
#!/bin/sh
#
# apmd proxy script for ALSA


[ -x /usr/sbin/alsactl ] || exit 0


case "$1,$2" in
   suspend,*) /usr/bin/amixer -q sset Master PCM mute /usr/sbin/alsactl store && /sbin/alsa suspend ;;
   resume,suspend) /sbin/alsa resume && /usr/sbin/alsactl restore /usr/bin/amixer -q sset Master PCM unmute;;
esac

```

All I'm really trying to find is a way of scripting it so that the speakers are muted when the sound chip turns on or off. If this was a desktop machine I would just power it on and off without the speakers turned on, but you can't do that on a laptop, obviously.

I really love Mint, and once it gets going I much prefer it over Windoze, especially the mess that is Windows 8. But when Windows is installed on this machine, it doesn't make this horrible sound.

I tried a Lubuntu live boot CD and it exhibits the same behaviour.

Any help is greatly appreciated.

**EDIT**

I have *pretty much* fixed this! The steps I took:

1. edit /etc/pulse/client.conf as root and uncomment the lines:

```
autospawn = yes
daemon-binary = /usr/bin/pulseaudio
```

Then change it to "autospawn = no"

2. edit /etc/init/alsa-store.conf as root and add these lines right at the end (after exec /usr/sbin/alsactl -E HOME="$ALSACTLHOME" store)

```
exec /usr/bin/amixer set Master mute >/dev/null
exec /sbin/modprobe -r snd-hda-intel
```

3. Add the command "/usr/bin/pulseaudio" a Startup Application with a delay of 0. This means Pulse Audio starts at boot and you get the login sound. Presumably if Pulse Audio is killed somehow you have to manually restart it by issuing "pulseaudio --start"

Save and reboot. Only a tiny tiny popping sound now, barely audible.

---

### Post by slickymaster on 2014-12-16
*Moved to the ***MINT*** sub-forum*

---

### Post by gordonthegopher on 2014-12-17
Recently I acquired an old Sony Vaio VGN-FS515E. It had Windows XP installed on it (boo) but hardware wise everything is working fine. I figured I would use it as a guinea pig machine to mess about with Mint. So I have put Mint 17 XFCE on it, installed to the hard drive.

Everytime it boots, there is a horrible pop/crackle from the speakers just before the desktop appears. 

The difference with the Vaio is that the horrible crackle and pop sound only happens on boot, not on shutdown or restart. I have tried the same things I did for the Acer above, but they haven't helped. All I really want to do is make the speakers muted before the snd-hda-intel module loads and then unmute them afterwards.

Anyone have any ideas?

---

### Post by mörgæs on 2014-12-17
Threads merged. Please don't create multiple threads on the same or a closely related topic.

If the problem is not solved then it helps removing [RESOLVED] from the title, and when it is please read the footnote in post #2.

---

