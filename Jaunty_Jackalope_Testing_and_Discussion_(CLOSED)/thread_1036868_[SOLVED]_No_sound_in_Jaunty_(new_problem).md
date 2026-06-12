---
title: "[SOLVED] No sound in Jaunty (new problem?)"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by samjh on 2009-01-11
Pretty straight-forward problem: no sound in Jaunty.  I just did a dist-upgrade from Intrepid several hours ago.

I have looked at every Jaunty-related audio bug report on Launchpad, and worked through several existing threads, including:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=979093](http://ubuntuforums.org/showthread.php?t=979093)

I've tried "alsamixer -Dhw" and "alsamixer -Dhw:0", but to no avail (there are no error messages when running alsamixer).  I have noticed that the Front speaker is always at 0 volume after each reboot, but even when I manually set it to 100, there is no sound.  It also appears that my headphone output is off (I use headphones), and although I don't know whether it was ever "on", I can't find a way to get it on (I've checked the physical connection).

I have run through the diagnostics in the PulseAudio HOWTO.  The result is that the PulseAudio Device Chooser and the Volume Control shows various applications playing sound, but no sound can be heard.

I have reinstalled alsa-utils, pulseaudio and related packages.  Tried playing with the sliders in both the Sound Preferences volume control and the alsamixer application.  Still nothing can be heard.

Sessions applet shows PulseAudio Session Management and Sound System are set to run at startup.

Here are some CLI outputs:

lspci | grep Audio
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm not sure if this one is relevant, but here's the contents of /etc/modules
```
fuse
lp
rtc
sbp2
```

Contents of /etc/init.d/pulseaudio
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          pulseaudio esound
# Required-Start:    $remote_fs $syslog hal
# Required-Stop:     $remote_fs $syslog hal
# Should-Start:      hal
# Should-Stop:       hal
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start the PulseAudio sound server
# Description:       System mode startup script for
#                    the PulseAudio sound server.
### END INIT INFO

DAEMON=/usr/bin/pulseaudio
PIDFILE=/var/run/pulse/pid 
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -x $DAEMON || exit 0

. /lib/lsb/init-functions

PULSEAUDIO_SYSTEM_START=0
DISALLOW_MODULE_LOADING=1
test -f /etc/default/pulseaudio && . /etc/default/pulseaudio
if [ "$PULSEAUDIO_SYSTEM_START" != "1" ]; then
	log_warning_msg "PulseAudio configured for per-user sessions"
	exit 0
fi

pulseaudio_start () {
	log_daemon_msg "Starting system PulseAudio Daemon"
	start-stop-daemon -x $DAEMON -p $PIDFILE --start -- --system --daemonize --high-priority --log-target=syslog --disallow-module-loading=$DISALLOW_MODULE_LOADING
	if [ -e /var/run/pulse/.esd_auth ]; then
		chown pulse:pulse-access /var/run/pulse/.esd_auth
		chmod 640 /var/run/pulse/.esd_auth
	fi
	if [ -e /var/run/pulse/.pulse-cookie ]; then
		chown pulse:pulse-access /var/run/pulse/.pulse-cookie
		chmod 640 /var/run/pulse/.pulse-cookie
	fi
	log_end_msg $?
}

pulseaudio_stop () {
	local status
	log_daemon_msg "Stopping system PulseAudio Daemon"
	start-stop-daemon -p $PIDFILE --stop --retry TERM/3 || status=$?
	case "$status" in
		1)
			log_warning_msg "PulseAudio Daemon is not running"
			;;
		2)
			log_warning_msg "PulseAudio Daemon is still running..."
			;;
	esac
	log_end_msg $status
}

case "$1" in
	start|stop)
		pulseaudio_${1}
		;;
	restart|reload|force-reload)
		pulseaudio_stop
		pulseaudio_start
		;;
	force-stop)
		pulseaudio_stop
		killall pulseaudio || true
		sleep 2
		killall -9 pulseaudio || true
		;;
	*)
		echo "Usage: /etc/init.d/pulseaudio {start|stop|force-stop|restart|reload|force-reload}"
		exit 1
		;;
esac

exit 0
```

Some ideas would be wonderful. :)

---

### Post by LordVeovis on 2009-01-11
I know wen I first installed I had no sound and I could not figure it out for about a week... It was just user error in my case though.  I had to unmute the "front" speakers (as in front, rear, surround, center.....)
make sure none of your outputs are muted that shouldnt be

---

### Post by samjh on 2009-01-11
> **LordVeovis said:**
> I know wen I first installed I had no sound and I could not figure it out for about a week... It was just user error in my case though.  I had to unmute the "front" speakers (as in front, rear, surround, center.....)
make sure none of your outputs are muted that shouldnt be

How would I check this?

The older volume controls had individual sliders and mute buttons for each channel.  The new volume controls have just one slider and mute button for input, output, etc. - not front, main, pcm...

Also any changes I make in alsamixer are reset after reboot.

---

### Post by LordVeovis on 2009-01-11
ya, I was looking for where you would do it now, I am not sure yet.  My volume Control wont open at the moment.  This has happened before and it will like require a restart.  I only restart about once a day, and not yet.  I hate typing my large encryption key for each of my encrypted drives.  But I would never go back to an unencrypted system :P

---

### Post by ubername on 2009-01-11
I think I have the same problem. I have just posted a thread called 'Where is the sound control' but the symptoms described here are the same. I had not moved as far in the analysis as the poster of this thread.

---

### Post by LordVeovis on 2009-01-11
Ok, if you right click you can go to preferences and look at the volumes individually.  I guess I will restart here so I can access my 'Volume Control'

---

### Post by ubername on 2009-01-11
Some forward (and backward) movement here. I went into 'preferences' from right-clicking my volume control and set the volume control to 'front'. I then noticed the volume icon on my task-bar had a muted symbol next to it so I pushed the mute button on the keyboard and was logged out. I logged back in and un-muted the sound via left clicking the volume control and deselecting the mute option and my sound worked (I only know this because I happened to have a website with sound open) 

I guess my big problem now (in terms of usability, not understanding how it all fits together) is that all my keyboard sound controls seem to log me out. I have a logitech cordless MX3000 if that helps.

I would also welcome simple suggestions as to how to check the sound is working (similar to the 'test' button in gnome-sound-propertoies) so I can diagnose better where the problems are.

TIA

---

### Post by LordVeovis on 2009-01-11
I think we should submit a bug about the front starting off muted.  It did this to me as well.  I'm sure we are not the only 2.

EDIT:  Especially since they made it a little harder (IMHO) to change individual volumes like those.

---

### Post by tawmas on 2009-01-11
> **ubername said:**
> I guess my big problem now (in terms of usability, not understanding how it all fits together) is that all my keyboard sound controls seem to log me out. I have a logitech cordless MX3000 if that helps.

I also noticed the same (I have a Microsoft cordless keyboard, so it's not specific to a single brand or model). We need to open a bug about that in Launchpad.

---

### Post by tawmas on 2009-01-11
> **LordVeovis said:**
> I think we should submit a bug about the front starting off muted.  It did this to me as well.  I'm sure we are not the only 2.

Looks like we are in good company. Mine was not muted, but set so low as to not be audible. There was a thread about that a few days ago, that I cannot find right now.

In there, there's a command for adjusting the levels from the command line, which is what got me my sound back.

---

### Post by LordVeovis on 2009-01-11
All of my touch buttons for volume / media playback stopped working partway through 8.10 and I have never been able to get them to work again.  However I have never tested that the keyboard still works via Window$.  For all I know my buttons are broken now.  >.<  any way to know for sure?

---

### Post by autocrosser on 2009-01-11
And if you want a "friendlyier" mixer---download gnome-alsa-mixer---the GUI is rather self-evident......

---

### Post by LordVeovis on 2009-01-11
> **autocrosser said:**
> And if you want a "friendlyier" mixer---download gnome-alsa-mixer---the GUI is rather self-evident......

Thanks for the advice!  I didnt know there was an app I could still D/L  +1 thanks for you. :P

---

### Post by ubername on 2009-01-11
Is anyone else experiencing the logout issue when using the sound controls on the keyboard? I have just reconfigured my system to use a generic logitech cordless keyboard hoping that would resolve the problem but to no avail.

---

### Post by autocrosser on 2009-01-11
> **LordVeovis said:**
> Thanks for the advice!  I didnt know there was an app I could still D/L  +1 thanks for you. :P

No problem--I've used it for years & keep a shortcut of it in my bottom panel.....

---

### Post by LordVeovis on 2009-01-11
> **ubername said:**
> Is anyone else experiencing the logout issue when using the sound controls on the keyboard? I have just reconfigured my system to use a generic logitech cordless keyboard hoping that would resolve the problem but to no avail.

Have you looked at your error logs yet so we can try to narrow what is actually causing the logoff?  I know it's the buttons, but what are those buttons causing the system to do that logs you off.  Not sure what all the logs you should look at, other people here will be able to better guide you to which ones.

---

### Post by autocrosser on 2009-01-11
You might also take a look at keyboard shortcuts & see if your keys have been remapped--I have found that several of mine have.

---

### Post by tawmas on 2009-01-11
> **autocrosser said:**
> You might also take a look at keyboard shortcuts & see if your keys have been remapped--I have found that several of mine have.

I have the same problem. The keyboard shortcuts look correct to me. When I tried to edit one for testing, I got logged out as well. To me, it looks like all the extended buttons behave like CTRL-ALT-BACKSPACE (and they started doing so more or less at the same time when this combination was disabled).

I'd like to file a bug, but I don't know what the proper package for that.

---

### Post by LordVeovis on 2009-01-11
> **tawmas said:**
> I have the same problem. The keyboard shortcuts look correct to me. When I tried to edit one for testing, I got logged out as well. To me, it looks like all the extended buttons behave like CTRL-ALT-BACKSPACE (and they started doing so more or less at the same time when this combination was disabled).

I'd like to file a bug, but I don't know what the proper package for that.

Perhaps you can re-enable the ctrl-alt-backspace and test again?  There is a way to re-enable it, but I don't remember where.

---

### Post by ubername on 2009-01-11
> **autocrosser said:**
> And if you want a "friendlyier" mixer---download gnome-alsa-mixer---the GUI is rather self-evident......

Thanks. There was a hyphen too many there. The command is gnome-alsamixer

---

### Post by autocrosser on 2009-01-11
The main place is configuration editor--it is not enabled by default---edit your menu under System Tools to have it available.  After you have it, look at metacity>global_keybindings. You can edit in a not as friendly way....but at least you won't get logged out during editing that way...........:mad:

---

### Post by autocrosser on 2009-01-11
> **ubername said:**
> Thanks. There was a hyphen too many there. The command is gnome-alsamixer

Not enough coffee yet:lolflag:

---

### Post by LordVeovis on 2009-01-11
> **ubername said:**
> Thanks. There was a hyphen too many there. The command is gnome-alsamixer

I used tab so I didn't notice.

---

### Post by tawmas on 2009-01-11
> **autocrosser said:**
> The main place is configuration editor--it is not enabled by default---edit your menu under System Tools to have it available.  After you have it, look at metacity>global_keybindings. You can edit in a not as friendly way....but at least you won't get logged out during editing that way...........:mad:

Thanks, I already have Configuration Editor enabled. I've just looked in there, but there don't seem to be any configuration keys related to media or anything. Just those for desktop actions.

---

### Post by ubername on 2009-01-11
> **autocrosser said:**
> The main place is configuration editor--it is not enabled by default---edit your menu under System Tools to have it available.  After you have it, look at metacity>global_keybindings. You can edit in a not as friendly way....but at least you won't get logged out during editing that way...........:mad:

Thanks for this. I'm afraid I can't follow your post as I don't have anything called system tools. Can you help? (I've looked in System>Preferences>Main Menu  for options about tools or configuration editor but can't find anything.)

TIA

---

### Post by ShirishAg75 on 2009-01-11
ubername, 
 I think he was talking of first installing the package named gnome-system-tools.

```
$ sudo apt-get install gnome-system-tools
```

Or can do the same thing in synaptic/packagekit (whatever your poison)

Then go Application >? System Tools. 

You should see stuff like Alternatives Configurator and stuff.

---

### Post by ubername on 2009-01-11
Hi all and thanks for the help so far

To let you know I have discovered that pretty much all my 'extra' keys cause me to log out so I have started a new thread for that. I will investigate the Config editor thing now.

---

### Post by ubername on 2009-01-11
> **ShirishAg75 said:**
> ubername, 
 I think he was talking of first installing the package named gnome-system-tools.

```
$ sudo apt-get install gnome-system-tools
```

Or can do the same thing in synaptic/packagekit (whatever your poison)

Then go Application >? System Tools. 

You should see stuff like Alternatives Configurator and stuff.

Thanks. I did the synaptic thing and discovered that I already had gnome-system-tools installed. So then I went to Preferences>Main Menu and looked in Applications>System Tools. Lo and behold, there was something called Configuration Editor. I haven't tried it yet but thought I would just thank you for the help so far.

---

### Post by ubername on 2009-01-11
> **tawmas said:**
> Thanks, I already have Configuration Editor enabled. I've just looked in there, but there don't seem to be any configuration keys related to media or anything. Just those for desktop actions.


Likewise

---

### Post by autocrosser on 2009-01-11
The problem is that you need the keyboard shortcuts window open to see the key name & config editor to "create" a new key shortcut---I remember a tutorial about that from a couple of years ago---anyway, after you see what the key is you can make the replacement---not friendly as I said---but afterwards you'll get the actions you want--explore the keybindings_commands. I can post a old tutorial I made on CD ejection to show what you can do with it......


[http://ubuntuforums.org/showthread.php?t=660515](http://ubuntuforums.org/showthread.php?t=660515)

---

### Post by BwackNinja on 2009-01-11
Same keyboard shortcuts logging me out problem as others. I've had it for a while, but I assumed it was because of something I did and that my install was messed up because I saw no thread and couldn't find a bug report on it. Seems I was wrong :)

---

### Post by LordVeovis on 2009-01-11
> **BwackNinja said:**
> Same keyboard shortcuts logging me out problem as others. I've had it for a while, but I assumed it was because of something I did and that my install was messed up because I saw no thread and couldn't find a bug report on it. Seems I was wrong :)

If you ever notice something liek that, just toss it up somewhere on the forums, someone should be able to at least point you in the right direction.

---

### Post by giorsat on 2009-01-11
i had to disable sound in gdm . it hanged on login at a very low volume and it stopped everything else from working. I noticed because after 1 week I tried head phones and i noticed a very low beep cracking. it was gdm

---

### Post by tawmas on 2009-01-11
> **BwackNinja said:**
> Same keyboard shortcuts logging me out problem as others. I've had it for a while, but I assumed it was because of something I did and that my install was messed up because I saw no thread and couldn't find a bug report on it. Seems I was wrong :)

What kind of keyboard do you have?

---

### Post by samjh on 2009-01-11
> **LordVeovis said:**
> ya, I was looking for where you would do it now, I am not sure yet.  My volume Control wont open at the moment.  This has happened before and it will like require a restart.  I only restart about once a day, and not yet.  I hate typing my large encryption key for each of my encrypted drives.  But I would never go back to an unencrypted system :P

> **autocrosser said:**
> And if you want a "friendlyier" mixer---download gnome-alsa-mixer---the GUI is rather self-evident......

> **ubername said:**
> Thanks. There was a hyphen too many there. The command is gnome-alsamixer

You sirs, are legends among living men. :)

Fixed!

And a bug report has been filed on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/316199](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/316199)
Please confirm it if you had the same issue.

Thanks people! :)

---

### Post by mewithafez on 2009-01-11
For some reason, even though the new volume control applet has the volume up and recognizes that stuff is being played on the speakers, and the pulse audio controller shows that the applications are outputting and the speakers should be as well, virtually no sound comes out of the speakers. 

This came about after I tried to use Jokosher, so I think it might have been something with GStreamer's configuration that got messed with but I have no idea. I've tried reinstalling many components and even dpkg-reconfigure on many parts of gstreamer and pulseaudio but no dice. The inputs (built in mic and USB webcam/mic) all work and the output (speakers) claim to work in all mixers I've tried. 

Not sure whether to report a bug, or even how in this case. Thanks for any help!

EDIT: On second review, it looks like I have the same bug as the OP, front always resets to no volume on reboot but even when I turn it up, no dice. I'll give gnome-alsamixer a go and update this if it works :)

DOUBLE EDIT: Well, I can turn up front, but I could do that before with the volume applet. Even if the volume is all the way up, which it is in every mixer (even amixer) the sound is basically inaudible (if you press your ear to the case, you can hear it faintly).

---

### Post by sudo panda on 2009-02-01
hey,
im not sure if this has already been covered. but i found a fix to my no sound problem in jaunty.

I didn't have any sounds from rhythmbox when i played music after installing the latest jaunty updates, so i installed **asoundconf-gtk** and selected my card (mine being CA0106) in the Default Sound Card section under System | Preferences | Default Sound Card.

Then i went into Applications | Sound and Video | Pulse Audio Device chooser, left-clicked the icon up the top right and made my Default Server **Default**.

Finally i left-clicked the device chooser again, went to my volume control and made sure when i played my music through rythmbox that under the playback tab under the down arrow i selected** Move Stream** to CA0106 (my default sound card again)

---

