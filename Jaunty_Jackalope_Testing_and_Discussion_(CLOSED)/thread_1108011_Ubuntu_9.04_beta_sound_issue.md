---
title: "Ubuntu 9.04 beta sound issue"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Wonslung on 2009-03-27
i'm not sure which forum to post this in so i'll put it here.
I'm trying out the new beta of 9.04 and i can't open the volume controls.  the first boot there wasn't a volume control on the gnome panel so i tried adding one, no matter how many times i clicked to add it nothing appeared. Also, if i went to system > preferences > sound it would start to open but never actually open.

the next boot i had an error message about how the gnome panel sound couldn't load (there were several of these error, i think one for each panel button i tried to add, because i couldn't see them i must have added like 10-15 of them)

i have a ca0106 sound blaster audigy se

---

### Post by overdrank on 2009-03-27
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by TBerk on 2009-04-01
I too lost sound in 9.04 beta. (It worked OK in 8.10.)

I installed from a LIVE CD into a new partition (no older OS portions around.)

I dual boot WinXP and Ubuntu, the Windows side of things still works OK so I don't think it's broken hardware.

I have a Creative Labs Audigy2; it has support for multichannel sound, at the moment I'd be happy with simple stereo.


TBerk

---

### Post by markbuntu on 2009-04-01
Well, in hardy and intrepid the audigy driver came default with digital turned on so no analog sound. Did you check the switch in the volume control or alsa-mixer?

---

### Post by Cphood on 2009-04-02
I was able to get audigy 5.1 surround sound with the following procedures:

Open Terminal

enter: "gedit /etc/pulse/daemon.conf"

scroll down and find "; default-sample-channels = 2"

for 5.1 sound change the 2 to a 6. save and close.

From the tool bar select "system-preferences-sound" use the drop down menu to change "autodetect" to "audigy4 multi-channel playback(ALSA) for all execpt "capture" -- select "audigy4 capture/playback(ALSA)

Right click the sound icon on the toolbar and click on "Open Volume Control".  Select the 'Switches" tab and put a check in the block by
"Audigy Analog Digital Output Jack".  Select the preferences tab at the bottom of the volumn control panel.  Select/check "Master". "Front". "Surround", "Center". "LFE", and "Side".

Reboot and you should have 5.1 sound.

---

### Post by TBerk on 2009-04-02
> **Cphood said:**
> I was able to get audigy 5.1 surround sound with the following procedures:

Open Terminal

enter: "gedit /etc/pulse/daemon.conf"

scroll down and find "; default-sample-channels = 2"

for 5.1 sound change the 2 to a 6. save and close.

From the tool bar select "system-preferences-sound" use the drop down menu to change "autodetect" to "audigy4 multi-channel playback(ALSA) for all execpt "capture" -- select "audigy4 capture/playback(ALSA)

Right click the sound icon on the toolbar and click on "Open Volume Control".  Select the 'Switches" tab and put a check in the block by
"Audigy Analog Digital Output Jack".  Select the preferences tab at the bottom of the volumn control panel.  Select/check "Master". "Front". "Surround", "Center". "LFE", and "Side".

Reboot and you should have 5.1 sound.


Everything works the way you spell it out, except of course No Sound. 

I'm thinking I may need to Root Canal the OSS, PulseAudio, Creative SB Audigy2 files and reinstall.


TBerk
the drag is; the thing works in WinXP...

---

### Post by george1984 on 2009-04-03
> **Wonslung said:**
> i'm not sure which forum to post this in so i'll put it here.
I'm trying out the new beta of 9.04 and i can't open the volume controls.  the first boot there wasn't a volume control on the gnome panel so i tried adding one, no matter how many times i clicked to add it nothing appeared. Also, if i went to system > preferences > sound it would start to open but never actually open.



i have a ca0106 sound blaster audigy se

Same soundcard, same problem.

Otherwise sound ok, except for flightgear, supertux2 and supertuxkart which have nasty crackling.

Don't know if this is relevant but ....

            sudo cat /proc/asound/modules...gives

                0 snd_intel8x0
                1 snd_ca0106

                                                  Should the sound card be placed second?

---

### Post by TBerk on 2009-04-03
Seems the original poster, with his Audigy se board has a different chipset than mine; an Audigy2:


In my case 
$ sudo cat /proc/asound/modules
reveals-

 0 snd_emu10k1


I'm going to let this lay awhile and see what the roll out of 9.04 delivers.


TBerk
edit:

> 
Alsa doesn't work on Debian (snd_emu10k1) 
[http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy](http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy)


**wet-willy**

I have SB Audigy 2ZS, I was troubleshooting another member's 'no sound' issue with the same card and suggested playing with mixer settings, like mute things you don't use etc. The next day I found I had no sound also, didn't know that when I was troubleshooting buddies issues.
Anyway, he was talking about the Audigy output jack channel in his mixer, he had Gnome and I was in Mandriva with KDE and noticed I did not have that channel in kmix. Through kmix settings I enabled it, but still no sound like him, then I muted it and VOILA!, I had sound. But disabling the Audigy output jack again rendered Mandriva soundless. It had to be enabled but muted if not used...I guess.


---

### Post by PiotrekS on 2009-04-04
> i'm not sure which forum to post this in so i'll put it here.
I'm trying out the new beta of 9.04 and i can't open the volume controls. the first boot there wasn't a volume control on the gnome panel so i tried adding one, no matter how many times i clicked to add it nothing appeared. Also, if i went to system > preferences > sound it would start to open but never actually open.

the next boot i had an error message about how the gnome panel sound couldn't load (there were several of these error, i think one for each panel button i tried to add, because i couldn't see them i must have added like 10-15 of them)

i have a ca0106 sound blaster audigy se

Already submitted to launchpad:
[https://bugs.launchpad.net/bugs/345550]("https://bugs.launchpad.net/bugs/345550")

Fix would be soon in repository.
I have this issue too.

---

### Post by elvie on 2009-04-13
Try disabling the onboard soundcard from bios. It worked for me.

---

