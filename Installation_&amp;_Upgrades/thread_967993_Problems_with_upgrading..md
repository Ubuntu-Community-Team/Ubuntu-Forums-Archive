---
title: "Problems with upgrading."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by UmbraAngelus on 2008-11-02
I'm not very experienced but I have tried to read up on things before posting here. Please don't assume that because I've tried something I necessarily know what I'm doing!

I just used the update function of Ubuntu to upgrade from 8.04 to 8.10 and I have two issues. The first (can't log in) I've managed to work around, the second is making my machine unusable as my normal desktop (no sound).

Firstly I couldn't log in normally at all. I'd try to log in and get booted out immediately with a message about my session being under 10 seconds.
Luckily I have another machine in the house with a different OS on it, so I was able to get some advice and by using Ctrl+ALt+F1 I was able to get to a console login, and when I tried to log in there I was spammed with a lot of lines about a problem with /dev/null.
When I did an ls -al /dev/null I saw the permissions on it were set as 600 (crw-------) not 666 (crw-rw-rw-).

I reset the permissions using sudo but it changed back when the machine rebooted.

There are a few bug reports from earlier versions, such as 
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53040](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53040)
[https://launchpad.net/ubuntu/+bug/63031](https://launchpad.net/ubuntu/+bug/63031)
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/69516](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/69516)

and so I followed the advice and from what I can tell udev is set properly:
me@mymachine$ grep null /etc/udev/rules.d/*
/etc/udev/rules.d/40-basic-permissions.rules:KERNEL=="null",			MODE="0666"


There is no udev entry in /etc/rc2.d/
me@mymachine$ ls -al /etc/rc2.d | grep udev
me@mymachine$


me@mymachine$ egrep -sr "chmod.*/dev/null" /etc/rcS.d/*
me@mymachine$ egrep -sr "chmod.*/dev/null" /etc/rc2.d/*
/etc/rc2.d/S20cups:	chmod 3775 /usr/share/ppd/custom 2>/dev/null || true
me@mymachine$ 


And to check my run level is correct:

me@mymachine$ RUNLEVEL=`runlevel | cut -d" " -f2`
me@mymachine$ echo $RUNLEVEL
2
me@mymachine$ egrep -sr "chmod.*null" /etc/rc$RUNLEVEL.d/* /etc/rc.local
/etc/rc2.d/S20cups:	chmod 3775 /usr/share/ppd/custom 2>/dev/null || true
/etc/rc.local:chmod 666 /dev/null
me@mymachine$


I added the last line that appears to rc.local as a workaround (suggested in lots of places) for when there's no udev entry in rc2.d, but this seems inelegant.
Anyone have any ideas?





Secondly my machine no longer produces any sound. In fact I've found it doesn't even appear to have a sound device in /dev/snd :

me@mymachine$ ls -al /dev | grep snd
lrwxrwxrwx   1 root   root        24 2008-10-31 23:29 sndstat -> /proc/asound/oss/sndstat

me@mymachine$ alsamixer 
No mixer elems found

me@mymachine$ aplay -l
aplay: device_list:215: no soundcards found...



My soundcard (on the motherboarsd) worked before - it's an nvidia AC97 chipset which (from serching on the web) should work using ALSA drivers intel8x0 and it appears to be there but with the wrong modules:

me@mymachine$ lspci -v 

[...]

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at ec200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

Whatever I try to do to fix this fails (and I've tried to follow the instructions from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) without a huge amount of success).

Any ideas?

---

