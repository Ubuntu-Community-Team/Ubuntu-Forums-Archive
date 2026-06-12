---
title: "New Ubuntu Studio set-up: need to detect FP10 interface"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kvk on 2008-10-19
I've just set up a new installation of Ubuntu Studio over Ibex. I have a PreSonus FP10 firewired to the box. I'm completely new to U.Studio and configuring JACK and ALSA. What's the general procedure for getting the FP10 detected and setting up JACK and ALSA to play nicely together?

Thanks!

---

### Post by Stochastic on 2008-10-20
You'll need to do ```
sudo apt-get install libfreebob0 ubuntustudio-controls
```

Then open up System -> Administration -> UbuntuStudio Controls and check off all three options, set the memlock to about 95% or so, and nice can be set to about -5 (i think).  Then open up qjackctl settings window and select freebob as your driver.  Unfortunately it's highly recommended that audio users use the Realtime preempted kernel version, but Intrepid has yet to implement a 2.6.27-rt kernel (it's on the way, but not done yet), so until that happens you'll probably not get very good audio out of the FP10 (lots of dropouts/XRUNS in Jack).

If you need a system right now for audio, move back to Hardy, it has a working RT kernel.  (procedure for setting up your FP10 is the same)

---

### Post by kvk on 2008-10-20
Thanks! I was reading through some of the Ubuntu Studio set-up wikis and couldn't figure out which way was up.

I know Ibex hasn't yet run a rt kernel, but unfortunately I need to stick with Ibex due to some hardware conflicts in Hardy. I'll spend the time until the rt kernel is released learning the ropes so when it comes out I can hit the ground running.

Thanks again! I'm sure I'll post again if I have problems I can't solve through the wiki.

---

### Post by Stochastic on 2008-10-20
Some of those wiki docs (particularly the ubuntustudio ones) are extremely old (like Dapper era) and are remnants of times when complicated setup procedures (including rolling your own kernel) were the norm to get audio production going in Ubuntu.  If you learn that some of the info is out of date, feel free to edit, chop, change, fix, etc...

---

### Post by kvk on 2008-10-21
Okay- still having some difficulties. Here's the output from the JACK terminal when I attempt to open it:

14:11:09.701 Patchbay deactivated.
14:11:09.701 Statistics reset.
14:11:09.752 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
14:11:14.689 Startup script...
14:11:14.689 artsshell -q terminate
14:11:15.244 Startup script terminated with exit status=256.
14:11:15.244 JACK is starting...
14:11:15.244 /usr/bin/jackd -dfreebob -r44100 -p1024 -n3 -D
14:11:15.247 JACK was started with PID=6134.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
LibFreeBoB ERR: cannot create libfreebob handle
[0mcannot load driver module freebob
14:11:17.175 JACK was stopped successfully.
14:11:17.175 Post-shutdown script...
14:11:17.175 killall jackd
14:11:17.176 JACK has crashed.
jackd: no process killed
14:11:17.602 Post-shutdown script terminated with exit status=256.
14:11:18.571 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


Now, I checked Synaptic, and it appears the 1394 drivers/libraries are indeed loaded. The only 1394 entries there that are NOT loaded are either development files or state that they are specifically related to digital camera work.

I took Eye's suggestion and removed Pulseaudio and installed esound, but regardless of how I tried this, it ends up removing the UbuntuStudio desktop, leaving me only able to boot into the shell and reload it from there so I can access the gui. I tried it through Synaptic in addition to the terminal, thinking that maybe Synaptic would leave things in better order, but no such luck.

The mo soundcard was disabled at the BIOS level by the manufacturer and (supposedyl) the BIOS was set up to detect an external sound card (the FP10) but I'm still dead in the water here. 

What do you think?

---

### Post by Stochastic on 2008-10-24
> Ieee1394Service::initialize: Could not get 1394 handle: Permission denied

This is the killer line.  If you run ```
sudo jackd -dfreebob
``` you should be able to get the FP10 off the ground, but then the trouble is that every jack-aware app that you want will need to also be run with sudo
privileges (bad news security-wise).  But if you can get jack up, then it shows that things are generally in order (which I suspect they are).

Now to trouble shoot this problem, you need to grant yourself access to the raw firewire port (disabled by default for security reasons).  It should have worked by doing the settings in the UbuntuStudio-Controls panel (did you click apply, then click close?), but we'll go check manually; run: ```
sudo nano /etc/udev/rules.d/40-permissions.rules
```
Then find the section labeled "# IEEE1394 (firewire) devices" and READ THE WARNING!!!!! did you read the warning?  are you sure you understand the implications of changing these settings?  you're not about to go and plug anything other than your FP10 into the firewire port are you?  okay, I guess you can change the raw1394 group to read "audio" instead of "disk" then save and close.  DON'T FORGET THAT WARNING!!!!

Now you should be able to start jack normally.

As for your comment about eye's remove pulse audio recommendation (where did you read this?), I'd say that has nothing to do with your issue and that's just eye expressing grievance over his/her troubles with the pulse audio conversion in Hardy.  Pulse Audio gets out of the way when jack starts up if I recall correctly.

Oh and one last thing.  I've found that if jack shuts down in the middle of a session with the FP10/FirePod, then you'll need to either unplug the firewire cord & replug it, or turn the FP10 off&back on before attempting to restart jack.  I don't know why, I just know that's what works.

---

### Post by kvk on 2008-10-24
Thanks for all the help!! There is indeed a nice blue light on the FP10 now, instead of red, indicating sync. Yah!

This is the return from the first line:

arctos@arctos:~$ sudo jackd -dfreebob
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
FreeBoB ERR: Error opening ALSA sequencer.
FreeBoB ERR: -----------------------------------------------------------
FreeBoB ERR: Error creating midi device!
FreeBoB ERR: FreeBob will run without MIDI support.
FreeBoB ERR: Consult the above error messages to solve the problem. 
FreeBoB ERR: -----------------------------------------------------------


libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
LibFreeBoB ERR: Dropped packets on connection 1
LibFreeBoB ERR: Dropped packets on connection 1
LibFreeBoB ERR: Dropped packets on connection 1
LibFreeBoB ERR: Dropped packets on connection 1


I assume those dropped packets are due to not having a rt kernel for 8.10 yet?

I did indeed go ahead and change the permission setting for the raw1394. I don't own any other firewire devices at all!!

Now about needing to always run jack'd devices as sudo- does that mean always running everything from the command line (ha!)? Or can I use the gui interfaces after defining "sudo -s" in the terminal and leaving it open? 

Now when I start up Ardour just to check things, the first message is an error log message reading "No device found for driver ALSA". Do I need to change anything? I've enabled mem lock (0.95) and raw 1394 in the Ubuntu Studio controls, and set nice to -5.

Thanks again!! The help is very appreciated!

---

### Post by kvk on 2008-10-25
Things appear to be assembling themselves little by little. I can run JACK from the gui without becoming root (sudo) and the connection is fine. The issue remains with setting channels(?) which may be the reason for the dropped packets, instead of it being a rt kernel issue.

22:20:03.622 Patchbay deactivated.
22:20:03.622 Statistics reset.
22:20:03.689 Could not open ALSA sequencer as a client. ALSA MIDI patchbay will be not available.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
22:20:06.720 Startup script...
22:20:06.721 artsshell -q terminate
22:20:07.132 Startup script terminated with exit status=256.
22:20:07.132 JACK is starting...
22:20:07.132 /usr/bin/jackd -dfreebob -dhw:0 -r44100 -p1024 -n3 -D
22:20:07.133 JACK was started with PID=7082.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
22:20:07.339 Server configuration saved to "/home/arctos/.jackdrc".
22:20:07.340 Statistics reset.
22:20:07.340 Client activated.
22:20:07.341 JACK connection graph change.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
FreeBoB ERR: Error opening ALSA sequencer.
FreeBoB ERR: -----------------------------------------------------------
FreeBoB ERR: Error creating midi device!
FreeBoB ERR: FreeBob will run without MIDI support.
FreeBoB ERR: Consult the above error messages to solve the problem. 
FreeBoB ERR: -----------------------------------------------------------
22:20:08.563 JACK connection graph change.
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
22:20:08.749 JACK connection change.
LibFreeBoB ERR: Dropped packets on connection 1
22:20:14.794 XRUN callback (1).
LibFreeBoB ERR: Dropped packets on connection 1
22:20:31.033 XRUN callback (2).
LibFreeBoB ERR: Dropped packets on connection 1
22:20:56.251 XRUN callback (3).

---

