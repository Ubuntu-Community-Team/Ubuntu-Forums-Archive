---
title: "Alsa not running"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tuxkumar on 2009-04-17
I updated my PC from Ubuntu 8.10 to 9.04 yesterday and sound stopped working after that.

Below is what i get from lspci:

$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Alsa is installed but is not running. I tried to reload it and got the below error:
$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/saran/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/saran/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

Pulse audio is running and Pulse volume control shows only Master Control and there are no other devices.

Any hints? 

---
SK

I blog here: [http://techsk.blogspot.com](http://techsk.blogspot.com)

---

### Post by tuxkumar on 2009-04-17
I found a solution here: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(CategoryHardware](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(CategoryHardware))

All i had to do was to load the sound driver with the command:
$ sudo modprobe snd_hda_intel

Under System->Preferences->Sound i changed everything to ALSA.

Now i can hear the sound. Weird that the driver doesn't load by default.

I have now added the modprobe command to /etc/rc.local (just before exit 0). Have to check if sound works after reboot.

---

### Post by tuxkumar on 2009-04-17
It did not work after reboot (without logout).

Master Volume controller was muted when i logged in. Unmuted and set the controls correctly. After that I logged out and then logged in again. I could hear the login sound. 

Rebooted the system twice to check. No Problem. Sound still works.

Have to see how long this will be stable.

---

