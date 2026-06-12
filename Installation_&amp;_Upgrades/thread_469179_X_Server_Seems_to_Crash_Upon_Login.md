---
title: "X Server Seems to Crash Upon Login"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by asutula on 2007-06-09
I've recently built my own computer and I've been having a hard time getting Ubuntu 7.04 running correctly on it.  Here are the details of my machine:

[LIST]
[*]Asus AM2 M2N-SLI Deluxe Motherboard, version 0903 BIOS (latest)
[*]AMD Athalon 64 X2 4600+ CPU
[*]2 DDR2 800 MHz 1 GB memory modules
[*]eVGA e-GeForce 7600GS graphics card
[*]Pioneer SATA DVDRW optical drive
[*]Seagate 320 GB SATA hard drive
[*]Aspire 420 W power supply
[/LIST]

Here is my most recent installation scenario:

To help eliminate the possibility of bad hardware, I did a Windows install first. It seems to run pretty well except for a few strange, but expected, Windows errors. 

I used the Ubuntu 7.04 i386 alternate (text based) install disc (I heard about people having problems finding libraries etc. with AMD64 Ubuntu). When booting from the disc, I got a kernel panic message that suggested I boot with the 'noapic' option. I did that and things seemed to work smoothly from there. Ubuntu was installed onto its own partition. Upon first reboot, I was able to log into the system, but within seconds, the screen went blank and dumped me to the login screen. I tried to log in again with the same result.

From a text based console, I installed and enabled nvidia-glx hoping that would fix what seemed to be a problem with the X server. That did not seem to help. Same results: log into Gnome and get a blank screen and back to the login screen within seconds.

There is not much useful information in /var/log/messages. At the time I get kicked back to the login screen, messages looks like:

```
Jun  9 13:50:28 shambhala syslogd 1.4.1#20ubuntu4: restart.
Jun  9 14:06:03 shambhala gconfd (aaron-10157): starting (version 2.18.0.1), pid 10157 user 'aaron'
Jun  9 14:06:03 shambhala gconfd (aaron-10157): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun  9 14:06:03 shambhala gconfd (aaron-10157): Resolved address "xml:readwrite:/home/aaron/.gconf" to a writable configuration source at position 1
Jun  9 14:06:03 shambhala gconfd (aaron-10157): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  9 14:06:03 shambhala gconfd (aaron-10157): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun  9 14:06:03 shambhala gconfd (aaron-10157): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun  9 14:06:04 shambhala gconfd (aaron-10157): Received signal 15, shutting down cleanly
```

I should also say that I have tried to install other Linux distros (Fedora, Redhat, Knoppix) with even less success (freeze ups during and failed installation, failure to even boot off the cd).

Did I just choose a really Linux-unfriendly motherboard or could there be something else going on here?

Any advice will be GREATLY appreciated.

Thanks,
Aaron

---

