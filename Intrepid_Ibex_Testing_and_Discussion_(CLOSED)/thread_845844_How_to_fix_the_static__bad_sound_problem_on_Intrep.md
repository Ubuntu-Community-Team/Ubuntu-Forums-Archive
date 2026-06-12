---
title: "How to fix the static / bad sound problem on Intrepid"
date: 2008-07-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hobbsee on 2008-07-01
Hey all,

For those of you with static / bad sound, here is the recommended way to fix it:

Cause:  The indices of the cards changed, as the PC speaker gets alsa support, and loads first, before the other sound card.

The Solution:

1.  Run `asoundconf list` or `cat /proc/asound/cards` to look for the card that you want to use.
2.  Run `asoundconf set-default-card card-name-from-section-1`
3.  See if the sound sounds better.

Hope that helps...

---

### Post by philinux on 2008-07-01
Followed the instructions. 

I get a sound at login but once the desktop is loaded no sound at all. Got the prefs as autodetect but pressing test is silence. Maybe this is a different thing which will get fixed with updates.

---

### Post by Gina on 2008-07-01
Setting the  Device defaults to ALSA from **System > Preferences > Sound** fixed it for me.  That avoids PulseAudio which is buggy.  

Of course, if you want to help debug PuseAudio this isn't the way :lolflag:

---

### Post by philinux on 2008-07-01
Yep I tried that and it works, shame about pulse audio, and the clutter in the pull down with multiple pcsp entries.

---

### Post by plun on 2008-07-01
> **Hobbsee said:**
> Hey all,

For those of you with static / bad sound, here is the recommended way to fix it:

Cause:  The indices of the cards changed, as the PC speaker gets alsa support, and loads first, before the other sound card.


Hope that helps...

Well, its a poor solution for nailing bugs...

"psyke83" howto fixed it for me

Please take a look

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

A little more work.  :)

(running a Audigy 2 souncard)

---

### Post by PmDematagoda on 2008-07-01
I fixed the problem by switching the sink to the right one through padevchooser, but unfortunately this is only temporary and it switches back after a reboot.

---

### Post by Seisen on 2008-07-01
None of the fixes worked for me so I will just keep my sound muted till it gets fixed.

---

### Post by psyke83 on 2008-07-01
> **Hobbsee said:**
> Hey all,

For those of you with static / bad sound, here is the recommended way to fix it:

Cause:  The indices of the cards changed, as the PC speaker gets alsa support, and loads first, before the other sound card.

The Solution:

1.  Run `asoundconf list` or `cat /proc/asound/cards` to look for the card that you want to use.
2.  Run `asoundconf set-default-card card-name-from-section-1`
3.  See if the sound sounds better.

Hope that helps...

Unfortunately that won't work, as PulseAudio ignores the default card set in .asoundrc/asound.conf. There have been other solutions posted that fix PulseAudio (to blacklist the kernel module or use padevchooser to make PulseAudio choose the correct card).

---

### Post by psyke83 on 2008-07-01
> **plun said:**
> Well, its a poor solution for nailing bugs...

"psyke83" howto fixed it for me

Please take a look

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

A little more work.  :)

(running a Audigy 2 souncard)

My howto doesn't include the fix for this problem, as it is intended for Hardy users only.

---

### Post by PmDematagoda on 2008-07-01
> **Seisen said:**
> None of the fixes worked for me so I will just keep my sound muted till it gets fixed.

Did you try using padevchooser Seisen? You would have to get the correct sink name from the PA manager and then paste it in when padevchooser asks you to specify the name of the sink you want to change to.

---

### Post by psyke83 on 2008-07-01
> **PmDematagoda said:**
> Did you try using padevchooser Seisen? You would have to get the correct sink name from the PA manager and then paste it in when padevchooser asks you to specify the name of the sink you want to change to.

If you tell users to use this method, then you should also tell them to delete "~/.pulse/volume-restore.table". This file contains the saved volume for every PulseAudio client, but also saves the last used sink per-application. That will cause some applications to continue using the snd_pcsp device, even if it's not the default sink.

---

### Post by plun on 2008-07-01
> **psyke83 said:**
> My howto doesn't include the fix for this problem, as it is intended for Hardy users only.

Well, I cannot see the difference....

Maybe to make a thread within this forum ? 

Only asondconf doesn't solve "bad/stuttering" sound, I  had terrible sound on both 2.6.25 (home brewed) and 2.6.26 

During Hardys development it was nearly nothing about Pulseaudio and I don't know who is Ubuntus dev/maintainer for Pulseaudio....
(too lazy to check)

We can for sure help ourself and perhaps a dev is interested.

All bugs remains as sees it fom your howto.

Benefits using more Pulseaudio GUIs ????  


Or maybe Hobsee can clear this out  ?

---

### Post by psyke83 on 2008-07-01
> **plun said:**
> Well, I cannot see the difference....

These are completely separate issues. My guide deals with sound stuttering due to buffering/CPU usage, etc. This thread is dealing with the new snd_pcsp (PC Speaker) kernel module that's arrived in kernel 2.6.26. This is considered as a PCM device by ALSA (and thus PulseAudio), causing a conflict with the "real" sound card on your system.

Quite simply, there are two options:

1. Blacklist the snd_pcsp kernel module:
```
$ gksudo gedit /etc/modprobe.d/blacklist
```
Paste this to the end of the file:
```
blacklist snd_pcsp
```
 
2. Open PulseAudio Manager, click on Devices tab. Copy the ALSA sink name for your real sound card. Open PulseAudio Device Chooser, click "Default Sink", "Other..." and paste your sound card's sink name there. Finally, delete the file "~/.pulse/volume-restore.table".

The first option is much easier.

---

### Post by IronWolve on 2008-07-03
I'm using ibex in vmware, same issue, thought it was me until this thread. ;)

---

### Post by quique1hn on 2008-07-04
Same problem here, no sound... Let's wait... to see what happen :popcorn:

---

### Post by Gina on 2008-07-04
According to the release notes jittery sound is supposed to be fixed in 8.04.1 maybe it hasn't trickled through to Intrepid yet.

---

### Post by psyke83 on 2008-07-04
> **Gina said:**
> According to the release notes jittery sound is supposed to be fixed in 8.04.1 maybe it hasn't trickled through to Intrepid yet.

The release notes refer to a problem that has been marked fixed since around kernel 2.6.24-18-generic when CONFIG_FAIR_CGROUP_SCHED was enabled. See this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226)

Unfortunately it's not entirely fixed, even in 8.04.1; there is more than one issue causing stutters in PulseAudio. This bug deals with PulseAudio stuttering unrelated to kernel issues: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754)

If you still experience stuttering sound (*not*, I repeat, *not* distorted sound that's caused by the snd_pcsp kernel module being used in PulseAudio), you can find possible fixes in my guide here, Part C: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by MonkeeSage on 2008-07-07
> **psyke83 said:**
> These are completely separate issues. My guide deals with sound stuttering due to buffering/CPU usage, etc. This thread is dealing with the new snd_pcsp (PC Speaker) kernel module that's arrived in kernel 2.6.26. This is considered as a PCM device by ALSA (and thus PulseAudio), causing a conflict with the "real" sound card on your system.

Quite simply, there are two options:

1. Blacklist the snd_pcsp kernel module:
```
$ gksudo gedit /etc/modprobe.d/blacklist
```
Paste this to the end of the file:
```
blacklist snd_pcsp
```
 
2. Open PulseAudio Manager, click on Devices tab. Copy the ALSA sink name for your real sound card. Open PulseAudio Device Chooser, click "Default Sink", "Other..." and paste your sound card's sink name there. Finally, delete the file "~/.pulse/volume-restore.table".

The first option is much easier.


A third option for those who like the pc speaker (or need it for accessibility reasons):

Stop the daemon:

```
pulseaudio -k
```


Make a diversion for it:

```
sudo dpkg-divert --local --rename /usr/bin/pulseaudio
```


Create a wrapper in its place:

```
sudo sh -c 'echo "#!/bin/sh" > /usr/bin/pulseaudio
echo "sudo rmmod snd_pcsp 2>/dev/null" >> /usr/bin/pulseaudio
echo "pulseaudio.distrib \$@" >> /usr/bin/pulseaudio
echo "sudo modprobe snd_pcsp 2>/dev/null" >> /usr/bin/pulseaudio'
```


Make it executable:

```
sudo chmod a+x /usr/bin/pulseaudio
```


Remove stored volume & restart the daemon:

```
rm ~/.pulse/volume-restore.table
pulseaudio --daemonize
```


This only needs to be done once, and will allow the real PCM sink to be first, but also have the pc speaker sink present. It's a kludge, but it works.


This can be undone with the following:

```
pulseaudio -k
sudo rm /usr/bin/pulseaudio
sudo dpkg-divert --remove --local /usr/bin/pulseaudio
pulseaudio --daemonize
```

---

### Post by Rocket2DMn on 2008-07-08
> **Hobbsee said:**
> Hey all,

For those of you with static / bad sound, here is the recommended way to fix it:

Cause:  The indices of the cards changed, as the PC speaker gets alsa support, and loads first, before the other sound card.

The Solution:

1.  Run `asoundconf list` or `cat /proc/asound/cards` to look for the card that you want to use.
2.  Run `asoundconf set-default-card card-name-from-section-1`
3.  See if the sound sounds better.

Hope that helps...

This seems to help, but not completely fix the problem.  Now I can actually tell what is coming out of the laptop speakers, but it is still a little scratchy.

---

### Post by psyke83 on 2008-07-08
> **Rocket2DMn said:**
> This seems to help, but not completely fix the problem.  Now I can actually tell what is coming out of the laptop speakers, but it is still a little scratchy.

See post #13 for the proper solution. Hobsee's information is correct for a system using ALSA directly, but incorrect for PulseAudio as it does not honour the settings in .asoundrc.

---

### Post by phenest on 2008-07-26
> **psyke83 said:**
> These are completely separate issues. My guide deals with sound stuttering due to buffering/CPU usage, etc. This thread is dealing with the new snd_pcsp (PC Speaker) kernel module that's arrived in kernel 2.6.26. This is considered as a PCM device by ALSA (and thus PulseAudio), causing a conflict with the "real" sound card on your system.

Quite simply, there are two options:

1. Blacklist the snd_pcsp kernel module:
```
$ gksudo gedit /etc/modprobe.d/blacklist
```
Paste this to the end of the file:
```
blacklist snd_pcsp
```
 
2. Open PulseAudio Manager, click on Devices tab. Copy the ALSA sink name for your real sound card. Open PulseAudio Device Chooser, click "Default Sink", "Other..." and paste your sound card's sink name there. Finally, delete the file "~/.pulse/volume-restore.table".

The first option is much easier.

I have a Dell Precision M90. The sound was crackly, headphone socket didn't work, and I couldn't change the volume.

Option 1 fixed the lot. Phew! I can't do without music.

---

### Post by ubername on 2008-09-07
> **psyke83 said:**
> These are completely separate issues. My guide deals with sound stuttering due to buffering/CPU usage, etc. This thread is dealing with the new snd_pcsp (PC Speaker) kernel module that's arrived in kernel 2.6.26. This is considered as a PCM device by ALSA (and thus PulseAudio), causing a conflict with the "real" sound card on your system.

Quite simply, there are two options:

1. Blacklist the snd_pcsp kernel module:
```
$ gksudo gedit /etc/modprobe.d/blacklist
```
Paste this to the end of the file:
```
blacklist snd_pcsp
```
 
2. Open PulseAudio Manager, click on Devices tab. Copy the ALSA sink name for your real sound card. Open PulseAudio Device Chooser, click "Default Sink", "Other..." and paste your sound card's sink name there. Finally, delete the file "~/.pulse/volume-restore.table".

The first option is much easier.

Umm... How do I open PulseAudio Manager? and PulseAudio Device Chooser? I'll come back if I can't figure out what a sink name is. This is not meant to be critical of the advice; it just assumes a level of knowledge beyond my own.

---

### Post by psyke83 on 2008-09-07
> **ubername said:**
> Umm... How do I open PulseAudio Manager? and PulseAudio Device Chooser? I'll come back if I can't figure out what a sink name is. This is not meant to be critical of the advice; it just assumes a level of knowledge beyond my own.

This is a pretty old thread you resurrected... This bug has been fixed, so it's *not* recommended to follow those steps anymore.

You need to install the package "padevchooser" to get access to those utilities, by the way.

---

### Post by Nullack on 2008-09-07
Mate any updates on how you see things going with Intrepid builds now? Audio, FF and so forth please.

---

