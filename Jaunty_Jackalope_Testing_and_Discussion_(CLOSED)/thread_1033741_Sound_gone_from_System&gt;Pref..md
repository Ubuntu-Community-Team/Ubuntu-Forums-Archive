---
title: "Sound gone from System&gt;Pref."
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-07
I went into System>Pref. looking for Sound and it's not there. Did they do some thing I missed? If not, how can I get it back?
Thanks

---

### Post by gnomeuser on 2009-01-07
Welcome to a new and improved Linux.
[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

---

### Post by DougieFresh4U on 2009-01-07
> **gnomeuser said:**
> Welcome to a new and improved Linux.
[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

Thank you!
I always find your posts enlightening and informative!!:D

---

### Post by cecilpierce on 2009-01-07
Right click on the speaker and click "Open Volume Control" but nothing works for me ! Intel82801DB-ICH4 (Alsa mixer) is what i've got. Someday it will work I hope.

---

### Post by DougieFresh4U on 2009-01-07
> **cecilpierce said:**
> Right click on the speaker and click "Open Volume Control" but nothing works for me ! Intel82801DB-ICH4 (Alsa mixer) is what i've got. Someday it will work I hope.

When I right click on the volume control, the menu drops then my whole desktop locks up. I had made a thread about the menu dropping down and staying down the other day. Now my machine freezes and I am forced to do a hard shutdown. So I shall leave it alone. I can put mouse on the control and turn wheel to put volume up without a problem

---

### Post by LordVeovis on 2009-01-07
> **cecilpierce said:**
> Right click on the speaker and click "Open Volume Control" but nothing works for me ! Intel82801DB-ICH4 (Alsa mixer) is what i've got. Someday it will work I hope.

I had this same problem yesterday.  Dropped to terminal and ran:
```

sudo apt-get update
sudo apt-get upgrade
sudo reboot

```
It installed some new packages, and after reboot it worked fine.

---

### Post by pressureman on 2009-01-10
Has anyone found a way to set record levels or configure record source (eg. mic, line-in, CD etc)?

This severe "dumbing-down" of the mixer is exactly like what happened when GNOME took away all the individual screensaver settings.

What is this, MacOS?

---

### Post by Slug71 on 2009-01-10
> **pressureman said:**
> Has anyone found a way to set record levels or configure record source (eg. mic, line-in, CD etc)?

This severe "dumbing-down" of the mixer is exactly like what happened when GNOME took away all the individual screensaver settings.

What is this, MacOS?

Under the 'Input' tab.

---

### Post by autocrosser on 2009-01-10
Got to admit that I like it better...easier than Menu>System>Preferences>Sound

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> Got to admit that I like it better...easier than Menu>System>Preferences>Sound

Yeh i like it better too.
The mic volume and control could be better though but it works.

---

### Post by pressureman on 2009-01-10
> **Slug71 said:**
> Under the 'Input' tab.

Yeah found that already, but I only see one slider. Previously I could independently adjust levels and mute/unmute mic, line in, CD, etc. This is about as useful as a "general failure" lamp on a Boeing 747.

So far the only way I've found to actually select mic as the input source, is to right click, then select Preferences, change the "track to control" to mic, and then I'm able to unmute it. However, this also unmutes the mic for OUTPUT as well... so I can hear the mic input as speaker output. I don't want this - I just want to unmute the mic as a recording source.

This was feasible with the previous mixer.

Edit: I should clarify, I have an Intel 82801DB-ICH4 device. The previous mixer used to individually expose the various channels of this device, whereas the new mixer seems to simplify everything down to a single input device and single output device. Is there no way to enable "expert mode" setting?

---

### Post by Slug71 on 2009-01-10
> **pressureman said:**
> Yeah found that already, but I only see one slider. Previously I could independently adjust levels and mute/unmute mic, line in, CD, etc. This is about as useful as a "general failure" lamp on a Boeing 747.

So far the only way I've found to actually select mic as the input source, is to right click, then select Preferences, change the "track to control" to mic, and then I'm able to unmute it. However, this also unmutes the mic for OUTPUT as well... so I can hear the mic input as speaker output. I don't want this - I just want to unmute the mic as a recording source.

This was feasible with the previous mixer.

Hmm... 'track to control' is pretty much useless to me as i only have one device in the drop menu. 

Have you tried

```
alsamixer -Dhw
```

---

### Post by DougieFresh4U on 2009-01-10
I still do not have volume control in upper right panel. How do I get one there?
Thanks

---

### Post by pressureman on 2009-01-10
> **Slug71 said:**
> Hmm... 'track to control' is pretty much useless to me as i only have one device in the drop menu. 

Have you tried

```
alsamixer -Dhw
```

Yeah, that pretty much restores the previous functionality. Fast too, no mouse clicking! ;-)

Hopefully the new GNOME mixer will expose individual controls for each (sub)device and stop treating us all like idiots. Imagine how owners of 7.1 channel sound cards must feel.

---

### Post by Slug71 on 2009-01-10
> **DougieFresh4U said:**
> I still do not have volume control in upper right panel. How do I get one there?
Thanks

Right click the little speaker. Or click on the speaker and then on the Volume Control... button under the slider.

Or if you dont have the little speaker then right click on the panel and select 'add to panel...'

---

### Post by Slug71 on 2009-01-10
> **pressureman said:**
> Yeah, that pretty much restores the previous functionality. Fast too, no mouse clicking! ;-)

Hopefully the new GNOME mixer will expose individual controls for each (sub)device and stop treating us all like idiots. Imagine how owners of 7.1 channel sound cards must feel.

Haha, well i do like it better than before but i do also think it needs improvement. Its a good little start though and im sure it will get better.

---

### Post by jerrylamos on 2009-01-10
After yesterday's updates, PulseAudio Volume Meter shows bars going back and forth, but there's no sound out of the speakers.  The hardware is HDA ATI SB = ALC888 Analog on a Compaq Presario

Linux version 2.6.28-4-generic (buildd@palmer) (gcc version 4.3.3 20081217 (prerelease) (Ubuntu 4.3.2-2ubuntu9) ) #9-Ubuntu SMP Tue Jan 6 19:34:01 UTC 2009
 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

Dual boot, switch back to the 2.6.28-4 before yesterday's updates, plays fine on same hardware.

I do see the date 2009-01-09 on some pulsaudio files:
-rwxr-xr-x 1 root root 2045 2009-01-09 01:14 /etc/init.d/pulseaudio
-rw-r--r-- 1 root root 4427 2009-01-09 01:21 default.pa

Any clue how to hear the PulseAudio Volume Meter activity?  The workarounds on Bug #315809 didn't help.

Thanks, Jerry

---

### Post by Slug71 on 2009-01-10
> **jerrylamos said:**
> After yesterday's updates, PulseAudio Volume Meter shows bars going back and forth, but there's no sound out of the speakers.  The hardware is HDA ATI SB = ALC888 Analog on a Compaq Presario

Linux version 2.6.28-4-generic (buildd@palmer) (gcc version 4.3.3 20081217 (prerelease) (Ubuntu 4.3.2-2ubuntu9) ) #9-Ubuntu SMP Tue Jan 6 19:34:01 UTC 2009
 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

Dual boot, switch back to the 2.6.28-4 before yesterday's updates, plays fine on same hardware.

I do see the date 2009-01-09 on some pulsaudio files:
-rwxr-xr-x 1 root root 2045 2009-01-09 01:14 /etc/init.d/pulseaudio
-rw-r--r-- 1 root root 4427 2009-01-09 01:21 default.pa

Any clue how to hear the PulseAudio Volume Meter activity?

Thanks, Jerry

Hmm, not sure but i have HDA ATI SB - ALC268 Analog and i have sound.

Scratch that, i just did updates and now i have no sound.
I know which one it was but now i cant remember the name. There were only 5 updates to get and 1 of them was libvol something or other.

Rebooted and i have sound again.:confused::confused:

---

### Post by woodrobin on 2009-01-10
Slug71, many thanks!  You saved me from an evening of frustrating silence and restored unto me my Torchwood marathon!  :popcorn:

This:

Have you tried

```
alsamixer -Dhw
```[/quote]


... fixed it right up.  The command line controls let me find the problem - something had set the Front and PCM to about 5%, leaving cranking up the Master to 100% fairly feeble at best.  With the new and 'improved' controls, no way exists to access those channels through the GUI, but it is Linux, and the command line shall set you free!  :)

In all seriousness, visually I love the new layout of the the sound controls, and I think they work better as a user interface.  However, that does little good if the connection to under-the-hood functionality is neutered.  +100 for looks, -1,000 for function - especially if the settings previous to upgrade are not correctly preserved (I'm fairly sure I didn't have PCM and Front set to 5% at any point, as I know where the Mute control is if I don't want to hear anything).


Ubuntufraternally,

Woodrobin

---

### Post by DougieFresh4U on 2009-01-10
> **Slug71 said:**
> Right click the little speaker. Or click on the speaker and then on the Volume Control... button under the slider.

Or if you dont have the little speaker then right click on the panel and select 'add to panel...'

Thank you, got it. But I now still have the same problem I had been having with 'desktop' locks up when I click the volume control. I can 'scroll' the volume up and down but as soon as I click that control and the little menu drops down, my whole screen locks up accept mouse buts it's useless, therefore causing a 'hard' shut down.

---

### Post by Slug71 on 2009-01-10
> **DougieFresh4U said:**
> Thank you, got it. But I now still have the same problem I had been having with 'desktop' locks up when I click the volume control. I can 'scroll' the volume up and down but as soon as I click that control and the little menu drops down, my whole screen locks up accept mouse buts it's useless, therefore causing a 'hard' shut down.

Hmm..
I would suggest you file a bug against that as it would definitely be one.

Does it lock up if you right click the speaker and go down to 'Open Volume Control' too?

---

### Post by DougieFresh4U on 2009-01-10
> **Slug71 said:**
> Hmm..
I would suggest you file a bug against that as it would definitely be one.

Does it lock up if you right click the speaker and go down to 'Open Volume Control' too?

Yes it does. If I do anything but scroll the volume up and down, it locks up desktop

---

### Post by ShirishAg75 on 2009-01-10
Has anybody got the following error message. 

```

$ alsamixer -Dhw

alsamixer: function snd_ctl_open failed for hw: No such device

```

I have filed [lpbug]315981[/lpbug] for the same.

---

### Post by Slug71 on 2009-01-10
> **woodrobin said:**
> Slug71, many thanks!  You saved me from an evening of frustrating silence and restored unto me my Torchwood marathon!  :popcorn:

In all seriousness, visually I love the new layout of the the sound controls, and I think they work better as a user interface.  However, that does little good if the connection to under-the-hood functionality is neutered.  +100 for looks, -1,000 for function - especially if the settings previous to upgrade are not correctly preserved (I'm fairly sure I didn't have PCM and Front set to 5% at any point, as I know where the Mute control is if I don't want to hear anything).


Ubuntufraternally,

Woodrobin

No problem, and yes i agree about your comment in regards to look and function. 
It will get better though, im sure about that. Its a very new app and only just introduced.

---

### Post by Slug71 on 2009-01-10
> **DougieFresh4U said:**
> Yes it does. If I do anything but scroll the volume up and down, it locks up desktop

Time to file that bug i guess.
Is your system all up to date?

---

### Post by Slug71 on 2009-01-10
> **cecilpierce said:**
> Right click on the speaker and click "Open Volume Control" but nothing works for me ! Intel82801DB-ICH4 (Alsa mixer) is what i've got. Someday it will work I hope.


Does your desktop lock up like the OP's?

What happens with the output of
```

alsamixer -Dhw
```

?
File a bug if you need to or else that someday may be a very long time away.

---

### Post by DougieFresh4U on 2009-01-10
> **Slug71 said:**
> Time to file that bug i guess.
Is your system all up to date?

System is up-to -date. I do have Intel, and I am not thrilled with the way graphics are playing. I was having desktop lockups with the Intel865G. I did some editing to xserver-org file per other thread and lockups/freeze stopped.
I guess bug filing may be needed, but no one else seems to have that problem. Where would I look for any info in logs to see if they caught anything?
Thanks

---

### Post by Slug71 on 2009-01-10
> **DougieFresh4U said:**
> System is up-to -date. I do have Intel, and I am not thrilled with the way graphics are playing. I was having desktop lockups with the Intel865G. I did some editing to xserver-org file per other thread and lockups/freeze stopped.
I guess bug filing may be needed, but no one else seems to have that problem. Where would I look for any info in logs to see if they caught anything?
Thanks


It could well be an Intel thing then. Im on AMD. As for logs your guess would be as good as mine. I'd file the bug and one of the Devs will more than likely ask for the necessary logs.

---

### Post by Slug71 on 2009-01-10
Double post,

Damn Firefox!

---

### Post by ShirishAg75 on 2009-01-11
> **cecilpierce said:**
> Right click on the speaker and click "Open Volume Control" but nothing works for me ! Intel82801DB-ICH4 (Alsa mixer) is what i've got. Someday it will work I hope.

Cecilpierce, 
   I have filed a bug, can you look at that [lpbug]315981[/lpbug]

Btw found something interesting while look at the docs. 
/usr/share/doc/alsa-utils/README.alsamixer

> 
Alsamixer uses an ncurses interface, which may not display properly in
an xterm.


---

### Post by ace214 on 2009-01-18
I had to find the ALSA mixer to turn off the digital output to make my sound work... Otherwise I get the static crap... Would be a huge turn off for a newbie....

---

