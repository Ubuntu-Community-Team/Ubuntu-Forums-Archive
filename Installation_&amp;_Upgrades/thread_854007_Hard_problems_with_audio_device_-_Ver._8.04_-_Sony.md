---
title: "Hard problems with audio device - Ver. 8.04 - Sony Vaio VGN-AR31S"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by mrvaio on 2008-07-09
Hi all,

I'm new here and I hope that somebody help me to solve my pc enigma. I have a **Sony Vaio VGN-AR31S laptop**. It is a big laptop, a desktop replacement.

On board it has Windows Vista and all perifericals works good. I am a developer and I need to install a linux distribution to work.

**I have installed first of all Ubuntu using the wubi and the audio worked perfectly** so, I thought to install seriously the Ubuntu in one of 2 my SCSI HD but at the login **I can hear 3 welcome tamburine sound and the loop of any sound reproduced by the system**.

**I have updated all the system** and I have updated the alsa drivers too but nothing. 

I have spent 15 hours to solve this problem, these are the specifics of my sound card:: 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


#####################################################################################################################################

lspci -v


00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Sony Corporation Unknown device 81fd
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


#####################################################################################################################################



modinfo soundcore
filename:       /lib/modules/2.6.24-19-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-19-generic SMP mod_unload 586 


#####################################################################################################################################


#DMesg

[   45.482558]  [<f8c2c5c3>] snd_hda_codec_read+0x53/0x80 [snd_hda_intel]
[   45.482575]  [<f8c2ecbb>] snd_hda_codec_new+0xeb/0x530 [snd_hda_intel]
[   45.482592]  [<f8c2f987>] snd_hda_bus_new+0x97/0xf0 [snd_hda_intel]
[   45.482609]  [<f8c2b8a8>] azx_probe+0x818/0xb60 [snd_hda_intel]

#####################################################################################################################################


$ asoundconf list
Names of available sound cards:
Intel
SAA7134

#####################################################################################################################################
```

This is the card: **Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**

Furthermore if I can test the sound in the System -> Preferences -> Audio I can see this problem: [http://imagebin.antiyes.com/images/0152808001215559496_46.png](http://imagebin.antiyes.com/images/0152808001215559496_46.png)


I have talked with the #alsa, #ubuntu irc channel and no-one know this strange problem. :(

Anybody can help me?
Thanks
Mr.Vaio

---

### Post by mrvaio on 2008-07-09
I reply to myself helping all the Windows users who wants become a Ubuntu users.

After hacking a little bit the system of alsa for about 21 hours I have decided to restore the windows o.s but test for the last time the way to use Ubuntu on the VGN-AR31S!

**... Bingo! The problem is the normal installation of the Ubuntu O.S. there is a bug there. I'm sure!**

I have installed again the Ubuntu 8.04 but this time by Wubi tool. All works as I told in the previous post. The audio is perfect!

Furthermore I have the windows installed and the Ubuntu in the virtual drive. Yes I know it is not the best solution but if the Ubuntu Community share this thread maybe someone can fix the official setup for the VGN-AR31S.

At the end I suggest to use the LVPM tool [[http://lubi.sourceforge.net/lvpm.html]](http://lubi.sourceforge.net/lvpm.html]) to convert the virtual drive in real drive.

After 21 hours I can hear the music and begin to use the new version of the Ubuntu but a question comes in my mind: How many users spend their time to fix a problem that in Windows is not present? We are so near to share the Ubuntu in the home of the people and in the same time very far to a desktop solution. However thanks guys!

Mr. Vaio

---

### Post by Arschbohrung on 2008-07-09
Hi Mr Vaio

Same Laptop - Wubi install Ubuntu 8.04 - no problems with playback - works fine - BUT - problems with audio capture - Test sound - everything works except audio capture - This one momentarily starts with BEEP and then stops.

Interestingly, I had other funny problems with video. *.DAT extensions do not play with any player - VLC, Totem, gxine, mplayer etc., but *.avi works fine - however - one instance - picture displayed - inverted (literally) - mirror imaged (????!!!) any thoughts?

Mr Vaio

I forgot to say, I did too have some teething problems with audio devices but now things work though my "capture" remains as yet unrectified. 

Ubuntu 8.04 kept me busy till 14:00 hrs last night(morning!) - a good workout though!

Cheers

---

### Post by mrvaio on 2008-07-09
Hi Arschbohrung,

yes some times the computers begun owner of our life!

Usually *.DAT extensions is not a video or audio file but archive like a zip file.

My laptop multimedia functions are about 50 but with ubuntu I can use only 5 or 6 functions.

Have you a Sony Vaio? If yes, which is your model?

Regards,
Mr.Vaio

---

### Post by Arschbohrung on 2008-07-14
I have the Sony VAIO desktop replacement VGN - AR 31S mate.

---

### Post by Arschbohrung on 2008-07-14
By *.DAT, I meant VCD. Did you try to play a VCD yet?

---

### Post by mrvaio on 2008-10-18
No I have not tried it yet.

The problem persists in the live cd too! :(

---

