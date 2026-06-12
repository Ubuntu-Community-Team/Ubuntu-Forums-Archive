---
title: "Pulse Audio reconfiguration"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Killerah on 2009-04-17
Here's the situation, I just upgraded from Intrepid to Jaunty, Jaunty totally rocks my socks, very impressive. However, during the upgrade process, I was asked if I wanted to replace my configuration files with the new ones, I was dumb and clicked no. Now that I've looked around it seems like Pulse is working great in Jaunty. What I want to know is how do I get that message to come up again so I can click yes instead of no. Any suggestions? Sorry if this is a stupid question...

Thanks a ton,
Nate

---

### Post by priegog on 2009-04-18
hmm you could start by removing your /home/xxx/.pulse folder. I'm sure there are other configuration files scattered somewhere, I just don't know where. When you delete a config file, the next time that application starts it will create a new default one.

---

### Post by Killerah on 2009-04-18
Good thought, I gave that a shot, but it didn't work. I still get the same problem. Here's what the terminal says when I put in "pulseaudio": > I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: alsa-util.c: Failed to set hardware parameters on plug:equalized: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=equalized"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

I'm sure if I was just able to get pulse to reconfigure itself to defaults I could get this working. Maybe if I do a complete uninstall and reinstall of pulse that would do the trick?

---

### Post by priegog on 2009-04-18
You can try, but unless something was installed wrongly I don't think it'll do any good. For normal userland apps the specifications mandate that the config files be stored in the /home directory. But pulse audio isn't exactly a normal app, it's a part of the system. So MAYBE it has some sort of config files in the apps directories. But I wouldn't be able to help you out any further. 
Frankly, I don't think you'd gain anything from "resetting it to default settings". Are you having any sort of problems?

---

### Post by Killerah on 2009-04-18
The problem was pulseaudio wasn't working at all, it wasn't able to start up. I would go to my pulseaudio volume control and it would say "connection refused". I did a completely uninstall and reinstall and now pulse works, but the problem is only certian apps will use it! I can see which apps are connected to pulse in the volume control and the only thing I've been able to connect so far is Amarok. When I use firefox or skype or whatever else they will not connect but try to take over my sound card instead (and end up crashing because it's already in use).

Any suggestions?

---

### Post by priegog on 2009-04-18
Nope, not really... Sound servers aren't really my thing.
Sorry, but at least I'll bump you.

---

### Post by Killerah on 2009-04-18
OK, I've been playing around with it a bit more and looking at the padevchooser volume control at the same time. I'm able to see Amarok cranking it out (and I can hear it too), and nothing else. And then intermittently I'll see ALSA-Plugin blink for a fraction of a second over and over (as long as I'm using firefox or opera to play some audio). 

So it seems to me that ALSA is trying very hard to connect to Pulse but just isn't able to. Anybody got any thoughts of what could be causing this? I still feel like it's some sort of configuration setting.

---

### Post by mnfiddledragon on 2009-04-18
Killerah,

For what it's worth, I'm getting the exact same error message. And I *think* this issue is preventing me from being able to load and play WoW - or at least it was sound driver issues (ie., when pulseaudio would die before upgrading) that would crash WoW before.

---

### Post by markbuntu on 2009-04-18
You probably edited your ~/.asoundrc file and maybe your etc/pulse/default.pa or daemon.conf file. You can just get rid of the ~/.asoundrc and comment out the lines in the default.pa

You can go back to psykes thread to find out what you did and undo it.

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Killerah on 2009-04-19
Unfortunately, I've already tried that. I deleted my .asoundrc (which didn't come back), and my complete removal and reinstallation of pulse purged my old configuration files involved there. I've been screwing with this all day and I just can't figure out what's causing this problem... There's some sort of hang up with ALSA and Pulse, if I could get ALSA to connect to Pulse I'm sure everything would work just great...

---

### Post by crimsun on 2009-04-19
> **Killerah said:**
> Unfortunately, I've already tried that. I deleted my .asoundrc (which didn't come back), and my complete removal and reinstallation of pulse purged my old configuration files involved there. I've been screwing with this all day and I just can't figure out what's causing this problem... There's some sort of hang up with ALSA and Pulse, if I could get ALSA to connect to Pulse I'm sure everything would work just great...

Please run `ubuntu-bug pulseaudio', and tell us the bug number that is filed.

---

### Post by Killerah on 2009-04-19
OK, I reported it as #363747

For the moment I have temporarily disabled pulseaudio by screwing with /etc/pulse/default.pa a little. Now pulse doesn't start and alsa just takes over. Until I have a little more time to figure out what is going on with pulse this sloppy solution will do. If you guys can figure it out though I won't object to trying some more stuff.

Thanks a ton,
Nate

---

### Post by markbuntu on 2009-04-19
Try running 

pulseaudio -vvv

from a terminal and see what messages you get.

---

### Post by Killerah on 2009-04-19
Here's what I get:
> I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is a7420e18871da7c0f07d96df48127d98.
I: main.c: Using runtime directory /home/nate/.pulse/a7420e18871da7c0f07d96df48127d98:runtime.
I: main.c: Using state directory /home/nate/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 0 "combined" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 0 "combined.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-combine" (index: #0; argument: "").
I: module.c: Loaded "module-gconf" (index: #1; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #2; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/nate/.pulse/a7420e18871da7c0f07d96df48127d98:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #3; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/nate/.pulse/a7420e18871da7c0f07d96df48127d98:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #4; argument: "").
D: alsa-util.c: Trying default with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 170 ms
W: alsa-util.c: Device default doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device default doesn't support sample format s16le, changed to s32le.
I: module-alsa-sink.c: Successfully opened device default.
I: module-alsa-sink.c: Device is not a hardware device, disabling timer-based scheduling.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'default'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.default" with sample spec s32le 2ch 48000Hz and channel map front-left,front-right
I: source.c: Created source 1 "alsa_output.default.monitor" with sample spec s32le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 2 fragments of size 8192 bytes, buffer time is 42.67ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Plug PCM: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S32_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 32
D: alsa-util.c:   buffer_size  : 2048
D: alsa-util.c:   period_size  : 1024
D: alsa-util.c:   period_time  : 21333
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1024
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c: Slave: Direct Stream Mixing PCM
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S32_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 32
D: alsa-util.c:   buffer_size  : 2048
D: alsa-util.c:   period_size  : 1024
D: alsa-util.c:   period_time  : 21333
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1024
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-sink.c: Read hardware volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.default.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.default becomes idle.
I: module-combine.c: Configuring new sink: alsa_output.default
D: memblockq.c: memblockq requested: maxlength=16777216, tlength=16777216, base=4, prebuf=1, minreq=0 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=16777216, tlength=16777216, base=4, prebuf=4, minreq=4 maxrewind=0
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:filter.
I: module-stream-restore.c: Restoring mute state for sink input sink-input-by-media-role:filter.
D: module-suspend-on-idle.c: Sink alsa_output.default becomes busy.
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using float32le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=8, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=8, prebuf=0, minreq=8 maxrewind=0
I: sink-input.c: Created input 0 "Simultaneous output on dmix:0" on alsa_output.default with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module.c: Loaded "module-alsa-sink" (index: #5; argument: "").
D: alsa-util.c: Trying hw:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
E: alsa-util.c: Error opening PCM device hw:0,1: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:0,1"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-combine" (index: #0).
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-suspend-on-idle.c: Sink alsa_output.default becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.default becomes idle.
I: sink-input.c: Freeing input 0 "Simultaneous output on dmix:0"
D: core-subscribe.c: Dropped redundant event due to change event.
D: core-subscribe.c: Dropped redundant event due to change event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-combine.c: Thread shutting down
I: sink.c: Freeing sink 0 "combined"
I: source.c: Freeing source 0 "combined.monitor"
I: module.c: Unloaded "module-combine" (index: #0).
I: module.c: Unloading "module-gconf" (index: #1).
D: module-gconf.c: Unloading module #0
I: module.c: Unloaded "module-gconf" (index: #1).
I: module.c: Unloading "module-suspend-on-idle" (index: #2).
I: module.c: Unloaded "module-suspend-on-idle" (index: #2).
I: module.c: Unloading "module-device-restore" (index: #3).
I: module.c: Unloaded "module-device-restore" (index: #3).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-stream-restore" (index: #4).
I: module.c: Unloaded "module-stream-restore" (index: #4).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-alsa-sink" (index: #5).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "alsa_output.default"
I: source.c: Freeing source 1 "alsa_output.default.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #5).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

However, this is with my pulseaudio purposely set to a non-working state. If you want me to I can set it up to where it was, but where it was pulseaudio was able to get up and running with no problems. The problem comes in whenever I try to use any ALSA applications, they just can't seem to connect to pulseaudio.

---

### Post by markbuntu on 2009-04-19
The problem seems to be here

D: alsa-util.c: Trying hw:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
E: alsa-util.c: Error opening PCM device hw:0,1: No such file or directory
E: module.c: Failed to load module "module-alsa-source" (argument: "device=hw:0,1"): initialization failed.
E: main.c: Module load failed.

---

