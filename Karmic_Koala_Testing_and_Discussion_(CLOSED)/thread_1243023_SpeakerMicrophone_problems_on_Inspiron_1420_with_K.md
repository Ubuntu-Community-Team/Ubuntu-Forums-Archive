---
title: "Speaker/Microphone problems on Inspiron 1420 with Karmic"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fireman biff on 2009-08-17
My Inspiron 1420 has 3 audio ports in the front, 2 for output and 1 for input. It also has built-in speakers and microphones.

When I used the laptop with Hardy/Intrepid/Jaunty I always got sound on the built-in speakers and plugging headphones into the 1st output port would switch the audio to the headphones. Now, with Karmic I have no sound from the built-in speakers or on the 1st port, but the 2nd port has sound.

Also, with Karmic I can use the built-in microphones but when I connect an external mic it does not work - the built-in ones keep working though. With Hardy/Intrepid/Jaunty I was able to use the external mic.

Any idea how I can get things working properly?


I have all my packages up to date, and my Sound Preferences setup is as follows:
[LIST]
[*]I am using the profile "Analog Surround 4.0 Output + Analog Stereo Input".
[*]On the Input tab I have only one device to choose from, "Internal Audio Analog Stereo", and I have "Microphone 2" set as the connector (I have tried "Microphone 1" without any luck).
[*]On the Output tab I have only one device to choose from, "Internal Audio Analog Surround 4.0", and both Balance and Fade are in the middle.
[/LIST]

lspci:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f3
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by fireman biff on 2009-08-19
bump?

---

### Post by fireman biff on 2009-08-22
One last bump...

---

### Post by icb410 on 2009-09-06
There's a bug in karmic (#409819).  I haven't had any luck with it yet.  Microphone #2 is for the front input jack.  If you plug a microphone into it (or a pair of headphones), it will pick up audio and can be used as an input source.  Microphone 1 is the builtin mic and doesn't seem to work.

---

