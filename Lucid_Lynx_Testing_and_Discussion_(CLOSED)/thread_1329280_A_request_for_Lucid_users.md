---
title: "A request for Lucid users"
date: 2009-11-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by psyke83 on 2009-11-17
Hi,

I haven't upgraded to the development release yet, so I'm asking you folks for a favour... :)

Can you test my PulseAudio Equalizer on Lucid and report your experience? I want to verify that it's working correctly (I've tested it in Karmic against PA 0.9.20 from the [Ubuntu Audio Dev team PPA]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa"), but there may be other issues that cause it to fail in Lucid).

The link should be visible in my signature - thanks in advance.

Note 1: If your audio isn't working, then don't bother to test the script - it assumes a working PulseAudio configuration.
Note 2: If you have problems (and your audio otherwise works normally), you can get some debugging info like so:
```
$ pulseaudio-equalizer.sh debug
```

---

### Post by VMC on 2009-11-17
Setting up pulseaudio-module-x11 (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-module-gconf (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-module-bluetooth (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-esound-compat (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up libpulse-mainloop-glib0 (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...

That's completed, then:
===
$  pulseaudio-equalizer.sh debug
pulseaudio-equalizer.sh: command not found
===
$ sudo find / -name pulseaudio-equalizer.sh -print
vmc@vmc-desktop:~$


**What am I missing here?**

---

### Post by autocrosser on 2009-11-17
I've got it--I'll test tonight---

---

### Post by shakaran on 2009-11-17
You should make a PPA on LaunchPad, your app is awesome!.

Testing on lucid:
```
$ pulseaudio-equalizer.sh debug
Please wait (approximate time: 25 seconds)...
/usr/bin/pulseaudio-equalizer.sh: line 133: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 134: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 135: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 145: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 146: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 147: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 153: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 154: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 155: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 161: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 162: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 163: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 169: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 170: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 171: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
Finished! Log created at /home/shakaran/Desktop/pulseaudio-equalizer.log.
```

```
$ sudo cat /home/shakaran/Desktop/pulseaudio-equalizer.log
State: Initial state
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1e.2.analog-stereo plugin=mbeq_1197 label=mbeq control=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_1e.2.analog-stereo 131072
set-sink-mute alsa_output.pci-0000_00_1e.2.analog-stereo 0
### END: Equalized audio configuration
---

State: Disabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

State: Enabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

```

```
$ pulseaudio-equalizer.sh enable
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Suspending clients...
Unloading module-ladspa-sink...
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.pci-0000_00_1e.2.analog-stereo) preamp (2x)...
Transferring current mute (0) & volume (200%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Resuming clients...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [enabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
-------------------------------------

```

You also need make a l18n. I would love translate your app to spanish.

---

### Post by shakaran on 2009-11-17
> **VMC said:**
> Setting up pulseaudio-module-x11 (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-module-gconf (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-module-bluetooth (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up pulseaudio-esound-compat (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...
Setting up libpulse-mainloop-glib0 (1:0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1) ...

That's completed, then:
===
$  pulseaudio-equalizer.sh debug
pulseaudio-equalizer.sh: command not found
===
$ sudo find / -name pulseaudio-equalizer.sh -print
vmc@vmc-desktop:~$


**What am I missing here?**


You need download the .deb file:
[http://ubuntuforums.org/attachment.php?attachmentid=136581&d=1258467115](http://ubuntuforums.org/attachment.php?attachmentid=136581&d=1258467115)

Main thread: [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

---

### Post by Regenweald on 2009-11-17
I love you. will post a better response once I've tested some more. working :P

---

### Post by psyke83 on 2009-11-17
> **shakaran said:**
> You should make a PPA on LaunchPad, your app is awesome!.

I already have my PPA set up for other packages, but I want to wait until the script has been verified as working for as many people as possible. The debsource may also need some cleaning up.

> Testing on lucid:
```
$ pulseaudio-equalizer.sh debug
Please wait (approximate time: 25 seconds)...
/usr/bin/pulseaudio-equalizer.sh: line 133: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 134: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 135: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 145: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 146: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 147: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 153: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 154: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 155: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 161: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 162: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 163: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 169: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 170: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 171: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
Finished! Log created at /home/shakaran/Desktop/pulseaudio-equalizer.log.
```

The permission denied errors indicate a problem. Make sure that you only run the script with user privileges, from a user account, and that PulseAudio is working.

> ```
$ sudo cat /home/shakaran/Desktop/pulseaudio-equalizer.log
State: Initial state
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1e.2.analog-stereo plugin=mbeq_1197 label=mbeq control=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_1e.2.analog-stereo 131072
set-sink-mute alsa_output.pci-0000_00_1e.2.analog-stereo 0
### END: Equalized audio configuration
---

State: Disabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

State: Enabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=
PA_CURRENT_MUTE=
PA_CURRENT_VOLUME=
PA_REAL_VOLUME=0
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

```


This would indicate that the equalizer wasn't set up properly. However, the output may be inaccurate due to the "permission denied" errors. I also noticed that you're running "sudo cat" - sudo shouldn't be necessary.

> ```
$ pulseaudio-equalizer.sh enable
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Suspending clients...
Unloading module-ladspa-sink...
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.pci-0000_00_1e.2.analog-stereo) preamp (2x)...
Transferring current mute (0) & volume (200%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Resuming clients...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [enabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
-------------------------------------

```

This output looks fine, except for the 200% volume part - it appears to be mixing up the "preamp" with your actual volume. Perhaps that's a side-effect of the earlier problem with permissions.

> You also need make a l18n. I would love translate your app to spanish.

I'd be happy to add translations. The code is a bit messy (since it's my first try at programming in Python), so I'll need to clean things up, and read about how to properly add l18n string support.

Keep in mind that the bash script is only the support for the actual PulseAudio Equalizer interface (in the Applications -> Sound & Video menu) - you can't easily customize settings with the bash script alone.

---

### Post by Regenweald on 2009-11-17
Ok. Notes:

Outside of working flawlessly for my needs, I'd say the only thing of note is the break and distortion in audio when applying settings but I think I understand why this occurs so it's not a negative really.

Only thing I'd say could improve it currently is on the fly adjustments as in while the slider is moving ( I tested using spacelord by monster magnet and was expecting *slight* changes as is the usual case with linux equalizers. I was pleasantly blown out of my chair by your pre-amp) having said that, I assume that there are limitations to my suggestion or you would have done it already.

One question, I had been hearing of an equalizer for PA for a while now but I'm guessing this is independent of upstream, could you clarify ?

Gushing:
The Exaile project removed the equalizer for their reasons and in recent weeks I had really been missing the functionality of a system wide equalizer. Thought' of 'I can't wait for the PA equalizer I heard of' began to be common. This is a wonderful enhancement to my desktop. Thank you so much for the hard work and software that 'just works'.

Shot attached of it in action for anyone interested.

Edit: Side note, I used 'dpkg -i' for installation and the dependencies were not on my system, a simple aptitude update and safe upgrade pulled in the deps and configured the equalizer. No problems, just notes on my installation.

---

### Post by slakkie on 2009-11-17
Before I test it, what it the name of the PPA so I can add it to my sources.
I see based on the screenshots is mostly aimed at Gnome, is there a KDE GUI available? (I know I can run Gnome apps in KDE and the other way around, just asking).

---

### Post by psyke83 on 2009-11-17
> **Regenweald said:**
> Ok. Notes:

Outside of working flawlessly for my needs, I'd say the only thing of note is the break and distortion in audio when applying settings but I think I understand why this occurs so it's not a negative really.

This is a rough outline of what the script does
[LIST]
[*]Loads the equalization settings that are saved by the GUI;
[*]Pauses all PulseAudio client streams (applications' audio);
[*]Creates/reloads a LADSPA sink (output device) with the new equalization settings;
[*]Transfers all clients (applications) to the new LADSPA sink;
[*]Sets the proper volume/mute levels (the ALSA sink is set to the preamp volume, and the LADSPA sink is set to the volume that the ALSA sink previously used);
[*]Sets the LADSPA sink as the new master (default) sink.
[*]Resumes all PulseAudio client streams.
[/LIST]

Unfortunately, the pausing/resuming is necessary or else there is a risk of applications (or PulseAudio itself) crashing.

> Only thing I'd say could improve it currently is on the fly adjustments as in while the slider is moving ( I tested using spacelord by monster magnet and was expecting *slight* changes as is the usual case with linux equalizers. I was pleasantly blown out of my chair by your pre-amp) having said that, I assume that there are limitations to my suggestion or you would have done it already.

That would be ideal, but it's not feasible due to the necessity of stream pausing/resuming when changing settings.

If I were to change the interface to apply settings when you move a slider, the interface would lag significantly, and you would hear the distortions with each adjustment.

> One question, I had been hearing of an equalizer for PA for a while now but I'm guessing this is independent of upstream, could you clarify ?

The upstream equalizer is different - you can read about that on the [SystemEqualizer]("http://pulseaudio.org/wiki/SystemEqualizer") wiki page. I wasn't able to get the pqaeq interface working (even with the proper python-qt4/python-qt4-dbus packages installed), so I can't say what are the differences compared to my implementation.

My implementation uses the "module-ladspa-sink" module, which has been present in PulseAudio for some time - but quite buggy until recently. Since 0.9.19 (the version shipped with Karmic), the instability seems to have been solved, so writing an interface became feasible.

The bash script automates the process of setting up the configuration, and the GUI allows the actual customizations/adjustments to be made.

> Gushing:
The Exaile project removed the equalizer for their reasons and in recent weeks I had really been missing the functionality of a system wide equalizer. Thought' of 'I can't wait for the PA equalizer I heard of' began to be common. This is a wonderful enhancement to my desktop. Thank you so much for the hard work and software that 'just works'.

Shot attached of it in action for anyone interested.

You're welcome ;).

P.S. The dedicated thread goes into more detail as to the meaning of LADSPA, etc.

---

### Post by shakaran on 2009-11-17
> **psyke83 said:**
> I already have my PPA set up for other packages, but I want to wait until the script has been verified as working for as many people as possible. The debsource may also need some cleaning up.

Do not be afraid to put code unstable, the PPA is precisely for that. We are human, it is dificult that the code would be perfect always.

> **psyke83 said:**
> 
The permission denied errors indicate a problem. Make sure that you only run the script with user privileges, from a user account, and that PulseAudio is working.


The .deb file put the file with this permissions by default:

$ ls -ial /usr/bin/pulseaudio-equalizer.sh 
2685661 -rwxr-xr-x 1 root root 17349 2009-11-17 13:30 /usr/bin/pulseaudio-equalizer.sh

If I run as root:
```
$ sudo pulseaudio-equalizer.sh debug
[sudo] password for shakaran: 
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Please wait (approximate time: 25 seconds)...
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
E: core-util.c: Home directory /home/shakaran not ours.
E: main.c: Failed to kill daemon: Permission denied
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Home directory /home/shakaran not ours.
No PulseAudio daemon running, or not running as session daemon.
Finished! Log created at /home/shakaran/Desktop/pulseaudio-equalizer.log.

```


> **psyke83 said:**
> 
I also noticed that you're running "sudo cat" - sudo shouldn't be necessary.

$ cat /home/shakaran/Desktop/pulseaudio-equalizer.log
cat: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied

> **psyke83 said:**
> 
I'd be happy to add translations. The code is a bit messy (since it's my first try at programming in Python), so I'll need to clean things up, and read about how to properly add l18n string support.
It is easy! More than you think! Take a look to gettext. You can see on my app source code called Tivion (link on my signature and Launchpad).

> **psyke83 said:**
> 
Keep in mind that the bash script is only the support for the actual PulseAudio Equalizer interface (in the Applications -> Sound & Video menu) - you can't easily customize settings with the bash script alone.
Yeah, I know. I test the GUI too. When you set the setting a little flicker appear on tray icon. Could you avoid it?

---

### Post by psyke83 on 2009-11-17
> **slakkie said:**
> Before I test it, what it the name of the PPA so I can add it to my sources.
I see based on the screenshots is mostly aimed at Gnome, is there a KDE GUI available? (I know I can run Gnome apps in KDE and the other way around, just asking).

It's a deb attached to the post, not part of any PPA. And since the GUI part is a PyGTK script, it won't work in KDE without the GNOME/GTK libraries and Python GTK support packages installed. I don't know how difficult it would be to write a QT/KDE version.

There's another problem, however. As far as I'm aware, Kubuntu doesn't use PulseAudio at all (and to install it may preset integration issues with Phonon, etc).

---

### Post by shakaran on 2009-11-17
> **psyke83 said:**
> It's a deb attached to the post, not part of any PPA. And since the GUI part is a PyGTK script, it won't work in KDE without the GNOME/GTK libraries and Python GTK support packages installed. I don't know how difficult it would be to write a QT/KDE version.


You dont need make a port for QT anyways. PyGTK works perfectly with KDE.

---

### Post by psyke83 on 2009-11-17
> **shakaran said:**
> The .deb file put the file with this permissions by default:

$ ls -ial /usr/bin/pulseaudio-equalizer.sh 
2685661 -rwxr-xr-x 1 root root 17349 2009-11-17 13:30 /usr/bin/pulseaudio-equalizer.sh

That's normal, I think?

> If I run as root:

Please don't do this! The script writes settings to ~/.pulse/ - if the script is executed with root privileges, the setting files may have root privileges, and the interface may no longer have the ability to save settings properly.

Please, delete these files:
```
$ sudo rm ~/.pulse/equalizerrc* ~/.pulse/presets -r
```

Don't run the script as root again, otherwise you'll need to delete the files again. The next update will check for and prohibit execution of the script as root.

> It is easy! More than you think! Take a look to gettext. You can see on my app source code called Tivion (link on my signature and Launchpad).


Will do, thanks.

> Yeah, I know. I test the GUI too. When you set the setting a little flicker appear on tray icon. Could you avoid it?

No, that can't be avoided. When PulseAudio selects a new default sink, the applet needs to restart in order to get the accurate settings.

When the EQ is enabled, you'll see the volume icon's tooltip changes to "LADSPA Plugin Multiband EQ on... (your sound card)".

---

### Post by slakkie on 2009-11-17
> **psyke83 said:**
> It's a deb attached to the post, not part of any PPA. And since the GUI part is a PyGTK script, it won't work in KDE without the GNOME/GTK libraries and Python GTK support packages installed. I don't know how difficult it would be to write a QT/KDE version.

There's another problem, however. As far as I'm aware, Kubuntu doesn't use PulseAudio at all (and to install it may preset integration issues with Phonon, etc).

I use pulseaudio on Karmic (KDE). Would be a nice testcase to see if or how it works :)

I'll download the .deb for now.

---

### Post by shakaran on 2009-11-17
> **psyke83 said:**
> That's normal, I think?

Please, delete these files:
```
$ sudo rm ~/.pulse/equalizerrc* ~/.pulse/presets -r
```


I did the rm command, and the same:

```
$ pulseaudio-equalizer.sh debug
Please wait (approximate time: 25 seconds)...
/usr/bin/pulseaudio-equalizer.sh: line 133: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 134: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 135: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
rm: remove write-protected regular file `/home/shakaran/.pulse/default.pa'? y
/usr/bin/pulseaudio-equalizer.sh: line 145: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 146: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 147: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 153: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 154: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 155: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 161: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 162: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 163: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 169: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 170: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
/usr/bin/pulseaudio-equalizer.sh: line 171: /home/shakaran/Desktop/pulseaudio-equalizer.log: Permission denied
Finished! Log created at /home/shakaran/Desktop/pulseaudio-equalizer.log.

```

---

### Post by Vanishing on 2009-11-17
> **psyke83 said:**
> This is a rough outline of what the script does
[LIST]
[*]Loads the equalization settings that are saved by the GUI;
[*]Pauses all PulseAudio client streams (applications' audio);
[*]Creates/reloads a LADSPA sink (output device) with the new equalization settings;
[*]Transfers all clients (applications) to the new LADSPA sink;
[*]Sets the proper volume/mute levels (the ALSA sink is set to the preamp volume, and the LADSPA sink is set to the volume that the ALSA sink previously used);
[*]Sets the LADSPA sink as the new master (default) sink.
[*]Resumes all PulseAudio client streams.
[/LIST]

Unfortunately, the pausing/resuming is necessary or else there is a risk of applications (or PulseAudio itself) crashing.



That would be ideal, but it's not feasible due to the necessity of stream pausing/resuming when changing settings.

If I were to change the interface to apply settings when you move a slider, the interface would lag significantly, and you would hear the distortions with each adjustment.



The upstream equalizer is different - you can read about that on the [SystemEqualizer]("http://pulseaudio.org/wiki/SystemEqualizer") wiki page. I wasn't able to get the pqaeq interface working (even with the proper python-qt4/python-qt4-dbus packages installed), so I can't say what are the differences compared to my implementation.

My implementation uses the "module-ladspa-sink" module, which has been present in PulseAudio for some time - but quite buggy until recently. Since 0.9.19 (the version shipped with Karmic), the instability seems to have been solved, so writing an interface became feasible.

The bash script automates the process of setting up the configuration, and the GUI allows the actual customizations/adjustments to be made.



You're welcome ;).

P.S. The dedicated thread goes into more detail as to the meaning of LADSPA, etc.

nice one psyke83!!:D

---

### Post by psyke83 on 2009-11-17
> **shakaran said:**
> I did the rm command, and the same:

```
$ pulseaudio-equalizer.sh debug
<snip>
```

Ah yes, also delete the log:
```
$ sudo rm ~/Desktop/pulseaudio-equalizer.log
```

Is anyone else getting "permission denied" messages?

---

### Post by shakaran on 2009-11-17
> **psyke83 said:**
> Ah yes, also delete the log:
```
$ sudo rm ~/Desktop/pulseaudio-equalizer.log
```

Is anyone else getting "permission denied" messages?

Yep, the same errors too.

---

### Post by Regenweald on 2009-11-17
My setup is running pretty flawlessly, what series of commands can I run to submit the details of my system ?

---

### Post by MacUntu on 2009-11-17
'2x' doesn't seem to be a good default for 'Preamp'. *ouchmyears*

Other than that it seems to work fine.

Edit: When clicking the 'Apply Settings' button when 'EQ Enabled' isn't ticked, it really shouldn't pause the stream.

---

### Post by sports fan Matt on 2009-11-17
State: Initial state
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=150
PA_REAL_VOLUME=98304
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

State: Disabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=150
PA_REAL_VOLUME=98304
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

State: Enabled [not saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=1
PA_EQUALIZER_PERSISTENCE=0
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=150
PA_REAL_VOLUME=98304
PA_PREAMP=2
PA_REAL_PREAMP=131072
---

State: Disabled [saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=0
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=150
PA_REAL_VOLUME=98304
PA_PREAMP=2
PA_REAL_PREAMP=131072
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo 131072
set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo 0
### END: Equalized audio configuration
---

State: Enabled [saved]
---
SCRIPT_VERSION=2.3 (17/11/2009)
PA_LADSPA_PLUGIN=mbeq_1197
PA_LADSPA_LABEL=mbeq
PA_LADSPA_PLUGIN_NAME=Multiband EQ
PA_CURRENT_PRESET=
PA_EQUALIZER_STATUS=1
PA_EQUALIZER_PERSISTENCE=1
PA_NUM_LADSPA_INPUTS=15
PA_LADSPA_CONTROLS=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
PA_LADSPA_INPUTS=50,100,156,220,311,440,622,880,1250,1750,2500,3500,5000,10000,20000
PA_CONTROL_MIN=-30
PA_CONTROL_MAX=30
PA_MASTER_SINK=alsa_output.pci-0000_00_1b.0.analog-stereo
PA_LADSPA_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_SINK=ladspa_output.mbeq_1197.mbeq
PA_CURRENT_MUTE=0
PA_CURRENT_VOLUME=150
PA_REAL_VOLUME=98304
PA_PREAMP=2
PA_REAL_PREAMP=131072
### BEGIN: Equalized audio configuration
### Generated from: pulseaudio-equalizer.sh
load-module module-ladspa-sink sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
set-default-sink ladspa_output.mbeq_1197.mbeq
set-sink-volume alsa_output.pci-0000_00_1b.0.analog-stereo 131072
set-sink-mute alsa_output.pci-0000_00_1b.0.analog-stereo 0
### END: Equalized audio configuration
---

---

### Post by psyke83 on 2009-11-17
> **MacUntu said:**
> '2x' doesn't seem to be a good default for 'Preamp'. *ouchmyears*

Other than that it seems to work fine.

Edit: When clicking the 'Apply Settings' button when 'EQ Enabled' isn't ticked, it really shouldn't pause the stream.

On Karmic, the 2x preamp is roughly equal to non-equalized audio. However, when PulseAudio is configured for flat volumes (on Karmic, it's not), the preamp is probably much louder. Does Lucid use flat volumes by default?

```
cat /etc/pulse/daemon.conf | grep flat
```

---

### Post by psyke83 on 2009-11-17
> **sox fan Matt said:**
> State: Initial state
<snip>

Thanks, your log looks fine. Is the equalizer actually working for you?

---

### Post by Regenweald on 2009-11-17
Something I just noticed, before, my audio would level out at 15 then not change and simply cut off at zero. With the equalizer and it's dependencies I can now get levels until I get to zero. I assume LADSPA ?

---

### Post by plun on 2009-11-17
Broken for me with latest PA

```
plun@plun-laptop:~$ /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py
Getting settings...
Applying settings...
Disabling persistence...
Current operation: saving configuration (disable-config)
-------------------------------------
Equalizer setting saved (disable-config).
-------------------------------------
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------
Enabling...
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
**write(): Broken pipe**

```

Also high CPU...  pacmd

Events after killing pacmd

```
Suspending clients...
Unloading module-ladspa-sink...
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
/usr/bin/pulseaudio-equalizer.sh: line 403:  2452 Done                    pacmd "list-sink-inputs"
      2453 Exit 1                  | grep 'index: '
      2454                       | sed 's/    index: /move-sink-input /g'
      2455                       | sed "s/$/ $PA_LADSPA_SINK/g"
      2456 Killed                  | pacmd > /dev/null
Setting ALSA sink (auto_null) preamp (2x)...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Resuming clients...
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------


```

---

### Post by MacUntu on 2009-11-17
> **psyke83 said:**
> On Karmic, the 2x preamp is roughly equal to non-equalized audio. However, when PulseAudio is configured for flat volumes (on Karmic, it's not), the preamp is probably much louder. Does Lucid use flat volumes by default?

Nope, but it's definitely far away from "non-equalized" on this system. :) Will test the notebook (Intel HDA) later.

---

### Post by BwackNinja on 2009-11-17
For me, 1x preamp is equal to non-equalized audio, so I changed all the presets to use that.

Other than that, it sounds wonderful and works perfectly for me. I just find it a bit weird that all my music sounds better with the "Techno" preset rather than the "Rock" preset.

Also - thanks :D

---

### Post by plun on 2009-11-17
Reinstalled PA and removed .pulse, now it works....

```
plun@plun-laptop:~/Desktop/pulse$ /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py
Getting settings...
Applying settings...
Disabling persistence...
Current operation: saving configuration (disable-config)
-------------------------------------
Equalizer setting saved (disable-config).
-------------------------------------
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------
Enabling...
PulseAudio Equalizer/LADSPA Processor 2.3 (17/11/2009)
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
write(): Broken pipe
Suspending clients...
Unloading module-ladspa-sink...
Unloading & reloading stream-restore module...
write(): Broken pipe
Loading module-ladspa-sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.pci-0000_00_1e.2.analog-stereo) preamp (2x)...
Transferring current mute (1) & volume (8%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Resuming clients...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [disabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [5.3,2.6,2.6,-8.5,-10.5,-11.2,-16.0,-14.7,-6.6,-5.7,-3.0,3.0,6.7,7.3,7.3]
NOTE: Using user-customized settings from '/home/plun/.pulse/equalizerrc'...
-------------------------------------

```


Thanks !!!;)

---

### Post by shakaran on 2009-11-17
> **psyke83 said:**
> On Karmic, the 2x preamp is roughly equal to non-equalized audio. However, when PulseAudio is configured for flat volumes (on Karmic, it's not), the preamp is probably much louder. Does Lucid use flat volumes by default?

```
cat /etc/pulse/daemon.conf | grep flat
```

On Lucid: 
$ cat /etc/pulse/daemon.conf | grep flat
flat-volumes = no

---

### Post by cariboo on 2009-11-17
I've been playing with the equalizer for the last half hour, I'm now getting complaints to turn it down. :)

Thanks

---

### Post by Regenweald on 2009-11-18
> **cariboo907 said:**
> I've been playing with the equalizer for the last half hour, I'm now getting complaints to turn it down. :)

Thanks

Now it just doesn't sound right unless you adjust it, right ? :P

---

### Post by sports fan Matt on 2009-11-18
This is working fine and I echo the sentiments of cariboo..another "please turn it down" request.

---

### Post by Kevbert on 2009-11-18
Please can we also have a flat response preset so that it's easier to compare settings ?  Volume loud, but other than that works like a dream.

---

### Post by psyke83 on 2009-11-19
I'm going to update the equalizer, but I have a question before I do so: should the presets actually define the preamp level, or should the presets only use a global preamp set by the interface?

---

### Post by Regenweald on 2009-11-19
> **psyke83 said:**
> I'm going to update the equalizer, but I have a question before I do so: should the presets actually define the preamp level, or should the presets only use a global preamp set by the interface?
I think a global, preamp would work. The user can then adjust that once the preset is acceptable. (no more blowing out of chairs :P)
So 1 for global preamp. Hope you get more feedback!

---

### Post by MacUntu on 2009-11-19
+1 for global preamping.

---

### Post by cariboo on 2009-11-19
+1 for a global preamp. The default setting just about blew out the cones on one set of speakers.

---

### Post by psyke83 on 2009-11-19
> **cariboo907 said:**
> +1 for a global preamp. The default setting just about blew out the cones on one set of speakers.

Changed in v2.4 :)

The default preamp has also been changed to 1.5x (e.g., when somebody first tries the equalizer, or resets settings to default). This may still be too loud for Lucid users, but I suspect it's necessary on Karmic (as the equalizer tends to reduce the overall volume, at least on my machine).

---

### Post by Regenweald on 2009-11-19
Coolness, I'm using 2x as my default, but 1.5 makes sense. You made me want/need better speakers.....:)

---

### Post by psyke83 on 2010-02-04
(Mods: my apologies for resurrecting an old thread, but it seems like a good idea to follow up, as the original posters should avail of the new version of this script to prevent problems with PulseAudio on their systems).

Hey folks,

Since December I've been busy with personal issues and the holidays, and then my poor laptop died :(, along with my Ubuntu installation. Today I'm back up and running, and decided to update the [PulseAudio EQ interface]("http://ubuntuforums.org/showthread.php?t=1308838").

If anybody is still using version 2.4 in Lucid, I suggest that you upgrade to v2.5 that I released today. I'm sorry that it's not available in a PPA as of yet, but that's another thing on my list of things to do.

Changelog:
```
pulseaudio-equalizer (2.5) lucid; urgency=low

  * Preamp range is now between 0x and 2x, defaulting to 1x
  * Improved script compatibility with PulseAudio 0.9.21/Lucid Lynx
  * Misc. bugfixes to prevent hangs on moving streams
  * Optimized script execution to improve speed, minimize popping sounds
  * Adjusted support script/added GUI wrapper (Fedora guideline compliance)

 -- Conn <conn@portable>  Thu, 04 Feb 2010 05:37:24 +0000


```

If anybody finds any bugs or problems with Lucid, please let me know. Thanks in advance! :)

---

