---
title: "PulseAudio ver 9.0.16"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-08-05
Strange...

Yesterday test 3 came up and built ok for all flavors but
no accetance from an archive-manager

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/005596.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/005596.html)

Today test 4 came up and also built OK

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/005685.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/005685.html)


Upstream reference:
[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004620.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004620.html)


Whats up....:confused:

--

---

### Post by OliW on 2009-08-05
Slightly off-topic. I know progress is progress but but seeing a new version of PA scares the hell out of me...

... Just as I got all my audio working as expected.

---

### Post by plun on 2009-08-05
Well... who knows ?  :D

Test 3 is available at Ubuntu-dev-audio ppa

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

Works excellent also wine and Spotify

:guitar:

---

### Post by taavikko on 2009-08-05
> **plun said:**
> Well... who knows ?  :D

Test 3 is available at Ubuntu-dev-audio ppa

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)


Test4 is available through main repos... (main server)
```
apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.16~test4-0ubuntu1
  Candidate: 1:0.9.16~test4-0ubuntu1
  Version table:
 *** 1:0.9.16~test4-0ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by plun on 2009-08-05
> **taavikko said:**
> Test4 is available through main repos...
```
apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.16~test4-0ubuntu1
  Candidate: 1:0.9.16~test4-0ubuntu1
  Version table:
 *** 1:0.9.16~test4-0ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```


Yes, now....:D

The archive manager woke up....:P

---

### Post by Regenweald on 2009-08-05
No audio here. Default user a member of 'audio' and alsamixer 'front' at maximum. deleted .pulse and logged back in also. :) very quiet here. I'm on test 4

---

### Post by taavikko on 2009-08-05
> **Regenweald said:**
> No audio here. Default user a member of 'audio' and alsamixer 'front' at maximum. deleted .pulse and logged back in also. :) very quiet here. I'm on test 4

Are you sure it's the righ channel "front" i have to raise speakers to get adequate levels.
Also check the pulse levels with volume-applet or "alsamixer -Dhw"

---

### Post by plun on 2009-08-05
Also install pavucontrol  .........

Otherwise a user is blind !

---

### Post by Regenweald on 2009-08-05
> **taavikko said:**
> Are you sure it's the righ channel "front" i have to raise speakers to get adequate levels.
Also check the pulse levels with volume-applet or "alsamixer -Dhw"

Yes, all checked and all set to max. Tried using Preferences>>Multimedia Systems Selector to test also but no output. Will keep trying.

Thanks.

Edit: will install pavucontrol now :)

---

### Post by plun on 2009-08-05
Well, my sound also broke after reboot...:---)

Error-search...:D

EDIT

kill command fixed my sound
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```

Reference
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Regenweald on 2009-08-05
> **plun said:**
> Well, my sound also broke after reboot...:---)

Error-search...:D

:P funny. I usually log out an in after large updates, got about 22 that time. i see output volume in pavucontrol when using exaile but get no actual noise.

Will keep checking.

---

### Post by plun on 2009-08-05
> **Regenweald said:**
> :P funny. I usually log out an in after large updates, got about 22 that time. i see output volume in pavucontrol when using exaile but get no actual noise.

Will keep checking.

I wrote an edit to my earlier post, a pkill fixed my sound.

---

### Post by Regenweald on 2009-08-05
Thanks Plun, how long should the pkill take to run though ? mine has been going for a few mins.

---

### Post by plun on 2009-08-05
> **Regenweald said:**
> Thanks Plun, how long should the pkill take to run though ? mine has been going for a few mins.

Its instant
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```


Did you reboot after this update ?

---

### Post by Regenweald on 2009-08-05
> **plun said:**
> Its instant
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```


Did you reboot after this update ?

indeed i did. my pkill is decidedly longer than an instant :)

---

### Post by Starks on 2009-08-05
With each and every Pulseaudio regression, OSSv4 looks better and better.

<__<

---

### Post by psyke83 on 2009-08-05
If you can't seem to get audio working, try this:

Run PulseAudio Volume Control (if not yet installed, it's the pavucontrol package).

On the Output Devices tab:
a) If you have more than one audio card, ensure your desired card is set as the default (green fallback icon).
b) Ensure the card isn't muted, and the volume levels are OK.
c) Change the Port* from "Analog Output" to "Analog Output/Amplifier" **or** your desired output port.

On the Input Devices tab:
a) If you have more than one audio card, ensure your desired card is set as the default (green fallback icon).
b) Ensure the card isn't muted, and the volume levels are OK.
c) Change the Port to the desired setting (in my case, it's "Analog Microphone / Microphone 1").

On the Configuration tab:
a) Ensure the Profile is set to the appropriate configuration (for me, it's "Analog Stereo Duplex").

*FYI, I was getting no sound until I switched the Port to "Analog Output/Amplifier", so this may be the only option you need to change.

**Edit:** It seems that the /usr/share/alsa/pulse.conf file is missing, which means that ALSA applications won't work correctly.

A temporary workaround until this gets fixed:
```
$ gedit ~/.asoundrc
```
Paste into this (empty) file and save:
```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}
```

You may need to log out and back in for changes to take effect.

---

### Post by psyke83 on 2009-08-05
> **Starks said:**
> With each and every Pulseaudio regression, OSSv4 looks better and better.

<__<

Yes, you're completely correct. A testing version of PulseAudio on a distribution that's still under development doesn't work. Stop the presses!

Or, perhaps the supporting infrastructure (including a sane default configuration) simply hasn't caught up in the few hours that we've been testing this new release.

---

### Post by mc4100 on 2009-08-05
Just upgraded, everything seems fine.

Lennart wrote a nice summary of what's in "[Oh Nine Sixteen]("http://0pointer.de/blog/projects/oh-nine-sixteen.html")" -- it all looks like good stuff, the only thing I find fault with is the combining of mixer elements (means PCM is almost 100% and that Master will be adjusted) because, I think, when combined with the fact that the loudest app's volume level effectively becomes Master (flat volume logic) and a bug in totem, clicking totem's volume control button (to access the actual slider) by itself changes the volume, that might end up setting both master and PCM at 100%!

---

### Post by no1wantdthisname on 2009-08-05
Sound on 64bit flash broken for anyone else?
Removed ~/.pulse and restarted pulseaudio.  Still no sound.

Firefox shows the following:
```

ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave

```

---

### Post by jmmL on 2009-08-05
> **mc4100 said:**
> it all looks like good stuff, the only thing I find fault with is the combining of mixer elements (means PCM is almost 100% and that Master will be adjusted) 

This worries me slightly. I'm not really sure what the problem with my laptop sound chain is (but it's hardware, not software I think - same problems in Windows). Whenever my PCM is high (say above 65%) then even if my Master is low, the sound will experience heavy distortion and crackling for a particular volume. Reversing the situation, by having a high Master and mid PCM gets me the same volume without any distortion issues. I experience a similar problem, although it is less pronounced, when using headphones.

Will this combination of mixer elements be user-reversible? I couldn't immediately find any elaboration about this, so any links you have would be great!

---

### Post by mc4100 on 2009-08-05
> **jmmL said:**
> Will this combination of mixer elements be user-reversible? I couldn't immediately find any elaboration about this, so any links you have would be great!

[This]("https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-June/004229.html") might be worth a read; it gives a technically-minded explanation of how element "merging" is being done, and why.

Edit: Whoops, totally said it wasn't configurable, no idea why, that's removed. It looks, or sounds (by which I mean reads), like it's configurable via some sort of profile. Also looks, or sounds, very complicated, too. 

Oh Pulseaudio, why do you have to be so hostile?

---

### Post by mc4100 on 2009-08-05
> **no1wantdthisname said:**
> Sound on 64bit flash broken for anyone else?
Removed ~/.pulse and restarted pulseaudio.  Still no sound.

Firefox shows the following:
```

ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave

```
[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-July/004527.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-July/004527.html)

---

### Post by malachi1990 on 2009-08-05
Might be related, but I only have no sound in totem and rhythmbox.  FF and music123 (a commandline music player) both play normally.

And pavucontrol doesn't allow me to connect.

---

### Post by psyke83 on 2009-08-06
Anybody who is experiencing issues with ALSA applications or PulseAudio itself since these updates, please see [comment #17]("http://ubuntuforums.org/showpost.php?p=7739984&postcount=17") before posting.

---

### Post by andresmh on 2009-08-06
I followed the instructions but sound recording is still not working. 

I set up the right settings, I think:

[[IMG]http://img190.imageshack.us/img190/7273/soundissues.th.png[/IMG]](http://img190.imageshack.us/my.php?image=soundissues.png)

[[IMG]http://img44.imageshack.us/img44/941/sound2.th.png[/IMG]](http://img44.imageshack.us/my.php?image=sound2.png)

My config file:
```

cat /home/andresmh/.asoundrc 
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}

```

I even tried using alsamixer to increase the volume directly there but no luck. All I hear is noise. It used to work before the update.

---

### Post by taavikko on 2009-08-06
Hmm, after restart no sound...
checked "alsamixer / alsamixer -Dhw" almost every level was set to nil(0) (the ones that matter)
Raising them required some serious keypressing, since almost like as they didn't want to be raised.

No sound using RB, looked the time on the progress bar, seemed to travel at double speed.

checked "gstreamer-properties", had sound with test on ALSA, nothing else.
Left it with "auto detect".

checked with "aplay /usr/share/sounds/question.wav" hooray, sound
so ALSA works.

time to fireup mplayer,
"mplayer -ao pulse <file>" no dice
"mplayer -ao alsa <file>" sound
"mplayer -ao oss <file>" sound

So gstreamer backend should be working, it's only the PA that's screwing around.
Like Psyke said. (not an direct quote ;) )

And mysteriously during this test session, "alsamixer" somehow dropped all the levels back down (the ones that matter)


EDIT// gnome-volume-manager had switched my default output to "HD3200 HDMI" which doesn't work.
switched back to "Stereo" and Yay, RB works :)

---

### Post by rudenko_ruslan on 2009-08-06
As for me, the only thing that doesn't work after PA updates - is YouTube. It doesn't have sound, and "Sound Preferences" says that "No application is currently playing or recording audio". Totem is working fine, BTW.

Don't know how to solve this :( I wonder what I should do now - follow psyke's instructions, or wait for another PA updates.

UPDATED: I solved this problem. Rebooted - and YouTube is working without any problems. Strange.

---

### Post by plun on 2009-08-06
Followup....  on 32 bit everything works, the only issue I can notice is that the volume is muted after reboot. 

I am also glad that we can see a Ubuntu developer within a upstream changelog, great TheMuso (Luke)


:popcorn:

---

### Post by andresmh on 2009-08-06
For me, sound output never stopped working. But sound INPUT hasn't worked. I think I am going to revert the update.

---

### Post by plun on 2009-08-06
> **andresmh said:**
> For me, sound output never stopped working. But sound INPUT hasn't worked. I think I am going to revert the update.

Well thats wrong approach with a development version....  IMHO :)

- Check bugs and maybe file a bug....

- In this case...  install [URL="http://packages.ubuntu.com/karmic/pavucontrol"]pavucontrol
[/URL]

- Go to tab "Input Devices".....  Is it muted ????


--

---

### Post by andresmh on 2009-08-06
I did install pavucontrol. I'll submit a bug report. Something interesting is that the volume indicator for the microphone seems to indicate that sound is coming in but it's only noise. See:

[[IMG]http://img139.imageshack.us/img139/7273/soundissues.th.png[/IMG]](http://img139.imageshack.us/my.php?image=soundissues.png)

When I play the sonud is just static.

---

### Post by andresmh on 2009-08-06
So it seems that I cannot downgrade any of the pulseaudio packages via synaptic. The "Force version" option is disabled for some reason, as if there wasn't an older version availbale.

---

### Post by psyke83 on 2009-08-06
> **andresmh said:**
> I did install pavucontrol. I'll submit a bug report. Something interesting is that the volume indicator for the microphone seems to indicate that sound is coming in but it's only noise. See:

[[IMG]http://img139.imageshack.us/img139/7273/soundissues.th.png[/IMG]](http://img139.imageshack.us/my.php?image=soundissues.png)

When I play the sonud is just static.

Have you tried all the different devices available in pavucontrol's Input Devices tab? None of your screenshots indicate that you were looking there.

---

### Post by psyke83 on 2009-08-06
> **andresmh said:**
> So it seems that I cannot downgrade any of the pulseaudio packages via synaptic. The "Force version" option is disabled for some reason, as if there wasn't an older version availbale.

That's normal. You can only force a package if different versions exist across multiple repositories.

---

### Post by andresmh on 2009-08-06
Yes, I tried selecting each one of the devices listed here by clicking on the green checkbox symbol:

[[IMG]http://img171.imageshack.us/img171/4830/screenshot2z.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshot2z.png)


Only when I selected "Internal Audio Analog Stereo" it let me record a sound with the Sound Recorder but again it only records noise which 9.0.15 version didn't happen. If listening to the sound is of any help I put it here:
[http://dl.getdropbox.com/u/285483/tmp/noise.ogg](http://dl.getdropbox.com/u/285483/tmp/noise.ogg)

---

### Post by tekstr1der on 2009-08-06
All the recent pulse package upgrades are being held back by aptitude for me. Based on this thread, I'm in no rush to get these installed. But, I was wondering if everyone here did a partial distribution upgrade to get these installed? Maybe there is some other reason the packages are being held back on my system?

---

### Post by taavikko on 2009-08-06
> **tekstr1der said:**
> All the recent pulse package upgrades are being held back by aptitude for me. Based on this thread, I'm in no rush to get these installed. But, I was wondering if everyone here did a partial distribution upgrade to get these installed? Maybe there is some other reason the packages are being held back on my system?

If "sudo aptitude dist-upgrade" complains about the pulse-module-hal to be removed, go ahead, it's replaced by pulse-module-udev.

but it's easier to said if we see the output ;)

---

### Post by andresmh on 2009-08-06
Yeah, I wish I had held back.

---

### Post by taavikko on 2009-08-06
> **andresmh said:**
> Yeah, I wish I had held back.

If you want stable, use Jaunty-9.04 or Hardy-8.04.
This is testing alpha, breakage is most likely to happen sometimes.

---

### Post by andresmh on 2009-08-06
I know, I know :) I just thought I could easily revert if something went wrong.

---

### Post by rudenko_ruslan on 2009-08-06
> **plun said:**
> Followup....  on 32 bit everything works, the only issue I can notice is that **the volume is muted after reboot. **

I am also glad that we can see a Ubuntu developer within a upstream changelog, great TheMuso (Luke)


:popcorn:
Hm, now I'm too affected with this problem :confused:

---

### Post by nanog on 2009-08-06
Someday I would like to have a pulseaudio update that does not set pcm to zero and selects the wrong output device. And while I am ranting can we please, please bring back the sound test buttons.

---

### Post by Regenweald on 2009-08-06
> **nanog said:**
> Someday I would like to have a pulseaudio update that does not set pcm to zero and selects the wrong output device. And while I am ranting can we please, please bring back the sound test buttons.

What about preferences>>multimedia systems selector

---

### Post by rudenko_ruslan on 2009-08-06
Sound in flash applications doesn't work again. It seems like playing roulette - you never know when you get lucky.

Some information from "Log Viewer":
> Aug  6 22:36:07 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
Aug  6 22:36:25 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
Aug  6 22:37:11 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error

---

### Post by Vaun on 2009-08-06
I just filed a bug on Launchpad.  I have a 32 bit install on my desktop with no issues.  My 64 bit install on my laptop is not working well.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409897]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409897")

---

### Post by psyke83 on 2009-08-06
> **Vaun said:**
> I just filed a bug on Launchpad.  I have a 32 bit install on my desktop with no issues.  My 64 bit install on my laptop is not working well.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409897]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409897")

Your bug appears to be set to private, is that correct? Unless it has sensitive information you should leave it as a public bug report.

---

### Post by Vaun on 2009-08-06
Hrm,

Changed to public.  Not sure why that happened.

---

### Post by miegiel on 2009-08-06
> **psyke83 said:**
> Yes, you're completely correct. A testing version of PulseAudio on a distribution that's still under development doesn't work. Stop the presses!

Or, perhaps the supporting infrastructure (including a sane default configuration) simply hasn't caught up in the few hours that we've been testing this new release.

:lolflag:

On the up-side my laptop sounds a lot better since the patch.

---

### Post by plun on 2009-08-06
Update is uploaded

> pulseaudio (1:0.9.16~test4-0ubuntu2) karmic; urgency=low

  * debian/pulseaudio.install:
    - Re-add the pm-utils script that was inadvertantly left out with the
      previous Debian merge
    - Add udev rules from upstream, needed for particular sound hardware

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/005782.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/005782.html)



---

### Post by Regenweald on 2009-08-06
> **plun said:**
> Update is uploaded

just finished an update, did not catch that one. Will do again in a couple hours.

---

### Post by Regenweald on 2009-08-06
Sorry to kind of bump. can anyone confirm if the latest updates are working ?

Edit: no progress here :(:)

---

### Post by wayne_cat on 2009-08-06
> **Regenweald said:**
> Sorry to kind of bump. can anyone confirm if the latest updates are working ?

Edit: no progress here :(:)

Have a look at the system log files:

```
sudo grep pulseaudio /var/log/*
```

Any errors?

---

### Post by Regenweald on 2009-08-06
> **wayne_cat said:**
> Have a look at the system log files:

```
sudo grep pulseaudio /var/log/*
```

Any errors?

thanks,hate to paste so much code but quite a few:
```

nd(): Address already in use
/var/log/user.log:Aug  5 17:27:19 Horsford pulseaudio[4932]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  5 17:27:19 Horsford pulseaudio[4932]: main.c: Module load failed.
/var/log/user.log:Aug  5 17:27:19 Horsford pulseaudio[4932]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  5 17:27:19 Horsford pulseaudio[4930]: main.c: Daemon startup failed.
/var/log/user.log:Aug  5 17:27:20 Horsford pulseaudio[4938]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  5 17:27:20 Horsford pulseaudio[4938]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  5 17:27:20 Horsford pulseaudio[4938]: main.c: Module load failed.
/var/log/user.log:Aug  5 17:27:20 Horsford pulseaudio[4938]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  5 17:27:20 Horsford pulseaudio[4936]: main.c: Daemon startup failed.
/var/log/user.log:Aug  5 17:29:14 Horsford pulseaudio[2947]: pid.c: Daemon already running.
/var/log/user.log:Aug  5 17:39:09 Horsford pulseaudio[2915]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 17:48:43 Horsford pulseaudio[2915]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 17:50:11 Horsford pulseaudio[2915]: dbus-util.c: Asked to handle disabled watch: 0xd76540 17
/var/log/user.log:Aug  5 17:50:11 Horsford pulseaudio[2915]: alsa-sink.c: Increasing wakeup watermark to 20.00 ms
/var/log/user.log:Aug  5 17:50:18 Horsford pulseaudio[3550]: pid.c: Daemon already running.
/var/log/user.log:Aug  5 17:56:40 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  5 17:56:40 Horsford pulseaudio[2915]: alsa-source.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 17:56:58 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:56:58 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to create watch on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:56:58 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:56:58 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to create watch on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:03 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:03 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to create watch on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:08 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:08 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to create watch on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:08 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 17:57:08 Horsford pulseaudio[2915]: reserve-wrap.c: Failed to create watch on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 18:09:16 Horsford pulseaudio[3976]: pid.c: Daemon already running.
/var/log/user.log:Aug  5 18:22:47 Horsford pulseaudio[4135]: dbus-util.c: Asked to handle disabled watch: 0x1284540 17
/var/log/user.log:Aug  5 18:24:20 Horsford pulseaudio[5431]: pid.c: Daemon already running.
/var/log/user.log:Aug  5 18:39:06 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 18:45:31 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  5 18:45:58 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  5 18:45:58 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 18:47:05 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 18:51:11 Horsford pulseaudio[4135]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  5 23:19:27 Horsford pulseaudio[2888]: pid.c: Daemon already running.
/var/log/user.log:Aug  5 23:35:34 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 23:35:34 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 23:35:46 Horsford pulseaudio[2869]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  5 23:35:46 Horsford pulseaudio[2869]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  5 23:35:46 Horsford pulseaudio[2869]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  5 23:35:47 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 23:35:53 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 23:36:23 Horsford pulseaudio[2869]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 23:36:23 Horsford pulseaudio[2869]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 23:36:40 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 23:36:40 Horsford pulseaudio[2869]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 23:37:53 Horsford pulseaudio[2869]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 23:37:53 Horsford pulseaudio[2869]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  6 01:32:25 Horsford pulseaudio[3379]: dbus-util.c: Asked to handle disabled watch: 0x22a3540 17
/var/log/user.log:Aug  6 01:32:34 Horsford pulseaudio[8158]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 10:24:09 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 10:24:29 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 10:24:37 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 10:24:55 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 10:25:08 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 10:25:08 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 10:26:05 Horsford pulseaudio[3379]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 10:26:38 Horsford pulseaudio[3379]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  6 10:26:40 Horsford pulseaudio[3379]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  6 10:27:03 Horsford pulseaudio[3379]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  6 10:27:36 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 10:27:41 Horsford pulseaudio[3379]: alsa-sink.c: Increasing wakeup watermark to 20.00 ms
/var/log/user.log:Aug  6 15:36:33 Horsford pulseaudio[2923]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 16:27:41 Horsford pulseaudio[2989]: dbus-util.c: Asked to handle disabled watch: 0x1618540 17
/var/log/user.log:Aug  6 18:05:17 Horsford pulseaudio[2932]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 18:09:40 Horsford pulseaudio[3922]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 18:29:03 Horsford pulseaudio[2903]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 18:31:28 Horsford pulseaudio[4781]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 18:31:53 Horsford pulseaudio[2903]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 18:32:09 Horsford pulseaudio[2903]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 18:32:38 Horsford pulseaudio[2903]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 18:32:43 Horsford pulseaudio[2903]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 18:32:44 Horsford pulseaudio[2903]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  6 18:33:46 Horsford pulseaudio[5028]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:46 Horsford pulseaudio[5028]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:46 Horsford pulseaudio[5028]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:46 Horsford pulseaudio[5028]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:46 Horsford pulseaudio[5026]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:47 Horsford pulseaudio[5081]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:47 Horsford pulseaudio[5081]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:47 Horsford pulseaudio[5081]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:47 Horsford pulseaudio[5081]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:48 Horsford pulseaudio[5105]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:48 Horsford pulseaudio[5105]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:48 Horsford pulseaudio[5105]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:48 Horsford pulseaudio[5105]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:48 Horsford pulseaudio[5041]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:49 Horsford pulseaudio[5111]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:49 Horsford pulseaudio[5111]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:49 Horsford pulseaudio[5111]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:49 Horsford pulseaudio[5111]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:49 Horsford pulseaudio[5085]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5117]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5117]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5117]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5117]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5115]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5123]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5123]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5123]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5123]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:50 Horsford pulseaudio[5121]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:51 Horsford pulseaudio[5129]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:51 Horsford pulseaudio[5129]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:51 Horsford pulseaudio[5129]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:51 Horsford pulseaudio[5129]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:51 Horsford pulseaudio[5127]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:52 Horsford pulseaudio[5135]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:52 Horsford pulseaudio[5135]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:52 Horsford pulseaudio[5135]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:52 Horsford pulseaudio[5135]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:52 Horsford pulseaudio[5133]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:53 Horsford pulseaudio[5141]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:53 Horsford pulseaudio[5141]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:53 Horsford pulseaudio[5141]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:53 Horsford pulseaudio[5141]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:53 Horsford pulseaudio[5139]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5169]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5169]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5169]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5169]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5167]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5175]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5175]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5175]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5175]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:54 Horsford pulseaudio[5173]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:55 Horsford pulseaudio[5181]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:55 Horsford pulseaudio[5181]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:55 Horsford pulseaudio[5181]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:55 Horsford pulseaudio[5181]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:55 Horsford pulseaudio[5176]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:56 Horsford pulseaudio[5187]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:56 Horsford pulseaudio[5187]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:56 Horsford pulseaudio[5187]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:56 Horsford pulseaudio[5187]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:56 Horsford pulseaudio[5182]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5193]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5193]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5193]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5193]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5191]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5199]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5199]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5199]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5199]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:57 Horsford pulseaudio[5197]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:58 Horsford pulseaudio[5205]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:58 Horsford pulseaudio[5205]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:58 Horsford pulseaudio[5205]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:58 Horsford pulseaudio[5205]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:58 Horsford pulseaudio[5203]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:33:59 Horsford pulseaudio[5211]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:33:59 Horsford pulseaudio[5211]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:33:59 Horsford pulseaudio[5211]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:33:59 Horsford pulseaudio[5211]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:33:59 Horsford pulseaudio[5209]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5217]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5217]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5217]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5217]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5215]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5223]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5223]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5223]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5223]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:34:00 Horsford pulseaudio[5221]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:34:01 Horsford pulseaudio[5229]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:34:01 Horsford pulseaudio[5229]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:34:01 Horsford pulseaudio[5229]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:34:01 Horsford pulseaudio[5229]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:34:01 Horsford pulseaudio[5227]: main.c: Daemon startup failed.
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[5236]: socket-server.c: bind(): Address already in use
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[5236]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[5236]: main.c: Module load failed.
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[5236]: main.c: Failed to initialize daemon.
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[5246]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 18:34:02 Horsford pulseaudio[2903]: pid.c: PID file '/home/rhiken/.pulse/6b7214f2e15306d3bc39997c4a3c8e57-runtime/pid' not mine!
/var/log/user.log:Aug  6 19:00:31 Horsford pulseaudio[5242]: dbus-util.c: Asked to handle disabled watch: 0x219c540 17
/var/log/user.log:Aug  6 19:02:22 Horsford pulseaudio[2893]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:08:20 Horsford pulseaudio[2920]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:08:20 Horsford pulseaudio[2930]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:11:01 Horsford pulseaudio[3297]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:11:17 Horsford pulseaudio[2899]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 22:11:27 Horsford pulseaudio[2899]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 22:11:57 Horsford pulseaudio[2899]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
/var/log/user.log:Aug  6 22:12:04 Horsford pulseaudio[2899]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 22:12:46 Horsford pulseaudio[2899]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 22:12:51 Horsford pulseaudio[2899]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log.0:Jul 26 19:31:25 Horsford pulseaudio[3489]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 26 19:39:49 Horsford pulseaudio[3489]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 26 19:39:49 Horsford pulseaudio[3489]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 26 19:39:49 Horsford pulseaudio[3489]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 27 09:41:00 Horsford pulseaudio[3489]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
/var/log/user.log.0:Jul 27 11:00:24 Horsford pulseaudio[6186]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 27 11:01:16 Horsford pulseaudio[6186]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 27 11:01:16 Horsford pulseaudio[6186]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 27 11:01:16 Horsford pulseaudio[6186]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 28 08:10:59 Horsford pulseaudio[2838]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 28 08:10:59 Horsford pulseaudio[2838]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 28 08:10:59 Horsford pulseaudio[2838]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 28 15:28:35 Horsford pulseaudio[5935]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 28 16:09:12 Horsford pulseaudio[5935]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 28 16:09:12 Horsford pulseaudio[5935]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 28 16:09:12 Horsford pulseaudio[5935]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 29 10:40:29 Horsford pulseaudio[3110]: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
/var/log/user.log.0:Jul 30 01:55:09 Horsford pulseaudio[3547]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 31 01:14:40 Horsford pulseaudio[2862]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log.0:Jul 31 01:16:24 Horsford pulseaudio[2862]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log.0:Jul 31 02:05:30 Horsford pulseaudio[2862]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log.0:Jul 31 18:10:35 Horsford pulseaudio[2862]: alsa-sink.c: Increasing wakeup watermark to 23.20 ms
/var/log/user.log.0:Jul 31 19:23:50 Horsford pulseaudio[2862]: alsa-sink.c: Increasing wakeup watermark to 33.20 ms
/var/log/user.log.0:Jul 31 19:59:30 Horsford pulseaudio[2862]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 31 19:59:30 Horsford pulseaudio[2862]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 31 19:59:30 Horsford pulseaudio[2862]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 31 20:20:53 Horsford pulseaudio[2862]: ratelimit.c: 2 events suppressed
/var/log/user.log.0:Jul 31 20:26:56 Horsford pulseaudio[2862]: alsa-sink.c: Increasing wakeup watermark to 43.20 ms
/var/log/user.log.0:Jul 31 21:16:46 Horsford pulseaudio[18135]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 31 21:24:09 Horsford pulseaudio[18898]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 31 21:24:51 Horsford pulseaudio[19136]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 31 21:26:44 Horsford pulseaudio[19370]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Jul 31 22:34:23 Horsford pulseaudio[19370]: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
/var/log/user.log.0:Jul 31 22:48:08 Horsford pulseaudio[19370]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log.0:Jul 31 22:48:08 Horsford pulseaudio[19370]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
/var/log/user.log.0:Jul 31 22:48:08 Horsford pulseaudio[19370]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log.0:Jul 31 22:48:21 Horsford pulseaudio[19370]: ratelimit.c: 10 events suppressed
/var/log/user.log.0:Jul 31 22:55:47 Horsford pulseaudio[19370]: alsa-sink.c: Increasing wakeup watermark to 40.00 ms
/var/log/user.log.0:Jul 31 22:59:07 Horsford pulseaudio[19370]: alsa-sink.c: Increasing wakeup watermark to 50.00 ms
/var/log/user.log.0:Aug  1 11:22:05 Horsford pulseaudio[23180]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Aug  1 14:39:14 Horsford pulseaudio[23896]: pid.c: Stale PID file, overwriting.
/var/log/user.log.0:Aug  2 01:16:16 Horsford pulseaudio[23896]: alsa-sink.c: Increasing wakeup watermark to 30.00 ms

```

@wayne_cat, ran it again what do you guys think ?

---

### Post by wayne_cat on 2009-08-06
I think this is the problem

```
/var/log/user.log:Aug  6 10:24:55 Horsford pulseaudio[3379]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
```

edit: copy&paste error

---

### Post by Slug71 on 2009-08-06
A bit OT but anyone know if we will get ALSA 1.0.21 also?

---

### Post by wayne_cat on 2009-08-06
> **Slug71 said:**
> A bit OT but anyone know if we will get ALSA 1.0.21 also?

When did they release the 1.0.21 developent version? It is not available from the project page

[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page)  (Development Versions: none)

and also not in the GIT repository

[http://git.alsa-project.org/](http://git.alsa-project.org/)

---

### Post by BwackNinja on 2009-08-06
A step forward, but...

This release came so close to working around [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011830.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011830.html) and got my hopes up, but at least its progress. Instead of combining my Master (which is just a silly name because it only affects the front) and Surround to give me 4.0, when moving the volume slider in pavucontrol and watching in alsamixer, PCM increases to a maximum (not all the way up, but that's a good thing), then Surround increases all the way, then Master increases all the way.

This happens regardless of how I configured /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf to have Master be all-front & front-left and front-right which I expected would increase at the same time as Surround at least when in 4.0 channel mode (front-left, front-right, rear-right, rear-left). To get any control that isn't terrible in my setup I just set those to 'ignore' instead of 'merge' in aformentioned file.

As usual, 2.0 controls work well and surround sound controls go to hell. But at least sound still works and its really nice (and I mean spectacular) to know that this is actually being worked on.

---

### Post by Slug71 on 2009-08-06
> **wayne_cat said:**
> When did they release the 1.0.21 developent version? It is not available from the project page

[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page)  (Development Versions: none)

and also not in the GIT repository

[http://git.alsa-project.org/](http://git.alsa-project.org/)

It isnt available yet, as far as i know anyway but a new ALSA version usually appears somewhere close to a PA version.

---

### Post by rudenko_ruslan on 2009-08-07
Updated PA again this morning, flash still doesn't have sound. Tried command from wayne_cat (sudo grep pulseaudio /var/log/*) and that's my results:
```
/var/log/syslog:Aug  4 02:42:51 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 02:42:53 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 02:45:20 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing wakeup watermark to 10.00 ms
/var/log/syslog:Aug  4 02:45:29 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  4 12:04:22 ruslan-desktop pulseaudio[3048]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 12:04:29 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 12:04:31 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 12:16:25 ruslan-desktop pulseaudio[2996]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 12:16:30 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 12:16:34 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 12:20:34 ruslan-desktop pulseaudio[2994]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 12:20:39 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  4 12:20:42 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  4 12:29:10 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/syslog:Aug  4 13:03:15 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/syslog:Aug  4 15:37:14 ruslan-desktop pulseaudio[2941]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 15:37:19 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 15:37:20 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 15:37:23 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  4 15:37:24 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  4 16:32:04 ruslan-desktop pulseaudio[2944]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 16:32:10 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 16:32:11 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 16:32:13 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  4 16:32:15 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  4 18:10:11 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/syslog:Aug  4 18:11:57 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/syslog:Aug  4 18:20:20 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 46.00 ms
/var/log/syslog:Aug  4 21:06:01 ruslan-desktop pulseaudio[2957]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 21:06:06 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 21:06:07 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 22:29:50 ruslan-desktop pulseaudio[2984]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 22:30:01 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 22:39:11 ruslan-desktop pulseaudio[3000]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  4 22:39:17 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  4 22:50:12 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 00:54:25 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/syslog:Aug  5 10:03:21 ruslan-desktop pulseaudio[2969]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 10:03:26 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 10:03:26 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 10:03:27 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 10:03:27 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 10:16:16 ruslan-desktop pulseaudio[3002]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 10:16:21 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 10:16:21 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 10:16:23 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 10:44:47 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 10.00 ms
/var/log/syslog:Aug  5 10:45:54 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 10:58:39 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 14:17:26 ruslan-desktop pulseaudio[3041]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 14:17:37 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 16:15:56 ruslan-desktop pulseaudio[3012]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 16:16:03 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 16:16:04 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 16:16:05 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 16:16:05 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 16:55:46 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 19:34:32 ruslan-desktop pulseaudio[2974]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 19:34:36 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 19:34:36 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 19:34:38 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 19:34:38 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 21:18:12 ruslan-desktop pulseaudio[2979]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 21:18:17 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 21:18:18 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 21:18:19 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 21:18:21 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 21:18:23 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 22:37:34 ruslan-desktop pulseaudio[2960]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  5 22:37:41 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  5 22:37:42 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  5 22:37:43 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  5 22:37:43 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  5 22:37:46 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  5 23:09:48 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/syslog:Aug  5 23:10:00 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/syslog:Aug  6 12:33:05 ruslan-desktop pulseaudio[3025]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/syslog:Aug  6 12:33:14 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/syslog:Aug  6 12:33:14 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  6 12:33:16 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/syslog:Aug  6 14:06:37 ruslan-desktop pulseaudio[3157]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 14:25:11 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
/var/log/syslog:Aug  6 14:26:35 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Increasing wakeup watermark to 40.00 ms
/var/log/syslog:Aug  6 14:47:39 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  6 14:47:41 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  6 14:47:42 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  6 14:47:43 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 8.00 ms
/var/log/syslog:Aug  6 14:47:45 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 16.00 ms
/var/log/syslog:Aug  6 14:51:26 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 26.00 ms
/var/log/syslog:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 15:03:44 ruslan-desktop pulseaudio[3056]: dbus-util.c: Asked to handle disabled watch: 0x80dd5d8 17
/var/log/syslog:Aug  6 15:03:49 ruslan-desktop pulseaudio[3056]: dbus-util.c: Asked to handle disabled watch: 0x81581d0 45
/var/log/syslog:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 15:04:46 ruslan-desktop pulseaudio[3216]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 15:05:29 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  6 15:05:30 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 2.00 ms
/var/log/syslog:Aug  6 15:05:31 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 4.00 ms
/var/log/syslog:Aug  6 15:32:41 ruslan-desktop pulseaudio[3120]: dbus-util.c: Asked to handle disabled watch: 0x8192bd8 43
/var/log/syslog:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 15:51:22 ruslan-desktop pulseaudio[4558]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 21:01:10 ruslan-desktop pulseaudio[4455]: dbus-util.c: Asked to handle disabled watch: 0x91a9e28 43
/var/log/syslog:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 21:02:22 ruslan-desktop pulseaudio[3142]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 22:04:46 ruslan-desktop pulseaudio[3042]: dbus-util.c: Asked to handle disabled watch: 0x85c55d8 17
/var/log/syslog:Aug  6 22:04:49 ruslan-desktop pulseaudio[3042]: dbus-util.c: Asked to handle disabled watch: 0x8630780 43
/var/log/syslog:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 22:05:47 ruslan-desktop pulseaudio[3144]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  6 22:24:16 ruslan-desktop pulseaudio[3120]: pid.c: Daemon already running.
/var/log/syslog:Aug  6 22:31:27 ruslan-desktop pulseaudio[3024]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/syslog:Aug  6 22:36:07 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/syslog:Aug  6 22:36:25 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/syslog:Aug  6 22:37:11 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/syslog:Aug  7 01:55:50 ruslan-desktop pulseaudio[3024]: dbus-util.c: Asked to handle disabled watch: 0x8f455d8 17
/var/log/syslog:Aug  7 01:55:55 ruslan-desktop pulseaudio[3024]: dbus-util.c: Asked to handle disabled watch: 0x8fb0bd8 43
/var/log/syslog:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  7 12:57:44 ruslan-desktop pulseaudio[3141]: pid.c: Daemon already running.
/var/log/syslog:Aug  7 13:07:19 ruslan-desktop pulseaudio[3040]: dbus-util.c: Asked to handle disabled watch: 0x93045c0 17
/var/log/syslog:Aug  7 13:07:23 ruslan-desktop pulseaudio[3040]: dbus-util.c: Asked to handle disabled watch: 0x936de28 43
/var/log/syslog:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/syslog:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/syslog:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/syslog:Aug  7 13:08:19 ruslan-desktop pulseaudio[3082]: pid.c: Daemon already running.
/var/log/syslog.1:Aug  4 07:55:12 ruslan-desktop pulseaudio[3561]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
/var/log/syslog.1:Aug  4 07:55:12 ruslan-desktop pulseaudio[3561]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
/var/log/user.log:Aug  4 00:55:19 ruslan-desktop pulseaudio[3212]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
/var/log/user.log:Aug  4 00:55:19 ruslan-desktop pulseaudio[3212]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
/var/log/user.log:Aug  4 01:02:02 ruslan-desktop pulseaudio[3298]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
/var/log/user.log:Aug  4 01:02:02 ruslan-desktop pulseaudio[3298]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
/var/log/user.log:Aug  4 02:42:46 ruslan-desktop pulseaudio[3418]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 02:42:50 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 02:42:50 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 02:42:50 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 02:42:51 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 02:42:51 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 02:42:53 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 02:45:20 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing wakeup watermark to 10.00 ms
/var/log/user.log:Aug  4 02:45:29 ruslan-desktop pulseaudio[3418]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  4 12:04:22 ruslan-desktop pulseaudio[3048]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 12:04:26 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 12:04:29 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 12:04:31 ruslan-desktop pulseaudio[3048]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 12:16:25 ruslan-desktop pulseaudio[2996]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 12:16:29 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 12:16:30 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 12:16:34 ruslan-desktop pulseaudio[2996]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 12:20:34 ruslan-desktop pulseaudio[2994]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 12:20:38 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 12:20:39 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  4 12:20:42 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  4 12:29:10 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/user.log:Aug  4 13:03:15 ruslan-desktop pulseaudio[2994]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/user.log:Aug  4 15:37:14 ruslan-desktop pulseaudio[2941]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 15:37:18 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 15:37:19 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 15:37:20 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 15:37:23 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  4 15:37:24 ruslan-desktop pulseaudio[2941]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  4 16:32:04 ruslan-desktop pulseaudio[2944]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 16:32:09 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 16:32:10 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 16:32:11 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 16:32:13 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  4 16:32:15 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  4 18:10:11 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/user.log:Aug  4 18:11:57 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/user.log:Aug  4 18:20:20 ruslan-desktop pulseaudio[2944]: alsa-sink.c: Increasing minimal latency to 46.00 ms
/var/log/user.log:Aug  4 21:06:01 ruslan-desktop pulseaudio[2957]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 21:06:05 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 21:06:06 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 21:06:07 ruslan-desktop pulseaudio[2957]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 22:29:50 ruslan-desktop pulseaudio[2984]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 22:29:55 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 22:30:01 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 22:39:11 ruslan-desktop pulseaudio[3000]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  4 22:39:15 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  4 22:39:16 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  4 22:39:17 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  4 22:50:12 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 00:54:25 ruslan-desktop pulseaudio[3000]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/user.log:Aug  5 10:03:21 ruslan-desktop pulseaudio[2969]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 10:03:25 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 10:03:26 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 10:03:26 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 10:03:27 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 10:03:27 ruslan-desktop pulseaudio[2969]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 10:16:16 ruslan-desktop pulseaudio[3002]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 10:16:20 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 10:16:21 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 10:16:21 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 10:16:23 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 10:44:47 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 10.00 ms
/var/log/user.log:Aug  5 10:45:54 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 10:58:39 ruslan-desktop pulseaudio[3002]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 14:17:26 ruslan-desktop pulseaudio[3041]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 14:17:31 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 14:17:37 ruslan-desktop pulseaudio[3041]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 16:15:56 ruslan-desktop pulseaudio[3012]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 16:16:00 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 16:16:03 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 16:16:04 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 16:16:05 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 16:16:05 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 16:55:46 ruslan-desktop pulseaudio[3012]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 19:34:32 ruslan-desktop pulseaudio[2974]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 19:34:36 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 19:34:36 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 19:34:37 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 19:34:38 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 19:34:38 ruslan-desktop pulseaudio[2974]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 21:18:12 ruslan-desktop pulseaudio[2979]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 21:18:16 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 21:18:17 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 21:18:18 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 21:18:19 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 21:18:21 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 21:18:23 ruslan-desktop pulseaudio[2979]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 22:37:34 ruslan-desktop pulseaudio[2960]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  5 22:37:38 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  5 22:37:41 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  5 22:37:42 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  5 22:37:43 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  5 22:37:43 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  5 22:37:46 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  5 23:09:48 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing minimal latency to 36.00 ms
/var/log/user.log:Aug  5 23:10:00 ruslan-desktop pulseaudio[2960]: alsa-sink.c: Increasing wakeup watermark to 25.99 ms
/var/log/user.log:Aug  6 12:33:05 ruslan-desktop pulseaudio[3025]: bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.ServiceUnknown
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  6 12:33:09 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 7.98 ms
/var/log/user.log:Aug  6 12:33:14 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 8.00 ms
/var/log/user.log:Aug  6 12:33:14 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  6 12:33:16 ruslan-desktop pulseaudio[3025]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
/var/log/user.log:Aug  6 14:06:37 ruslan-desktop pulseaudio[3157]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 14:25:11 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
/var/log/user.log:Aug  6 14:26:35 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Increasing wakeup watermark to 40.00 ms
/var/log/user.log:Aug  6 14:47:39 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 14:47:41 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  6 14:47:42 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  6 14:47:43 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 8.00 ms
/var/log/user.log:Aug  6 14:47:45 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 16.00 ms
/var/log/user.log:Aug  6 14:51:26 ruslan-desktop pulseaudio[3056]: alsa-source.c: Increasing minimal latency to 26.00 ms
/var/log/user.log:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 14:52:21 ruslan-desktop pulseaudio[3056]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 15:03:44 ruslan-desktop pulseaudio[3056]: dbus-util.c: Asked to handle disabled watch: 0x80dd5d8 17
/var/log/user.log:Aug  6 15:03:49 ruslan-desktop pulseaudio[3056]: dbus-util.c: Asked to handle disabled watch: 0x81581d0 45
/var/log/user.log:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 15:04:43 ruslan-desktop pulseaudio[3120]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 15:04:46 ruslan-desktop pulseaudio[3216]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 15:05:29 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 15:05:30 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 2.00 ms
/var/log/user.log:Aug  6 15:05:31 ruslan-desktop pulseaudio[3120]: alsa-source.c: Increasing minimal latency to 4.00 ms
/var/log/user.log:Aug  6 15:32:41 ruslan-desktop pulseaudio[3120]: dbus-util.c: Asked to handle disabled watch: 0x8192bd8 43
/var/log/user.log:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 15:51:19 ruslan-desktop pulseaudio[4455]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 15:51:22 ruslan-desktop pulseaudio[4558]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 21:01:10 ruslan-desktop pulseaudio[4455]: dbus-util.c: Asked to handle disabled watch: 0x91a9e28 43
/var/log/user.log:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 21:02:19 ruslan-desktop pulseaudio[3042]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 21:02:22 ruslan-desktop pulseaudio[3142]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:04:46 ruslan-desktop pulseaudio[3042]: dbus-util.c: Asked to handle disabled watch: 0x85c55d8 17
/var/log/user.log:Aug  6 22:04:49 ruslan-desktop pulseaudio[3042]: dbus-util.c: Asked to handle disabled watch: 0x8630780 43
/var/log/user.log:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 22:05:45 ruslan-desktop pulseaudio[3046]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 22:05:47 ruslan-desktop pulseaudio[3144]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  6 22:24:13 ruslan-desktop pulseaudio[3024]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  6 22:24:16 ruslan-desktop pulseaudio[3120]: pid.c: Daemon already running.
/var/log/user.log:Aug  6 22:31:27 ruslan-desktop pulseaudio[3024]: alsa-source.c: Increasing minimal latency to 1.00 ms
/var/log/user.log:Aug  6 22:36:07 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 22:36:25 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  6 22:37:11 ruslan-desktop pulseaudio[3024]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio1': Input/output error
/var/log/user.log:Aug  7 01:55:50 ruslan-desktop pulseaudio[3024]: dbus-util.c: Asked to handle disabled watch: 0x8f455d8 17
/var/log/user.log:Aug  7 01:55:55 ruslan-desktop pulseaudio[3024]: dbus-util.c: Asked to handle disabled watch: 0x8fb0bd8 43
/var/log/user.log:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  7 12:57:41 ruslan-desktop pulseaudio[3040]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  7 12:57:44 ruslan-desktop pulseaudio[3141]: pid.c: Daemon already running.
/var/log/user.log:Aug  7 13:07:19 ruslan-desktop pulseaudio[3040]: dbus-util.c: Asked to handle disabled watch: 0x93045c0 17
/var/log/user.log:Aug  7 13:07:23 ruslan-desktop pulseaudio[3040]: dbus-util.c: Asked to handle disabled watch: 0x936de28 43
/var/log/user.log:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
/var/log/user.log:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_emu10k1'. Please report this issue to the ALSA developers.
/var/log/user.log:Aug  7 13:08:17 ruslan-desktop pulseaudio[2984]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
/var/log/user.log:Aug  7 13:08:19 ruslan-desktop pulseaudio[3082]: pid.c: Daemon already running.
/var/log/user.log.1:Aug  4 07:55:12 ruslan-desktop pulseaudio[3561]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
/var/log/user.log.1:Aug  4 07:55:12 ruslan-desktop pulseaudio[3561]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
/var/log/user.log.1:Aug  4 00:34:48 ruslan-desktop pulseaudio[3180]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
/var/log/user.log.1:Aug  4 00:34:48 ruslan-desktop pulseaudio[3180]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
```
:confused:

Added later: I returned my flash sound (again). What I've done - opened "Sound Preferences", clicked on "Hardware" tab, and changed profile for SB Audigy from "Analog Surround 5.1 Output" to "Analog Surround 5.1 Output + Analog Stereo Input". That helped me.

---

### Post by Vaun on 2009-08-07
Still no luck with the latest updates:

pulseaudio (1:0.9.16~test4-0ubuntu4) karmic; urgency=low

  * debian/pulseaudio.install: ...and also re-add droped apport hook, and
    alsa configuration files

I can get sound only if I enable and turn the volume up via alsamixer as it's constantly getting muted.  I can only play one sound stream at a time whether it be event sounds, banshee, etc.  I'm not able to get sound yet via flash.  Still testing various configurations.

---

### Post by Regenweald on 2009-08-07
Update on my end, pulse seems to be ignoring the front jack. getting beautiful audio from the 'back'of my board. Green jack, 5.1 onboard. Poor testing on my part. Too accustomed to one thing working and ignored the other.

Thanks Guys :)

---

### Post by BobCFC on 2009-08-07
I've lost sound in the front port of my case

If if plugin the port at the back directly into the motherboard I get sound.

Switching output config from Analog Output to Analog Headphones turns the motherboard socket off and on at the back, but it doesn't turn the front socket on.

Using Intel HDA internal sound,I think it is the Realtek ALC888

USB headphones work fine as they appear as a second soundcard

---

### Post by VMC on 2009-08-07
The only error I get is this.
sudo grep pulseaudio /var/log/*:

" alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense."

---

### Post by MaX on 2009-08-07
Ok so now that we can configure 4.1 sound and everything...

How about a software mixer to get that down to 2.1 or 3.1?
I don't have room for all of my speakers (I have 5.1 speakers) but I would like to at least have 2.1 but that is not an option.
In windows I solved it with a software mixer that mixed the rear right and left channels into the front left and right and kept the subwoofer working.

In Linux it doesn't feel like I have a subwoofer at all.

---

### Post by miegiel on 2009-08-07
To all with **[color=red]no sound[/color] on the [color=red]front/headphones[/color] jack**, it works better after un-muting it. :twisted: see Vaun's post above.
```
alsamixer
```

Also check your levers ;)

Regrettably I need to reset it after every reboot (or every boot without the jack plugged in ... not really sure there).

> **Vaun said:**
> Still no luck with the latest updates:

pulseaudio (1:0.9.16~test4-0ubuntu4) karmic; urgency=low

  * debian/pulseaudio.install: ...and also re-add droped apport hook, and
    alsa configuration files

I can get sound only if I enable and turn the volume up via alsamixer as it's constantly getting muted.  I can only play one sound stream at a time whether it be event sounds, banshee, etc.  I'm not able to get sound yet via flash.  Still testing various configurations.

I get sound in flash if nothing else is [s]using[/s] making sound.

**Edit:** yay ... moar pulsaudio updates :D

---

### Post by rajeev1204 on 2009-08-07
I lost sound in quake 4.

Error 

asoundlib version: 1.0.20
Alsa is available
------ Alsa Sound Initialization -----
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/pcm/pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: No such file or directory
dlclose

So what can i do now?

---

### Post by Vaun on 2009-08-08
Just rebuilt pulseaudio from git and the consistent crashes have seemed to subside.  

Still testing and will report with feedback.  Pavucontrol turned from Analog Stereo to Analog Headphones seems to be keeping my sound from muting.

---

### Post by lazka on 2009-08-08
I had no sound and deleting ~/.pulse and "killall pulseaudio" (restart) got everything back to normal.

maybe it helps someone.

---

### Post by ghindo on 2009-08-08
> **psyke83 said:**
> **Edit:** It seems that the /usr/share/alsa/pulse.conf file is missing, which means that ALSA applications won't work correctly.

A temporary workaround until this gets fixed:Is there a bug report for this particular issue?

---

### Post by gnomeuser on 2009-08-08
> **VMC said:**
> The only error I get is this.
sudo grep pulseaudio /var/log/*:

" alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense."

ALSA bug, please go and file it

ubuntu-bug -p linux should get you started.

---

### Post by psyke83 on 2009-08-08
> **ghindo said:**
> Is there a bug report for this particular issue?

That issue was fixed in [1:0.9.16~test4-0ubuntu4]("https://lists.ubuntu.com/archives/karmic-changes/2009-August/005808.html"):
> pulseaudio (1:0.9.16~test4-0ubuntu4) karmic; urgency=low

  * debian/pulseaudio.install: ...and also re-add droped apport hook, and
    alsa configuration files



You can go ahead and delete the temporary ~/.asoundrc file, though it won't do much harm.

---

### Post by VMC on 2009-08-08
> **gnomeuser said:**
> ALSA bug, please go and file it

ubuntu-bug -p linux should get you started.

Thanks. Done. Bug #410887.

---

### Post by Nyoro on 2009-08-09
Do you guys see anything new in terms of volume control panel in Karmic so far? The pavu control + normal gnome volume applet really needs some work.

---

### Post by smbm on 2009-08-10
Hi all

Just installed Karmic and so far it's great.

Do have one slight issue though:

My laptop's (Lenovo R61) headphone socket doesn't seem to be able to work correctly in relation to the the internal speakers without changing settings in the software. 

When I plug something into the headphone socket under Jaunty the internal speakers would be muted and the signal would just be coming out the headphone socket.

Under Karmic I have to change a setting in PAVUcontrol.

The hardware seems to be handling muting the internal speakers on it's own though.

Is it possible to have the sound routed to both of them simultaneously and let the hardware sort out whether the internal speakers should be sounding or not?

Many thanks in advance for your help.

---

### Post by miegiel on 2009-08-10
> **smbm said:**
> Hi all

Just installed Karmic and so far it's great.

Do have one slight issue though:

My laptop's (Lenovo R61) headphone socket doesn't seem to be able to work correctly in relation to the the internal speakers without changing settings in the software. 

When I plug something into the headphone socket under Jaunty the internal speakers would be muted and the signal would just be coming out the headphone socket.

Under Karmic I have to change a setting in PAVUcontrol.

The hardware seems to be handling muting the internal speakers on it's own though.

Is it possible to have the sound routed to both of them simultaneously and let the hardware sort out whether the internal speakers should be sounding or not?

Many thanks in advance for your help.

```
alsamixer
```
or alternatively
```
gnome-alsamixer
```
and unmute headphone

---

### Post by Macchia on 2009-08-10
I'm having an awful audio using teamspeak, even adding padsp.
Bad quality, like 3 seconds of delay of my voice or anyone voice to me.
Disabling pulseaudio everything works perfectly, the only thing i've noticed in logs is "increasing latency..."

---

### Post by smbm on 2009-08-10
> **miegiel said:**
> ```
alsamixer
```
or alternatively
```
gnome-alsamixer
```
and unmute headphone

Brilliant, I figured it'd be something more complex than that, I guess I should've checked that first :oops:

Thanks

---

### Post by Starks on 2009-08-11
It normal for audio to cut out for certain apps?

---

### Post by Nullack on 2009-08-12
Ive got a return of the dreaded crackles and hissing coming from my audigy 2. Any ideas?

---

### Post by rajeev1204 on 2009-08-12
Iam having the missed or sudden crackles though iam on onboard sound.

Sometimes individual speaker gives out a burst.

---

### Post by Jay_Bee on 2009-08-12
I hear a loud "pop" sound every time before a sound is played. Anyone else with this issue?

---

### Post by taavikko on 2009-08-12
> **Jay_Bee said:**
> I hear a loud "pop" sound every time before a sound is played. Anyone else with this issue?

I presume your running intel chipset which has power_save feature,
and your chipset is powered down. Pop comes when it's powered up.

you can test this by commenting "/etc/modprobe.d/alsa-base.conf"
options snd-hda-intel power_save=10
off

---

### Post by Jay_Bee on 2009-08-12
Thanks taavikko, that helped!

---

### Post by tekstr1der on 2009-08-12
> **taavikko said:**
> I presume your running intel chipset which has power_save feature,
and your chipset is powered down. Pop comes when it's powered up.

you can test this by commenting "/etc/modprobe.d/alsa-base.conf"
options snd-hda-intel power_save=10
off

If you are running an Intel chipset with this issue, the developers would like you to file a duplicate bug as per the directions here:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

---

### Post by Jay_Bee on 2009-08-12
Thanks tekstr1der, I reported it

---

### Post by soapytheclown on 2009-08-12
> **smbm said:**
> Brilliant, I figured it'd be something more complex than that, I guess I should've checked that first :oops:

Thanks

did u find a way for this unchecking headphone thing to be persistant? everytime i reboot i have to do it :( bloody annoying!! :lolflag:

---

### Post by miegiel on 2009-08-12
> **soapytheclown said:**
> did u find a way for this unchecking headphone thing to be persistant? everytime i reboot i have to do it :( bloody annoying!! :lolflag:

I need to do that too. I'm also getting a ** PulseAudio configured for per-user sessions* warning during boot (no splash). I think it's related, but I'm not annoyed enough to take a better look yet :twisted:

---

### Post by Vaun on 2009-08-12
Upstream pulseaudio seems to be working good for me now.  No crashes in quite some time.

```
cat /proc/asound/cards
```

```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6ffc000 irq 21

```

---

### Post by mc4100 on 2009-08-12
> **miegiel said:**
> I'm also getting a ** PulseAudio configured for per-user sessions* warning during boot (no splash). I think it's related, but I'm not annoyed enough to take a better look yet :twisted:
That's normal, it's supposed to run per-user.

---

### Post by Vaun on 2009-08-12
Spoke to soon.  Testing the ubuntu packages from:

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")

Not a single crash yet.  Appears good so far.  Will continue testing.

---

### Post by BwackNinja on 2009-08-12
Anyone else having problems with surround sound control not increasing all the relevant hardware controls at the same time?

---

### Post by Nullack on 2009-08-12
Why cant ubuntu get pulse audio right? Upstream has said publicly that they consider ubuntu to have botched pulse.

I find again Im having problems with static and crackling. Im running speex float 1 and have tried rming ther pulse setup to no effect

---

### Post by Starks on 2009-08-12
I want glitch-free.

---

### Post by psyke83 on 2009-08-12
> **Starks said:**
> I want glitch-free.

Glitch-free has been enabled for a few weeks already.

---

### Post by Yes_It's_Me on 2009-08-12
I have so many issues I have no idea where to begin or if any of them are related (also quite hard to describe some of them in bug reports)

Sound is of bad quality, it seems as if when master is above say 50 percent or so it forces the PCM meter in alsamixer to 100 percent. And that makes quality go to hell, it's been the case forever that I have to turn down PCM to around 80 percent to get good quality, but pulse just doesn't stay still if you increase master.

Surround sound "sort of" works, as in it detects my AC97 onboard and allows me to use it, and sound does come out of the rear speakers (but softly), but the sound seems to kind of fade in and out of the left and right channels constantly no matter what application is producing sound. (utterly headache inducing) It's comparable to holding both your hands near your ears and alternating putting your left hand to your left ear, then right hand to the right ear over and over and over...

When changing the fade or balance settings in the sound applet all sound suddenly either bursts, randomly goes insane, dies, and occasionally this causes pulse to crash and I have to start it again.

There are random crashes, splutterings etc, and sometimes when altering volume in totem or other apps pulse dies and causes the app to go to lala land with it.

I have said it before and say it again. Sound is simply unworkable and it will be forever unworkable until we have one framework that just handles sound. No crap between alsa and pulse and esd and oss and what have you. Just one framework for everything sound related. One that actually works.

---

### Post by Vaun on 2009-08-13
Still having issues.  

I believe there may a conflict somewhere with libcanberra.  I am using the freedesktop-soundtheme which has many additional sounds incorporate, minimize, maximize, empty trash, etc., and it the sound seems to crash and restart while implementing these actions and playing another stream i.e Banshee. The sound crashes then restarts. 

It also crashes while switching gtk themes.

---

### Post by plun on 2009-08-14
New update and also for gnome-media

> pulseaudio (1:0.9.16~test4-0ubuntu6) karmic; urgency=low

  * Correct changelog entry for 1:0.9.16~test4-0ubuntu5
    (5fcb8a3c0838a4ecdb00a0af09b6e1a358b114d0 was _not_
    applied)
  * Resync proper 0050-backport-git-post-test4.patch
    from the ~ubuntu-audio-dev PPA branch
  * debian/control: Drop libgdbm-dev; use tdb-dev instead
    since it's upstream's approach

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006170.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006170.html)




> gnome-media (2.27.90-0ubuntu1) karmic; urgency=low

  [ Chris Coulson ]
  * debian/control:
    - gnome-media recommends pulseaudio.

  [ Luke Yelavich ]
  * New upstream release
    - gnome-volume-control
      + UI fixes (mnemonics, spacing)
      + Fix the Connectors list not getting updating when
        switching inputs or outputs
      + Fix the status icon disappearing when the default input
        or output gets disconnected
      + Plenty of fixes for possible feedback loops
      + Fix memory leak
      + Fix possible crasher
  * 99_autoconf.patch: refreshed

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006164.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006164.html)


Works for me....

---

### Post by Yes_It's_Me on 2009-08-14
Hmm.. the latest upgrade may be making the sound come out of the rear speakers in proportion to the front properly but my other issues still seems to exist.

At least they are working on it, I am happy that finally when i say "i want surround sound", sound actually comes out of the rear without me having to mirror front.

---

### Post by ghindo on 2009-08-14
Quick question - I don't seem to be able to turn down the volume below 14% or 16% before the volume cuts off entirely.  Has anybody else experienced this issue or heard of it?

---

### Post by Regenweald on 2009-08-14
> **ghindo said:**
> Quick question - I don't seem to be able to turn down the volume below 14% or 16% before the volume cuts off entirely.  Has anybody else experienced this issue or heard of it?

Turned my speakers to full and getting audio at 1%, -129.57db. After my initial issues, pulse is now flawless :) at least for my modest uses.

---

### Post by plun on 2009-08-15
> **ghindo said:**
> Quick question - I don't seem to be able to turn down the volume below 14% or 16% before the volume cuts off entirely.  Has anybody else experienced this issue or heard of it?

No problem for me but "phenest" started a thread about his challenge

[http://ubuntuforums.org/showthread.php?t=1234894&highlight=Dell+M90](http://ubuntuforums.org/showthread.php?t=1234894&highlight=Dell+M90)

I cannot find any bug-reports for this.....

---

### Post by plun on 2009-08-15
More fixes....:)

> libcanberra (0.15-0ubuntu2) karmic; urgency=low

  * debian/control: gnome-session-canberra should recommend libcanberra-pulse,
    to use pulseaudio as the sound backend for theme playback. (LP: #413567)

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006234.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006234.html)



---

### Post by rudenko_ruslan on 2009-08-15
> **plun said:**
> More fixes....:)
And right after this update my sound is muted at startup again :)

---

### Post by plun on 2009-08-15
> **rudenko_ruslan said:**
> And right after this update my sound is muted at startup again :)

Yup...:---)

Bug filed and it needs confirmation.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/413983](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/413983)

---

### Post by smbm on 2009-08-15
Has anyone managed to get network streaming of audio working in Karmic yet?

If so how did you do it?

---

### Post by andresmh on 2009-08-16
If your microphone is also not working since you upgraded to 9.0.16 please confirm this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/409819](https://bugs.edge.launchpad.net/ubuntu/+bug/409819)

---

### Post by Nullack on 2009-08-17
As usual pulse remains a mess for me. Static, crackling, drop outs of audio etcetc. Bug reports have been filed for many cycles now.

---

### Post by Yes_It's_Me on 2009-08-17
Is it sad that Windows 98 did a better job at audio and surround sound than karmic does?

---

### Post by miegiel on 2009-08-17
> **Yes_It's_Me said:**
> Is it sad that Windows 98 did a better job at audio and surround sound than karmic does?

Well karmic isn't finished yet. Maybe you should try win98 for 2 months and check karmic end october :D

---

### Post by Yes_It's_Me on 2009-08-17
> **miegiel said:**
> Well karmic isn't finished yet. Maybe you should try win98 for 2 months and check karmic end october :D

Regardless. I will eat my hat if karmic's pulseaudio works even somewhat satisfactory with surround sound.

---

### Post by miegiel on 2009-08-17
Just got more updates, among which the 2.6.31-6 kernel. Sound is a lot louder now. **Be warned:** check you volume before hitting play on anything :twisted:

Personally I never understood surround, but then action movies aren't my thing and in my opinion music just sounds better in stereo. It feels like karmic is getting better every couple of days.

---

### Post by plun on 2009-08-19
Test 5 is outupstream:

> 
Heya,

Forgot to mention that I released another snapshot of 0.9.16
yesterday:

[http://0pointer.de/public/pulseaudio-0.9.16-test5.tar.gz](http://0pointer.de/public/pulseaudio-0.9.16-test5.tar.gz)

As mentioned this brings a revamped flat volume logic where stream
volumes can increase sink volumes but can never lower it. Restored
volumes are always measured relative to the sink volume. The sink
volume hence operates as upper limit of everything that is played
which I think makes a lot of sense. This turned out to be a much
bigger change than anticipated but otoh the flat vol handling code
actually got simpler.

The two now are:

1.) stream volume changes can 'push' the sink volume, i.e. increase it
    to make sure the sink volume always stays >= the max of all stream
    volumes. stream volume changes will however never decrease the sink
    volume. a stream volume change of a stream A will never affect the
    volume of a stream B.

2) sink volume changes scale all stream volumes equally. if you halve
   the sink's volume this will halve the stream volume's too.

[B]I'd like to ask everyone to test the new flat vol logic. It's quite a
big change this late in the game for 0.9.16 unfortunately, so it would
really help if this area gets some focussed testing love.
[/B]
There's now only one thing left on my todo list before the final 0.9.16. 



[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004786.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004786.html)


Probably first arrives to Ubuntus test ppa

---

### Post by plun on 2009-08-20
Test 5 uploaded to Karmic

> pulseaudio (1:0.9.16~test5-0ubuntu1) karmic; urgency=low

  * New upstream release
  * debian/patches/0050-backport-git-post-test4.patch: drop
  * debian/patches/0050-revert-pacmd-poll-argv.patch: revert pacmd
    changesets due to excessive cpu usage (poll()) with resume:
    - aae7054b1c442e62cc1154d15a4b7a569d60d8f4
    - 5fcb8a3c0838a4ecdb00a0af09b6e1a358b114d0
  * debian/01PulseAudio: Escape hash when passed to sudo -u
    (LP: #414385). Thanks, Christoph Kurrat and Dana Goyette!
  * debian/pulseaudio.init: Add NetworkManager to
    Should-St{art,op} to fix sink/source publishing with Avahi
    (LP: #413443). Thanks, Martin-Éric Racine!

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006715.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006715.html)



---

### Post by rudenko_ruslan on 2009-08-20
> I'd like to ask everyone to test the new flat vol logic. It's quite a
big change this late in the game for 0.9.16 unfortunately, so it would
really help if this area gets some focussed testing love.
I can't get it. "Flat vol logic" - what is that? :confused:
> As mentioned this brings a revamped flat volume logic where stream
volumes can increase sink volumes but can never lower it. Restored
volumes are always measured relative to the sink volume. The sink
volume hence operates as upper limit of everything that is played
which I think makes a lot of sense. This turned out to be a much
bigger change than anticipated but otoh the flat vol handling code
actually got simpler.This?

---

### Post by plun on 2009-08-20
> **rudenko_ruslan said:**
> I can't get it. "Flat vol logic" - what is that? :confused:
This?

Well.... "upstream" language :P

I don't know exactly but it seems that Lennart has changed how all volume adjustments is hooked up.

We have some threads with volume adjustments challengies....

---

### Post by crimsun on 2009-08-20
I posted the call for testers at [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html).

Please direct all responses to that mailing list (per request). If you must respond on the forum, please preface your posts with [pulse 0.9.16-test5] in the subject, preferably under [http://ubuntuforums.org/showthread.php?p=7816629#post7816629](http://ubuntuforums.org/showthread.php?p=7816629#post7816629).

---

### Post by plun on 2009-08-20
> **crimsun said:**
> I posted the call for testers at [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html).

Please direct all responses to that mailing list (per request). If you must respond on the forum, please preface your posts with [pulse 0.9.16-test5] in the subject, preferably under [http://ubuntuforums.org/showthread.php?p=7816629#post7816629](http://ubuntuforums.org/showthread.php?p=7816629#post7816629).

Thanks crimsun for informing us   !

Another option is maybe a sticky thread within this forum ???

---

### Post by andresmh on 2009-08-20
omg, I'm so scared of running pulseaudio updates!

not really, my sound is so messed up that at this point I'll do any sound updates :)

---

### Post by plun on 2009-08-20
> **andresmh said:**
> omg, I'm so scared of running pulseaudio updates!

not really, my sound is so messed up that at this point I'll do any sound updates :)

Well, Karmic IS a development version, if you are scared just install Jaunty !

Karmic should not be stable.... must be tested and bugs must be filed.

:)

---

### Post by uBeer on 2009-08-20
> **rudenko_ruslan said:**
> I can't get it. "Flat vol logic" - what is that? :confused:
This?

I think he means that now the volume control is logarithmic. That means that if you have the slider halfway, it only takes off about 3dB, which means: you'll hear half the volume.

So now the amount you move the slider linearly changes the way you experience the volume of the audio.

---

### Post by hugmenot on 2009-08-20
> **uBeer said:**
> I think he means that now the volume control is logarithmic.

No. Decibels are by definition logarithmic. What flat volume control refers to is that all volume sliders are staggered and controlled as one.

---

### Post by jmmL on 2009-08-20
> **hugmenot said:**
> No. Decibels are by definition logarithmic. What flat volume control refers to is that all volume sliders are staggered and controlled as one.

Is there a way to undo this flat volume control? It's really bugging me that the PCM is set too high by default and I can't lower it because of this. The high PCM leads to noticable distortion and crackling on my laptop speakers.

---

### Post by psyke83 on 2009-08-20
> **jmmL said:**
> Is there a way to undo this flat volume control? It's really bugging me that the PCM is set too high by default and I can't lower it because of this. The high PCM leads to noticable distortion and crackling on my laptop speakers.

I get this problem as well. Perhaps it would be better to file a bug and try to get this distortion issue fixed in the ALSA kernel drivers themselves? Unfortunately the ALSA bugtracker seems to be largely ignored.

---

### Post by jmmL on 2009-08-20
> **psyke83 said:**
> I get this problem as well. Perhaps it would be better to file a bug and try to get this distortion issue fixed in the ALSA kernel drivers themselves? Unfortunately the ALSA bugtracker seems to be largely ignored.

Would it be possible for you to file and then I'll confirm it? I've only ever filed one bug before (against pulseaudio) and I felt that it took a long time to get anywhere because I'm inexperienced in providing the right information. Once it was taken off my hands (by Daniel Chen I think) it started to build a lot more momentum and the bug was squashed shortly thereafter.

Also, what hardware do you have? I get this information from alsamixer:```
Card: HDA Intel
Chip: Conexant CX20549 (Venice)
```and```
jmmL@karmic-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by psyke83 on 2009-08-20
> **jmmL said:**
> Would it be possible for you to file and then I'll confirm it? I've only ever filed one bug before (against pulseaudio) and I felt that it took a long time to get anywhere because I'm inexperienced in providing the right information. Once it was taken off my hands (by Daniel Chen I think) it started to build a lot more momentum and the bug was squashed shortly thereafter.

Also, what hardware do you have? I get this information from alsamixer:```
Card: HDA Intel
Chip: Conexant CX20549 (Venice)
```and```
jmmL@karmic-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I can't, as I have a AC'97 based card. Perhaps file a bug on Launchapad against the "linux" source package (but mention that the new PulseAudio version makes the problem more difficult to manage).

You could file the bug like so:
```
$ ubuntu-bug alsa-base
```

Also mention that the new PulseAudio version in Karmic (which uses flat volume logic) makes this problem more unmanageable.

See: [https://wiki.ubuntu.com/Audio/AlsaInfoOutput](https://wiki.ubuntu.com/Audio/AlsaInfoOutput)

---

### Post by uBeer on 2009-08-20
> **hugmenot said:**
> No. Decibels are by definition logarithmic. What flat volume control refers to is that all volume sliders are staggered and controlled as one.

Ah, so true! Thanks for pointing that out. I don't know if I really like the flat volume thing, but maybe after a bit of experimenting it'll grow on me.

---

### Post by Hero of Time on 2009-08-20
I just got test5 as an update, and now I lost my analogue output. I'm left with digital stereo, which produces very good quality audio on my analogue speakers (aka, no sound at all). I can't change any setting or sink to analogue. Does anyone have an idea how to fix this?

lspci -vvv
```
01:0d.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Micro-Star International Co., Ltd. Device 1009
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at de00 [size=32]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106
```
/proc/asound/devices:
```
  2:        : timer
  3: [ 0- 0]: raw midi
  4: [ 0- 3]: digital audio playback
  5: [ 0- 3]: digital audio capture
  6: [ 0- 2]: digital audio playback
  7: [ 0- 2]: digital audio capture
  8: [ 0- 1]: digital audio playback
  9: [ 0- 1]: digital audio capture
 10: [ 0- 0]: digital audio playback
 11: [ 0- 0]: digital audio capture
 12: [ 0]   : control
```
Any more info needed?

---

### Post by martijntje on 2009-08-20
I had that too! I just killed pulseaudio, when it restarted a few seconds later everything worked again.

---

### Post by Hero of Time on 2009-08-20
Well, that didn't work for me. Killed it a dozen times, rebooted three times, still no analogue output.

If it matters at all, pavucontrol says I don't have any cards available for configuration. I used to have that so I could select my speaker set up and input options.

---

### Post by martijntje on 2009-08-20
Have you checked the profile is not set to 'Off' in the configuration tab of pavucontrol?

---

### Post by Hero of Time on 2009-08-20
There are no devices in the configuration tab of the volume control. That's the whole problem.

---

### Post by Regenweald on 2009-08-20
The new behavior is quite cool. I'd try to describe it but i think everyone in here is already testing. I think it is quite sensible. Especially when managing output from multiple apps simultaneously.

---

### Post by hugmenot on 2009-08-20
I especially like that with flat volume control the volume is controlled via the analog amp output of the sound card. This gives the best sound quality.

With the old system you could use digital attenuation in several places separately: In the app (e.g. Gstreamer), for the audio stream, for the tunnel or audio sink, for the PCM slider in ALSA. And then finally for the physical output (this one analog/voltage-based). Every digital attenuation leads to loss of bit depth. And that affects signal to noise ratio.

The problem people report here is, I think, that ALSA for some drivers stupidly allows to the PCM slider to get above 0dB. This is digital amplification that easily leads to clipping and distortion if you play audio that is mastered with no headroom.

---

### Post by Hero of Time on 2009-08-20
I removed PA 0.9.16 test 5 and grabbed 0.9.15 from a ppa. At least that one gives me audio.

---

### Post by crimsun on 2009-08-21
> **Hero of Time said:**
> I removed PA 0.9.16 test 5 and grabbed 0.9.15 from a ppa. At least that one gives me audio.

Please file a bug using "ubuntu-bug pulseaudio" _while running 0.9.16-test5_ if you're experiencing problems.

More than likely you'll need "killall pulseaudio && pulseaudio -vvvv" to get any useful debugging information to attach to the bug report.

---

### Post by crimsun on 2009-08-21
> **jmmL said:**
> Is there a way to undo this flat volume control? It's really bugging me that the PCM is set too high by default and I can't lower it because of this. The high PCM leads to noticable distortion and crackling on my laptop speakers.

echo flat-volumes = no|tee ~/.pulse/daemon.conf && killall pulseaudio

---

### Post by plun on 2009-08-21
Update uploaded

> pulseaudio (1:0.9.16~test5-0ubuntu2) karmic; urgency=low

  [ Daniel T Chen ]
  * debian/patches/0051-leave-hp-enabled.patch: Leave
    headphones enabled in the default analog mixer profiles

  [ Luke Yelavich ]
  * debian/patches/0052-reduce-lib-linking.patch: Reduce the number of
    libraries that the libpulse libraries are linked against as much as
    possible, to lessen the work needed to make bi-arch libpulse packages
    in the future
  * Remove pulseaudio.desktop once again, as the a11y special case is
    not being honoured, and we have the Xsession.d script to start pulse
    for us, to avoid any races with other apps wanting to play sounds on
    session startup

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006819.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006819.html)



---

### Post by yelo3 on 2009-08-21
With this new version I lost analog output. I only have digital HDMI output selectable. So I currently can't hear anything!

---

### Post by Hero of Time on 2009-08-21
> **crimsun said:**
> Please file a bug using "ubuntu-bug pulseaudio" _while running 0.9.16-test5_ if you're experiencing problems.

More than likely you'll need "killall pulseaudio && pulseaudio -vvvv" to get any useful debugging information to attach to the bug report.
It won't be any help, because I'm actually running Jaunty and added the Karmic repo for only a few packages that are newer (like Xfce, 4.6.0 has a nasty bug that is fixed in 4.6.1).

> **yelo3 said:**
> With this new version I lost analog output. I only have digital HDMI output selectable. So I currently can't hear anything!
Sounds a lot like my problem, where PA didn't detect, nor used, my analogue output.

---

### Post by yelo3 on 2009-08-21
But previously it worked!

---

### Post by Hero of Time on 2009-08-21
> **yelo3 said:**
> But previously it worked!
So did it with me, I got analogue output with test 4 just fine, but test 5 didn't use/see analogue anymore.

---

### Post by yelo3 on 2009-08-21
my problem was solved with a trink, see here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/417176](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/417176)

---

### Post by jmmL on 2009-08-21
> **crimsun said:**
> echo flat-volumes = no|tee ~/.pulse/daemon.conf && killall pulseaudio

I've executed this and wasn't able to independently move PCM and master using alsamixer. I rebooted and I still wasn't able. Am I right in thinking that this command should have allowed me to do so?

---

### Post by BwackNinja on 2009-08-21
I you really want to independently control your alsa sliders, then edit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf and /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common and replace "merge" for any slider you want to control with "ignore". I'm hoping this'll work really nicely soon.

---

### Post by peacewithall on 2009-08-24
The latest version seems to have brought back a nasty crash bug with Openal applications, the application(Secondlife), forces pulseaudio to quit after a few minutes. Unfortunately the workaround of killing pulseaudio, just causes pulseaudio to restart automatically. Removing pulseaudio pulls out the volume adjust function of my keyboard and TV remote, and starting the 'sounds' option from the menu I am met with an error window. Other than the problems with the volume and sounds, removing pulseaudio returns my system to fully working reliable audio. I hope it gets fixed.

---

### Post by plun on 2009-08-24
Test 6 is out upstream, no sign of it yet for Karmic...

> Yo!

This should be the final test release before the final release of
0.9.16. My todo list of bugs to fix before the release is now empty.

[http://0pointer.de/public/pulseaudio-0.9.16-test6.tar.gz](http://0pointer.de/public/pulseaudio-0.9.16-test6.tar.gz)

Biggest changes are Wim's MMX/SSE optimization work and numerous
changes to the udev code to fix all races on session switching. Also,
we will now automatically decrease the watermark times in the ALSA
code again after a phase of stability. i.e. previously on a drop out
PA would make sure it woke up earlier for the next buffer fill
iteration to avoid the drop-out from then on. This scheme was
one-way. On each drop-out we woke up earlier and earlier, effectively
increasing the CPU load each time without the chance to revert
this. With these changes we will sleep for longer again after a phase
where we didn't come near to a drop-out.

 
Lennart Poettering                        Red Hat, Inc.
lennart [at] poettering [dot] net

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004841.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-August/004841.html)


---

### Post by plun on 2009-08-25
Test 6 uploaded and built

> pulseaudio (1:0.9.16~test6-3-g57e1-0ubuntu1) karmic; urgency=low

  [ Daniel T Chen ]
  * New git snapshot of origin/master (0.9.16~test6-3-g57e1)
  * debian/patches/:
    + 0050-revert-pacmd-poll-argv.patch: Retain, still seeing
      excessive cpu usage with resume
    - 0051-leave-hp-enabled.patch: Drop, applied upstream
    + 0051-reduce-lib-linking.patch: Refresh and rename previous
      0052-reduce.. so that minimal changes are made

  [ Luke Yelavich ]
  * debian/control: Promote rtkit from suggests to recommends

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/007092.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/007092.html)



---

### Post by | MM | on 2009-08-25
Anyone using banshee-gapless?  If i double click to start a new song (as opposed to just letting banshee shuffle to a new song) the volume resets to 100% from whatever i had it set at.  Bit annoying.

---

### Post by hanzomon4 on 2009-08-25
urgh.... What a mess

---

### Post by Yes_It's_Me on 2009-08-25
> **hanzomon4 said:**
> urgh.... What a mess

Couldn't put it better.

---

### Post by taavikko on 2009-08-25
I must be the exception here, since PA is working nice, with me.

---

### Post by plun on 2009-08-25
> **taavikko said:**
> I must be the exception here, since PA is working nice, with me.

Yup, works excellent also here....:guitar:

Except som minor mute and system sound trouble which for sure will be solved.;)

---

### Post by peacewithall on 2009-08-25
Installed test 6 and I have to say things have got worse, pulseaudio has definitely returned to it's first introduction into Hardy for me, it's a real shame, because pulseaudio seemed to work OK in Jaunty, it still had minor problems, but now it's quite bad, it crashes so easily. Most applications recover audio, so this crashing goes unnoticed. The most annoying part about this , is that pulseaudio is so tied into Ubuntu now, I would like the option to remove it, and try another sound server, without too much trouble.

---

### Post by taavikko on 2009-08-25
> **peacewithall said:**
> now, I would like the option to remove it, and try another sound server, without too much trouble.

In what way, you can't uninstall it?
```
Remove the following packages:
libcanberra-pulse
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
ubuntu-desktop

```

seems to be **not so much tied to** ubuntu.

---

### Post by peacewithall on 2009-08-25
I have removed it and all sounds worked fine, but I had problems with adjusting the volume from my keyboard and remote control(e.g. stopped being recognised by Ubuntu as volume inputs), I also had a volume 'on screen' indicator, which no longer appears with pulseaudio removal, and choosing 'sounds' from the menu results in an error, which means that menu option is targeted at pulseaudio. Removing pulseaudio gives me back all my sounds and I am able to watch youtube, play rhythmbox, run games, and all sounds work together flawlessly, but removing it results in the above problems, with the volume controls.

---

### Post by zenarcher on 2009-08-25
Same here.  I just removed pulseaudio and got my sound back with Kubuntu Karmic.

Cheers,
zenarcher

---

### Post by crimsun on 2009-08-25
> **hanzomon4 said:**
> urgh.... What a mess

Are you filing bugs and/or confirming existing ones? If so, which ones?

---

### Post by crimsun on 2009-08-25
> **zenarcher said:**
> Same here.  I just removed pulseaudio and got my sound back with Kubuntu Karmic.

Cheers,
zenarcher

That's obviously not the right approach to fix the bug (albeit it "gets your sound back"). In the future, please file a bug using "ubuntu-bug pulseaudio", or confirm an existing one, thanks.

---

### Post by crimsun on 2009-08-25
People experiencing PA crashing with *malloc errors need to ensure that libcanberra-pulse remains installed before filing a bug report.

---

### Post by crimsun on 2009-08-25
> **Hero of Time said:**
> It won't be any help, because I'm actually running Jaunty and added the Karmic repo for only a few packages that are newer (like Xfce, 4.6.0 has a nasty bug that is fixed in 4.6.1).

Doing this spot-upgrading is a recipe for disaster when it comes to the audio stack. You need to upgrade udev, linux, alsa-lib, pulseaudio, gstreamer, (pavucontrol, paprefs,) ...

At that point you may as well be running Karmic from a thumbdrive or CD.

---

### Post by crimsun on 2009-08-25
> **jmmL said:**
> I've executed this and wasn't able to independently move PCM and master using alsamixer. I rebooted and I still wasn't able. Am I right in thinking that this command should have allowed me to do so?

No, disabling flat volumes is an entirely different workaround to an entirely different problem. I was addressing the first part of your question.

---

### Post by tekstr1der on 2009-08-25
> **crimsun said:**
> People experiencing PA crashing with *malloc errors need to ensure that libcanberra-pulse remains installed before filing a bug report.

Installing this package results in absolutely no sound for me. Anything that would generate a sound by clicking on it causes sound to mute immediately. Without this package, I have only one known issue with sound, the mute on startup. Otherwise looks like I'm one of the lucky few with pulse.

---

### Post by zenarcher on 2009-08-25
> **crimsun said:**
> That's obviously not the right approach to fix the bug (albeit it "gets your sound back"). In the future, please file a bug using "ubuntu-bug pulseaudio", or confirm an existing one, thanks.

I guess I'm a bit frustrated about filing bugs.  I filed one a couple of months ago in regard to not being able to read CD's in my drive...it was confirmed, but went no further.  I even installed another drive, but still the problem persists.  I'm stuck using a jump drive to transfer data, using another computer.  

(Yes, I did supply all the information requested to go with the bug report.)

Cheers,
zenarcher

---

### Post by fab.head on 2009-08-25
I've just installed pulseaudio (1:0.9.16~test6-3-g57e1-0ubuntu1) on Karmic Alpha 4 (with all the other recent updates installed) and rebooted.
Now my sound output has gone...

Now when I open Sound Preferences I have the following under each tab:

- **Hardware** > **Choose a device to configure:** > (empty field)

- **Input** > **Inpout volume** > (Grayed out)
- **Input** > **Choose a device for sound input:** >  (empty field)

- **Output** > **Choose a device for sound output:** > Null Output


My computer is a HP laptop, model DV9850EL.

**lspci | grep -i audio** returns the following (if this could be of any help):
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by rajeev1204 on 2009-08-25
Got a whopping 90 MB of updates including pulseaudio and now sound is totally distorted.

Starts with the krrrrrr then slows to a stop then starts again.

---

### Post by peacewithall on 2009-08-25
Other errors are occurring using Ubuntu's own applications, audio mixing don't seem to work at all for me. For example, a crash occurs 100% of the time starting a audio stream with Rhythmbox, opening firefox and attempting to play a Youtube video, pulseaudio dies instantly, I get this error message:

Couldn't start playback

pa_stream_writable_size() failed: Connection terminated.

---

### Post by rajeev1204 on 2009-08-25
> **peacewithall said:**
> pulseaudio dies instantly


Thats why ***this time*** i killed pulseaudio myself :D

Edit:It cannot be killed it seems,so it had to be stopped for now.We'll deal with it later:p

---

### Post by andresmh on 2009-08-25
> **taavikko said:**
> In what way, you can't uninstall it?
```
Remove the following packages:
libcanberra-pulse
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
ubuntu-desktop

```

seems to be **not so much tied to** ubuntu.

What are the consequences of uninstalling ubuntu-desktop? 

Once pulse is uninstalled does the system automatically use alsa?

---

### Post by crimsun on 2009-08-25
> **fab.head said:**
> I've just installed pulseaudio (1:0.9.16~test6-3-g57e1-0ubuntu1) on Karmic Alpha 4 (with all the other recent updates installed) and rebooted.
Now my sound output has gone...

Look at your volume settings in alsamixer, amixer, ...

---

### Post by taavikko on 2009-08-25
> **andresmh said:**
> What are the consequences of uninstalling ubuntu-desktop? 


Pretty much nothing happens when you uninstall it.

You'll only miss what would be the final release. Unless you watch closely on ubuntu-meta upgrades to find out. to manually install the correct packages.

---

### Post by crimsun on 2009-08-25
> **andresmh said:**
> What are the consequences of uninstalling ubuntu-desktop? 

Once pulse is uninstalled does the system automatically use alsa?

ubuntu-desktop is just a metapackage useful for smoothing dist-upgrades.

Assuming that you haven't created /etc/asound.conf and/or ~/.asoundrc, removing all PA-related packages (well, using --force-depends) falls back to an existing sound subsystem. If you've mucked with OSSv4, then it's used. Otherwise, the default ALSA (directly) is used.

You don't need to purge PA to use ALSA directly, however. Just look at /usr/bin/pulse-session and /etc/pulse/client.conf for hints. I've written separately how to prevent PA from starting on login and how to prevent it from autospawning.

---

### Post by peacewithall on 2009-08-25
I uninstalled pulseaudio just to see if there were any underlying problems, there wasn't the sound worked perfectly, so pulseaudio is back on, I think unless your using Karmic as your main operating system, you may need to remove pulseaudio for now (Although I dont recommend it), I think pulseaudio requires more testing, after all it proved for me at least it can work, as it's currently working just right, in Jaunty right now on my system. 

Of course if pulseaudio is finalized in it's current state and released with Karmic final, I will then have to remove it permanently, but it's just in testing phase, so hopefully that won't happen.

---

### Post by crimsun on 2009-08-25
> **peacewithall said:**
> Couldn't start playback

pa_stream_writable_size() failed: Connection terminated.

We need a backtrace (use the bug reporter or apport when the app crashes). The error message itself is fairly useless.

---

### Post by crimsun on 2009-08-25
> **peacewithall said:**
> Of course if pulseaudio is finalized in it's current state and released with Karmic final, I will then have to remove it permanently, but it's just in testing phase, so hopefully that won't happen.

Jaunty's audio stack is **very** different to Karmic's. A simple comparison of PA versions is similar to comparing popcorn to desk chairs.

---

### Post by fab.head on 2009-08-25
> **crimsun said:**
> Look at your volume settings in alsamixer, amixer, ...

The volume settings are correct in alsamixer.
The alsa volume is neither muted nor very low. 

It's just pulseaudio which reports no input/output devices...

---

### Post by tuppe666 on 2009-08-25
> /var/log/syslog:Aug 25 18:04:04 Ubuntu-box pulseaudio[3153]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_01_0b.0" card_name="alsa_card.pci-0000_01_0b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
/var/log/syslog:Aug 25 18:04:04 Ubuntu-box pulseaudio[3153]: module-alsa-card.c: Failed to find a working profile.


I haven't seen anyone else with this! I get this over and over again. First time I have had a problem with pulseaudio on any machine, apart from the volume getting muted with an update.

---

### Post by tuppe666 on 2009-08-25
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 16
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfddfd000 irq 16

I have two cards...but the second one is my tv-card which is the one I don't want to use hmmm

---

### Post by crimsun on 2009-08-25
> **fab.head said:**
> The volume settings are correct in alsamixer.
The alsa volume is neither muted nor very low. 

It's just pulseaudio which reports no input/output devices...

Please use "ubuntu-bug pulseaudio", then attach the dump from "killall pulseaudio;pulseaudio -vvvv" to the created bug report.

---

### Post by crimsun on 2009-08-25
> **tuppe666 said:**
> I haven't seen anyone else with this! I get this over and over again. First time I have had a problem with pulseaudio on any machine, apart from the volume getting muted with an update.

Please use "ubuntu-bug pulseaudio", then attach the dump from "killall pulseaudio;pulseaudio -vvvv" to the created bug report.

---

### Post by fab.head on 2009-08-26
> **crimsun said:**
> Please use "ubuntu-bug pulseaudio", then attach the dump from "killall pulseaudio;pulseaudio -vvvv" to the created bug report.


Thanks crimsun.

All done (subscribed to bug #394500 in pulseaudio)

---

### Post by fab.head on 2009-08-26
> **fab.head said:**
> Thanks crimsun.

All done (subscribed to bug #394500 in pulseaudio)

Hmmm, now I'm not quite sure I subscribed to the correct bur report..

**[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500")**

crimsun, could you please have a look at the above link and let me know whether I need to file a new bug report instead?

Many thanks

---

### Post by fab.head on 2009-08-26
Please disregard my previous post.
It seems that the status of this bug (394500) has just been changed from **Invalid** to **New**

---

### Post by Anubis on 2009-08-26
Can only play audio from one source at a time, kubuntu 9.10. And now just noticed only time video has sound is if I move the volume meter constantly. Enabling muilticast rtp causes a flood of network traffic.:confused:

Can't get ANY help in #ubuntu+1.

---

### Post by fab.head on 2009-08-28
> **fab.head said:**
> Please disregard my previous post.
It seems that the status of this bug (394500) has just been changed from **Invalid** to **New**



I've now tried to connect a USB audio interface to my laptop, and this one gets perfectly recognised.
Therefore the issue must be with the internal audio device (which used to work fine up to pulseaudio 1:0.9.16~test5).

Regarding my internal audio device, **cat /proc/asound/cards** returns the following message:

>  0 [Intel ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 22

What can I do to get my internal audio device recognised?

Thanks

---

### Post by fab.head on 2009-08-28
PS: I have also tried the latest update from [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa") with no success...

---

### Post by rajeev1204 on 2009-08-28
I reported new bug here.I followed procedure as requested by crimsun.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420597](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420597)


I hope this gets fixed soon.




rajeev

---

### Post by fab.head on 2009-08-28
Update: I've just tested **pulseaudio 1:0.9.16~test6-30-g300384-0ubuntu1** from the **Ubuntu Audio Dev team PPA**...

The internal soundcard (ALC268) is still not recognised.

The Output still says Null Output

---

### Post by fab.head on 2009-08-29
I think I've found a temporary workaround (not a solution) to my "Null Output" issue

I've opened **/etc/pulse/default.pa** and commented 4 lines.

Before:
> ### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

After:
> ### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif

Then I killed/restated pulseaudio and now I have audio input/output from the internal audio device.

Still, the Hardware tab under Sound Preferences is empty, as if there was no audio device available.

**Sound Preferences** > **Hardware** > **Choose a device to configure:** > (empty field)

---

### Post by golusweet on 2009-08-30
I'm using latest kernel.

My laptop's mute button goes red always, when I open sound preferences, It goes back to normal blue.

It's very wierd, since with latest kernel, sound does not get mute on startup. still, laptop's key shows red.


Also, sound does not play nice with VLC.

How can i report these bugs?

---

### Post by miegiel on 2009-08-30
> **golusweet said:**
> I'm using latest kernel.

My laptop's mute button goes red always, when I open sound preferences, It goes back to normal blue.

It's very wierd, since with latest kernel, sound does not get mute on startup. still, laptop's key shows red.


Also, sound does not play nice with VLC.

How can i report these bugs?

This should get you started : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I'm having issues in VLC too but I'm not really sure if it's pulse or VLC (hitting pause and play a couple of times helps).

---

### Post by andresmh on 2009-08-30
I also have problems with sound while playing a dvd on vlc. My solution so far has also been to pause it and play again.

---

### Post by plun on 2009-08-31
Alsa 1.0.21 released.

> **ALSA 1.0.21 Released With Many Driver Updates**
Posted by Michael Larabel on August 31, 2009
With it being a few months since the release of ALSA 1.0.20, it's now time for the ALSA 1.0.21 update. The ALSA driver package update (finally) brings the Creative X-Fi Linux driver officially along with a horde of updates to the other drivers and more.

The Creative X-Fi driver for the Advanced Linux Sound Architecture has improved a fair amount over the past few months and is certainly better than Creative's binary driver mess before they gave into open-source.

The CMI8788 Oxygen driver (used by sound cards like the Razer Barracuda AC-1) now includes support for HDAV S/PDIF inputs and when it comes to sound cards now works with the ASUS Xonar Essence ST. Another driver used by many Linux users is the HDA codec driver, which now supports many new notebooks and other sound devices. The HDA Intel driver also supports a new AMD HD audio device. On top of this, the USB audio support for ALSA has received numerous improvements in ALSA 1.0.21.

The lengthy change-log listing all of the work that has went into ALSA 1.0.21 can be read at alsa-project.org. Beyond the ALSA drivers, the ALSA library, utilities, tools, plug-ins, and PyALSA have all been updated to a version 1.0.21 status. These Linux sound driver updates come with optimal timing for getting into the Linux 2.6.32 kernel, with the merge window opening in a week or two.

[http://www.phoronix.com/scan.php?page=news_item&px=NzQ5NQ](http://www.phoronix.com/scan.php?page=news_item&px=NzQ5NQ)





Compiled and installed it but the mute challenge remains....

I hope that this anyway will be included in Karmic.

---

### Post by BobCFC on 2009-09-02
Fix for the pops/crackles in VLC


[http://ubuntuforums.org/showthread.php?t=1256366](http://ubuntuforums.org/showthread.php?t=1256366)

---

### Post by Podex on 2009-09-03
> **plun said:**
> Alsa 1.0.21 released.




Compiled and installed it but the mute challenge remains....

I hope that this anyway will be included in Karmic.

According to [_this guy_](http://www.phoronix.com/forums/showpost.php?p=90415&postcount=12) it will. He has [_a PPA_](https://edge.launchpad.net/~thefirstm/+archive/karmic-testing) where you can get this new version.

---

### Post by plun on 2009-09-03
Test 7 is out upstream, also available within Ubuntu dev ppa

> Heya!

Here's another test release. The previous test release was supposed to
be the last one, but uh, given the amount of changes committed I
decided to push another snapshot.

[http://0pointer.de/public/pulseaudio-0.9.16-test7.tar.gz](http://0pointer.de/public/pulseaudio-0.9.16-test7.tar.gz)

Some of the changes are quite important, as they fix some memory
corruption in the MMX/SSE code.

Lennart

-- 
Lennart Poettering                        Red Hat, Inc.
lennart [at] poettering [dot] net


[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-September/004921.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-September/004921.html)





---

### Post by fab.head on 2009-09-04
> **plun said:**
> Test 7 is out upstream, also available within Ubuntu dev ppa

Thanks.

Installed, but still have the same problem: Null Output :(

---

### Post by golusweet on 2009-09-04
Anyone knows how to fix mute problem?

---

### Post by crimsun on 2009-09-04
> **Podex said:**
> According to [_this guy_](http://www.phoronix.com/forums/showpost.php?p=90415&postcount=12) it will. He has [_a PPA_](https://edge.launchpad.net/~thefirstm/+archive/karmic-testing) where you can get this new version.

Huh? No, it (1.0.21 wholesale) won't.

We already carry the important fixes from alsa-lib 1.0.21 in our alsa-lib source.

The kernel will remain with what it ships (aka alsa-kernel 1.0.20 + fixes pushed to Linus by Takashi, so it's 1.0.20 + backported fixes from alsa-kernel git) barring any last-minute bug fixes I can push in.

alsa-utils, alsa-plugins, and alsa-tools will see backported bug fixes if necessary.

To reiterate: no, Karmic will not be carrying 1.0.21.

---

### Post by fab.head on 2009-09-06
Hi Crimsum,

Do you have any idea if and when bug # [**394500**]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500") will be taken care of?

I've tried all the latest updates from Ubuntu Audio Dev team PPA but still the "Null Output" issue is there

Thanks
fab

---

### Post by Podex on 2009-09-07
> **crimsun said:**
> Huh? No, it (1.0.21 wholesale) won't.

We already carry the important fixes from alsa-lib 1.0.21 in our alsa-lib source.

The kernel will remain with what it ships (aka alsa-kernel 1.0.20 + fixes pushed to Linus by Takashi, so it's 1.0.20 + backported fixes from alsa-kernel git) barring any last-minute bug fixes I can push in.

alsa-utils, alsa-plugins, and alsa-tools will see backported bug fixes if necessary.

To reiterate: no, Karmic will not be carrying 1.0.21.

Thanks for clearing that up. Good luck with all the work that is still ahead for Karmic.

---

### Post by xerosis on 2009-09-17
I'm still seeing PA muted on boot with the latest packages, I couldn't find a bug for it so is it supposed to be fixed or has no-one reported a bug?

---

### Post by waspbr on 2009-09-17
anyone with an hp laptop here? for some strange reason PA won't detect my tx1320us my audiocard,though it alsamixer shows it and it is also listed on lspci. 

sorry if this has already been discussed before, though I would appreciate any insights.

---

### Post by plun on 2009-09-20
PA ver 9.0.18 is out upstream

> Heya!

Here's another release:

[http://0pointer.de/lennart/projects/pulseaudio/pulseaudio-0.9.18.tar.gz](http://0pointer.de/lennart/projects/pulseaudio/pulseaudio-0.9.18.tar.gz)

These are mostly bug fixes, so an update is recommended.

This also installs a Vala .vapi file now by default. This should be
considered a preview only. It's only minimally tested, so this will
probably receive quite a few more updates in the near future.

Lennart Poettering                        Red Hat, Inc.
lennart [at] poettering [dot] net

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-September/005019.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-September/005019.html)




Available at [Ubuntu-dev ppa ]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")

---

### Post by hugmenot on 2009-09-20
Too bad they disabled flat volume now. I found it great and will certainly re-enable it.

---

### Post by fab.head on 2009-09-20
> **waspbr said:**
> anyone with an hp laptop here? for some strange reason PA won't detect my tx1320us my audiocard,though it alsamixer shows it and it is also listed on lspci. 

sorry if this has already been discussed before, though I would appreciate any insights.

Have a look at this bug report: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500")

It seems that the softmodem driver is somehow conflicting with pulseaudio.

You could disable/remove the **Software modem** driver from **System** > **Administration** > **Hardware drivers** and see whether this helps you.

---

### Post by Slug71 on 2009-09-20
Whoa, 0.9.17 and 0.9.18 came out fast!!

---

### Post by andresmh on 2009-09-20
I added [https://launchpad.net/~ubuntu-audio-dev](https://launchpad.net/~ubuntu-audio-dev) repo to my source lists but I noticed I can only select .17 or .18. Is there any repo where I can find older versions? The reson I ask is because my mic only worked with .15

Thanks!

---

### Post by Slug71 on 2009-09-20
> **andresmh said:**
> I added [https://launchpad.net/~ubuntu-audio-dev](https://launchpad.net/~ubuntu-audio-dev) repo to my source lists but I noticed I can only select .17 or .18. Is there any repo where I can find older versions? The reson I ask is because my mic only worked with .15

Thanks!

Since Karmic is still in Alpha(testing) we should really be testing Karmic vanilla at this stage and filing bugs.

---

### Post by andresmh on 2009-09-20
I totally agree. In fact, I've submited my bug a while ago [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819) and every time there is a pulse update I apply it to see if the bug is fixed. Unfortunatelly the bug is still Importance = "Undecided" So I would like to roll back to 0.9.15 and keep applying the latest updates until the bug is (hopefully) fixed.

---

### Post by Slug71 on 2009-09-20
> **andresmh said:**
> I totally agree. In fact, I've submited my bug a while ago [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819) and every time there is a pulse update I apply it to see if the bug is fixed. Unfortunatelly the bug is still Importance = "Undecided" So I would like to roll back to 0.9.15 and keep applying the latest updates until the bug is (hopefully) fixed.

Have you tried tweaking Volume Control, input devices etc?

You may want to see if you can find Alpha 2 or 3 which still has .15 i think.
Check you configuration then and submit it to your bug report and for yourself check to see how your input devices have changed with the newer releases.

---

### Post by andresmh on 2009-09-20
Yup, I've tried pretty much everything there is to try. In fact, I think the problem is that there are two microphone devices in my laptop. The built-in that is next to the screen and another one that has a jack-in port next to the jack for the headphones. If I plug in a microphone to the mic jack it works. So this leads me to think it's just the other mic that is not working with Pulse. In fact, I *think* I remember seeing 2 input devices before those Pulse Audio updates and now I only see one.

---

### Post by Slug71 on 2009-09-20
[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

Scroll down.

---

### Post by andresmh on 2009-09-20
Not sure what you are point out on that page :)

---

### Post by Slug71 on 2009-09-21
> **andresmh said:**
> Not sure what you are point out on that page :)

Karmic Alpha 2 iso., Should have Pulseaudio .15

---

### Post by andresmh on 2009-09-21
Ah yes, I can get the files but I am already on Alpha 6 and unless I downgrade to Alpha 2 I don't know how I can downgrade Pulse Audio. Do you?

---

### Post by psyke83 on 2009-09-21
> **andresmh said:**
> Ah yes, I can get the files but I am already on Alpha 6 and unless I downgrade to Alpha 2 I don't know how I can downgrade Pulse Audio. Do you?

From your bug report:

> As per this post: [http://ubuntuforums.org/showpost.php?p=7739984&postcount=17](http://ubuntuforums.org/showpost.php?p=7739984&postcount=17) I created:
~/.asoundrc
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

I suggest that you delete this file, as Ubuntu already has this configuration in place (the ALSA libraries are patched to detect PulseAudio's presence and enable these plugins when necessary). The post you quoted was at a time when these plugins were not even installed (and I mistakenly believed that it was merely the configuration that was missing).

You may want to try a newer PulseAudio release here: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

Another possibility that may be worth investigating is to disable the flat volume logic. See: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-August/009227.html)

I realize you've probably done this, but a reminder to do so after you have tested the newer PulseAudio package and/or with flat volume disabled:

I recommend you run PulseAudio Volume Control (pavucontrol) and check the Input Devices tab - it exposes PulseAudio related options that aren't yet available in the Sound Preferences applet or alsamixer. In your bug report, I only see a screenshot of the Recording tab.

---

### Post by Gourgi on 2009-09-21
i'm searching my logs but i can't figure it out...
is glith-free enabled by default in karmic's pulseaudio?
if no how one can enable it?

**edit**: nevermind, i figured it out 
```
killall pulseaudio && pulseaudio -vvv > Desktop/log.log 2>&1
```
```
$ cat Desktop/log.log |grep tsched
D: module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" **tsched=yes** ignore_dB=no card_properties="module-udev-detect.discovered=1"'
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
```
it is enabled :-D

---

### Post by Slug71 on 2009-09-21
> **andresmh said:**
> Ah yes, I can get the files but I am already on Alpha 6 and unless I downgrade to Alpha 2 I don't know how I can downgrade Pulse Audio. Do you?

Well you can install Alpha 2, and upgrade to Alpha 6 by updating and just unchecking any Pulseaudio Updates. Youll have a ton of updates to do but you will be at Alpha 6 with PA .15.

---

