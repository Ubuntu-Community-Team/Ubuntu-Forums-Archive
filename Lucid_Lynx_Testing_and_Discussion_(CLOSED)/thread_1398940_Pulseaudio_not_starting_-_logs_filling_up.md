---
title: "Pulseaudio not starting - logs filling up"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-02-05
Hi

Although my sound is working, pulseaudio is not starting and my logs are filling up with messages (syslog, user, daemon) such as 


every three seconds on daemon.log
Feb  5 10:22:40 USBKarmic rtkit-daemon[1976]: Sucessfully made thread 12050 of process 12050 (n/a) owned by '1000' high priority at nice level -11.
Feb  5 10:22:40 USBKarmic rtkit-daemon[1976]: Supervising 1 threads of 1 processes of 1 users.

debug.log every minute
Feb  5 10:21:48 USBKarmic rtkit-daemon[1976]: last message repeated 24 times
Feb  5 10:22:48 USBKarmic rtkit-daemon[1976]: last message repeated 24 times
Feb  5 10:23:48 USBKarmic rtkit-daemon[1976]: last message repeated 24 times

syslog
Feb  5 10:25:29 USBKarmic rtkit-daemon[1976]: Sucessfully made thread 12335 of process 12335 (n/a) owned by '1000' high priority at nice level -11.
Feb  5 10:25:29 USBKarmic rtkit-daemon[1976]: Supervising 1 threads of 1 processes of 1 users.
Feb  5 10:25:29 USBKarmic pulseaudio[12335]: module-stream-restore.c: Failed to parse module arguments
Feb  5 10:25:29 USBKarmic pulseaudio[12335]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
Feb  5 10:25:29 USBKarmic pulseaudio[12335]: main.c: Module load failed.
Feb  5 10:25:29 USBKarmic pulseaudio[12335]: main.c: Failed to initialize daemon.
Feb  5 10:25:29 USBKarmic pulseaudio[12333]: main.c: Daemon startup failed.
Feb  5 10:25:30 USBKarmic rtkit-daemon[1976]: Sucessfully made thread 12338 of process 12338 (n/a) owned by '1000' high priority at nice level -11.
Feb  5 10:25:30 USBKarmic rtkit-daemon[1976]: Supervising 1 threads of 1 processes of 1 users.
Feb  5 10:25:30 USBKarmic pulseaudio[12338]: module-stream-restore.c: Failed to parse module arguments
Feb  5 10:25:30 USBKarmic pulseaudio[12338]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
Feb  5 10:25:30 USBKarmic pulseaudio[12338]: main.c: Module load failed.
Feb  5 10:25:30 USBKarmic pulseaudio[12338]: main.c: Failed to initialize daemon.
Feb  5 10:25:30 USBKarmic pulseaudio[12336]: main.c: Daemon startup failed.
Feb  5 10:25:34 USBKarmic rtkit-daemon[1976]: Sucessfully made thread 12341 of process 12341 (n/a) owned by '1000' high priority at nice level -11.
Feb  5 10:25:34 USBKarmic rtkit-daemon[1976]: Supervising 1 threads of 1 processes of 1 users.
Feb  5 10:25:34 USBKarmic pulseaudio[12341]: module-stream-restore.c: Failed to parse module arguments
Feb  5 10:25:34 USBKarmic pulseaudio[12341]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
Feb  5 10:25:34 USBKarmic pulseaudio[12341]: main.c: Module load failed.
Feb  5 10:25:34 USBKarmic pulseaudio[12341]: main.c: Failed to initialize daemon.
Feb  5 10:25:34 USBKarmic pulseaudio[12339]: main.c: Daemon startup failed.
Feb  5 10:25:35 USBKarmic rtkit-daemon[1976]: Sucessfully made thread 12344 of process 12344 (n/a) owned by '1000' high priority at nice level -11.
Feb  5 10:25:35 USBKarmic rtkit-daemon[1976]: Supervising 1 threads of 1 processes of 1 users.
Feb  5 10:25:35 USBKarmic pulseaudio[12344]: module-stream-restore.c: Failed to parse module arguments
Feb  5 10:25:35 USBKarmic pulseaudio[12344]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
Feb  5 10:25:35 USBKarmic pulseaudio[12344]: main.c: Module load failed.
Feb  5 10:25:35 USBKarmic pulseaudio[12344]: main.c: Failed to initialize daemon.
Feb  5 10:25:35 USBKarmic pulseaudio[12342]: main.c: Daemon startup failed.

any clues?

The only thing I can think is that I have just installed pulseaudio-equalizer_2.5, but I thought that was just a front end?

---

### Post by dino99 on 2010-02-05
several ways to go ahead:

- first: clean, autoclean, autoremove then "sudo apt-get install -f"
- check groups: your user might be in pulse group
- remove/purge pulseaudio then reinstall
- clean your system with bleachbit: apps --> system tools --> bleachbit (as root)

install the last one (ppa) and take time to understand what you do (bleachbit is very powerfull and can wipe your system if you make an error)

Are you running this distro on an external drive (usb) ?

---

### Post by ubername on 2010-02-05
> **dino99 said:**
> several ways to go ahead:

- first: clean, autoclean, autoremove then "sudo apt-get install -f"
- check groups: your user might be in pulse group
- remove/purge pulseaudio then reinstall
- clean your system with bleachbit: apps --> system tools --> bleachbit (as root)

install the last one (ppa) and take time to understand what you do (bleachbit is very powerfull and can wipe your system if you make an error)

Are you running this distro on an external drive (usb) ?

Thanks for the response

Done the first one (do that anyway as a matter of routine)
Checked groups- user is not in group 'pulse' (according to GUI user admin tool)
Used bleachbit a couple of days ago - is there something specific you were thinking of or just generally 'spring cleaning'?

Interesting question re: USB - Yes, I am running on an external drive (does USBKarmic give it away, or was there something else?)

p.s. although it's called USBKarmic it is actually Lucid upgraded from Karmic.

edit - also removed (complete) pulseaudio and reinstalled via synaptic

---

### Post by ubername on 2010-02-05
Seem to have fixed it by deleting ~/.pulse directory

Might have been some kind of conflict with parameters from old version of pulse-equaliser?

---

### Post by dino99 on 2010-02-05
oh yeah of course, i've forgotten about hidden .pulse and maybe .gstreamer.
myself having hda-intel chipset not recognized: lucid don't see that hardware but can play alsa/esound without problem, curious, logs don't help at time.

i often use into console: alsamixer -Dhw when things are broken and drop down volume on header

---

### Post by psyke83 on 2010-02-05
> **ubername said:**
> Hi

Although my sound is working, pulseaudio is not starting and my logs are filling up with messages (syslog, user, daemon) such as 

<snip>

The only thing I can think is that I have just installed pulseaudio-equalizer_2.5, but I thought that was just a front end?

There was a bug in v2.5 of pulseaudio-equalizer which caused your problem. It's fixed in v2.6 onwards, but you must first remove the invalid configuration that was created by v2.5.

After you've upgraded to the latest version, delete the configuration and restart pulseaudio:
```
$ rm ~/.pulse/default.pa; pkill pulseaudio
```

You won't have the problem any more.

---

### Post by ubername on 2010-02-06
Thanks psyke83

---

