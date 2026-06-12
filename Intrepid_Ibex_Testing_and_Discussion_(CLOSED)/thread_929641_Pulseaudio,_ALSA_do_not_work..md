---
title: "Pulseaudio, ALSA do not work."
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by badp on 2008-09-25
Pulseaudio has never really worked on my computer, for some reason. As of the latest few batches of updates, though, ALSA (which was my workaround) fails as well.

Error messages from the Audio applet:

[LIST]
[*]**Intel ICH6 with ALC250 Intel ICH6 - IEC958 (Alsa)**: (no sound output)
[*]**Intel ICH6 with ALC250 Intel ICH6 (OSS)**: (seems to work correctly)
[*]**Intel ICH6 with ALC250 Intel ICH6 (OSS)**: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
[*]**OSS**: (seems to work correctly)
[*]**ESD**: (no sound output)
[*]**ALSA**: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.
[*]**Pulseaudio**: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument[/LIST]

However, when I try and put all playbacks on OSS, nothing happens.

Weirdly enough, the net result is that applications like espeak or TeamSpeak work all the time flawlessly. Sonata also works fine.

None of the three were activated while I did the tests above, though.

From /var/log:

```

badp:/var/log$ grep "pulseaudio" user.log -i   
*<snip; system started with Sonata stopped and full PulseAudio configuration.>*
Sep 25 12:05:55 bPortatile pulseaudio[6239]: ltdl-bind-now.c: Failed to find original dlopen loader.
Sep 25 12:05:55 bPortatile pulseaudio[6239]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Sep 25 12:05:55 bPortatile pulseaudio[6239]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Sep 25 12:05:55 bPortatile pulseaudio[6239]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Sep 25 12:05:55 bPortatile pulseaudio[6239]: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_266e_alsa_playback_0"): initialization failed.
Sep 25 12:13:16 bPortatile pulseaudio[6239]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.
Sep 25 12:13:40 bPortatile pulseaudio[6239]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.
Sep 25 13:01:01 bPortatile pulseaudio[6239]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.

```

Suggestions?

EDIT: I'm running: libpulsecore5 0.9.10-2ubuntu6, gstreamer0.10-pulseaudio 0.10.10-1, linux-sound-base 1.0.17.dfsg-2ubuntu1. Default config.

---

### Post by tturk on 2008-09-25
I am also having no sound since the last three days with an Intel 82801H (ICH8 Family) HD Audio Controller. My Intrepid is updated with the latest kernel (2.6.27-4) and the latest pulseaudio libs.
In gstreamer-properties, when I select "pulseaudio" plugin, it says in the device "Unsupported".

---

### Post by rbmorse on 2008-09-25
I see all the same fine things here, too.  

My audio is via USB...Bose Companion FIVE system...and the Sound applet shows two options:

Bose Corporation Bose USB Bose USB Audio (OSS)
Bose Corporation Bose USB Bose USB Audio (ALSA)

The OSS selection works.  The ALSA does not. Autodetect works.

---

### Post by ELD on 2008-09-25
I get no sound what-so-ever, totem says "cannot connect to this stream".

Tested with OSS via the sound in preferences and sound worked.

---

### Post by Slug71 on 2008-09-25
Working fine for me but i hope PA 0.9.12 and ALSA 1.0.18 or at least PA 0.9.12 makes it to Intrepid before Kernel Freeze. I think this may solve a lot of peoples issues.
Intrepid currently has 0.9.10 which means its 2 versions behind.
Updates can always be given to fix bugs etc.

---

### Post by ELD on 2008-09-25
Well once it is all final i will be doing a fresh install anyway as i always do, so hopefuly that will fix any lingering sound problems my end.

---

### Post by dreamstogo on 2008-09-25
I too have the "failed to connect stream: invalid argument problem" when sound settings are left as default. If I change them to OSS, totem works.

This only happened after today's batch of updates.

---

### Post by ELD on 2008-09-25
Well hopefully it will get fixed it someone has sent a bug report for it, as it is highly annoying.

---

### Post by badp on 2008-09-25
Rebooting fixed it for me.

Now I've switched to full PulseAudio, let's see what that will bring me.

---

### Post by Quikee on 2008-09-25
I have problems too.. I think it is not pulseaudio but but the updated "libasound2" (alsa). I have the problem in games like openarena for example and in "Multimedia system selector", but not anywhere else.

---

### Post by lordofwinds on 2008-09-25
Yeah, this is my bug today, too :(

Rebooting is not solution.

I uninstall all pulseaudio packages and ALSA works!

Can anybody post a bug to launchpad?

---

### Post by rbmorse on 2008-09-25
For me, after the last update, ALSA works even if I don't uninstall the PulseAudio packages, after a reboot.

---

### Post by plun on 2008-09-25
> **rbmorse said:**
> For me, after the last update, ALSA works even if I don't uninstall the PulseAudio packages, after a reboot.

I saw the other thread and you must probably move the stream to USB.

I am also using USB output and the same time analog output.  Benefit
with PulseAudio

But you need [padevchooser]("http://packages.ubuntu.com/intrepid/padevchooser") > and the Volume control for moving streams

* * Start the auxiliary tools PulseAudio Volume Control, PulseAudio Volume Meter, PulseAudio Manager, PulseAudio Preferences*


```
sudo apt-get install padevchooser
```


[[img]http://ubuntu-pics.de/thumb/3673/padev_8QJh8o.jpg[/img]](http://ubuntu-pics.de/bild/3673/padev_8QJh8o.jpg)


```

 alsamixer -Dhw
```

Gives alsas mixer and not the PA mixer....

---

### Post by psyke83 on 2008-09-25
> **plun said:**
> I saw the other thread and you must probably move the stream to USB.

I am also using USB output and the same time analog output.  Benefit
with PulseAudio

But you need [padevchooser]("http://packages.ubuntu.com/intrepid/padevchooser") > and the Volume control for moving streams

* * Start the auxiliary tools PulseAudio Volume Control, PulseAudio Volume Meter, PulseAudio Manager, PulseAudio Preferences*


```
sudo apt-get install padevchooser
```


[[img]http://ubuntu-pics.de/thumb/3673/padev_8QJh8o.jpg[/img]](http://ubuntu-pics.de/bild/3673/padev_8QJh8o.jpg)


```

 alsamixer -Dhw
```

Gives alsas mixer and not the PA mixer....

It's better to right-click on the desired device on the Output Devices tab and select "Default" - then all programs (using PulseAudio) will select this device as the default for PulseAudio.

---

### Post by psyke83 on 2008-09-25
> **plun said:**
> I saw the other thread and you must probably move the stream to USB.

I am also using USB output and the same time analog output.  Benefit
with PulseAudio

But you need [padevchooser]("http://packages.ubuntu.com/intrepid/padevchooser") > and the Volume control for moving streams

* * Start the auxiliary tools PulseAudio Volume Control, PulseAudio Volume Meter, PulseAudio Manager, PulseAudio Preferences*


```
sudo apt-get install padevchooser
```


[[img]http://ubuntu-pics.de/thumb/3673/padev_8QJh8o.jpg[/img]](http://ubuntu-pics.de/bild/3673/padev_8QJh8o.jpg)


```

 alsamixer -Dhw
```

Gives alsas mixer and not the PA mixer....

It's better to right-click on the desired device on the Output Devices tab and select "Default" - then all programs will select this device as the default.

---

### Post by pluckypigeon on 2008-09-25
[http://ubuntuforums.org/showthread.php?t=866965]("http://ubuntuforums.org/showthread.php?t=866965")

try this thread

---

### Post by 68pontiac on 2008-09-25
I have a pulseaudio problem I've been dealing with for over a week and I just want to ditch it and go with ALSA. The latest updates (today, 9/25) don't seem to do much and changing the sound output to ALSA and testing it gives me a crazy error. I can post the output of the error (or screenshot) when I get home if it would help.

Perhaps I need to remove all pulseaudio packages?

---

### Post by plun on 2008-09-25
> **psyke83 said:**
> It's better to right-click on the desired device on the Output Devices tab and select "Default" - then all programs will select this device as the default.

No :)... the big benefit with PA is that you can have different outputs.

Skype only to analog front > earplugs

A Sound system to USB out

and so on,  otherwise we can remove PulseAudio...

Just great when I got USB out working...

---

### Post by plun on 2008-09-25
> **68pontiac said:**
> I have a pulseaudio problem I've been dealing with for over a week and I just want to ditch it and go with ALSA. The latest updates (today, 9/25) don't seem to do much and changing the sound output to ALSA and testing it gives me a crazy error. I can post the output of the error (or screenshot) when I get home if it would help.

Perhaps I need to remove all pulseaudio packages?

Restart with this command from a terminal

```
pulseaudio -k; sleep 4; pulseaudio -vv
```

---

### Post by jualin on 2008-09-25
I am running Intrepid Ibex with the latest updates and I had to make a manual change for Banshee and Totem to play audio. I am dual booting Intrepid and Hardy and they are sharing the same home partition and the same user. In Hardy I had my sound preferences options to use Alsa, and in Intrepid that didn't work for some reason. I went today to the sound preferences utility using System, Preferences, Sound and selected PulseAudio Sound Server for every Device and now Totem and Banshee work. Something I noticed was that VLC was playing music flawlessly before the PA change on the Sound Preferences. Hope this helps someone!
[[IMG]http://img144.imageshack.us/img144/1323/screenshotwo4.th.png[/IMG]](http://img144.imageshack.us/my.php?image=screenshotwo4.png)[[IMG]http://img144.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by 68pontiac on 2008-09-25
> **plun said:**
> Restart with this command from a terminal

```
pulseaudio -k; sleep 4; pulseaudio -vv
```

May I ask what exactly this command does? Will it need to be run on every startup?

---

### Post by plun on 2008-09-25
> **68pontiac said:**
> May I ask what exactly this command does? Will it need to be run on every startup?

This command kills running pulseaudio and the restarts in log mode

You can then probably find good clues about what is wrong within the terminal window.

All apps using sound must be closed before running this command otherwise
they lost sound or freezes.   

There are strange bugs and I filed one about esd_auth which controls permissions but no answer. 

So good clues and "**filing a bug**" is the only way....

---

### Post by 68pontiac on 2008-09-25
I appreciate the help, I'll give this a try when I get home. If this doesn't solve any problems I assume I have an ALSA issue?

---

### Post by rbmorse on 2008-09-25
I don't know what I did...but I did a reboot for an unrelated reason and just had my first login sound on Intrepid, ever.

Yea!

---

### Post by RAOF on 2008-09-25
> **Slug71 said:**
> Working fine for me but i hope PA 0.9.12 and ALSA 1.0.18 or at least PA 0.9.12 makes it to Intrepid before Kernel Freeze.
...

It won't.  0.9.12 introduces a bunch of (highly annoying, and serious) regressions, even with ALSA from git.  Pulseaudio 0.9.11 included some big new default features, and these are still not quite regression-free.

---

### Post by ktp on 2008-09-25
Something in recent update did break pulse plugin because I had flash 10 working correctly using /etc/asound.conf redirecting sound to pulse.  But after recent updates, flash will not play sound unless I stop all other apps playing sound.

---

### Post by jualin on 2008-09-25
> **ktp said:**
> Something in recent update did break pulse plugin because I had flash 10 working correctly using /etc/asound.conf redirecting sound to pulse.  But after recent updates, flash will not play sound unless I stop all other apps playing sound.

ouch! I am looking at the current updates right now that Update Manager suggests and I see an update on "alsa-utils" and "libasound2-plugins", everything else is not sound related. Maybe you can try to go back a version using Synaptic Package Manager, by right clicking on the package, selecting properties, and forcing a new version. Hope this helps!

---

### Post by 68pontiac on 2008-09-26
Can somebody help me understand what this means, and what I can do to fix it?
```
christopher@christopher-desktop:~$ pulseaudio
W: ltdl-bind-now.c: **Failed to find original dlopen loader**.
W: main.c: **setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted**
W: main.c: **setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted**
**[COLOR="Red"]E: shm.c: Invalid shared memory segment size[/COLOR]**
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

---

### Post by ktp on 2008-09-26
> **jualin said:**
> ouch! I am looking at the current updates right now that Update Manager suggests and I see an update on "alsa-utils" and "libasound2-plugins", everything else is not sound related. Maybe you can try to go back a version using Synaptic Package Manager, by right clicking on the package, selecting properties, and forcing a new version. Hope this helps!

I think it is the pulseaudio packages itself that cause this regression.  I downgraded them to 0.9.10-2ubuntu2 and things work again.

[https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio)

---

### Post by plun on 2008-09-26
> **68pontiac said:**
> Can somebody help me understand what this means, and what I can do to fix it?
```
christopher@christopher-desktop:~$ pulseaudio
W: ltdl-bind-now.c: **Failed to find original dlopen loader**.
W: main.c: **setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted**
W: main.c: **setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted**
**[COLOR="Red"]E: shm.c: Invalid shared memory segment size[/COLOR]**
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

I believe you just have updated your PC with new sound applications.
A reboot probably solves it.

Another solution is to open Nautilus  > **Ctrl-h** for hidden folders  > go to /.pulse and remove all files

Log out and in  and it probably works....:)  or use the command mentioned above.

---

### Post by nystire on 2008-09-26
> **plun said:**
> Restart with this command from a terminal

```
pulseaudio -k; sleep 4; pulseaudio -vv
```

This fixed it for me, and after rebooting it continued working - for now.

Quite a few of these problems appear to be caused by people updating, and then not rebooting. It may sound very "Windows-like", but the problems could be caused by the newer programs being unable to connect to the drivers on the fly.

---

### Post by ktp on 2008-09-26
For all that say it's working for them, 

Can you try to play a music in Rythmbox and then go to youtube and see if you can hear the music and the sound from the video?

---

### Post by rbmorse on 2008-09-26
Works here. Although I ended up with a rather disturbing combination of Sarah Palin and Madame Butterfly (Callas/Von Karajan)

---

### Post by 68pontiac on 2008-09-26
> **plun said:**
> I believe you just have updated your PC with new sound applications.
A reboot probably solves it.

Another solution is to open Nautilus  > **Ctrl-h** for hidden folders  > go to /.pulse and remove all files

Log out and in  and it probably works....:)  or use the command mentioned above.

I'm still failing to get sound, even trying both solutions. Removing the files did nothing and killing the pulseaudio command does nothing. Running a sound check from the preferences menu returns the following error:

---

### Post by jualin on 2008-09-26
> **68pontiac said:**
> I'm still failing to get sound, even trying both solutions. Removing the files did nothing and killing the pulseaudio command does nothing. Running a sound check from the preferences menu returns the following error:

How about if you change from ALSA to Pulse Audio on the Sound Preferences window on your attachment? I had the same problem when trying to test sound with ALSA, but switching to Pulse Audio did the trick

---

### Post by plun on 2008-09-26
> **68pontiac said:**
> I'm still failing to get sound, even trying both solutions. Removing the files did nothing and killing the pulseaudio command does nothing. Running a sound check from the preferences menu returns the following error:

Please take a look at this howto

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
```

aplay -l

lspci -v
```


Fully updated Intrepid ? 


```
sudo apt-get install ubuntu-desktop
```

---

### Post by ktp on 2008-09-26
> **rbmorse said:**
> Works here. Although I ended up with a rather disturbing combination of Sarah Palin and Madame Butterfly (Callas/Von Karajan)

Can you show your System -> Preferences -> Sound and make sure pulseaudio is running?

Are you also running updated Intrepid (8.10)?

---

### Post by psyke83 on 2008-09-26
The settings in System -> Preferences -> Sound are *not* system-wide settings, they only affect GStreamer applications (Totem, Rhythmbox, most official GNOME multimedia applications). The Playback options should *always* be set to Autodetect for best results.

With recent updates to PulseAudio, it is *not* required to have an .asoundrc/asound.conf configuration. The alsa-lib libraries have been patched so that if they detect the presence of PulseAudio, then the appropriate ALSA configuration is used.

The only useful applications for troubleshooting are PulseAudio Manager and PulseAudio Volume Control.

a) Install the PulseAudio GUI utilities:
```
$ sudo apt-get install padevchooser
```
b) System/Preferences/Sound. Set all Playback options to Autodetect.
c) Play a movie/music file in Totem.
d) Open the PulseAudio Volume Control (accessible via PulseAudio Device Chooser applet) and look at the Playback tab *while Totem is still playing*.

If you see no entry in PA Volume Control's Playback tab, PulseAudio is probably not running.

If you see an entry but hear no audio, it's possible that it's playing to the incorrect sound device. Right-click on the Totem playback entry and select "Move stream...", and try any alternative options.

By the way, there's already a HOWTO for PulseAudio.

For Intrepid: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)
For Hardy, with more detail about how PulseAudio functions in the Appendices: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by ktp on 2008-09-26
Thanks psyke83 for the information; it really helps.  But I already had it setup and working then it broke because of latest updates to Intrepid.  And I was just trying to find out why it was working for some and not for other.

---

### Post by 68pontiac on 2008-09-26
> **jualin said:**
> How about if you change from ALSA to Pulse Audio on the Sound Preferences window on your attachment? I had the same problem when trying to test sound with ALSA, but switching to Pulse Audio did the trick

Changing to either PulseAudio or Autodetect produces no sound and causes the Sound Preferences to lock up. I have to manually kill the process with the System Monitor. I haven't had any luck with [this thread]("http://ubuntuforums.org/showthread.php?t=866965") either.

---

### Post by ultra2k on 2008-10-06
> **nystire said:**
> This fixed it for me, and after rebooting it continued working - for now.

Quite a few of these problems appear to be caused by people updating, and then not rebooting. It may sound very "Windows-like", but the problems could be caused by the newer programs being unable to connect to the drivers on the fly.

pulseaudio -k; sleep 4; pulseaudio -vv
fixes but for me rebooting broke the audio again

---

### Post by pHr34kY on 2008-10-06
> **ultra2k said:**
> pulseaudio -k; sleep 4; pulseaudio -vv
fixes but for me rebooting broke the audio again

Same here. I'm running Intrepid on an Acer Aspire One. PluseAudio is running on reboot, but sound doesn't work until a restart it.

---

