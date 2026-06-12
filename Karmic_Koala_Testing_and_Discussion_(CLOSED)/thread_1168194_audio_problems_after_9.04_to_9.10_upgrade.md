---
title: "audio problems after 9.04 to 9.10 upgrade"
date: 2009-05-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by doomsword2001 on 2009-05-23
hello
i have upgraded ubuntu 9.04 to 9.10 and had the following problem:
when trying to play an avi movie i had terrible sound

I have changed  system-->preferences-->sounds--> and changed ALSA to OOS under the music and movies section. Then it worked fine.

i hope i help ):P

---

### Post by ranch hand on 2009-05-23
Let me get this straight, you have "upgraded" from a release that has barely become stable to an Alpha1?

WOW, and here I thought I was nuts for new stuff.

It would be a big help if you would geve a little more info: system you are running on, what codecs you have installed would be great.

In your system specs it would be great if you listed yor sound card or who made the intigrated deal if that is what you are running.

---

### Post by BwackNinja on 2009-05-23
Changing from alsa to oss means you're no longer going through pulseaudio - hence, this must be a pulseaudio issue somewhere.

---

### Post by psyke83 on 2009-05-24
I think that almost everybody is suffering from audio problems right now, because PulseAudio and ALSA are in an inconsistent state. I need to kill the pulseaudio process upon each log in for audio to work properly.

We shouldn't expect things to work correctly at Alpha 1.

---

### Post by ranch hand on 2009-05-24
psyke83
+1

---

### Post by mc4100 on 2009-05-24
> **psyke83 said:**
> I think that almost everybody is suffering from audio problems right now, because PulseAudio and ALSA are in an inconsistent state. I need to kill the pulseaudio process upon each log in for audio to work properly.

Yep, broken on login here too. The volume control applet says master, I think, is muted but unmuting does nothing --- need to kill and restart. So we're all in the same situation. 

Removed pulseaudio for now, until it's whipped back into shape.

---

### Post by Mazza558 on 2009-05-24
Looks like i'm in a more fortunate position then? Like the OP, I have poor sound quality with crackling, etc. Still, the fact that it works is pretty impressive for an Alpha

---

### Post by taavikko on 2009-05-24
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/var/log/user.log is flooded with pulseaudio and ALSA messages...

Hopefully alsa-1.0.20 is packaged in near future and uploaded to repos, to see if that fixes anything.

At least for me, this HW wasn't working without tweaking it with model=hp-m4 in previous version of ALSA.

---

### Post by ranch hand on 2009-05-24
Well I guess I am in great shape then.  Have been listening to news and now have a movie going.  Everything cooking right along.

---

### Post by BwackNinja on 2009-05-24
My sound works wonderfully.... after I unmute it in pavucontrol... after every reboot >.<

I also don't get any sounds at gdm

---

### Post by Nullack on 2009-05-24
Yes we need alsa .20 but Im also confused about if we have pulse .15 or .14 as package searches show some contrary information.

---

### Post by super.rad on 2009-05-25
Seems we have parts of PA .15 but some parts are still .14 which is probably not helping things.
Upgrade to .20 for alsa just came through although dpkg is giving me an error at the moment

---

### Post by Regenweald on 2009-06-12
Thought i'd wake this thread up. Anyone still having audio problems, I sure am :)

---

### Post by Regenweald on 2009-06-12
Digging through the forums sorted it out.

1. Add user to audio group
```

sudo adduser 'you' audio

```

2. Delete contents of ~/.pulse
3. Reboot.

---

### Post by pediatracancun on 2009-06-26
> **Regenweald said:**
> Digging through the forums sorted it out.

1. Add user to audio group
```

sudo adduser 'you' audio

```

2. Delete contents of ~/.pulse
3. Reboot.
This solution works for me.
Although to delete the contents of ~/.pulse I did it with sudo nautilus.

---

### Post by tjeremiah on 2009-06-30
> **Regenweald said:**
> Digging through the forums sorted it out.

1. Add user to audio group
```

sudo adduser 'you' audio

```

2. Delete contents of ~/.pulse
3. Reboot.

yup, this worked.Thanks!

---

### Post by Megatron3000 on 2009-09-03
thank you very much for the way out of (one of) my ongoing audio problems. and thanks google for getting me here. a fine day to you, gentlemen

---

### Post by mfox on 2009-09-09
I was having similar problems with sound in 9.10 alpha 5 running on my Intel Mac in both VMware Fusion and VirtualBox.  In the former case, no mp3 or mp4's would play and I couldn't even get radio sound in Rhythmbox.  In VirtualBox, I fared slightly better, as only mp4's wouldn't play.  Removing pulseaudio solved the problem in Fusion and in VirtualBox.  Note that to solve the problem I had to first remove pulseaudio and then log out and back in.

---

### Post by peacewithall on 2009-09-11
Having serious problems here too, related to pulseaudio, recently it has been basically unusable for me, also having some bad crashes from it, I was reporting bugs with the crash report tool that appears right after it crashed for me, but recently I get an error about unable to send the report due to an assertion failure in pulseaudio?, something like that. I do hope that pulseaudio stabilises before karmics final release.

---

### Post by mfox on 2009-09-21
Unfortunately, deleting .pulse and rebooting didn't work for me.  My particular problem is slow-motion sound in a VirtualBox (3.0.6) virtual machine on my Intel iMac.  I tried deleting pulseaudio prior to deleting the .pulse folder, and that didn't do it, either.  The slow-mo sound occurs when I play mp3's or mp4's, and in the Ubuntu 9.10 startup sound. 

I also have a 9.10 virtual machine in VMware Fusion (the 3.0 beta). It was giving me worse sound problems when playing mp's, but deleting pulseaudio was enough to fix it.  In both cases, I am running 9.10 alpha 6.

---

### Post by smallgodinacan on 2009-09-21
I have been having issue with garbled playback when adjusting volume. Played around it a bit and found it is randomly messing with the PCM settings. In Jaunty there was an option to set the volume slider/controller to affect only the master volume, but I can't seem to make that adjustment in Karmic. My current work around is to use the Alsa mixer (gnome-alsamixer) to adjust the master and fix the PCM if use the volume controls on my keyboard by reflex.

---

### Post by bobince on 2009-09-22
> **smallgodinacan said:**
> I have been having issue with garbled playback when adjusting volume. Played around it a bit and found it is randomly messing with the PCM settings.

Are you sure you've got all the recent updates? I had similar problems from A5: altering volume levels resulted in horrible crackles, starting and stopping an audio session gave a big nasty click, and the main volume level kept changing itself. Since some updates around A6 time it's back to being smooth for me.

---

### Post by mfox on 2009-09-23
> **bobince said:**
> Are you sure you've got all the recent updates? I had similar problems from A5: altering volume levels resulted in horrible crackles, starting and stopping an audio session gave a big nasty click, and the main volume level kept changing itself. Since some updates around A6 time it's back to being smooth for me.
Today's updates solved my sound problems on my VirtualBox vm.  I continued to have the "slow-motion" sound before the updates.  After the updates, all mp3's and mp4's played at the correct speed.  I then reinstalled pulseaudio, and everything was still working!  Unfortunately, the new updates didn't fix pulseaudio for my VMware Fusion vm.  Putting pulseaudio back took away my sound; removing it gave me back my sound.

---

### Post by mfox on 2009-10-03
> **Regenweald said:**
> Digging through the forums sorted it out.

1. Add user to audio group
```

sudo adduser 'you' audio

```

2. Delete contents of ~/.pulse
3. Reboot.

Well, it turned out that my slow-motion sound problem went on and off in VirtualBox with further Ubuntu 9.10 updates, and deleting pulseaudio wasn't fixing the problem in the beta.  I finally tried the solution posted by Regenweald, and that fixed it!  Pulseaudio was added back and everything still works!  Thanks, Regenweald!

Update:  Nope; didn't permanently solve the problem.  Upon reboot, I still have noticeably slow-motion sound.  I'm still in the audio group, and deleting contents of ~/.pulse again had no effect; nor did removing pulseaudio.

I'm at a loss as to how to get my sound up to speed.  (By the way, the Ubuntu startup sound is similarly affected.)  Ideas anyone?

Update 2:

I now see that the slow sound problem is present in other virtual Linux machines I have installed on VirtualBox - openSUSE 11.0 and Vector 6.0.  I never noticed this before, so it's probably a bug in the latest VirtualBox update (3.0.6). It is not present in VMware Fusion virtual machines on the same Mac, so I will report this to VirtualBox.

---

### Post by NICU on 2009-10-26
I am having the same problem after upgrading from Ubuntu 9.04 to 9.10 in VMWare. All sound output through pulseaudio sounds garbled. It sounds very choppy or sped up - like the full sounds are played but chopped into pieces and sped up with quiet in between. ...not easy to describe. 

I have added my account to the audio group and I've deleted the .pulse directory contents a few times and rebooted, but the problem never goes away. Any new ideas?

---

