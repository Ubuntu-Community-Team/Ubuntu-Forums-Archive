---
title: "Feisty and Audigy... do they get along?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by benton on 2007-04-20
Hi there,

I plan to install the Feisty desktop CD over my current Edgy/XP dual-boot install. My sound card is the Creative Audigy, an early model from several years ago. Anyone using this card with Feisty? Is it working just as good as with Edgy?

Thanks,

-Benton

---

### Post by etherealremnant on 2007-04-20
I don't see why it wouldn't work. My Audigy 2 works fine... can't say for the regular Audigy but isn't that an EMU10k chipset anyway?

---

### Post by astronic on 2007-04-20
Yes, it should. Hardware support only very rarely gets worse in Linux and this most surely won't be the case with an open source driver of a very common soundcard modell.

HTH,
Stefan

---

### Post by Madmoose on 2007-04-20
Can anyone tell me why I'm not getting any sound?

Looking under sound I see my card.

Typing "aplay -l" get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I type: "lspci -v"

```
03:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at df80 [size=32]
        Capabilities: <access denied>

03:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at dfe0 [size=8]
        Capabilities: <access denied>

03:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at feadf000 (32-bit, non-prefetchable) [size=2K]
        Memory at fead8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

When I type: sudo modprobe snd-

```
FATAL: Module snd_ not found.
```

My computer isn't muted. The silly thing is my sound worked before I upgraded.

Moose

PS: PLEASE HELP ME!

---

### Post by WireMX on 2007-04-20
I having the same problem with sound! 

Please help us!

---

### Post by KillerBob-it on 2007-04-21
> **Madmoose said:**
> When I type: sudo modprobe snd-

```
FATAL: Module snd_ not found.
```

My computer isn't muted. The silly thing is my sound worked before I upgraded.

Moose

PS: PLEASE HELP ME!

I have the same problem.It worked on k/Ubuntu 6.04 and 6.10 and even Suse.

---

### Post by Luke Davis on 2007-04-22
I also have a Sound Blaster Audigy. sudo modprobe snd- returns
FATAL: Module snd- not found.

---

### Post by mhansen on 2007-04-22
I tried everything under the sun, and just couldn't get it to work until I disabled on-board sound thru the BIOS, even though I did everything "right" to make the Audigy the default card up to that point....Worth a shot anyway.



Regards,
Mike

---

### Post by AlbertTatlocksCap on 2007-04-22
I have an Audigy in my PC - I disabled the onboard card and it worked on Edgy and now  is again fine on Feisty

Check the settings in Preferences>Sound and make sure all is set correctly

---

### Post by zerosystem on 2007-04-22
I don't know about you guys, but I have the same 'FATAL: Module snd_ not found.' error, but I managed to get my sound working despite that by disabling digital output.

I still intend to go into the BIOS, but I managed to get sound working without having to reboot.

[quote=snotface]
Hi guys, first post here so hope this helps. I was having the same problem with my Audigy 2 ZS with Feisty / Gnome. I found that if you right click on your volume control and go to 'Open Volume Control' then 'Edit -> Preferences' you can add options to the control panel. My Audigy Analog/Digital Output Jack was disabled and my PC Speakers were muted. Also, under 'File -> Change Device' it was set to the wrong sound card. Once I corrected these settings, my sound has worked ever since.

Hope this helps. Good luck!
Reply With Quote[/quote]

---

### Post by KillerBob-it on 2007-04-22
I fixed it in this way:

> At the console type (or open the file with any other suitable editer):
Code:

```
sudo nano /etc/modprobe.d/alsa-base
```

At the end of the file add this line (found this option with modinfo -F parm snd-emu10k1):
Code:

```
options snd-emu10k1 enable=1
```


Save the file and exit the editor. (When you used nano, hit Ctrl+O, <ENTER>, Ctrl+X)

Back on the console enter:
Code:

```
sudo update-modules
sudo modprobe snd-emu10k1
```


Found [here]("http://ubuntuforums.org/showthread.php?t=205449&page=56")

---

### Post by bastos.sergio on 2007-04-22
I also had no sound and I am using an old Audigy Sound card.  My motherboard did not support onboard sound, luckily, I was able to fix the problem by disabling "digital output jack" as suggested in the previous post.
Thanks everybody,

---

### Post by Madmoose on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108378](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108378) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey everyone, 

I've posted a bug report, so if you're still having trouble (and this is your bug too) post info here I guess. 

Be sure to post the requested info found [here]("https://help.ubuntu.com/community/DebuggingSoundProblems") to save the Ubuntu Audio Team some time.

Thanks 

Moose

---

### Post by djamu on 2007-04-26
> **Madmoose said:**
> Can anyone tell me why I'm not getting any sound?
---snip

When I type: sudo modprobe snd-

```
FATAL: Module snd_ not found.
```


PS: PLEASE HELP ME!


> **Luke Davis said:**
> I also have a Sound Blaster Audigy. sudo modprobe snd- returns
FATAL: Module snd- not found.


and all the others, don't want to sound :)  rude,  but ** there is no such thing as a snd- module **
read the tutorials ! don't just copy and pasty

for the audigy you have to do ** sudo modprobe snd-emu10k1**   that is snd- + the correct module

on top of that your card is probably working, but you have to **disable the digital output**
**double**click on the sound icon > goto switches > disable digital out

easy....

---

### Post by cjnucette on 2007-04-29
Just type in terminal: alsamixer, disable Audigy A, and you're ready to go.

---

### Post by gerdez on 2007-05-13
> **bastos.sergio said:**
> I also had no sound and I am using an old Audigy Sound card.  My motherboard did not support onboard sound, luckily, I was able to fix the problem by disabling "digital output jack" as suggested in the previous post.
Thanks everybody,

I up this. Audigy, worked on Ubuntu 6.10, not on 7.04. Then I disabled **digital output jack** and it is fine. Thanks.

---

