---
title: "Audio stuttering with last Jaunty updates"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by psychok9 on 2009-03-07
I've audio stuttering with last alsa (i've killed pulseaudio without solve the stuttering problem) and CMI8788 audio card.

In the past, with pulseaudio and Wine I've problems, fixed with a kill of pulseaudio...
Today the problem is with Alsa and not pulseaudio :o (fresh install)

Tried with VLC, SMPlayer and audio test from gnome audio panel.

---

### Post by eyelessfade on 2009-03-07
you are sure pulseaudio isn't running. I've found it hard to kill these days. Apparently it spawns when an app asks for it. The only method I have actually got it to stay away is to disconnect it in the pulse management, killall instance of it, and run something with oss output while trying to use pulse. It then goes to a dev/null output and alsa works without running it trough pulse..


pew!

---

### Post by psychok9 on 2009-03-07
Yeah
With a play of Oss output... now alsa work correctly... now how can I fix pulse or disable it without break my Ubuntu?

---

### Post by geoff123 on 2009-03-09
I also have a crackling and stuttering problem. Its definitely pulse as it works fine if I do "pasuspender qjackctl" and then run audio programs that use jack.  

Intrepid worked fine once i changed the pulse config file, but no luck with jaunty.  I just updgraded to jaunty over the weekend so don't know if how long this has been around.

I can minimize it by using the "tsched=0" option and a self compiled kernel (stock jaunty kernel with options set for 1000HZ timer, Pentium-4, and low-latency desktop). 

Looking around on launchpad there appear to be a number of bugs related to stuttering or crackling, but nothing definitive.  

I'm going mess around and try and narrow down the problem a little more and then report a bug on launchpad.  I suggest you do the same to try and help get this fixed. 

Geoff

---

### Post by markbuntu on 2009-03-09
There is a long discussion about this on the pulseaudio mailing list, Feb22-28. It is a buffer filling problem between the kernel, alsa buffer, and the glitch free pulseaudio. crimsun is aware of this and hopes to have it all ironed out by Alpha 6.

---

### Post by nyarnon on 2009-03-09
In fact I think he's already very far in achieving this goal best thing is top add his ppa and update with that.

---

### Post by gnomeuser on 2009-03-09
I have a highly disturbing popping sound that occures every second or so as well as crackling.

---

### Post by Kevbert on 2009-03-09
To stop the stuttering sound you could try this in terminal
```
alsamixer -Dhw
```
You may find some of the settings are in the red zone. Reduce the levels and that should help.

---

### Post by psychok9 on 2009-03-09
> **Kevbert said:**
> To stop the stuttering sound you could try this in terminal
```
alsamixer -Dhw
```
You may find some of the settings are in the red zone. Reduce the levels and that should help.

Is not a volume problem that can make "sound stuttering", the problem is different and the pulseaudio driver have often this problems :(
High volume can cause distortions and I know good, because my speaker system is not the best on the market (Logitech Z-680), and with high amplified output of my X-Meridian 7.1... over the 50% can cause sound distortions :)

---

### Post by babyhuey on 2009-03-09
Perhaps try installing the newer pulseaudio packages. 
See this thread: [http://ubuntuforums.org/showthread.php?t=1066212]("http://ubuntuforums.org/showthread.php?t=1066212")

---

### Post by autocrosser on 2009-03-09
Take a look at this thread & read post#43: [http://ubuntuforums.org/showthread.php?t=1066212&page=5](http://ubuntuforums.org/showthread.php?t=1066212&page=5)

The various noise(s) are from kernel latency......[I]Lennart hits it right on the head.......

I'm using the 15 testing PPA & it is much better.
[/I]

---

### Post by Vaun on 2009-03-09
Aye.

PA 0.9.15 working much better for me too.  I've been testing it for the past few days and it has been flawless.

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

```
lsmod | grep snd
snd_hda_intel         556980  5 
```

---

### Post by markbuntu on 2009-03-10
Just got, finally, some 242 updates and sound is working much better. I think part of the problem was trying to use the glitch-free which crimsun now says is abandoned for jaunty due to the kernel issues. Hopefully they can get this kernel thing straightened out for koala, or alsa could abandon its 64k fixed buffer for something more flexible.

---

### Post by ravindran.k on 2009-04-19
I also have the same issue. Mother board : Intel DG33TL
 >lspci
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
 >lsmod 
 snd_hda_intel         424468  5
snd_pcm_oss            45856  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         17160  2 snd_hda_intel,snd_pcm
snd_hwdep              15236  1 snd_hda_intel
snd_seq_dummy          10884  0
snd_seq_oss            39296  0
snd_seq_midi           14240  0
snd_rawmidi            29344  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29320  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    65316  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 Also, I find this in my logs:
[   41.004849] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
 The Audio stutters whenever volume is changed (inc/dec)
 Also, the Sound Volume control Program behaves sluggishly..
 It as working fine prior to Jaunty upgrade.



        


>alsamixer -Dhw

I tried this.. It still stutters..

I have posted info here.. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429)

---

### Post by KhaaL on 2009-04-19
I also have the same problem as the above poster. Actually my PA hangs quite often aswell... my alsa info is located here: [http://www.alsa-project.org/db/?f=e90efba2cb85f1f245827db14c2ee495678605f4](http://www.alsa-project.org/db/?f=e90efba2cb85f1f245827db14c2ee495678605f4)

Is there a way to replace PA with alsa once for all? when I have PA disabled, apps behave like OSS, that is the soundcard is not shared between them.

---

### Post by crimsun on 2009-04-19
> **ravindran.k said:**
> I also have the same issue... It still stutters..


Have you tried some combination of my crimsun3 test kernel (see [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)) and changing the cpu governor?

---

### Post by KhaaL on 2009-04-19
> **crimsun said:**
> Have you tried some combination of my crimsun3 test kernel (see [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)) and changing the cpu governor?

Could you provide test kernel for the new .30 release? I'm affected by a filesystem bug which is supposedly to be fixed in .30. Also, how is cpu governor changed?

---

