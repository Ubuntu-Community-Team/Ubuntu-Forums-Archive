---
title: "ALSA: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alecjw on 2008-10-04
ALSA aint working. 
When i go to system>prefs>sound and test it, it throws the error "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource."
Simmilar message if i choose pulseaudio: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument"

OSS works fine

I'm a member of the "audio" group, and ive tried apt-get purging all of the sound-related packages and upgrading pulseaudio. Still nothing. Worked fine up until this afternoon. Happened before on intrepid, and I had to reinstall to fix it. Anyone got any other ideas?

---

### Post by alecjw on 2008-10-04
Edit: I've worked out how to fix it (only 2 mins after posting in the forums lol)
Run gstreamer-properties and change the output device
d'oh!

---

### Post by alecjw on 2008-10-04
Uhh sorry for the triple post but.... the fix i used only worked for the normal profile... How do I change it for other profiles eg music?


EDIT: seems to have fixed itself

---

### Post by jp_coll2003 on 2008-10-04
I had this exact problem a couple of days ago on my alpha 6 after my routine daily updates. Only the OSS option would work so I just reinstalled Hardy and done the Upgrade -d again. All is fine and the ALSA option is now default and working. Sorry that this isn't the ideal method but hey, I had everything backed up and was far the quickest way to fix things for me.

---

### Post by jonfenton on 2008-10-05
I got the same message when I upgraded to 8.10. I tried a number of suggestions but none worked. During this I noticed the file .asoundrc was missing from /home. I restored it from a backup and sound was fully restored.

---

### Post by ultra2k on 2008-10-06
i have this issue too,
running gstreamer-properties and change the output device dont fix the problem.
in the audio menu choosing alsa does not work




"pulseaudio -k; sleep 4; pulseaudio -vv"  fixes but after reboot of course is broke again.
how to fix permanently?

---

### Post by Tiftof on 2008-10-07
> **ultra2k said:**
> "pulseaudio -k; sleep 4; pulseaudio -vv"  fixes but after reboot of course is broke again.
how to fix permanently?

I'm having the same problem and that command gives me back sound after a reboot. Any more info on what this command does and what's wrong in the first place?

Thanks

---

### Post by psyke83 on 2008-10-07
> **alecjw said:**
> ALSA aint working. 
When i go to system>prefs>sound and test it, it throws the error "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource."
Simmilar message if i choose pulseaudio: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument"

OSS works fine

I'm a member of the "audio" group, and ive tried apt-get purging all of the sound-related packages and upgrading pulseaudio. Still nothing. Worked fine up until this afternoon. Happened before on intrepid, and I had to reinstall to fix it. Anyone got any other ideas?

The ALSA libraries have been patched to autodetect PulseAudio, and enable the PulseAudio ALSA plugins in the event that PulseAudio is running. 

What does this mean? Testing the ALSA GStreamer sink actually remaps to PulseAudio. As the Pulse GStreamer sink also does not work, it seems that your PulseAudio server is misconfigured.

You need to configure PulseAudio correctly. Look [here]("http://ubuntuforums.org/showthread.php?t=866965") to start.

---

