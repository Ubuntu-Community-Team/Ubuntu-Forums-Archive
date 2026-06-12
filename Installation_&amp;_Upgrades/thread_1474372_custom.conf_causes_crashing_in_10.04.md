---
title: "custom.conf causes crashing in 10.04"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2010-05-06
Hi,
I just installed Edubuntu 10.04 and Its crashed on me twice already (by comparison, I lost 8.10 only four or five times during the entire year and a half I was using it). The monitor goes blank, then produces odd color schemes and then loses the signal altogether, eventually rebooting. It seems to be somehow connected to a non-existent /etc/gdm/custom.conf file.
Here's the output from syslog:

======================
May  5 21:16:44 rishon kernel: [ 9036.624038] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  5 21:16:44 rishon kernel: [ 9036.624057] render error detected, EIR: 0x00000000
May  5 21:16:44 rishon kernel: [ 9036.624091] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 343078 at 343077)
May  5 21:16:46 rishon kernel: [ 9038.544032] [drm:i915_gem_idle] *ERROR* hardware wedged
May  5 21:16:46 rishon gnome-session[1487]: WARNING: Detected that screensaver has left the bus
May  5 21:16:47 rishon gdm-simple-slave[2804]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  5 21:16:47 rishon pulseaudio[2803]: pid.c: Stale PID file, overwriting.
May  5 21:16:47 rishon pulseaudio[2803]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-n7gcTngsoQ: Connection refused
May  5 21:16:47 rishon pulseaudio[2808]: pid.c: Daemon already running.
May  5 21:16:48 rishon pulseaudio[2811]: pid.c: Daemon already running.
May  5 21:16:48 rishon acpid: client connected from 2809[0:0]
May  5 21:16:48 rishon acpid: 1 client rule loaded
May  5 21:16:49 rishon kernel: [ 9041.509352] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May  5 21:16:49 rishon kernel: [ 9041.840010] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  5 21:16:49 rishon kernel: [ 9041.840020] render error detected, EIR: 0x00000000
May  5 21:16:49 rishon kernel: [ 9041.840943] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 343080 at 343077)
May  5 21:16:51 rishon bonobo-activation-server (dbclinton-2818): could not associate with desktop session: Failed to connect to socket /tmp/dbus-n7gcTngsoQ: Connection refused
May  5 21:16:51 rishon kernel: [ 9043.916015] [drm:i915_gem_idle] *ERROR* hardware wedged
May  5 21:16:51 rishon gdm-simple-slave[2825]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  5 21:16:51 rishon acpid: client 2809[0:0] has disconnected
May  5 21:16:51 rishon acpid: client connected from 2827[0:0]
May  5 21:16:51 rishon acpid: 1 client rule loaded
May  5 21:16:52 rishon kernel: [ 9045.048796] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May  5 21:16:53 rishon kernel: [ 9045.380008] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  5 21:16:53 rishon kernel: [ 9045.380015] render error detected, EIR: 0x00000000
May  5 21:16:53 rishon kernel: [ 9045.380894] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 343082 at 343077)
May  5 21:16:55 rishon kernel: [ 9047.440015] [drm:i915_gem_idle] *ERROR* hardware wedged
May  5 21:16:55 rishon gdm-simple-slave[2833]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  5 21:16:55 rishon acpid: client 2827[0:0] has disconnected
May  5 21:16:55 rishon acpid: client connected from 2835[0:0]
May  5 21:16:55 rishon acpid: 1 client rule loaded
May  5 21:16:56 rishon kernel: [ 9048.578284] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May  5 21:16:56 rishon kernel: [ 9048.908007] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  5 21:16:56 rishon kernel: [ 9048.908015] render error detected, EIR: 0x00000000
May  5 21:16:56 rishon kernel: [ 9048.908931] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 343084 at 343077)
May  5 21:16:58 rishon kernel: [ 9050.960014] [drm:i915_gem_idle] *ERROR* hardware wedged
May  5 21:16:58 rishon gdm-simple-slave[2841]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
May  5 21:16:58 rishon acpid: client 2835[0:0] has disconnected
May  5 21:16:58 rishon acpid: client connected from 2843[0:0]
May  5 21:16:58 rishon acpid: 1 client rule loaded
May  5 21:16:59 rishon kernel: [ 9052.095381] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May  5 21:16:59 rishon kernel: Kernel logging (proc) stopped.
May  5 21:16:59 rishon rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="598" x-info="http://www.rsyslog.com"] exiting on signal 15.
========================

And here's auth.log:
========================
May  5 21:16:46 rishon gnome-keyring-daemon[1469]: dbus failure unregistering from session: Connection is closed
May  5 21:16:46 rishon polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.34, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)
May  5 21:16:46 rishon gnome-keyring-daemon[1469]: dbus failure unregistering from session: Connection is closed
May  5 21:16:46 rishon gdm-session-worker[1308]: pam_unix(gdm:session): session closed for user 
========================
Any ideas?
Thanks,

---

### Post by dbclinton on 2010-05-13
It turns out that the crashes were unrelated to custom.conf or to GDM. They were actually the result of a known and unresolved bug involving my Intel i845 video device.
You can see the bug report and comments here:

[https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492?comments=all](https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492?comments=all)

and some workarounds here: 

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

