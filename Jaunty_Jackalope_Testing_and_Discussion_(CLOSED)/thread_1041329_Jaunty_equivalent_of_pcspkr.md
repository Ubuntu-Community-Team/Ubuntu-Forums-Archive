---
title: "Jaunty equivalent of pcspkr"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-01-16
Hi

I am trying to disable any and all 'system beeps'

I have this working on intrepid by adding 'blacklist pcspkr' to etc/modprobe.d/blacklist

But it doesn't work in jaunty, so when I try (as a more drastic solution)

sudo rmmod pcspkr

I get

ERROR: Module pcspkr does not exist in /proc/modules

My uneducated guess is that this is because jaunty sound does not use pcspkr, but I would welcome any guidance as to how to disable the terrible beep I get whenever I do something like type a search in Firefox which is not found, log-off, hit an invalid key etc.

TIA

---

### Post by syko21 on 2009-01-17
It hasn't been replaced, I have it on my machine.

---

### Post by vishalrao on 2009-01-18
"lsmod | grep pc" shows pcspkr for me on my desktop and tablet.
blacklisting pcspkr works on tablet but not on desktop! my desktop still makes ugly buzzes for the system bell...

---

### Post by ubername on 2009-01-18
> **vishalrao said:**
> "lsmod | grep pc" shows pcspkr for me on my desktop and tablet.
blacklisting pcspkr works on tablet but not on desktop! my desktop still makes ugly buzzes for the system bell...

My output from lsmod | grep pc:

parport_pc             45096  0 
parport                49712  3 ppdev,parport_pc,lp
snd_pcm                98952  3 snd_usb_audio,snd_hda_intel
snd_timer              34064  2 snd_pcm,snd_seq
snd                    78792  17 snd_usb_audio,snd_hda_intel,snd_rawmidi,snd_pcm,snd_hwdep,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm


So no pcspkr.

Any more clues anyone? The raucous 'Beep' (which comes from the speakers, not the pc speaker) is really irritating.

---

### Post by cariboo on 2009-01-18
On my system, I have snd_pcsp blacklisted in a default installation.

Jim

---

### Post by ubername on 2009-01-18
Thanks to this :

[http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

I can switch the beep off after each login, but I can't make it persistent.

I type

xset b off
xset b 0 0 0

in a terminal and the beep goes. However I have tried some of the suggestions for making it always (after each boot / login) work and not yet found a solution. I'll keep trying!

---

### Post by ubername on 2009-01-18
> **cariboo907 said:**
> On my system, I have snd_pcsp blacklisted in a default installation.

Jim
I also have that on my blacklist, but it doesn't stop the beeping beep!

---

### Post by marmuta on 2009-01-18
Have you tried putting "xset b off; xset b 0 0 0" in System->Preferences->Sessions?

---

### Post by no1wantdthisname on 2009-01-19
The beeping was driving me insane.

Here's how I disabled it.
Right click volume applet->Preferences.
Scroll down and select PC Beep and mute from the applet.

---

### Post by ubername on 2009-01-19
> **marmuta said:**
> Have you tried putting "xset b off; xset b 0 0 0" in System->Preferences->Sessions?

Hi

I have sort of tried this and apologies: I realise I have been posting in two threads about the same issue

See [http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

I will try your (slightly different) suggestion in a minute when I can get on my Jaunty box, and thanks for replying. I currently have 
xset b off && xset b 0 0 0
in Sessions.

---

### Post by luca_linux on 2009-01-19
I may sound a little bit drastic, but actually I do think the developer team should disable this annoying beep by default. It makes no sense on any modern desktop machine.

---

### Post by marmuta on 2009-01-19
Well that probably won't work much better then.
Is there anything interesting in ~/.xsession-errors?
Maybe there is a path problem and```
/usr/bin/xset b off && /usr/bin/xset b 0 0 0
``` helps.

Another place to put it in would be ~/.profile.
Try appending
```
/usr/bin/xset b off
/usr/bin/xset b 0 0 0

```there and logout and in again.

---

### Post by zolookas on 2009-01-19
There is another possibility: unplug speaker's wires from motherboard :popcorn:

---

### Post by ubername on 2009-01-19
> **marmuta said:**
> Well that probably won't work much better then.
Is there anything interesting in ~/.xsession-errors?
Maybe there is a path problem and```
/usr/bin/xset b off && /usr/bin/xset b 0 0 0
``` helps.

Another place to put it in would be ~/.profile.
Try appending
```
/usr/bin/xset b off
/usr/bin/xset b 0 0 0

```there and logout and in again.

Good call.

This is in my .xsession -errors (along with a lot of other stuff)
xset:  unknown option &&

usage:  xset [-display host:dpy] option ...
    To turn bell off:
	-b                b off               b 0
    To set bell volume, pitch and duration:
	 b [vol [pitch [dur]]]          b on

I'll try these as well as the option to edit .profile and get back to you all.

---

### Post by marmuta on 2009-01-19
> **ubername said:**
> Good call.

This is in my .xsession -errors (along with a lot of other stuff)
xset:  unknown option &&


Ha! This should do it then
```
sh -c "xset b off && xset b 0 0 0"
```

---

### Post by ubername on 2009-01-22
> **marmuta said:**
> Ha! This should do it then
```
sh -c "xset b off && xset b 0 0 0"
```

Many Thanks, job done! (Where's the thanks button gone?!  see my other threads!)

---

### Post by Starks on 2009-01-22
> **zolookas said:**
> There is another possibility: unplug speaker's wires from motherboard :popcorn:

that's a pretty tall order for a laptop owner.

---

### Post by m2.g5ru6y7s on 2009-04-23
Sorry to all, but I want to ENABLE the real pc solid speaker on my desktop (not the emulated one in volume control through the sound system).
The old fashioned solid pc speaker is muted in jaunty.
How to enable it again?

I have tried to un-blacklist all the mentioned hints in this thread but nothing helps. 

lsmod|grep spkr
returns:
pcspkr                 10496  0

Thanks in advance

---

### Post by m2.g5ru6y7s on 2009-04-23
Never mind. I just read that the pc speaker is disabled by default in the Linux kernel.
[http://howto.wikia.com/wiki/Howto_enable_PC_speaker_in_the_Linux_kernel](http://howto.wikia.com/wiki/Howto_enable_PC_speaker_in_the_Linux_kernel)

By default the PC speaker is disabled in the Linux kernel. So you must enable it and recompile you kernel.

Very lame to recompile the kernel for just to enable a simple speaker
Bah :confused:

---

