---
title: "Hardy, suspend, and Thinkpad T30 not happy together"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by poit on 2008-04-30
Hi there,

this is a follow up to a previous post about getting suspend to work on my T30 using Hardy. By reinstalling Hardy after it cleared beta I was able to clean up a few things, but there are still suspend issues. It will now suspend and hibernate, but when suspending there are two problems. 
First, the backlight doesn't go off. (I can turn it off using radeontool).

Second, the sound no longer works on resume. (I can restart the sound using this script "/etc/init.d/alsa-utils restart")

So, what's the problem you may ask?
Well, I don't have a clue what scripts are executed on suspend and resume and where they live. Seems it would be an easy task to add the readeontool command to the suspend script, and add the alsa restart to the resume scripts. Where are these scripts?

Thanks

---

### Post by sakurazukamori on 2008-05-03
Well...

I have the same laptop (a T30), actually I don't know were to put the code:

```
/usr/sbin/radeontool light off
```

The acpid configuration is kinda tricky, there are a lot of file that refers to others, so I got lost when I tried to look into /etc/acpi/
there's suspend.d, sleep.sh, the directory events.
So it was quite disturbing =_=°

However...
The sound problem for me has two different sub problem when resuming after a suspend to ram session:

1-At the beginning there's no sound, but... If I mute the pcm volume and after that the master volume, the sound will shows up again (the order is not important)

2-The sound comes back, but it's accelerated like chipmunk's voice : [ restarting alsa won't work -_-

---

### Post by poit on 2008-05-03
I was able to get the sound to restart without the chipmunk effect by switching the sound system from Autotdetect to ALSA in the Preferences>Sounds>Devices menu.  hope that helps.

 

> **sakurazukamori said:**
> Well...

I have the same laptop (a T30), actually I don't know were to put the code:

```
/usr/sbin/radeontool light off
```

The acpid configuration is kinda tricky, there are a lot of file that refers to others, so I got lost when I tried to look into /etc/acpi/
there's suspend.d, sleep.sh, the directory events.
So it was quite disturbing =_=°

However...
The sound problem for me has two different sub problem when resuming after a suspend to ram session:

1-At the beginning there's no sound, but... If I mute the pcm volume and after that the master volume, the sound will shows up again (the order is not important)

2-The sound comes back, but it's accelerated like chipmunk's voice : [ restarting alsa won't work -_-

---

### Post by Paul S on 2008-05-03
> **poit said:**
> Well, I don't have a clue what scripts are executed on suspend and resume and where they live. Seems it would be an easy task to add the readeontool command to the suspend script, and add the alsa restart to the resume scripts. Where are these scripts?

Thanks

Try this to see what scripts are executed:

```
cat /var/log/pm-suspend.log
```

HTH

---

### Post by poit on 2008-05-04
OK, here's what I see:

> Sat May  3 00:16:02 MDT 2008: running suspend hooks.
===== Sat May  3 00:16:02 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Sat May  3 00:16:02 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat May  3 00:16:02 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat May  3 00:16:02 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Sat May  3 00:16:04 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat May  3 00:16:04 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Sat May  3 00:16:04 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat May  3 00:16:06 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat May  3 00:16:06 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat May  3 00:16:06 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Sat May  3 00:16:06 MDT 2008: done running suspend hooks.
Sat May  3 00:16:31 MDT 2008: running resume hooks.
===== Sat May  3 00:16:31 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Function not supported
Function not supported
===== Sat May  3 00:16:38 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat May  3 00:16:38 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat May  3 00:16:38 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
   ...done.
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat May  3 00:16:39 MDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Sat May  3 00:16:39 MDT 2008: done running resume hooks.



So, it looks like the 99video module is bombing out, there is already a mention of the radeontool app in there.  I'll have to dig in there more.

---

### Post by sakurazukamori on 2008-05-04
Thanks Poit, the sound works again after suspend, the strange thing was that not all of my controls were handled by ALSA, so that maybe was the reason why the sound was similiar to a chipmunk's one.

However...

Paul S here's my output of

```
cat /var/log/pm-suspend.log
```

> Sun May  4 16:52:02 CEST 2008: running suspend hooks.
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sun May  4 16:52:03 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Sun May  4 16:52:04 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sun May  4 16:52:06 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sun May  4 16:52:06 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sun May  4 16:52:06 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Sun May  4 16:52:06 CEST 2008: done running suspend hooks.
Sun May  4 16:52:17 CEST 2008: running resume hooks.
===== Sun May  4 16:52:17 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Sun May  4 16:52:17 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sun May  4 16:52:17 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sun May  4 16:52:17 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
   ...done.
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sun May  4 16:52:19 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Sun May  4 16:52:19 CEST 2008: done running resume hooks.


But there's no trace of non working script in the folder /etc/acpi/resume.d/
I presume that in Hardy Heron the acpi daemon runs all the script in that folder in order to resume the pc.

What I've done in order to solve the situation was trying to get an idea of what happens in /etc/acpi/lid.sh and trying to reproduce it in the script that handle the suspend process.

But...

lid.sh handle the event that correspond to the closure of the monitor, this script is called by /etc/acpi/events/lidbtn file that consists in

> # /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh


It quite obvious that lid.sh is called when the monitor get closed, so...
Closing the monitor does shutdown correctly the backlight, the suspend process not, I've read that it's due to the switching in non graphic mode by the script, and that drives me mad : [
I'll report the code of /etc/acpi/lid.sh (just for sport)

> 
#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post


The problem is that I can't figure out what script I have to modify, I have to following script in the folder suspend.d

> -rwxr-xr-x 1 root root  90 2008-04-14 09:51 05-acpi-lock.sh
-rwxr-xr-x 1 root root  75 2008-04-14 09:51 10-thinkpad-standby-led.sh
-rwxr-xr-x 1 root root 168 2007-03-05 07:38 15-anacron.sh
-rwxr-xr-x 1 root root 698 2008-04-14 09:51 30-proc-sysfs-save-state.sh
-rwxr-xr-x 1 root root 137 2008-04-14 09:51 50-irda-stop.sh
-rwxr-xr-x 1 root root 343 2008-04-14 09:51 50-tosh-save-brightness.sh
-rwxr-xr-x 1 root root 310 2008-04-14 09:51 55-down-interfaces.sh
-rwxr-xr-x 1 root root 792 2008-04-14 09:51 60-generate-modules-list.sh
-rwxr-xr-x 1 root root 121 2008-04-14 09:51 65-services-stop.sh
-rwxr-xr-x 1 root root 276 2008-04-14 09:51 70-modules-unload.sh
-rwxr-xr-x 1 root root 158 2008-04-14 09:51 75-console-switch.sh
-rwxr-xr-x 1 root root 224 2008-04-14 09:51 80-video-pci-state.sh
-rwxr-xr-x 1 root root 314 2008-04-14 09:51 80-video-vesa-state.sh
-rwxr-xr-x 1 root root 106 2008-04-14 09:51 85-alsa-state.sh
-rwxr-xr-x 1 root root 109 2008-04-14 09:51 88-time.sh
-rwxr-xr-x 1 root root 233 2008-04-14 09:51 90-framebuffer-stop.sh


I can't realize wich one is to modify in order to shutdown the backlight
video-pci-state.sh or video-vesa-state.sh?
It should be one of those, because 75-console-switch.sh get the whole sistem to switch in console mode (I guess)

> 
75-console-switch.sh

#!/bin/sh

# And remember which console we're on
CONSOLE=`fgconsole`

# Change away from X, otherwise it'll blow up when we POST the video interface
chvt 12


respectively 80-video-pci-state.sh and 80-video-vesa-state.sh have the following code:
> 
80-video-pci-state.sh

# Save video PCI state?
if [ x$SAVE_VIDEO_PCI_STATE = xtrue ]; then
  for x in /sys/bus/pci/devices/*; do
    if [ `cat $x/class` = "0x030000" ]; then
        cat $x/config >/var/run/vga-pci-`basename $x`;
    fi
  done
fi

80-video-vesa-state.sh

#!/bin/sh

if [ x$SAVE_VBE_STATE = "xtrue" ]; then
  # Check if we're in a VESA mode - if so, we need to do things more
  # awkwardly. Otherwise, just use the state from boot.
  VBEMODE=`vbetool vbemode get`;
  if [ $VBEMODE != "3" ]; then
    vbetool vbemode set 3;
    vbetool vbestate save >$VBESTATE;
  fi
fi


Once I've realized all this mechanism, I'd like to know were can I put the magical code

```
/usr/sbin/radeontool light off
```

---

### Post by poit on 2008-05-04
I just had some success adding the magic code:

> /usr/sbin/radeontool light off

 to the end of /usr/lib/pm-utils/sleep.d/20video, right before the exit statement.  I'm not sure if that's the right thing to do, but the light now turns off on suspend and comes back on on resume.

---

### Post by sakurazukamori on 2008-05-05
Thanks Poit, that add works for me too : }
Now my backlight turn off correctly on suspend and get back on resume.

Sweeeeeeeeet : ]

---

### Post by poit on 2008-05-06
I've also figured a bandaid for the sound crash. I've added the following line:
> 
/etc/init.d/alsa-utils restart

to /usr/lib/pm-utils/sleep.d/50modules, just before the exit statement at the end. 

Again, I'm guessing I could have added it to any script called during the resume, and it's probably just a band aid and not the correct fix. but what the heck, at least now the laptop will sleep and resume without having to jump through hoops.

---

### Post by droundy on 2008-06-22
Thanks for the help guys! I came across your discussion when looking into trouble with my thinkpad x22, which showed the same symptoms, and I was able with your help to get things working.  I put the new commands in /etc/pm/sleep.d, however, which I think is a somewhat nicer solution--for instance, it won't be overwritten when pm-utils is upgraded.

I just created two executable shell scripts:

$ cat /etc/pm/sleep.d/21-turn-off-backlight.sh 
#!/bin/sh

/usr/sbin/radeontool light off
$ cat /etc/pm/sleep.d/51-restart-sound.sh 
#!/bin/sh

/etc/init.d/alsa-utils restart
$

And that's all! Thanks again for your helpful hints (conveniently provided before I even asked for help!).  :)

---

### Post by apos on 2008-06-23
See [https://bugs.launchpad.net/ubuntu/+bug/198218](https://bugs.launchpad.net/ubuntu/+bug/198218)
Greets Axel

---

### Post by poit on 2008-10-19
Update,
The same sound and video shutoff problems reappeared on Intreped. I am cluelessly working my way through the bandaid fixes for them, and it appears that this works for video shutoff on suspend for my thinkpad T30.

In the file /usr/lib/pm-utils/sleep.d$/99video

look for the section labeled "suspend_video()"
at the end of that section add the following line:

/usr/sbin/radeontool light off 

Save the file and try a suspend. For me this made the screen shut down and restart correctly. Of course, it's a bandaid fix and there is probably a better fix out there but I don't know it. I'm still looking for a way to get the sound to restart after a suspend.

---

