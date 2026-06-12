---
title: "Pulseaudio 0.9.15 testing preview"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-02-10
Hi!

I've just found an interesting [post by Lennart]("http://0pointer.de/blog/projects/oh-nine-fifteen.html") about the upcoming 0.9.15 release of Pulseaudio, of wich a test version has been released last week.

This is what I was most interested in, but looks like many new features are baking:

> PulseAudio will now automatically probe all possible combinations of configurations how to use your sound card for playback and capturing and then allow on-the-fly switching of the configuration. What does that mean? Basically you may now switch beetween "Analog Stereo", "Digital S/PDIF Stereo", "Analog Surround 5.1" (... and so on) on-the-fly without having to reconfigure PA on the configuration file level or even having to stop your streams. This fixes a couple of issues PA had previously, including proper SPDIF support, and per-device configuration of the channel map of devices.

Looks like Luke Yelavich has packages for the test release in his PPA:

> Hi all

I have made the latest test version of pulseaudio, 0.9.15-test1 available in my PPA, [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa), for jaunty. This is a test version of pulseaudio that has just been released, before the final 0.9.15 release due next week. I would appreciate it if people would test it, and get back to me on any issues you discover, particularly regressions from 0.9.14.

NOTE I do not plan to put 0.9.15 into jaunty, since too much in pulseaudio has changed to be sure of things being stable enough for the jaunty release, but testing newer versions is always useful for Ubuntu, and upstream.

Thanks in advance for any testing you may be able to do.

Luke
([https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027333.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027333.html))

I will jump on board tomorrow! :-)

---

### Post by MadsRH on 2009-02-10
> **tawmas said:**
> ...NOTE I do not plan to put 0.9.15 into jaunty...

When I read Lennart's post I was really hoping this would make it :(

---

### Post by BwackNinja on 2009-02-10
I'll be definitely using this, though I feel kind of selfish using such awesome knowing that it won't make it into jaunty. :P

It not being in jaunty also allows the new volume control to come back in jaunty +1 much more powerful than it is now and supporting the "On-the-fly Reconfiguration of Devices."

---

### Post by Gourgi on 2009-02-10
> **BwackNinja said:**
> "On-the-fly Reconfiguration of Devices."
i hope pacontrol gets this feature really soon :popcorn:

i tried to build PA from source but i forgot to prefix --usr and it didn't work well.
/me going to test the ppa now

---

### Post by autocrosser on 2009-02-10
HMMMM--it wants to remove libpulsecore9---how is it working for you Gourgi??

---

### Post by Gourgi on 2009-02-10
> **autocrosser said:**
> HMMMM--it wants to remove libpulsecore9---how is it working for you Gourgi??

the same here
i didn't installed it yet
maybe we should wait for luke's response to this.

---

### Post by RAOF on 2009-02-10
I *think* it's working as intended here (without libpulsecore9).  It's a little difficult to say - the new 'flat volume' feature behaves strangely, but I think it's by design.

---

### Post by autocrosser on 2009-02-11
Right then--I'll give it a go........Post after.

---

### Post by autocrosser on 2009-02-11
All works--I've yet to play with things, but the basics are working well--so far, so good....:)

---

### Post by plun on 2009-02-11
> **autocrosser said:**
> All works--I've yet to play with things, but the basics are working well--so far, so good....:)


I have been running it since last week and with that version default.pa must be changed.

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html)

> Colin Guthrie already pointed out that module-positional-event-sounds is completely borked. So, while testing make sure not to load it
otherwise volumes of all your streams might start moving in strangest
ways as if controlled by some ghost. [B]It is loaded by default though,
hence you need to manually disable it[/B].


And with also ALSA 1.0.19 running....

The pavucontrol is also a must now when gnomes volume control is out-of-order, "Made in Ubuntu"...

---

### Post by kj74 on 2009-02-11
> **plun said:**
> The pavucontrol is also a must now when gnomes volume control is out-of-order, "Made in Ubuntu"...

Or you could setup pbuilder, do some changes and rebuild gnome-media.

Edit: You might have to rebuild gnome-control-center too.

Edit2: Now gnome-settings-daemon too.

---

### Post by Slug71 on 2009-02-11
If Feature Freeze isnt for nearly another 2 weeks and the Final for this will be released next week then why skip it since it has so many advantages over .14?? Theres almost 2 months left of Jaunty testing and bug fix time. ](*,)

---

### Post by MacUntu on 2009-02-11
> I do not plan to put 0.9.15 into jaunty, since too much in pulseaudio has changed to be sure of things being stable enough for the jaunty release

What stable release? I don't have any problems but I see a lot of ppl complaining about what a mess current PA is.

---

### Post by plun on 2009-02-11
> **Slug71 said:**
> If Feature Freeze isnt for nearly another 2 weeks and the Final for this will be released next week then why skip it since it has so many advantages over .14?? Theres almost 2 months left of Jaunty testing and bug fix time. ](*,)

Yup...test it ! 

Perhaps another Debian problem..:rolleyes:

---

### Post by Slug71 on 2009-02-11
> **plun said:**
> Yup...test it ! 

Perhaps another Debian problem..:rolleyes:

Exactly my thoughts.

Will be filing a launchpad request for this. 

Not including it just doesnt make sense to me. Theres too many people having issues with PA because it wasnt implemented correctly to begin with and if this fixes some of their issues plus adds better functionality and compatibility with plenty of time for bug fixing and teting then thats just a ludacris decision. 
Too hell with Debian if thats who we're waiting on. We can't keep getting held back by them.

I thought bug fixing was one of the primary objectives of Jaunty. Sound has been a big one for Linux for a long time now.

---

### Post by plun on 2009-02-11
> **Slug71 said:**
> Exactly my thoughts.

Will be filing a launchpad request for this. 



OK....  but I cannot see any reason for not also upgrade Alsa to 1.0.19

There is a little time gap now and Debian is NOT a reason for stopping this.

But we are just from "the mob"....:lolflag:

---

### Post by plun on 2009-02-11
> **kj74 said:**
> Or you could setup pbuilder, do some changes and rebuild gnome-media.

Edit: You might have to rebuild gnome-control-center too.

Edit2: Now gnome-settings-daemon too.

OK....

A plain svn download from gnome-media builds just fine. (checkinstall also OK)

build-dep and libunique-dev as deps added

alsamixer -Dhw   for mixer sliders.

---

### Post by tawmas on 2009-02-11
Ok, I'm on board too! Everything looks fine, although I somewhat hoped that it would automagically handle 5.1 output from stereo sources... :-)

> **plun said:**
> A plain svn download from gnome-media builds just fine. (checkinstall also OK)

build-dep and libunique-dev as deps added

Now, I don't think there's a PPA for that too, isn't it?

/me looks away and whistles :-)

---

### Post by Eclipse. on 2009-02-11
> **Slug71 said:**
> Exactly my thoughts.

Will be filing a launchpad request for this. 

Not including it just doesnt make sense to me. Theres too many people having issues with PA because it wasnt implemented correctly to begin with and if this fixes some of their issues plus adds better functionality and compatibility with plenty of time for bug fixing and teting then thats just a ludacris decision. 
Too hell with Debian if thats who we're waiting on. We can't keep getting held back by them.

I thought bug fixing was one of the primary objectives of Jaunty. Sound has been a big one for Linux for a long time now.

Did Luke not make his point clear enough?

Can we please stop scrutanising every decision developers make, beleve it or not they do know whats best Ubuntu.This mind frame where highest version number must be the best has to stop.

For once lets actually listen to what the developers are saying and take it on board.   

Complaining on LP is going to get you nowhere.

---

### Post by plun on 2009-02-11
> **tawmas said:**
> Ok, I'm on board too! Everything looks fine, although I somewhat hoped that it would automagically handle 5.1 output from stereo sources... :-)
Now, I don't think there's a PPA for that too, isn't it?

/me looks away and whistles :-)

No, I have not seen any ppa and its a better idea to use pavucontrol

Install padevchooser and you will have all PA packages.  

Meta package info
[http://packages.ubuntu.com/jaunty/padevchooser](http://packages.ubuntu.com/jaunty/padevchooser)

pavucontrol  info
[http://packages.ubuntu.com/jaunty/pavucontrol](http://packages.ubuntu.com/jaunty/pavucontrol)


Surround settings
[http://ubuntuforums.org/showthread.php?t=1043641](http://ubuntuforums.org/showthread.php?t=1043641)


Maye there is a easier way to do it... ??   Have Fun !

---

### Post by Slug71 on 2009-02-11
> **Eclipse. said:**
> Did Luke not make his point clear enough?

Can we please stop scrutanising every decision developers make, beleve it or not they do know whats best Ubuntu.This mind frame where highest version number must be the best has to stop.

For once lets actually listen to what the developers are saying and take it on board.   

Complaining on LP is going to get you nowhere.

No the highest version number isnt always the best but it is for this version of PA.
Theres still almost 2 months left of the dev cycle for Jaunty and Kernel Freeze isnt for nearly 2 weeks.
:confused:

---

### Post by tawmas on 2009-02-11
> **plun said:**
> No, I have not seen any ppa and its a better idea to use pavucontrol

Install padevchooser and you will have all PA packages.

Ok, thanks, I already have those installed. I caressed the idea I might move to the very edge of the bleeding edge, but I don't like to compile my own software on this box because I'm running Jaunty on my primary box (please don't lecture me about that, I do my backups, I don't mind some breakage, and I think that real use is the best test we can do). :-) 

> **plun said:**
> Surround settings
[http://ubuntuforums.org/showthread.php?t=1043641](http://ubuntuforums.org/showthread.php?t=1043641)

Maye there is a easier way to do it... ??   Have Fun !

Yup! I had done that, but I was fool enough to only use my earphones afterwards! :-( I had the update overwrite my config file, so I lost that setting. I'll redo that and see how it works for me...

---

### Post by plun on 2009-02-12
9.0.15 - Test2   is announced by LennartP

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003122.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003122.html)

Testing....

---

### Post by Slug71 on 2009-02-12
Here is the link to the Launchpad request for PA 0.9.15 and Alsa v1.0.19.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/328823](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/328823)

Please go and add to it guys. :)

---

### Post by crjackson on 2009-02-12
> **Slug71 said:**
> Here is the link to the Launchpad request for PA 0.9.15 and Alsa v1.0.19.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/328823](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/328823)

Please go and add to it guys. :)

Done

---

### Post by Slug71 on 2009-02-12
> **crjackson said:**
> Done

Thanks. :D

---

### Post by MacUntu on 2009-02-12
Status: Won't Fix

Wow that was fast. :D

---

### Post by Slug71 on 2009-02-12
> **MacUntu said:**
> Status: Won't Fix

Wow that was fast. :D

That was fast. :lolflag:

---

### Post by jocko on 2009-02-15
I don't know if this is already known and I just missed it, but I just managed to figure out how to switch between outputs (not by configuring them in default.pa).
I've got a laptop with a intel hda sound card (using the alsa module snd-hda-intel), and pulseaudio only shows one available sink (analog stereo).

Run this in a terminal:
```
pacmd
```That gives you a shell with access to the pulseaudio daemon.
```
list-cards
```Will give you a list of available sound cards, including a number of different profiles (combinations of analog or digital output and input sources).
I get this:
```
>>> list-cards
1 card(s) available.
    [COLOR=Blue]index: 0[/COLOR]
    name: <alsa_card.pci_8086_27d8_sound_card_0>
    driver: <module-alsa-card.c>
    owner module: 5
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xd2300000 irq 22"
        alsa.driver_name = "snd_hda_intel"
        hal.udi = "/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0"
        hal.product = "HDA Intel Sound Card"
        hal.card_id = "HDA Intel"
        device.string = "0"
    [COLOR=Blue]profiles:
        output-analog-stereo+input-analog-stereo: Output Analog Stereo + Input Analog Stereo (priority 1010)
        output-analog-stereo: Output Analog Stereo (priority 1000)
        output-iec958-stereo+input-analog-stereo: Output IEC958 Digital Stereo + Input Analog Stereo (priority 510)
        output-iec958-stereo: Output IEC958 Digital Stereo (priority 500)
        input-analog-stereo: Input Analog Stereo (priority 10)
        off: Off (priority 0)
    active profile: <output-analog-stereo+input-analog-stereo>[/COLOR]
    sinks:
        alsa_output.pci_8086_27d8_sound_card_0/#0: HDA Intel - ALC861 Analog
    sources:
        alsa_output.pci_8086_27d8_sound_card_0.monitor/#0: Monitor of HDA Intel - ALC861 Analog
        alsa_input.pci_8086_27d8_sound_card_0/#1: HDA Intel - ALC861 Analog
```So, if I want to output digital stereo through spdif instead of analog stereo, I type this command:```
set-card-profile [COLOR=Blue]0 output-iec958-stereo[/COLOR]
```Where [COLOR=Blue]0[/COLOR] is the index of my sound card from the output above and [COLOR=Blue]output-iec958-stereo[/COLOR] is the profile I want to activate.
Note that if you exit pacmd, the pulseaudio daemon will exit as well.

If you already know the name of the profile, this command will do it without having to run a pacmd shell:
```
pactl set-card-profile [COLOR=Blue]0 output-iec958-stereo[/COLOR]
```Hopefully there will be a gui for this soon...

---

### Post by BwackNinja on 2009-02-15
Nice jocko, I found out how to do this too and I was so happy when I found out how this worked. Its the first step and most important step to making changing to surround sound or even other configurations easier with pulseaudio.

Go Lennart. :D

---

### Post by jfernyhough on 2009-02-15
OK, I'm jumping in now. Jaunty is too stable, even with a dozen PPAs for dev versions enabled! :D

--edit

Heh. Working better than before; this (or 29-rc5) has fixed my laptop volume control keys. :D

---

### Post by tawmas on 2009-02-15
I seem to have a regression here. For the first time, I observed the bug where you have to kill and restart pulseaudio before you have sound. There were a thread or two about that with 0.9.14, but to me it had never happened with 0.9.14...

I will investigate further.

---

### Post by markbuntu on 2009-02-17
Anbody know where to find a pulseaudio-module-jack amd64.deb for 0.9.15 or 0.9.14. The one in Debian experimental for 0.9.14.1 needs pulsecore8 and we at at pulsecore9.

---

### Post by ugkbunb on 2009-02-20
I am experiencing a regression -- I have been unable to open pavucontrol with PulseAudio 0.9.15... it flashes open then segfaults immediately.

Also -- with VLC set to PulseAudio audio output... sound is incredibly scratchy... this ceases if A) I switch media players or B) I set VLC to ALSA audio output.

EDIT: Fixed my issue by doing the following

/etc/pulse/daemon.conf 
resample-method = src-sinc-best-quality 
system-instance = yes 
high-priority = yes 
nice-level = -11

/etc/default/pulseaudio 
PULSEAUDIO_SYSTEM_START=1

I realize this is not the "recommended" way of running it (however my box is a single usr machine) but it fixes all my problems A) scratchy sound B) not correctly starting on boot and C) for some reason it fixed my access to pavucontrol.

pavucontrol segfaults when launched under a user as "pulseaudio &" ... however when run as a deamon systemwide it works fine.

---

### Post by hugmenot on 2009-02-25
Hm, with the preview package "test3" from Luke&#8217;s PPA I get this error now:

```
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found

```

But it&#8217;s there:
```
ll /usr/lib/pulse-0.9.15/modules/module-alsa-card.so
-rw-r--r-- 1 root root 13748 2009-02-25 06:40 /usr/lib/pulse-0.9.15/modules/module-alsa-card.so
```

Anyone else have this?

---

### Post by marijus on 2009-02-25
> **hugmenot said:**
> Hm, with the preview package "test3" from Luke’s PPA I get this error now:

```
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found
E: module.c: Failed to open module "module-alsa-card": file not found

```

But it’s there:
```
ll /usr/lib/pulse-0.9.15/modules/module-alsa-card.so
-rw-r--r-- 1 root root 13748 2009-02-25 06:40 /usr/lib/pulse-0.9.15/modules/module-alsa-card.so
```

Anyone else have this?

Yes, same problem here...

---

### Post by jocko on 2009-02-25
> **marijus said:**
> Yes, same problem here...
I also get that error message from "pulseaudio -C", and if I try to load it through pacmd:
```
>>> load-module module-alsa-card
Module load failed.

```Same if I try to load module-alsa-sink.

---

### Post by Starks on 2009-02-25
How do I disable glitch-free mode?

---

### Post by plun on 2009-02-25
> **Starks said:**
> How do I disable glitch-free mode?

Well, the glitch-free mode is mostly disabled on its own...):P

Just read PAs mailing list and they have a discussion about the same.
LennartP went out hard...:lolflag:
 
------------------------

I am not using Lukes PPA but installed Test3 from source and its stone dead broken with Jaunty... went back to Test2

---

### Post by ugkbunb on 2009-02-25
I am having the same issue loading the alsa sink module... i will file a bug on the PA bug tracker when I get off class if one isn't filed already. Sigh... no more sound and I had just gotten it work flawlessly + I had just purged my apt-cache... so looks like I can't downgrade.

---

### Post by jocko on 2009-02-26
There are new pulseaudio packages in the ppa now, and everything works again.

---

### Post by Vaun on 2009-03-08
I've had much more success with the 0.9.15 PPA then the 0.9.14 PPA in testing for Jaunty.  0.9.15 

I no longer get a distorted log in sound, CPU race on event sounds, loss of event sounds, etc.  Seems to be working well.

---

### Post by volanin on 2009-03-08
> **plun said:**
> Well, the glitch-free mode is mostly disabled on its own...):P
Just read PAs mailing list and they have a discussion about the same.
LennartP went out hard...:lolflag:

For those who have not read the reasons for the glich-free problems.
It seems the Ubuntu kernel falls in the high-latency category.
From Lennart:


[i]
Heya!

As one result of the alsa-time-test testing (see that last mail of
mine regarding broken sound drivers) input I got from folks, I learned
how very different the different distribution kernels actually
behave. They are much more different than i actually assumed.

Apparently OpenSUSE ships a kernel (2.6.27.7-9-pae) that causes
scheduling latencies of > 210ms. That is a lot. That is really really
really a lot. Other non-Fedora distributions apparently do something similar.

The parameters in the glitch-free logic are tuned for Fedora-kernels
that easily give latencies of 5ms or so.

ALSA artificially limits the overall buffer size to 64k (i.e. 371ms on
44100hz/2ch/s16le). That this size is not that much when speaking of
scheduling latencies of 210ms should be obvious.

Now, the glitch-free mode in PA is a major departure from the
traditional playback mode. In traditional playback mode the sound card
buffer is filled as soon as at least one 'fragment' of it ran
empty. Usually 4 fragments or so are used, i.e. the fill level will
oscillate between 'full' and 'full minus one fragment size minus the
scheduling latency'. If we have a buffer of 371ms we have a fragment
size of 91ms. With a kernel like that OpenSUSE kernel hence the fill
level oscillates between 371ms and 70ms. Which of course is usually
good enough to not get a drop out. Should a drop out happen nonethless
we continue as if nothing happened given that fragment settings cannot
be reconfigured during runtime.

Now, let's have a look what this means for glitch-free mode. In g-f
mode we disable sound card interrupts (and get rid of 'fragments'
entirely) as far as possible to minimize power consumption. We
schedule audio via system timers instead of the sound card's fragment
logic. Instead of already filling up after a single fragment was
played we delay the fill up until only 10 ms are still left in the
buffer (in PA 0.9.14 that is, i increased the default to 20ms now on
.15). i.e. with a Fedora scheduling latency of 5ms the buffer fill
level will hence oscillate between 371ms and 5ms. Still good enough to
not get into drop outs. If a drop out happens nonethelless we will
double the 10 ms to 20ms and go on. If that still turns out to not be
enough we double again, and so on. If this logic with these parameters
is run on an OpenSuse kernel, drop-outs will necessarily happen right
away. Because 10ms minus the sched latency of 210ms equals
FAILURE. And doubling the wakeup time again and again will require
quite a number of iterations, i.e. more than just a few underruns at
the beginning. Also the doubling will quickly come near to the full
buffer size of 371ms causing a lot of CPU to be eaten, since we will
wake up very very often.

So, what do we read from this?

0) Fedora is awesome, other distributions suck ;-)

1) For ***** sakes: get your bloody kernels fixed. Enable preempt, set
   HZ to 1000. Get rid of low-quality drivers that block the
   CPU. Latencies of 210ms is *REALLY NOT NECESSARY*.

2) If you want to stick with your crap kernel, then either disable g-f
   entirely or adjust the #defines at the top of
   src/modules/alsa-sink.c and src/modules/alsa-source.c.

Thank you very much,

Lennart[/i]

---

### Post by crimsun on 2009-03-09
> **volanin said:**
> For those who have not read the reasons for the glich-free problems.
It seems the Ubuntu kernel falls in the high-latency category.

We'll be working hard to ensure that Karmic has a much better PulseAudio performance WRT kernel configuration settings. To the extent possible, I've worked around Jaunty's kernel configuration for both glitch-free and non-glitch-free in a pending 0.9.14 upload (should land before Alpha 6).

---

### Post by plun on 2009-03-09
Latest update broke Wine and alsa for me

```
plun@plun:~$ winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": /usr/bin/../lib32/wine/winealsa.drv.so: symbol snd_pcm_forward, version ALSA_0.9.0rc8 not defined in file libasound.so.2 with link time reference

```

:confused:

---

### Post by psychok9 on 2009-03-09
I can't upgrade (I've Jaunty x64) with [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa).
Update manager miss pulseaudio 0.9.15... ?

---

### Post by asimon on 2009-03-10
> **crimsun said:**
> I've worked around Jaunty's kernel configuration for both glitch-free and non-glitch-free in a pending 0.9.14 upload (should land before Alpha 6).
Lennart has a real point here. It's hardly acceptable that Ubuntu's kernel has latencies 40 times worse then Fedora. The real fix should come from the kernel team, do they know about their latencies?

---

### Post by crimsun on 2009-03-10
> **asimon said:**
> Lennart has a real point here. It's hardly acceptable that Ubuntu's kernel has latencies 40 times worse then Fedora. The real fix should come from the kernel team, do they know about their latencies?

Yes, we and the kernel team have been aware for quite some time. PREEMPT will not be enabled due to the schedule - it is too late to iron out regressions for such a change. I (or someone else clueful) will be pushing the necessary changes for Karmic's kernel configuration at UDS.

The good news is that we've figured out the hwptr sync issue in Alsa-kernel that was breaking glitch-free PA. A fix has already been queued for 2.6.30. Depending how invasive the change is (I have to evaluate it later today), it may land in 9.04.

---

### Post by asimon on 2009-03-10
> **crimsun said:**
> [...]I (or someone else clueful) will be pushing the necessary changes for Karmic's kernel configuration at UDS. [...]
A fix has already been queued for 2.6.30. Depending how invasive the change is (I have to evaluate it later today), it may land in 9.04.

Great to hear, thanks for your effort.

---

### Post by volanin on 2009-03-10
> **crimsun said:**
> Yes, we and the kernel team have been aware for quite some time. PREEMPT will not be enabled due to the schedule - it is too late to iron out regressions for such a change. I (or someone else clueful) will be pushing the necessary changes for Karmic's kernel configuration at UDS.

The good news is that we've figured out the hwptr sync issue in Alsa-kernel that was breaking glitch-free PA. A fix has already been queued for 2.6.30. Depending how invasive the change is (I have to evaluate it later today), it may land in 9.04.

Indeed awesome news!
Thanks crimsun.
:D

---

### Post by psychok9 on 2009-03-10
I don't know how work a kernel, but with tsched=0 on default.pa, the stuttering seem to be solved... but I don't know if can cause negative effects.

On PPA repository I found all packages, but without the main pulseaudio 0.9.15: it's normal?
Thank you and sorry for my bad english :p

---

### Post by crimsun on 2009-03-10
> **psychok9 said:**
> I don't know how work a kernel, but with tsched=0 on default.pa, the stuttering seem to be solved... 

Disabling glitch-free can cause "higher cpu usage". I've attempted to balance that in ubuntu11 by choosing a lesser quality but less resource-intensive resampler.

We will ship Jaunty with glitch-free disabled due to -generic's kernel configuration.

---

### Post by lithorus on 2009-03-11
> **psychok9 said:**
> I don't know how work a kernel, but with tsched=0 on default.pa, the stuttering seem to be solved... but I don't know if can cause negative effects.

On PPA repository I found all packages, but without the main pulseaudio 0.9.15: it's normal?
Thank you and sorry for my bad english :p

It is indeed there :
[https://launchpad.net/%7Ethemuso/+archive/ppa/+files/pulseaudio_0.9.15~test5-0ubuntu1~ppa2_amd64.deb](https://launchpad.net/%7Ethemuso/+archive/ppa/+files/pulseaudio_0.9.15~test5-0ubuntu1~ppa2_amd64.deb)
or
[https://launchpad.net/%7Ethemuso/+archive/ppa/+files/pulseaudio_0.9.15~test5-0ubuntu1~ppa2_i386.deb](https://launchpad.net/%7Ethemuso/+archive/ppa/+files/pulseaudio_0.9.15~test5-0ubuntu1~ppa2_i386.deb)

Which package manager are you using for updating?

---

### Post by sunbear on 2009-04-07
> **volanin said:**
> For those who have not read the reasons for the glich-free problems.
It seems the Ubuntu kernel falls in the high-latency category.
From Lennart:

1) For ***** sakes: get your bloody kernels fixed. Enable preempt, set
   HZ to 1000. Get rid of low-quality drivers that block the
   CPU. Latencies of 210ms is *REALLY NOT NECESSARY*.

[/i]

Can anyone explain why setting HZ to 1000 requires you to build a custom kernel rather than this just being a boot-time configuration option?

Also, why isn't 1000 Hz the default for all desktop builds of Linux given that anything lower seems to wreck the performance of not only sound, but also video, and running of virtual machine (e.g. VMWare guests).

It seems totally unreasonable to expect Ubuntu to have a serious hope of unseating Windows if multimedia doesn't work smoothly out of the box. At the moment, getting a decent user experience requires a custom kernel which is way beyond what most users will be willing to tolerate.
 
Mark

---

### Post by markbuntu on 2009-04-07
> **sunbear said:**
> Can anyone explain why setting HZ to 1000 requires you to build a custom kernel rather than this just being a boot-time configuration option?

Also, why isn't 1000 Hz the default for all desktop builds of Linux given that anything lower seems to wreck the performance of not only sound, but also video, and running of virtual machine (e.g. VMWare guests).

It seems totally unreasonable to expect Ubuntu to have a serious hope of unseating Windows if multimedia doesn't work smoothly out of the box. At the moment, getting a decent user experience requires a custom kernel which is way beyond what most users will be willing to tolerate.
 
Mark

From what I can find it seems that PREMPT and HZ=1000 are not set because supposedly the nvidia drivers do not like PREMPT and HZ=1000 and will crash. This causes the 64k alsa buffer to run out before pulse can gain cpu access so the audio glitches out. tsched=0 is just a klunky workaround.

There may be other reasons besides nvidia but I have not come across any.

It is a bad joke, crippling the kernel to accommodate a proprietary blob.

---

### Post by Yashiro on 2009-04-07
While it may be true that there are kernel compilation issues it does not excuse Pulseaudio failing in situations where Alsa, and even OSS, do not.

I'm sure there will be much fun when Debian comes to package Gnome 2.26 and it's related pulse audio dependencies.

---

### Post by RAOF on 2009-04-07
> **sunbear said:**
> ...
Also, why isn't 1000 Hz the default for all desktop builds of Linux given that anything lower seems to wreck the performance of not only sound, but also video, and running of virtual machine (e.g. VMWare guests).
...

Because HZ=1000 won't actually do anything; we're using the tickless kernel config anyway.

---

### Post by markbuntu on 2009-04-07
Alsa and oss and the kernel configuration were fine for the days of one sound hardware device playing to one set of stereo speakers but those days are over.

ALSA and oss cannot do what pulseaudio can and jackd has had similar issues with the kernel for a long time. 

This used to be pretty much confined to jackd and so the kernel devs could just ignore this issue and let the people who need rt access use the rt patches but this is no longer the case. These days it is very common for people to have a multiple of sound using devices attached to their machines, this means faster access to the cpu is necessary to keep everything sounding right. alsa and oss are just not up to the task, and neither is the kernel anymore.

Debian is far ahead of ubuntu and much more careful about integration so I wouldn't worry so much about that. Pulse0.9.15 is already in experimental.

---

### Post by plun on 2009-04-10
Test 8 is out in town.....

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003481.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003481.html)


Just nice...:guitar:

---

### Post by plun on 2009-04-14
ver 9.0.15 released...

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003506.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003506.html)


> Heya!

Now that my todo list of bugs to fix for PulseAudio 0.9.15 is empty I
siezed the opportunity to actually do the release. That's not to say
it doesn't have bugs. But at least none I am aware of that are
relevant.

[http://0pointer.de/lennart/projects/pulseaudio/pulseaudio-0.9.15.tar.gz](http://0pointer.de/lennart/projects/pulseaudio/pulseaudio-0.9.15.tar.gz) 

Rejoice!

An updated package is already in Rawhide.



and a new pavucontrol

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003507.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003507.html)

Lets go Karmic.....):P

---

### Post by tawmas on 2009-04-14
Do you think we're going to get this through Luke's PPA?

---

### Post by Eversmann on 2009-04-14
Would be great if we could have this bug-free release for jaunty. Hope to see it on the ppa soon ;-)

---

### Post by plun on 2009-04-14
> **tawmas said:**
> Do you think we're going to get this through Luke's PPA?

Sooner or later....

The version number was also blown because of a human mistake earlier. For Ubuntu it will be 1.9.0.15.

---

### Post by kurros on 2009-04-14
> **plun said:**
> Sooner or later....

The version number was also blown because of a human mistake earlier. For Ubuntu it will be 1.9.0.15.

I think you are referring to the epoch: 1:0.9.0.15

---

### Post by Sarvatt on 2009-04-14
hz=1000 does horrible things on my laptops that resort to polling mode because of the crappy EC support. It uses 20% more power just idling vs hz=100 and way more when using the touchpad. hz=100+nohz+preempt_voluntary has the best battery life for me.

---

### Post by jblackhall on 2009-04-15
Has anyone tried using the new version in Luke's PPA?  Does upgrading from Jaunty's PA add any weird bugs or anything?  Do all the features in this new version work with no/minimal configuration?  I really want to try it (for BT audio support), but I don't want to totally screw up my system.

---

### Post by paradigm2 on 2009-04-16
I would be EXTREMELY interested as to whether this new version of pulseaudi (which has now been officially released) will make it into 9.04 in the near future.

Where I can I find the policies for inclusion?

Also failing that it is included within the next few weeks can I install this myself and have it NOT break things?

Sound is the only thing not working correctly on my production system.  The specific problem is the volume level is too low.

Thank you.

---

### Post by RAOF on 2009-04-16
> **paradigm2 said:**
> I would be EXTREMELY interested as to whether this new version of pulseaudi (which has now been officially released) will make it into 9.04 in the near future.

No.  Not a chance.  We've entered [Final Freeze](https://wiki.ubuntu.com/JauntyReleaseSchedule), and the RC should be spun about now.  It's not going to be in the release.

> **paradigm2 said:**
> 
Where I can I find the policies for inclusion?

Although it won't be in the release, there's a chance that it could be [backported](https://help.ubuntu.com/community/UbuntuBackports) once it hits Karmic.

---

### Post by paradigm2 on 2009-04-16
> **RAOF said:**
> No.  Not a chance.  We've entered [Final Freeze](https://wiki.ubuntu.com/JauntyReleaseSchedule), and the RC should be spun about now.  It's not going to be in the release.


Although it won't be in the release, there's a chance that it could be [backported](https://help.ubuntu.com/community/UbuntuBackports) once it hits Karmic.

Thank you.  Nice information, although not exactly what I wanted to hear.  i will probably manually install the new ALSA and Pulseaudio then.  I'm hesitant to do that though due to worries about conflicts.  Does anyone have any tips on minimising this and/or doing the install of the new versions?

---

### Post by plun on 2009-04-16
> **paradigm2 said:**
>  Does anyone have any tips on minimising this and/or doing the install of the new versions?

Release notes must include this as a "known issuse" otherwise its "Singing in the rain"....

Please also read the sticky thread about Pulse and a test kernel.

---

### Post by tawmas on 2009-04-16
> **plun said:**
> Sooner or later....

I hope sooner. I had just found a nasty bug (if I turn off the PC with earphones plugged in and unplug them before starting it again, I have no sound until I kill and restart the daemon; I think the reverse is also true). I want to make sure I can reproduce it with the released version before reporting it.

---

### Post by RAOF on 2009-04-16
> **plun said:**
> Release notes must include this as a "known issuse" otherwise its "Singing in the rain"...

What is "this"?  A link to an unresolved bug report would be useful.  I reinstalled a couple of days ago, and the audio stack hasn't presented me with any problems at all.  All the glitches I experienced earlier in the cycle are gone.

---

### Post by plun on 2009-04-16
> **RAOF said:**
> What is "this"?  A link to an unresolved bug report would be useful.  I reinstalled a couple of days ago, and the audio stack hasn't presented me with any problems at all.  All the glitches I experienced earlier in the cycle are gone.

Well... you can find tons of PA Bugs ;)

as I understands it the HDA INTEL bugs are resolved within crimums kernel.

[http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen)


[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=fa00e046b41663cbda9b1affc0594669e5f14219)
[http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc](http://git.alsa-project.org/?p=alsa-kernel.git;a=commitdiff;h=bbf6ad1399e9516b0a95de3ad58ffbaed670e4cc)

Crimsum about it:

> They're available (along with several other ALSA core fixes) at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/) . These fixes bump the ABI and may need to be delayed until after Jaunty releases. Please comment on your experiences here in this thread and in bug 345627.


"Known issue" or "singing in the rain"  .....???

---

### Post by jblackhall on 2009-04-16
[Quote from Phoronix]("http://phoronix.com/forums/showpost.php?p=70605&postcount=24") about Luke's PPA:
> Just a warning to anyone who might try it.
This repo breaks 32bit compatibility on 64-bit systems, so things like Skype (and certain non-64-bit-precompiled games) won't work.
Also it's a pain in the *** to rollback. You need to download the changed packages from packages.ubuntu.com and manually 'downgrade' them using dpkg --force-all
Good times. 

Is this true that it breaks 64-bit compatibility?  If so, is there a PPA available with a version that works with 64-bit correctly?  I need Skype to work.

---

### Post by mirko_3 on 2009-04-18
Nope, it works here!

---

### Post by Sarvatt on 2009-04-18
> **jblackhall said:**
> [Quote from Phoronix]("http://phoronix.com/forums/showpost.php?p=70605&postcount=24") about Luke's PPA:


Is this true that it breaks 64-bit compatibility?  If so, is there a PPA available with a version that works with 64-bit correctly?  I need Skype to work.

It shouldn't break x86-64 compatability, raw debian repackaging will though because it uses /emul for 32 bit libs instead but the ones on his PPA look right to me. I've got some on my PPA too that work fine on my amd64 machine.

[https://launchpad.net/~sarvatt/+archive/ppa](https://launchpad.net/~sarvatt/+archive/ppa)

---

### Post by priegog on 2009-04-19
Hi, I just installed Luke's PPA (in Intrepid, if that's good for something... Jaunty's kernel doesn't support my computer's ACPI events... long story, but it's the reason I'm still in Intrepid on this machine), apt-get updated, and the 0.9.15 version is NOWHERE to be found. The funny thing is it appears on the launchpad page as being put there 2 days ago. 
Anyone know what gives?

---

### Post by jblackhall on 2009-04-20
> **Sarvatt said:**
> It shouldn't break x86-64 compatability, raw debian repackaging will though because it uses /emul for 32 bit libs instead but the ones on his PPA look right to me. I've got some on my PPA too that work fine on my amd64 machine.

[https://launchpad.net/~sarvatt/+archive/ppa](https://launchpad.net/~sarvatt/+archive/ppa)

It does cause problems.  Whether it's a pulse problem or a skype problem I'm not sure, but Skype doesn't work with the 64-bit package. Arg...

jonathan@jonathan-ubuntu:~$ skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference
jonathan@jonathan-ubuntu:~$

---

