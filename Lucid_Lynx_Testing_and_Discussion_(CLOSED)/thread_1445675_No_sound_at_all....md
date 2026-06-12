---
title: "No sound at all..."
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-04-02
So, am I the only one who has NO SOUND at all?

Help would be appreciated.

```
ubuntu@ubuntu:~$ cat /proc/asound/card0/codec#0
Codec: Realtek ALC268
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0268
Subsystem Id: 0x103c30cc
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x28 0x28]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x28 0x28]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01211020: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a11840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x99a3094e: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x99430130: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
  Processing Coefficient: 0x00
  Coefficient Index: 0x09
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x18 0x19* 0x1a 0x1c 0x14 0x15 0x12
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14* 0x15 0x13
ubuntu@ubuntu:~$

```

---

### Post by crjackson on 2010-04-03
As usual, I guess I'll be the only one replying to my own thread  :lolflag:

---

### Post by drucer on 2010-04-03
> **crjackson said:**
> As usual, I guess I'll be the only one replying to my own thread  :lolflag:

Not sure if this helps, but this has always fixed my audio-problems instantly on recent Ubuntu versions and Lucid Lynx was no different. This worked for me - it may not work for you, but you can try. I have M-Audio Delta 66 professional PCI audio card that has ICE1712 audio chip.

1) Remove pulse-audio.

sudo apt-get remove pulseaudio

2) Restart the computer.

3) Go to YouTube and test some video to see if the audio works.

---

### Post by williejones on 2010-04-03
Try ```
sudo killall pulseaudio.
```I have to do this when my sound preferences show output as dummy.
It stops and rebuilds pulseaudio to give sound.

---

### Post by crjackson on 2010-04-04
> **williejones said:**
> Try ```
sudo killall pulseaudio.
```I have to do this when my sound preferences show output as dummy.
It stops and rebuilds pulseaudio to give sound.

I'll give it a shot..

---

### Post by crjackson on 2010-04-04
> **williejones said:**
> Try ```
sudo killall pulseaudio.
```I have to do this when my sound preferences show output as dummy.
It stops and rebuilds pulseaudio to give sound.

That did the trick.  Do you suppose this will still be the case with the final build?  I'd hate to think a person would have to do that after rebooting the computer each time.

---

### Post by wightghost on 2010-04-04
> **williejones said:**
> Try ```
sudo killall pulseaudio.
```I have to do this when my sound preferences show output as dummy.
It stops and rebuilds pulseaudio to give sound.


Just had a problem with no sound, too.  This code worked like a charm. Thanks

---

### Post by miegiel on 2010-04-04
> **crjackson said:**
> ...  I'd hate to think a person would have to do that after rebooting the computer each time.

You don't have to reboot,
```
pulseaudio --start
```
will start the daemon if it is not running.

---

### Post by crjackson on 2010-04-04
> **miegiel said:**
> You don't have to reboot,
```
pulseaudio --start
```
will start the daemon if it is not running.

That's not what I meant.  I turn off my laptop every day.  I would like for the sound to work upon booting without having to kill pulseaudio each time to make it work.

---

### Post by crjackson on 2010-04-05
Just installed today's daily live on a LiveUSB.  Still problems with loading dummy package for the device on boot.  killall pulseaudio works still.

---

### Post by crjackson on 2010-04-12
It's been a while since I posted to this thread.  I just wanted to report that the problem persists.  I don't think it's going to be resolved before release.  I'm thinking I'll have to stick with karmic for 6 more months.

---

### Post by miegiel on 2010-04-12
> **crjackson said:**
> It's been a while since I posted to this thread.  I just wanted to report that the problem persists.  I don't think it's going to be resolved before release.  I'm thinking I'll have to stick with karmic for 6 more months.

You have no sound when pulse is running, but sound does work after you killed pulse? Or do you only have sound after pulse has restarted after you killed it first?

Assuming you have done all the regular stuff you can find in the sound troubleshooting guides (even if it's not written for lucid it can still provide inspiration); I remember I had to remove the (hidden) pulse stuff in my home dir, once a long time ago, to get pulse to behave. There's a *.pulse/* directory and a *.pulse-cookie* file, try renaming them / backing them up somewhere else (just in case you want to put them back). Pulse should recreate the dir and file automatically if it needs to.

---

### Post by rps63ifid on 2010-04-13
I'm bumping into this same problem running beta 2 from a bootable USB stick on my Asus Eee PC 1000HE. Killing and starting pulseaudio seems to solve the problem, but I'm wondering how to "really" solve this problem if/when I install?

---

### Post by Saghaulor on 2010-04-13
Until it is finally fixed, you blokes with the pulseaudio problems could write a script that kills and restarts pulse, then make it autostart.

That way you're not living in cli every boot.

Never done this sort of thing before, but I'd imagine it looks something like the following:

```
killall pulseaudio && /etc/init.d/pulseaudio
```

Then save it, make sure it's executable, and add it to your session start-up.

It ain't pretty but it should do the trick.

---

### Post by Reiger on 2010-04-13
Hmm I'd try using the following instead:
```

# restart the service
restart pulseaudio

```
```

# stop the service
stop pulseaudio

```
```

# manually start the service
start pulseaudio

```

IIRC Ubuntu is moving away from old style init.d scripts.

---

### Post by crjackson on 2010-04-13
> **rps63ifid said:**
> I'm bumping into this same problem running beta 2 from a bootable USB stick on my Asus Eee PC 1000HE. Killing and starting pulseaudio seems to solve the problem, but I'm wondering how to "really" solve this problem if/when I install?

The same here.  killing it and letting restart works but it's doing it on 3 different machines here so I know it's not isolated.  I hope they fix this soon.  It's deal breaker for me.

---

### Post by crjackson on 2010-04-13
> **Saghaulor said:**
> Until it is finally fixed, you blokes with the pulseaudio problems could write a script that kills and restarts pulse, then make it autostart.

That way you're not living in cli every boot.

Never done this sort of thing before, but I'd imagine it looks something like the following:

```
killall pulseaudio && /etc/init.d/pulseaudio
```

Then save it, make sure it's executable, and add it to your session start-up.

It ain't pretty but it should do the trick.

Of course I realize that.  The point is I'm reporting it's still not working or fixed yet.  I'm getting the same result on multiple machines.  Only one of my machines doesn't exhibit this behavior and it's a VERY OLD eMachines laptop.  All my newer machines have this issue.

And don't call me a bloke please.  I know it only means guys or dudes or some such...  However I don't like being referred to as such.

---

### Post by jwssr on 2010-04-13
Im running Lucid on 4 different boxes....all different sound devices and video devices.  I also reload daily builds quite frequently.

Ater every build, I usually dont have sound...as you.

Here is what I do to establish sound on all of my different boxes.

  1.  install gnome-alsamixer.
     gnome-alsa-mixer will be in Apps/sounds&video.
   this will show you all of your sound cards out/in connections...perhaps some of them may be muted..if so,  unmute.  Also if you have a digital connection....ice958 must be checked.      

2 .  install paman. 
   This will give you Apps/Sound&Video/pulse audio volume control....which you cant live without if you have multiple sinks.

The first thing after new install is to click on Playback tab (one of five tabs)....if the sound slider is down (to the left)...pull it up to 95-100%...you will not have system sounds (ie  login/logout, etc) if not.

When you have multiple apps outputing sound...control the sink and the vol from playback tab.

I use bluetooth headsets/digital sound cards/analog I alternate between sound output here..  Impossible without using PA vol control.

But the first step is very important...if a device is muted...guess what.

I hope this may help...It works for me flawlessly

---

### Post by crjackson on 2010-04-14
> **jwssr said:**
> Im running Lucid on 4 different boxes....all different sound devices and video devices.  I also reload daily builds quite frequently.

Ater every build, I usually dont have sound...as you.

Here is what I do to establish sound on all of my different boxes.

  1.  install gnome-alsamixer.
     gnome-alsa-mixer will be in Apps/sounds&video.
   this will show you all of your sound cards out/in connections...perhaps some of them may be muted..if so,  unmute.  Also if you have a digital connection....ice958 must be checked.      

2 .  install paman. 
   This will give you Apps/Sound&Video/pulse audio volume control....which you cant live without if you have multiple sinks.

The first thing after new install is to click on Playback tab (one of five tabs)....if the sound slider is down (to the left)...pull it up to 95-100%...you will not have system sounds (ie  login/logout, etc) if not.

When you have multiple apps outputing sound...control the sink and the vol from playback tab.

I use bluetooth headsets/digital sound cards/analog I alternate between sound output here..  Impossible without using PA vol control.

But the first step is very important...if a device is muted...guess what.

I hope this may help...It works for me flawlessly

So, after all these adjustments do you have sound after rebooting?  Basic sound should work after a clean install.  I realize I can make adjustments and tweaks, and run scrips or manually kill and restart pulseaudio to make sound work, I just hope basic sound will work without all of this by release date.

I have a few long distance friends who run Ubuntu at my suggestion and I have to provide phone support for them.  I got tired of helping them with windows every time they would become virus infected and such, so I had them make the switch to make MY live easier.  So far that has worked for the most part (except one friend who is on dialup).

If I have to walk them through a bunch of adjustments, the upgrade won't be worth it.

---

### Post by Saghaulor on 2010-04-15
> **crjackson said:**
> Of course I realize that.  The point is I'm reporting it's still not working or fixed yet.  I'm getting the same result on multiple machines.  Only one of my machines doesn't exhibit this behavior and it's a VERY OLD eMachines laptop.  All my newer machines have this issue.

And don't call me a bloke please.  I know it only means guys or dudes or some such...  However I don't like being referred to as such.

Sorry about that. Didn't mean to insult you in any way. Please accept my apology.

---

### Post by Nightstrike2009 on 2010-04-15
Hiya Crjackson,

I just opened the audio mixer gadget (top panel bar, right side) and fiddled around with settings (unmuted main volume, selected different "playback" source from pulldown menu) worked for me anyhow. :-)

Hope that helps you out.

PS: Don't ask why some ubuntus "mute" sound as default setting, I don't know either LOL.

PPS: I am sorry if this doesn't solve it, it worked for me don't mean to sound patronising just trying to assist.

---

### Post by crjackson on 2010-04-16
> **Saghaulor said:**
> Sorry about that. Didn't mean to insult you in any way. Please accept my apology.:wink:

No worries friend.

---

### Post by myddewji13 on 2010-04-16
Download alsa from the realtek website and manually compile. This tends to solve problems with the newer Realtek codecs (this worked for me) 

See:
[http://ubuntuforums.org/showthread.php?t=1434922](http://ubuntuforums.org/showthread.php?t=1434922)

I'm pretty sure I had the same realtek codec as you but I'm not on my machine now. Will probably check tomorrow and post back.

---

### Post by crjackson on 2010-04-16
I just tried today's daily LiveUSB and still no official resolution.  I'm looking for a fix on the Live builds.  Not looking to fix an installed version yet.  I want it fixed on the install CD/USB so that when I send out CD's etc... I don't have start walking people through a fixing process.  It should just work out of the box.

---

### Post by crjackson on 2010-04-17
Today's Daily Live build fixed the sound issue on one of my machines.  Great job!  Now I'll test on other machines.

I have now installed Lucid on my main desktop and replaced Karmic.  I have a back-up image of Karmic and additional back-ups of all important files in case something awry.

---

### Post by crjackson on 2010-04-17
Well, I'm satisfied. I tested Lucid on my other machines and pulse-audio loads correctly now.

I'll mark this thread as SOLVED!

---

