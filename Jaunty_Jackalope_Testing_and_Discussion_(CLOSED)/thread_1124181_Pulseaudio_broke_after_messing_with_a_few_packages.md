---
title: "Pulseaudio broke after messing with a few packages"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by blithen on 2009-04-13
Basically I was working with some networking things, and now pulseaudio is broken with this as the output
```
blithen@Sparky:~$ pulseaudio 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```
There is no sound

---

### Post by blithen on 2009-04-13
Anybody?

---

### Post by biji on 2009-04-13
i guess daemon already running:
E: pid.c: Daemon already running.

try to killall pulseaudio first

---

### Post by blithen on 2009-04-13
Still doesn't work, and has the same error, except without the daemon running.

---

### Post by miegiel on 2009-04-13
Did you check the volume levers? Sometimes software changes them "for your convenience".

---

### Post by blithen on 2009-04-13
:P Yes I did.

---

### Post by markbuntu on 2009-04-13
The message said you are not a member of the group pulse-rt. You should make your users and root members of that group and
pulse
pulse-access

If you want to find out what pulse is doing, kill the daemon and then run

pulseaudio -vvv

---

### Post by blithen on 2009-04-15
```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.15-test7
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is f0b09f618d9114ea686080ef4945d56a.
I: main.c: Using runtime directory /home/blithen/.pulse/f0b09f618d9114ea686080ef4945d56a:runtime.
I: main.c: Using state directory /home/blithen/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: rtclock.c: Timer slack is set to 50 us.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
I: module.c: Loaded "module-suspend-on-idle" (index: #0; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/blithen/.pulse/f0b09f618d9114ea686080ef4945d56a:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #1; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/blithen/.pulse/f0b09f618d9114ea686080ef4945d56a:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #2; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/blithen/.pulse/f0b09f618d9114ea686080ef4945d56a:card-database.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-card-restore" (index: #3; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-hal-detect.so': success
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-card with arguments 'device_id=0 name=pci_10de_3f0_sound_card_0 card_name=alsa_card.pci_10de_3f0_sound_card_0 tsched=1'
W: reserve-wrap.c: Unable to contact D-Bus session bus: org.freedesktop.DBus.Error.Spawn.ExecFailed: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
D: alsa-util.c: Checking for playback on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Stereo + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Stereo'
D: alsa-util.c: Checking for playback on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Digital Stereo (IEC958) + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Digital Stereo (IEC958)'
D: alsa-util.c: Checking for playback on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Surround 4.0 + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Surround 4.0'
D: alsa-util.c: Checking for playback on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Surround 4.1 + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Surround 4.1'
D: alsa-util.c: Checking for playback on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Surround 5.0 + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Surround 5.0'
D: alsa-util.c: Checking for playback on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Surround 5.1 + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Surround 5.1'
D: alsa-util.c: Checking for playback on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Output Analog Surround 7.1 + Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: module-alsa-card.c: Found output profile 'Output Analog Surround 7.1'
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-card.c: Found output profile 'Input Analog Stereo'
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1c failed
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3c failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: card.c: Created 0 "alsa_card.pci_10de_3f0_sound_card_0"
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 371 ms
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected configuration 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_10de_3f0_sound_card_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC888 Analog"
I: sink.c:     alsa.id = "ALC888 Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA NVidia"
I: sink.c:     alsa.long_card_name = "HDA NVidia at 0xfe028000 irq 23"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: sink.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0"
I: sink.c:     hal.product = "HDA NVidia Sound Card"
I: sink.c:     hal.card_id = "HDA NVidia"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "65536"
I: sink.c:     device.buffering.fragment_size = "32768"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "HDA NVidia"
I: sink.c:     device.icon_name = "audio-card"
I: source.c: Created source 0 "alsa_output.pci_10de_3f0_sound_card_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of HDA NVidia"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA NVidia"
I: source.c:     alsa.long_card_name = "HDA NVidia at 0xfe028000 irq 23"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: source.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0"
I: source.c:     hal.product = "HDA NVidia Sound Card"
I: source.c:     hal.card_id = "HDA NVidia"
I: source.c:     device.string = "0"
I: source.c:     device.icon_name = "audio-card"
I: alsa-sink.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms
I: alsa-sink.c: Time scheduling watermark is 20.00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=15502
I: alsa-sink.c: Volume ranges from 0 to 31.
I: alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
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
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 15502
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
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
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 15502
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-sink.c: Read hardware volume: 0:  25% 1:  25%
D: alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_3f0_sound_card_0 becomes idle.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Maximum hw buffer size is 371 ms
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected configuration 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_10de_3f0_sound_card_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "ALC888 Analog"
I: source.c:     alsa.id = "ALC888 Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA NVidia"
I: source.c:     alsa.long_card_name = "HDA NVidia at 0xfe028000 irq 23"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
I: source.c:     hal.udi = "/org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0"
I: source.c:     hal.product = "HDA NVidia Sound Card"
I: source.c:     hal.card_id = "HDA NVidia"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "65536"
I: source.c:     device.buffering.fragment_size = "32768"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "HDA NVidia"
I: source.c:     device.icon_name = "audio-card"
I: alsa-source.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms
I: alsa-source.c: Time scheduling watermark is 20.00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=15502
I: alsa-source.c: Volume ranges from 0 to 31.
I: alsa-source.c: Volume ranges from -16.50 dB to 30.00 dB.
I: alsa-source.c: Fixing base volume to -30.00 dB
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
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
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 15502
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
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
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 15502
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1073741824
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1073741824
D: alsa-source.c: Read hardware volume: 0: 100% 1: 100%
D: alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_3f0_sound_card_0 becomes idle.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id=0 name=pci_10de_3f0_sound_card_0 card_name=alsa_card.pci_10de_3f0_sound_card_0 tsched=1").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 1 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "").
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
I: module-default-device-restore.c: Saved default sink 'alsa_output.pci_10de_3f0_sound_card_0_alsa_playback_0' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'alsa_input.pci_10de_3f0_sound_card_0_alsa_capture_0' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: client.c: Created 1 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session236"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session236
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
I: module.c: Loaded "module-cork-music-on-phone" (index: #16; argument: "").
W: main.c: Unable to contact DBUS: org.freedesktop.DBus.Error.Spawn.ExecFailed: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
I: main.c: Daemon startup complete.
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_10de_3f0_sound_card_0.
I: module-device-restore.c: Storing volume/mute for device source:alsa_output.pci_10de_3f0_sound_card_0.monitor.
I: module-device-restore.c: Storing volume/mute for device source:alsa_input.pci_10de_3f0_sound_card_0.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_3f0_sound_card_0 idle for too long, suspending ...
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_3f0_sound_card_0 idle for too long, suspending ...
I: alsa-source.c: Device suspended...
I: module-device-restore.c: Synced.
^CE: module-gconf.c: Unable to read or parse data from client.
I: module.c: Unloading "module-gconf" (index: #10).
I: module.c: Unloaded "module-gconf" (index: #10).
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-suspend-on-idle" (index: #0).
I: module.c: Unloaded "module-suspend-on-idle" (index: #0).
I: module.c: Unloading "module-device-restore" (index: #1).
I: module.c: Unloaded "module-device-restore" (index: #1).
I: module.c: Unloading "module-stream-restore" (index: #2).
I: module.c: Unloaded "module-stream-restore" (index: #2).
I: module.c: Unloading "module-card-restore" (index: #3).
I: module.c: Unloaded "module-card-restore" (index: #3).
I: module.c: Unloading "module-augment-properties" (index: #4).
I: module.c: Unloaded "module-augment-properties" (index: #4).
I: module.c: Unloading "module-alsa-card" (index: #5).
D: alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_10de_3f0_sound_card_0"
I: source.c: Freeing source 0 "alsa_output.pci_10de_3f0_sound_card_0.monitor"
D: alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_10de_3f0_sound_card_0"
I: card.c: Freed 0 "alsa_card.pci_10de_3f0_sound_card_0"
I: module.c: Unloaded "module-alsa-card" (index: #5).
I: module.c: Unloading "module-hal-detect" (index: #6).
I: module.c: Unloaded "module-hal-detect" (index: #6).
I: module.c: Unloading "module-bluetooth-discover" (index: #7).
I: module.c: Unloaded "module-bluetooth-discover" (index: #7).
I: module.c: Unloading "module-esound-protocol-unix" (index: #8).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #8).
I: module.c: Unloading "module-native-protocol-unix" (index: #9).
I: module.c: Unloaded "module-native-protocol-unix" (index: #9).
I: module.c: Unloading "module-default-device-restore" (index: #11).
I: module.c: Unloaded "module-default-device-restore" (index: #11).
I: module.c: Unloading "module-rescue-streams" (index: #12).
I: module.c: Unloaded "module-rescue-streams" (index: #12).
I: module.c: Unloading "module-always-sink" (index: #13).
I: module.c: Unloaded "module-always-sink" (index: #13).
I: module.c: Unloading "module-console-kit" (index: #14).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session236
I: client.c: Freed 1 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session236"
I: module.c: Unloaded "module-console-kit" (index: #14).
I: module.c: Unloading "module-position-event-sounds" (index: #15).
I: module.c: Unloaded "module-position-event-sounds" (index: #15).
I: module.c: Unloading "module-cork-music-on-phone" (index: #16).
I: module.c: Unloaded "module-cork-music-on-phone" (index: #16).
I: main.c: Daemon terminated.
```
There is the output of pulseaudio -vvv

---

### Post by markbuntu on 2009-04-15
You need alsa 1.0.19 to use pulse 0.9.15, do you have that?

You can try deleting /home/blithen/.pulse and see if it runs with the /etc/pulse defaults

---

### Post by blithen on 2009-04-16
> **markbuntu said:**
> You need alsa 1.0.19 to use pulse 0.9.15, do you have that?

You can try deleting /home/blithen/.pulse and see if it runs with the /etc/pulse defaults

Okay I will try that.
Well deleteting it didn't work, and I'm not sure what version alsa is, how do I check?

---

