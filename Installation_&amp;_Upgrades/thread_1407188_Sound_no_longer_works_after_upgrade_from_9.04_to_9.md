---
title: "Sound no longer works after upgrade from 9.04 to 9.10"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by jasonkoberg on 2010-02-15
I recently upgraded from 9.04 to 9.10 and the sound on my machine no longer works.  I was previously using the OSS for sound.  I'd like the sound solution that requires the minimal effort and I don't necessarily need to run OSS again.  Ubuntu is installed on a Dell Optiplex 960.  

```

aplay -l 

```results in:

```

aplay: device_list:223: no soundcards found...

``````

lspci -v 

```Shows this as my audio device:

```

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 0276
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fdfdc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```Any suggestions as to how to get this working?

Thanks,
Jason

---

### Post by shanix on 2010-02-15
someone mention to check the hardware driver and remove the entry "modem" and reboot. Can you try that?

---

### Post by arizonalarry2 on 2010-02-15
I installed 9.10 and everything worked fine. Yesterday the sound stopped working ( conspicuously after an update ). Any ideas what happened?

---

### Post by shanix on 2010-02-15
@arizonalarry2, are you using the same card as jasonkoberg?? Please run aplay -l & lspci -vvnn | grep Audio to confirm that.

---

### Post by ericrichards420 on 2010-02-15
This happens to my computer too. just goto system>preferences>sound from there ajust the hardware settings. I always start a mp3 player and just ajust the seetings untill I get it to work.

---

### Post by arizonalarry2 on 2010-02-15
Oh wait, I found it... I went to System\Preferences\Sound and the mute button was checked in the dialog box. I know I didn't do it... how did it check itself?

---

### Post by ahso4271 on 2010-02-15
Sound is a mess....at least on OpenSuse...hope this gets fixed in the next version. On openSuse I had to use pulseaudio and disalbe alsa!

---

### Post by jasonkoberg on 2010-02-15
My System->Preferences->Sound shows nothing in the hardware tab.  If I have an application play sound it will display this application in the "Application" tab but I still hear nothing...

---

### Post by shanix on 2010-02-15
@jasonkoberg, can you check under System> Administration> hardware drivers and see if there are any entry called modem that is being installed?

---

### Post by jasonkoberg on 2010-02-15
There is nothing under hardware drivers that specifies "modem"

---

### Post by shanix on 2010-02-15
run the command "group" and see which group you are in. Maybe you are just not in the right group.

---

### Post by jasonkoberg on 2010-02-17
It appears I am in the right groups.  Does anyone have any other suggestions?  I feel like it should find my device via aplay -l but it doesn't...

---

### Post by jasonkoberg on 2010-02-19
bump

---

### Post by jasonkoberg on 2010-02-22
Anyone else have any ideas..?

---

### Post by jasonkoberg on 2010-02-26
Anyone?  I have went through countless forums and tutorials and I have had no luck.  

Some extra information:

ALSA does not seem to be recognized.  I.e. /proc/asound doesn't exist.  When playing music, Preferences->Sound shows that an application is indeed playing sound.  My device still is not detected but it is listed in "lspci"

Please help

---

### Post by jasonkoberg on 2010-03-08
For those with the same trouble, this thread fixed my problem:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

