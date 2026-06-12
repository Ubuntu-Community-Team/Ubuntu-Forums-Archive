---
title: "user switch crashes 'target' session"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2010-11-09
I have a relatively new 10.10 (AMD64) setup.  I believe I first installed it around the Beta 3 or RC 1 and only as a test setup?  Now I'm running it as my main workstation and with both my wife and I sharing it.  Unfortunately, one thing I did not test beforehand was the user switching and now it's causing crashes.  I have a bunch of log-files I think are apropos but I can't figure-out how to file a Launchpad bug; I've done it in the past but I know they've tightened-up on submissions.

**MY SYSTEM**

- Ubuntu 10.10 (AMD64)
- AMD BE-2300, 4 GB RAM
- Nvidia 8400GS
- Nvidia proprietary video v260.19.06
- dual-HD sw RAID

I've done very little to customize anything?  For instance, the Nvidia driver was installed via the built-in Additional Drivers tool.  I have not made any manual changes to any configuration files, that I can remember.

**SYMPTOM**

I'll return home after work and find that my wife has switched the workstation from my session to her own.  I clear her screensaver (we use the same pw), then click on the drop-down menu for Lock Screen, Switch User etc and select myself.

Most of the time it will correctly switch to 'my' screensaver and everything's fine.  Other times, however, it will return to the original login screen and it will show my account as Not Logged In.  At this point I know my session has crashed, along with any apps I had open.

**LOG FILES**

I have attached a ZIP file with several log files right at the time of one of these crashes.  In this instance, I had tried to switch back to my own session at 13:59.  I also included a bunch of messages from 11:51 that looked suspicious, i.e., maybe my session had already crashed 2 hours earlier?

**EXAMPLES OF LOG-FILE ERRORS?**

From the logs I see a bunch of warnings but nothing that clearly tells me what's wrong, e.g. from syslog:
[LIST]
[*]Unable to load file '/etc/gdm/custom.conf' no such file"
[*]server acpid: client 1347 has disconnected
[*]server gdm-simple-greeter: Gtk-WARNING, widget not within a GtkWindow
[*]alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 2 is less than avail 38
[*]server NetworkManager[1209]: Could not get owner of name '
[*]server jungledisk: xServerTransport - Transport error: couldn't connect to host [127.0.0.1]
[/LIST]
I _know_ that that last one shows that my existing session had disappeared!

---

### Post by mashedbear on 2010-11-20
Sorry I can't provide any solutions  - but I (and others) have similar problems...

[http://ubuntuforums.org/showthread.php?p=10111811#post10111811](http://ubuntuforums.org/showthread.php?p=10111811#post10111811)

Help anyone?

---

### Post by Lokiii on 2011-06-13
I have the same problem in 11.04. I found [this thread](http://www.nvnews.net/vbulletin/showthread.php?p=2260258) which suggests its a bug in xorg which has been fixed in 1.8.1, so Im going to try and update xorg somehow as the xorg version in ubuntu 11.04 is 1.7.6

---

### Post by bsmith1051 on 2011-06-13
Nope, that discussion is over a year old.  Ubuntu 10.10 already includes Xorg **1.9** and 11.04 is obviously newer still.
[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

In the meantime I've abandoned the Nvidia binary drivers and just rely on generic drivers.  Might abandon Ubuntu for Win7, actually, as I've also had problems with my other Ubuntu machine and none on my Win7 machines :(

---

