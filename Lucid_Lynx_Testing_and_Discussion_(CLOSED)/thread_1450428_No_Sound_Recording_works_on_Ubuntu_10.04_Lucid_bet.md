---
title: "No Sound Recording works on Ubuntu 10.04 Lucid beta"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MBHAKM on 2010-04-09
Hi I need your help advise on Sound Recording . On Ubuntu lucid 10.04   Beta , I can see on Sound Preferences -->Input Tab , No input level   sliding moving where input volume is 100% and device for sound input is   Internal Audio Analog stereo. That's why I am unable to record on Sound   Recorder. But the sound works where I can listen to music or video but   not sound recording.

Please see also attachment for Sound Prefernces

Do u have solutions or fix to work.
Please advise...

Thanks & regards

---

### Post by Studebaker Hoch on 2010-04-09
I haven't been able to get JACK to start in duplex mode (only in playback only mode), but I haven't tried recording directly with ALSA. I'll give it a try later on and see if it works.

---

### Post by warjowuch on 2010-04-09
Can you try switching back and forth, the choice of input? See if it works when you re-select your choice of input, after selecting another.
(e.g. when you've got 2 choices, and you want to record from inpout 1, switch to 2, and then back to one. See if it works then--> see if you can see the input-level-meter moving)

Greets!

---

### Post by bhagwad on 2010-04-09
Follow the instructions here - they worked for me:

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

### Post by MBHAKM on 2010-04-09
> **bhagwad said:**
> Follow the instructions here - they worked for me:

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

Thanks for all your reply. I already tried the above link. I had open up a bugs to the launchpad - [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/555978](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/555978).

There is only issue is something somewhere in the script, record goes to silent. I don't know where none of the developer helps.

If anybody came across any resolution, please share it in this thread.

Thanks & regards
AK

---

### Post by MBHAKM on 2010-04-09
> **MBHAKM said:**
> Thanks for all your reply. I already tried the above link. I had open up a bugs to the launchpad - [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/555978](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/555978).

There is only issue is something somewhere in the script, record goes to silent. I don't know where none of the developer helps.

If anybody came across any resolution, please share it in this thread.

Thanks & regards
AK

I would like to add one more thing. If I select Hardware Profile = Analog Stereo output and Output Connector = Analog Speakers / Analog Headphone from Sound Preferences, I can do sound recorder with playing music. But I cannot record my own voice when I select Hardware Profile = Analog Stereo output and Output Connector =  Analog Speakers / Analog Headphone from Sound Preferences . or neither via Hardware Profile = Analog Stereo Duplex..

Please advise is there any way we can solve to  record my own voice.

---

### Post by MBHAKM on 2010-04-09
> **MBHAKM said:**
> I would like to add one more thing. If I select Hardware Profile = Analog Stereo output and Output Connector = Analog Speakers / Analog Headphone from Sound Preferences, I can do sound recorder with playing music. But I cannot record my own voice when I select Hardware Profile = Analog Stereo output and Output Connector =  Analog Speakers / Analog Headphone from Sound Preferences . or neither via Hardware Profile = Analog Stereo Duplex..

Please advise is there any way we can solve to  record my own voice.

Here is my alsa-info.sh information:

                 By running wget -O ~/Desktop/alsa-info.sh  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)  && bash ~/Desktop/alsa-info.sh from terminal window.
 My ALSA information is located at
 [http://www.alsa-project.org/db/?f=a0e206c71f68386430efdab4b32c668ad1dd14a2](http://www.alsa-project.org/db/?f=a0e206c71f68386430efdab4b32c668ad1dd14a2).


Please advise if u found anything...

---

### Post by MBHAKM on 2010-04-10
> **MBHAKM said:**
> Here is my alsa-info.sh information:

                 By running wget -O ~/Desktop/alsa-info.sh  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)  && bash ~/Desktop/alsa-info.sh from terminal window.
 My ALSA information is located at
 [http://www.alsa-project.org/db/?f=a0e206c71f68386430efdab4b32c668ad1dd14a2](http://www.alsa-project.org/db/?f=a0e206c71f68386430efdab4b32c668ad1dd14a2).


Please advise if u found anything...

After research, added options snd-hda-intel model=auto in /etc/modprobe.d/alsa-base.conf file at my dell machine. Then Reboot. My sound gone i.e no sound. But I can see Microphone1 on my input connector from Sound Preferences.

Any idea how to get my sound back with snd-hda-intel model=auto.

---

### Post by cariboo on 2010-04-10
Did you try:

```
pulseaudio -k
```

Also can you revert back to the default settings, from the backups you made before making any changes?

---

### Post by MBHAKM on 2010-04-10
> **cariboo907 said:**
> Did you try:

```
pulseaudio -k
```Also can you revert back to the default settings, from the backups you made before making any changes?

I try pulseaudio -k but not worked out. if I removed options snd-hda-intel model=auto in /etc/modprobe.d/alsa-base.conf, the sound work but not sound recording.

---

