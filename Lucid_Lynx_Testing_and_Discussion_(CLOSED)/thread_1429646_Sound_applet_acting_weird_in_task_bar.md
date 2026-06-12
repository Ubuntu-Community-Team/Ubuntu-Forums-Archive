---
title: "Sound applet acting weird in task bar"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ndefontenay on 2010-03-14
Hi.

Laptop Dell Studio 17.
Historically on 9.10 the sound didn't work at all and I had to add an option as follow:
options snd-hda-intel model=dell-m6 

This time the sound worked but not the headset. I used the same option and it all worked... Except it seems my sound controller applet in the task bar is acting weird.

It shows sound at its lowest settings (sound icon with --- next to it), yet when I click on it I got the sound scroll bar to its maximum.
If I just touch that scroll bar the icon will display the correct setting, only to go back to minimum later.

From time to time in an unpredictable way, I simply can't scroll the bar at all. When this happens, I'll have to choose "sound preferences" and modify the sound from there. Only then it will start working again...

I can't decide if it's because I added that extra option or if there's some bugs currently with pulseaudio.

Nico

---

### Post by tekstr1der on 2010-03-14
> **ndefontenay said:**
> ...It shows sound at its lowest settings (sound icon with --- next to it), yet when I click on it I got the sound scroll bar to its maximum.
If I just touch that scroll bar the icon will display the correct setting, only to go back to minimum later.


Yes. I filed the following in regards:

Bug #538583: indicator-sound volume level disappears
[https://bugs.launchpad.net/indicator-sound/+bug/538583](https://bugs.launchpad.net/indicator-sound/+bug/538583)

---

### Post by QwUo173Hy on 2010-03-14
Thanks for filing - I've 'me too'd it.

---

### Post by ndefontenay on 2010-03-14
metoo'ing it as well :)

Thanks.

---

### Post by tekstr1der on 2010-03-15
Someone beat me to it I guess. I duped my bug over to theirs:

[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/537977](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/537977)

Need to select "affects me" again.

---

### Post by QwUo173Hy on 2010-03-15
Nice catch. Don't forget folks that the new 'master' bug report doesn't inherit the 'me too' count from it's registered duplicates. Makes me wonder if the features just there to pacify us and stop mail noise.

---

### Post by zika on 2010-03-15
If I open Sound Properties and try to change balance to the left I get sound muted. Slider for balance and slider for volume are "glued" together... Balance can be changed only if sound is muted. If I try to get volume up, balance goes to center...

---

### Post by oryan_dunn on 2010-03-21
I have experienced a similar issue.  The applet icon shows the volume at 0, even though the slider when you click it is full.  However, I do not get any audio at all.  I can fix the audio, and get the applet to work correctly, by issuing the command "pulseaudio -k".  After that, things work just fine, until I reboot.  I have to issue that command after each boot.  I'm not sure if this is the same or different bug as what is reported in the bugs linked from this thread.

---

