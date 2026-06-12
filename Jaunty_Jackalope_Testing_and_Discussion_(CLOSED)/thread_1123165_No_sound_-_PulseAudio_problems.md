---
title: "No sound - PulseAudio problems"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sjk44 on 2009-04-11
I am not getting any sound.  When I try to bring up PulseAudio Manager, in the lower left hand corner of the PA Mgr window it says “FAILURE: Connection refused”.  I believe that I have permission for PulseAudio.  I have a Soundblaster sound card (and a Nvidia card on the motherboard that is not in use):

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]

The output of lspci is:
:~$ lspci -v
01:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
Subsystem: Creative Labs Device 100a
Flags: bus master, medium devsel, latency 64, IRQ 18
I/O ports at cc00 [size=32]
Capabilities: <access denied>
Kernel driver in use: CA0106
Kernel modules: snd-ca0106

When I kill pulse audio and try to restart it I get the following errors:
:~$ pkill pulseaudio
:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: main.c: RLIMIT_RTPRIO failed: Operation not permitted
W: alsa-util.c: Device surround41:CA0106 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
E: alsa-util.c: Error opening PCM device default:CA0106: Invalid argument
E: module.c: Failed to load module "module-alsa-source" (argument: "device=default:CA0106"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

I do not know enough to figure out what is happening with the sound; does anyone have insight?

---

### Post by dino99 on 2009-04-12
hi, 
on wich version are you ?
there is a lot wiki & howto around the net, use google.
Jaunty and pulseaudio are both young and nothing is perfect at time, so you can add this pulse ppa to have the last versions for all the sound updates:

deb [http://ppa.launchpad.net/themuso/ubuntu](http://ppa.launchpad.net/themuso/ubuntu) jaunty main (choose your distro)
and update the sources.list with pubkey

see: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) for some details

have a good week end

---

### Post by sjk44 on 2009-04-12
Dino99 - 

Thank you for your response. I am using the Beta version of Jaunty, and have tried to use Google to find a solution as to why PulseAudio is not coming up correctly.  

I have looked at the references you sent, but they seem to pertain to a prior version of Ubuntu.  Do you think the references are appropriate and will work with Jaunty?  Thank you again.

sjk44

---

### Post by markbuntu on 2009-04-13
Can you open a mixer?
Is the analog/digital switch checked?
If so uncheck it and reboot

Analog and digital are mutually exclusive on those cards and the default on install is digital so no analog controls are available so alsa-utils cannot find any so pulse fails to load the modules and the daemon is unable to start. This is very specific to the soundblaster audigy cards and has been going on since hardy.

---

### Post by sjk44 on 2009-04-13
I apologize, as a relative n00bie, I do not know how to open a mixer.  

I have the Volume Applet version 2.26.0, the Pulse Audio Manager, the Pulse Audio Device Chooser, and a program called paconfig.  Is one of these functions what you want me to check?

Thank you,

sjk44

---

### Post by markbuntu on 2009-04-13
The volume applet on your panel, the little speaker. Right click on it and choose Open Volume Control. Go to the switches tab. If you do not have that tab or the analog/digital switch choose Edit/Preferences and check the box for it. It should be in the switches tab now and you can uncheck it. You might need to reboot to get it working.

---

### Post by sjk44 on 2009-04-14
markbuntu - thank you for hanging in with me.  I opened the volume control, on the preferences display I chose for the switches tab to be included, then I unchecked the "IEC958" box.  I then rebooted.  Looking at the PulseAudio Manager, it appears that the connection to PulseAudio is still refused.  

Do you think I may have done something incorrectly?

Thank you,

sjk44

---

### Post by Peasantoid on 2009-04-14
Try restarting avahi-daemon (sudo /etc/init.d/avahi-daemon restart).

---

### Post by markbuntu on 2009-04-15
From a terminal type

pulseaudio -vvv

post the output.

---

### Post by sjk44 on 2009-04-15
Here is the output; thank you for your investment of time and intellect !!

:~$ pulseaudio -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: We're in the group 'pulse-rt', allowing real-time scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
W: main.c: RLIMIT_RTPRIO failed: Operation not permitted
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is dc735783bae5f047ece0294c48923976.
I: main.c: Using runtime directory /home/stanleyk/.pulse/dc735783bae5f047ece0294c48923976:runtime.
I: main.c: Using state directory /home/stanleyk/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: alsa-util.c: Trying surround41:CA0106 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 341 ms
W: alsa-util.c: Device surround41:CA0106 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device surround41:CA0106.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: module-alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL surround41:CA0106
I: alsa-util.c: Unable to attach to mixer surround41:CA0106: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
I: sink.c: Created sink 0 "CA0106" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: source.c: Created source 0 "CA0106.monitor" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 2 fragments of size 32768 bytes, buffer time is 341.33ms
I: module-alsa-sink.c: Time scheduling watermark is 20.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=15424
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Route conversion PCM
D: alsa-util.c:   Transformation table:
D: alsa-util.c:     0 <- 0
D: alsa-util.c:     1 <- 1
D: alsa-util.c:     2 <- 2
D: alsa-util.c:     3 <- 3
D: alsa-util.c:     4 <- none
D: alsa-util.c:     5 <- 4
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 16384
D: alsa-util.c:   period_size  : 8192
D: alsa-util.c:   period_time  : 170666
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 15424
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c: Slave: Multi PCM
D: alsa-util.c:   Channel bindings:
D: alsa-util.c:     0: slave 0, channel 0
D: alsa-util.c:     1: slave 0, channel 1
D: alsa-util.c:     2: slave 1, channel 0
D: alsa-util.c:     3: slave 1, channel 1
D: alsa-util.c:     4: slave 2, channel 0
D: alsa-util.c:     5: slave 2, channel 1
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_COMPLEX
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 6
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       :
D: module-alsa-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 5.
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
D: module-alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device=surround41:CA0106 sink_name=CA0106").
D: module-alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying default:CA0106 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters CA0106
I: (alsa-lib)pcm.c: Unknown PCM default:CA0106
E: alsa-util.c: Error opening PCM device default:CA0106: Invalid argument
E: module.c: Failed to load  module "module-alsa-source" (argument: "device=default:CA0106"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "CA0106"
I: source.c: Freeing source 0 "CA0106.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: main.c: Daemon terminated.

---

### Post by sjk44 on 2009-04-16
Markbuntu - Last night while navigating around the system looking for new features, under the System Preferences section I came across an icon labeled Default Sound Card.  

I opened this applet and it showed the default sound card as PulseAudio.  I changed it to CA0106 and Songbird started to work!  I changed it back to PulseAudio, and lo and behold, Songbird still worked!  Also, the PulseAudio Manager now shows it is connected and "ready".  I have no idea what has happened but perhaps this behavior will help the thought process.

Thank you, 

sjk44
ps: the output from the command you were looking for is in the post above.

---

### Post by dino99 on 2009-04-17
pavucontrol install needed

---

### Post by sjk44 on 2009-04-19
dino99 - I have pavucontrol installed, and it has been installed all along as far as I know.  Can you please tell what your thoughts were in recommending the installation?

Thank you,

sjk44

---

