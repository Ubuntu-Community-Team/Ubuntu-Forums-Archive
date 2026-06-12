---
title: "how to check if pulseaudio is working or not?"
date: 2009-01-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-13
Hi all, 
 Is there anyway to check if pulseaudio is working or not? There doesn't seem to be a way to check the same. 

Trying to restart gives the following. 

```

$ /etc/init.d/pulseaudio restart
 * PulseAudio configured for per-user sessions

```I ask because trying to get gnome-volume-control gives me the following.

```


$ gnome-volume-control

** (gnome-volume-control:9103): WARNING **: Failed to acquire org.gnome.VolumeControl

** (gnome-volume-control:9103): WARNING **: Could not acquire name on session bus

```

gnome-sound-properties is there anymore as people know.

```


$ gnome-sound-properties
The program 'gnome-sound-properties' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-control-center
bash: gnome-sound-properties: command not found


```

While gnome-control-center is already installed. 

```


$ dpkg -l gnome-control-center
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnome-control- 1:2.25.3-0ubun utilities to configure the GNOME desktop


```

---

### Post by hivelocitydd on 2009-01-13
The following thread looks helpful to you

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by RAOF on 2009-01-13
> **hivelocitydd said:**
> The following thread looks helpful to you

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

No, probably not.

You can check whether pulseaudio is working or not by connecting a client to it; I'd suggest installing pavucontrol (the pulse volume control). Fire that up; if it works, so is pulse. It'll fail with "could not connect to server" if pulse isn't working.

This:
```

$ gnome-volume-control

** (gnome-volume-control:9103): WARNING **: Failed to acquire org.gnome.VolumeControl

** (gnome-volume-control:9103): WARNING **: Could not acquire name on session bus

```
is because the volume control is already running.  The applet's running, too, but it doesn't appear for me unless I start it after the session's up properly.  It's possible this is another race.

---

### Post by ShirishAg75 on 2009-01-14
pavucontrol is already installed but got the error 

```
Connection failed: Connection refused 
```

Its in /bin/ so don't think need sudo rights for the same. 

Here's something more I got, although this might be a diferent issue. 

```


$ pavucontrol 

(pavucontrol:20107): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(pavucontrol:20107): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

```

---

### Post by BwackNinja on 2009-01-14
Not working for you then. You can try running 'pulseaudio' in a terminal (no --daemon so that you can see if/when it fails) and if you don't see any output more than like 3 lines, then its probably working and you should check pavucontrol then to make sure.

also - to check if it is running, 'ps ax | grep pulseaudio' is always a nice thing to do.

---

### Post by ShirishAg75 on 2009-01-14
These are the outputs I got of the following. 

```


$ pulseaudio no --daemon
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.


```

Grepping for pulseaudio 

```


$ ps ax | grep pulseaudio
21491 ?        S<sl   0:00 pulseaudio no --daemon
21494 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
21498 pts/2    S+     0:00 grep pulseaudio


```

doing pavucontrol showed it for couple of minutes and then hanged.

---

### Post by ShirishAg75 on 2009-01-14
gave another shot and got this on the cli. 

```


pulseaudio no--daemon
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: pid.c: Stale PID file, overwriting.
[COLOR=DarkOrange]W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
E: source.c: Assertion 'PA_SOURCE_IS_OPENED(s->thread_info.state)' failed at pulsecore/source.c:428, function pa_source_post(). Aborting.[/COLOR]
[COLOR=SandyBrown]Aborted[/COLOR]

```

Btw put up a bug-report on the missing gnome-sound-properties as well [lpbug] 316991 [/lpbug]

---

### Post by handaxe on 2009-01-14
FYI, ```
pulseaudio no --deamon
``` is not a valid command.

The suggestion was to run pulseaudio without the -D or --daemonize options, although the writing was misleading.

It probably will not effect the outcome though, as it did not generate an error.

HA

---

