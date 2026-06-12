---
title: "installation problems w/ inspiron 1520"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2007-11-21
I'm having problems helping someone install Gutsy on an Inspiron 1520 -- any help would
be greatly appreciated!

It's to be dual boot, and everything works with the other OS, so no hardware issues....

Shrank the other OS's partition, installed off the standard desktop CD.  Went fine.  Boots
ok, runs fine... but:
1) No sound whatsoever.  It shows lots of *snd* modules, but the volume control
complains about no device or something.  Haven't looked into this too much, thought I
would follow some of the advice on various forum threads, *except*:
2) Wireless not working at all.  It knows it has a wireless card (which is a broadcom
BCM93411MCG or something like that), the interface comes up in the network manager
applet, but no networks are detected and no progress.  I thought I would fiddle with
this a bit, perhaps with help from various forum threads and downloading new stuff
with synaptic... only:
3) Weirdness even when connected with the ethernet cable!  Plugged in, it says
it's on the network, and ping always works to every site I can think of, but inside
Firefox, often it downloads a bit and then sits there at "Transferring data from
www.ubuntuforums.org..." or "Connecting to www.google-analytics.com..." or
something, *forever*.  I ping those sites in a terminal window, and everything works.
But in Firefox, no joy!

Any ideas/ suggestions/pointers would be greatly appreciated!

---

### Post by Pumalite on 2007-11-21
Post your complete specs, including memory, graphics, drives, etc.

---

### Post by bodhidharma on 2007-11-21
Pumalite suggests I post complete specs of the offending machine.  Here they are:

Information from the Hardware Manager of the commercial OS:
Brand spanking new Dell Inspiron 1520.
CPU: dual Pentium
HD: Fujitsu MHY2120BG
Video: "Mobile Intel(R) 965 Express Chipset Family
DVD/CD drive: TSSTcorp DVD+-RW TS-L632H
Network adapters:  1394 Net Adapter
                                Broadcom 440x 10/100 Integrated Controller
                                Dell Wireless 1390 WLAN Mini-Card
Various audio CODECs reported (?)


running lspci under linux, I see:
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio controller (rev 02)

...
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev02)
...
0c:00.0 Network controller:  Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I hope that helps!

---

### Post by Pumalite on 2007-11-21
[http://ubuntuforums.org/showthread.php?t=601729](http://ubuntuforums.org/showthread.php?t=601729)
You can try the Alternate CD, but the story is not pretty.

---

### Post by bodhidharma on 2007-11-21
Um, Pumalite, I'm a little confused ... it seems like that thread was a very messed-up
person who made very little progress with several attempts.  My situation is that I
have Gutsy running, there are a couple of little issues with (a) sound (but there are
guides of a series of steps to try to fix this) and (b) network, particularly wireless
and some possible flakiness with wired (but again there are guides, and the wired
flakiness is probably associated with some weird Firefox problem, other network
access seems fine).  So I really was asking the collective genius of these forum
readers if they knew the shortcut to the correct final answer, mostly to save myself
the time of trying all the various steps, one by one, on the various threads that
suggest approaches to my problems.  I don't think I will give up, the way the thread
you linked to seems to suggest, and the way your final comment seems to imply I
should.

I'll post a shortcut guide to the single thing which fixes the sound and the network
issues, as soon as I find it... which I remain fairly confident I will.

---

### Post by linux23dragon on 2007-11-22
> **bodhidharma said:**
> Um, Pumalite, I'm a little confused ... it seems like that thread was a very messed-up
person who made very little progress with several attempts.  My situation is that I
have Gutsy running, there are a couple of little issues with (a) sound (but there are
guides of a series of steps to try to fix this) and (b) network, particularly wireless
and some possible flakiness with wired (but again there are guides, and the wired
flakiness is probably associated with some weird Firefox problem, other network
access seems fine).  So I really was asking the collective genius of these forum
readers if they knew the shortcut to the correct final answer, mostly to save myself
the time of trying all the various steps, one by one, on the various threads that
suggest approaches to my problems.  I don't think I will give up, the way the thread
you linked to seems to suggest, and the way your final comment seems to imply I
should.

I'll post a shortcut guide to the single thing which fixes the sound and the network
issues, as soon as I find it... which I remain fairly confident I will.


OK you need to install the 32bit version of Ubuntu-07.10 (if you haven't already).

Then to get the sound working you need to install linux-backports-modules-generic : -
```

sudo apt-get install linux-backports-modules-generic
```
Then reboot.

Now you might as well read this [***[COLOR="Blue"]_thread_[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=501195&highlight=dell+1520") for some of your hardware setup. (It is for Ubuntu-7.04 but some of the solutions are still relevant to Gusty).  You wont need to worry about the web cam.

And then read this [***_[COLOR="Blue"]thead[/COLOR]_***](" http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+1520") for more Gutsy information

---

