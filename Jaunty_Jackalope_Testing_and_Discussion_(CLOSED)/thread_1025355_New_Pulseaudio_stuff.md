---
title: "New Pulseaudio stuff"
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-12-30
Just a FYI--pulseaudio upgrade just came thru--about 9:30 Pacific time......

---

### Post by vishalrao on 2008-12-30
Got it. Sound still skips for the first few seconds when I start a Internet radio stream playback on VLC, and I don't believe it's due to buffering of the radio stream.

---

### Post by ShirishAg75 on 2008-12-30
This is new update. 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002342.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002342.html)

> 
pulseaudio (0.9.13-2ubuntu4) jaunty; urgency=low

  * Demote paprefs to suggests (LP: #309422)
  * Add fixes from git:
    - 0010_check_before_using_environment.patch,
    - 0011_load_restore_before_other_modules.patch,
    - 0012_dont_hit_assert_checking_for_idleness.patch,
    - 0013_dont_hit_assert_issuing_two_rewinds_in_single_iter.patch,
    - 0014_retry_without_snd-pcm-no-auto-format.patch.


What I don't understand is why the need to be on PA 0.9.13 as versioning and taking fixes from GIT rather than going onto PA 0.9.14 ?

---

### Post by vishalrao on 2008-12-30
Could it be because .14 is not released yet? I don't see it (.14) on PA website.

---

### Post by plun on 2008-12-30
> **ShirishAg75 said:**
> This is new update. 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002342.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002342.html)

What I don't understand is why the need to be on PA 0.9.13 as versioning and taking fixes from GIT rather than going onto PA 0.9.14 ?

Well... who knows..  several Ubuntu patches must probably be rolled backed before going into 9.0.14 for 100%.

[http://git.0pointer.de/?p=pulseaudio.git](http://git.0pointer.de/?p=pulseaudio.git)

LennartP probably also releases this version now when the kernel also is stable, 2.6.28.

---

### Post by ShirishAg75 on 2008-12-30
0.9.14 doesn't seem to have a binary but on trac doesn't seem to have any tickets left . 

[http://www.pulseaudio.org/roadmap?show=all](http://www.pulseaudio.org/roadmap?show=all)

---

### Post by plun on 2008-12-30
> **ShirishAg75 said:**
> 0.9.14 doesn't seem to have a binary but on trac doesn't seem to have any tickets left . 

[http://www.pulseaudio.org/roadmap?show=all](http://www.pulseaudio.org/roadmap?show=all)

Yes but LennartP probably wants to be sure with this one...  too much "bashing" from some elements within the eco-system.

You can also take a look at PAs mailing list...

Another little challenge is that GIT uses a **automake **version higher then Jaunty... available within Debian experimental.

---

### Post by xens on 2008-12-30
I'm waiting for the bluetooth support. To be able to use my bluetooth headphone :) hope to see it soon.

---

### Post by cszikszoy on 2008-12-31
> **xens said:**
> I'm waiting for the bluetooth support. To be able to use my bluetooth headphone :) hope to see it soon.

Bluetooth would be nice.  I'm also waiting to be able to use the airport express as an audio sink.

---

### Post by Nullack on 2008-12-31
They have not fixed OpenAL in this upgrade.

---

### Post by Slug71 on 2009-01-01
I still have absolutely NO sound in Jaunty. :(

---

### Post by plun on 2009-01-01
> **Slug71 said:**
> I still have absolutely NO sound in Jaunty. :(

OK... lets find the da--ed sound...

psyke83 master howto

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


What gives this....

```
aplay -l


pkill pulseaudio; sleep 2; pulseaudio -vv
```


and maybe start from the beginning with the howto...or wake up psyke83, his area...:D

---

### Post by Slug71 on 2009-01-01
aplay -l output

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


pkill pulseaudio; sleep 2; pulseaudio -vv output

> I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
N: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
N: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
W: core-util.c: setpriority(): Permission denied
D: main.c: Can realtime: no, can high-priority: no
W: ltdl-bind-now.c: Failed to find original dlopen loader.
I: main.c: This is PulseAudio 0.9.13
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.28-4-generic #5-Ubuntu SMP Fri Dec 26 22:48:55 UTC 2008
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 775ceeb37eab9e2c45ec20f2495cefde.
I: main.c: Using runtime directory /home/courtney/.pulse/775ceeb37eab9e2c45ec20f2495cefde:runtime.
I: main.c: Using state directory /home/courtney/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB
I: module-stream-restore.c: Sucessfully opened database file '/home/courtney/.pulse/775ceeb37eab9e2c45ec20f2495cefde:stream-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #0; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/courtney/.pulse/775ceeb37eab9e2c45ec20f2495cefde:device-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #1; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_4
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=1'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 371 ms
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: module-alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms
I: module-alsa-sink.c: Time scheduling watermark is 20.00ms
D: module-alsa-sink.c: hwbuf_unused_frames=0
D: module-alsa-sink.c: setting avail_min=62005
I: module-alsa-sink.c: Volume ranges from 0 to 64.
I: module-alsa-sink.c: Volume ranges from -64.00 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 8192
D: alsa-util.c:   period_time  : 185759
D: alsa-util.c:   tstamp_mode  : NONE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 62005
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : -1
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 4611686018427387904
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 8192
D: alsa-util.c:   period_time  : 185759
D: alsa-util.c:   tstamp_mode  : NONE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 62005
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   st
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0:  80% 1:  80%
D: module-alsa-sink.c: Got hardware volume: 0:  81% 1:  81%
D: module-alsa-sink.c: Calculated software volume: 0:  98% 1:  98%
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=1").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=1'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 371 ms
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: module-alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms
I: module-alsa-source.c: Time scheduling watermark is 20.00ms
D: module-alsa-source.c: hwbuf_unused_frames=0
D: module-alsa-source.c: setting avail_min=62005
I: module-alsa-source.c: Volume ranges from 0 to 31.
I: module-alsa-source.c: Volume ranges from -16.50 dB to 30.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 8192
D: alsa-util.c:   period_time  : 185759
D: alsa-util.c:   tstamp_mode  : NONE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 62005
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : -1
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 4611686018427387904
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 8192
D: alsa-util.c:   period_time  : 185759
D: alsa-util.c:   tstamp_mode  : NONE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 62005
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   star
D: module-alsa-source.c: Requested volume: 0:  75% 1:  75%
D: module-alsa-source.c: Got hardware volume: 0:  75% 1:  75%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=1").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
I: module.c: Loaded "module-always-sink" (index: #10; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session5"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session5
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified

D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified

---

### Post by SeePU on 2009-01-01
I don't care about updates.  I care about good instructions. :(

---

### Post by Nullack on 2009-01-01
> **SeePU said:**
> I don't care about updates.  I care about good instructions. :(

Read the documentation?

---

### Post by Slug71 on 2009-01-01
> **plun said:**
> OK... lets find the da--ed sound...

psyke83 master howto

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


What gives this....

```
aplay -l


pkill pulseaudio; sleep 2; pulseaudio -vv
```


and maybe start from the beginning with the howto...or wake up psyke83, his area...:D

Sound is working. :D

---

### Post by SeePU on 2009-01-03
Pulseaudio is probably the worst application in Linux and is problematic in every distro.  IMHO!   That includes Ubuntu.  

It won't work for long if you think it's working.

What does it matter if I followed the documentation and instructions for it if it still doesn't work?!?

> W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.


$ pulseaudio (gives:)

> W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

There are threads in the forums of people trying to remove it!!!

I'd say that illustrates a problem.

Edit:  I made some changes and edited some files.  I have some instructions I followed and now it is working.  If it works for a while, I will post them to the forum.  I want to make sure it is working for some length of time.  I think a lot of the writeups are good but for many, I think pulseaudio still doesn't work properly.  I only want the pulseaudio apps to work with one sound card and that it works properly without turning off my sound and stuff like that.  I'll followup soon.  

Thanks for your followups!

---

### Post by bjerngaard on 2009-02-21
Regarding Airport Express support, have a look at this: [http://www.pulseaudio.org/ticket/69](http://www.pulseaudio.org/ticket/69)

---

### Post by cszikszoy on 2009-02-23
> **bjerngaard said:**
> Regarding Airport Express support, have a look at this: [http://www.pulseaudio.org/ticket/69](http://www.pulseaudio.org/ticket/69)

I'm so happy to hear that.  Now the only question, is when 0.9.15 hits Ubuntu?  Jaunty will be 0.9.14, no?

---

### Post by markbuntu on 2009-02-23
The plan now is for 0.9.14 for Jaunty. 0.9.15 will be in Koala but by then pulse will probably be up to 1.0 or something.

---

### Post by Starks on 2009-02-23
> **markbuntu said:**
> The plan now is for 0.9.14 for Jaunty. **0.9.15 will be in Koala** but by then pulse will probably be up to 1.0 or something.

*insert rage*

Is there any room for negotiation on that?

---

### Post by markbuntu on 2009-02-23
You could talk to Luke Yelavich. He has a Lanchpad PPA for 0.9.15 for Jaunty (testing only, meh).

---

### Post by ugkbunb on 2009-02-23
> **SeePU said:**
> Pulseaudio is probably the worst application in Linux and is problematic in every distro.  IMHO!   That includes Ubuntu.  


sure it can be a pain to setup but once it is... imho it is sweet heaven. I am loving PA after I got all my kinks worked out (no sound on startup, scratchy sound, SPDIF pass-through + thanks to 0.9.15)

---

