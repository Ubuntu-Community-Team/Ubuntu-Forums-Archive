---
title: "Sound Crackles after Hardy Heron Upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by DocHolliday2006 on 2008-04-26
I'm usually playing music on rhythmbox in the background as I'm browsing the web, doing work, etc. 

After the upgrade, I noticed that whenever I'm switching between open windows/firefox/Open Office/ etc, the music starts to crackle and skip. 

Is this because of the new system that manages how the processor manages tasks?

I consider this to be really annoying, and a real detractor to the otherwise awesome quality of Hardy Heron. The GUI looks fantastic and everything else runs smoothly, though I haven't played any games yet to see if there will be problems with that.

What can I do about this? Thoughts?

Thanks.

---

### Post by DocHolliday2006 on 2008-04-26
Where do I go with this bug to report it? I'm not getting responses so I'm assuming I need to officially log it somewhere.

Thanks.

---

### Post by alkamid on 2008-04-27
I'm having the same issue. I upgraded to Ubuntu 8.04 Hardy Heron on Friday. I've tried both Rhythmbox and Exaile - it seems it doesn't depend on music player.

---

### Post by Peter09 on 2008-04-27
I have found that the default levels of source found in PulseAudio are often set at 100%. This results in clipping of the signal. You will need to look in the depths of the Soundmanager to find it.

At present PulseAudio is a maze which is difficult to navigate.

PC

---

### Post by alkamid on 2008-04-27
> **Peter09 said:**
> I have found that the default levels of source found in PulseAudio are often set at 100%. 

I've tried to change System -> Preferences -> Sound -> Music and Movies to ALSA but it didn't help.

---

### Post by alkamid on 2008-04-27
I partly solved the problem: I changed all the values in Prefs -> Sounds to ALSA. It seems that there's something wrong with the new PulseAudio.

---

### Post by DocHolliday2006 on 2008-04-27
Is the Ubuntu team aware of this? Should I report it?


> **alkamid said:**
> I partly solved the problem: I changed all the values in Prefs -> Sounds to ALSA. It seems that there's something wrong with the new PulseAudio.

---

### Post by Smaskens on 2008-04-27
I solved this problem with Pulse Audio. I have Sound Blaster Audigy and now at least Urban Terror sounds are ok.

System -> Preferences -> Sounds -> Pulse Audio

---

### Post by objem on 2008-04-27
I had the same problem since upgrading to Hardy. If I load several pages in firefox at the same time, audio becomes choppy and skips. 

Managed to fix it by changing all audio output to ALSA. System->Prefs->Sound

---

### Post by kunami on 2008-04-27
My problem's different. Now all my sound looks like it's coming out of a guitar amp with loads of distortion. I've already tried changing to ALSA and PulseAudio without any luck.

---

### Post by kunami on 2008-04-27
Nevermind. Changing the PCM volume solved it. Changed it to the max again, too. It's as though it was at 150% or something. Weird.

---

### Post by psyke83 on 2008-04-27
Please see my post here for a possible solution to skipping audio: [http://ubuntuforums.org/showpost.php?p=4816308&postcount=6](http://ubuntuforums.org/showpost.php?p=4816308&postcount=6)

---

### Post by Mad-Halfling on 2008-05-02
Just an expansion (for newer users who might not know where all the settings are) of Kunami's solution:-

Right-click the volume icon and select [Open Volume Control] then reduce the level of the PCM volume, play a bit of music, this ma have fixed the quality problem, you can then put the PCM back to it's original value (mine was at max) and the quality will still be ok - I'm guessing there is an initial calibration problem with the volume control that's causing the PCM to be way off the scale to start with, but changing it resets it and corrects the problem

---

### Post by sir_woland on 2008-05-05
Same issue here. After upgrading to Hardy, just about anything and everything from closing a tab in a web browser to switching workspaces to swapping between applications tends to interfere with audio playback, causing snaps and crackles. I use Amarok via ALSA mainly, but other programs aren't immune to this either.

Everything was fine and dandy with Gutsy, but now suddenly this is driving me nuts.

---

### Post by IraqiMousl on 2008-05-05
thanks man,,, u solved my problem

---

### Post by diimaan on 2008-05-19
if still facing teh distorted/crackled/rattled sound...

there is a smart way around...

install 
audacious for audio and 
xine for video...

change the output plugin to alsa in audacious and 
in xine change the audio driver to alsa instead of automatic...

if you open the audacious player you can notice the reduced volume instead of boosted one... but with clear quality...

please let me know if it helps... :)

cheers...

---

### Post by Wehrmacht on 2008-05-24
I've changed System -> Preferences -> Sound -> Music and Movies to ALSA and it seemed to cure my ails.

Everytime i would minimize or move around windows, or start a new application my music would clip, and crackle.

Changing these settings to ALSA seems to have stifled all that nonsense.

AMD 64 3000+ on SOLtek 939 board.  2 gigs ram, Ubuntu 8.04.

---

### Post by OpIvy on 2008-06-03
> **Mad-Halfling said:**
> Just an expansion (for newer users who might not know where all the settings are) of Kunami's solution:-

Right-click the volume icon and select [Open Volume Control] then reduce the level of the PCM volume, play a bit of music, this ma have fixed the quality problem, you can then put the PCM back to it's original value (mine was at max) and the quality will still be ok - I'm guessing there is an initial calibration problem with the volume control that's causing the PCM to be way off the scale to start with, but changing it resets it and corrects the problem

Just wanted to say that this fixed my problem immediatly.  I was getting a lot of crackling and popping, but now its crystal clear.  So if you are having similar problems start here.

---

### Post by sir_woland on 2008-06-12
> **sir_woland said:**
> Same issue here. After upgrading to Hardy, just about anything and everything from closing a tab in a web browser to switching workspaces to swapping between applications tends to interfere with audio playback, causing snaps and crackles. I use Amarok via ALSA mainly, but other programs aren't immune to this either.

Everything was fine and dandy with Gutsy, but now suddenly this is driving me nuts.

This issue still remains even after a few kernel updates. Any sudden CPU intensive action causes transient skips and stutters in sound playback. I haven't got the faintest idea what this is about, it began instantly after Gutsy -> Hardy transition.

---

### Post by Roti78 on 2008-07-15
Hi!

 My problem solved by adding myself to the pulse-rt group by entering:

```
sudo usermod -a -G pulse-rt $USER 
``` 

Afterthat: log out and log in.

My soundcard:

```
$lspci | grep audio

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

```

Roti

---

### Post by flakjack47 on 2008-11-15
Tried adjusting the pcm volume, helped a little but still some crackling. 

Switched all the audio to ALSA from pulse audio, seemed to reduce it but not eliminate it - using audacious for audio, and vlc for video. 

Then found this tip on another forum and it seems to have sorted it out:

You need to install &#8220;libflashsupport&#8221; using synaptic or enter this in a terminal

    sudo apt-get install libflashsupport

I don't know why this worked as it is a flash related app by the look of things. 

Really surprised there were issues like this with Ubuntu. Sadly I've had to reimpose windows xp onto my pc as the secondary dual boot os. Us Ubuntu newbs need some kind of backup. 

Still prefer Ubuntu way more than XP, can't wait til they sort these minor problems out.

---

