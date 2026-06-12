---
title: "Mic Problems I've tried Pavucontrol!"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by Alex Eagle on 2014-10-04
So, I was looking for a solution to a mic that has distortion or nothing. [Mine barely picks up anything.]("http://is.gd/IOh5ob") I've already tried the alsamixer and pavucontrol solutions. Please help.

Thanks guys. ;)

---

### Post by Alex Eagle on 2014-10-04
UPDATE:

Just watched my video. I unplug my webcam mic to show what happens in pavu when I do that, and the sound came back when I plugged it back in?! Still need help though because it's temperamental.

Thanks :-D

---

### Post by tgalati4 on 2014-10-04
What is the computer that you are using?  What is the microphone that you are using?  Some microphone ports put out 5 volts DC and require a microphone that takes 5 volts to get decent gain out of it.  Other microphone ports are really Line-in ports.  They don't have strong enough preamps to raise the signal level to something usable.

Open a terminal:

```
alsamixer
```  Look for a capture switch called "microphone boost".

---

### Post by Alex Eagle on 2014-10-04
I've tried alsamixer too. There's two screenshots of alsa in the settings I've got it in ATM.

I have a Fujitsu Siemens Esprimo Mobile V5535. I don't know the specs of my mic jack. I'm using a Panther GT webcam and my internal mic. They both work, but my headphone mic doesn't. I'm using a basic trust headset.

[ATTACH=CONFIG]256942[/ATTACH][ATTACH=CONFIG]256943[/ATTACH]

Thanks

---

### Post by tgalati4 on 2014-10-04
How is the headset plugged in?  USB or microphone 1/8" jack?  Does your webcam have a microphone?  Internal laptop mics are crappy.  They might as well include a can and some string.

What is the output of:

```
aplay -l
```

The specification page reveals the following:

> 
Designed for the value conscious mobile professional, ESPRIMO&#8482; Mobile is the perfect synthesis of form, function and style.

RealTek ALC268
HD Audio-in: Line-in, Microphone

The RealTek ALC268 chip is OK.  Do you have two input ports, a Line-in and Microphone-in?

*Value conscious* means made of cat food.  *Perfect synthesis of form, function, and style* means the laptop is a compromise of all three and does none of them well.

My Acer laptop has an ALC268 with both an "Internal Mic Boost" and a "Mic Boost".  It's possible that the webcam or the internal microphone is blocking the headset microphone.

---

### Post by Alex Eagle on 2014-10-05
Mic jack at the front. It's a regular 3.5mm. Webcam has a mic, but everything about my cam is cheap and crappy, just like the internal. I've always had bad experiences with internal mics. I'm a bit of a PC buff and people ask me to fix stuff sometimes. Some of the problems are with mics. And half of the time I walk out their front door and say, "Stick your short arm in your long pocket and shell out for a good mic". :-P

```
 aplay -l 
``` returns:

```
 **** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I have two jacks, and by the sound of it, it's a line in and mic in, although don't quote me because I'm somewhat a novice on the audio front. I would have thought it's whatever you said.

:-)

---

