---
title: "Just installed Feisty - No Sound on E-Mu APS soundcard"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by fyl2u on 2007-05-19
Hi all,

I've done it, I've installed Ubuntu (dual boot with XP) on my tower PC at home after having used it all week at work, setting up a new FTP server.

I was half-expecting this, being a fairly obscure old sound card (but still a great one for writing/recording/producing music), but I'm getting no sound.

The card *is* being recognised and the ALSA mixer is there, nothing is muted, the cables are all in correctly (I haven't touched them and I still have sound in XP).

Any ideas, anyone? :(

P.S. Does this help?

| | | | | | | | | | | | | | | 
vvvvvvvvvvvvvvvvv

phil@phil-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: APS [E-mu APS [4001]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: APS [E-mu APS [4001]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: APS [E-mu APS [4001]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by fyl2u on 2007-05-21
Anyone?

I noticed that there's an archived thread asking this same thing that never got sorted :-(

ALSA claim that the card is "partially supported" - I would like to think that the part which IS supported is the basic sound output :neutral:

Any ideas?

---

### Post by fyl2u on 2007-05-23
Sorry to bump my own post, but having sound will make the difference between me using Ubuntu regularly for various different things, or only ever using it when I need to administrate my ftp server at work.  :neutral:

Any ideas, anyone?

---

### Post by fyl2u on 2007-05-23
P.S. all my cables are fine, my amp is switched on and turned up, and the mixer channel faders are all the way up and not muted :-)

---

### Post by sd.chen on 2007-05-29
Try this troubleshooter:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

It will at least tell you whether or not your sound card is even being detected by Ubuntu.

---

### Post by cern.th.skei on 2007-06-28
i have the same problem... no sound with e-mu aps. everything LOOKS ok, audio programs seems like working, except, no sound...
i think i have tried everythnig, and probably visited every result for google searches, tried every suggestions, etc.... no success...
asoundconf list shows the card as APS, have selected it as default card, have tried to disable and/or remove all other cards that cound interfere (on-board sound, etc)... no success... as if the wires to the speakers have been cut or something :-/
so i had to go back to a half-crappy soundblaster audigy 2 nx (usb2), not good for "pro" sound production (energy xt2 / ardour / jack)

to me it seems like the "partially supported" thing i see in all (alsa) lists including e-mu aps, means everything works, except 'sound'

have absolutely nobody gotten e-mu aps to work in ubuntu?
do i really have to go shopping for a new card?

cern.th.skei

---

### Post by Sidewinder1 on 2007-11-29
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's gotta be a bug. I've tried everything including Chen's link (!Watch out, the advice in there did exactly as it said; I LOST MY DESKTOP and had to do the "sudo apt-get..." fix) and with the EMU10K1 driver, no joy. Hopefully an update or patch will be available soon

---

