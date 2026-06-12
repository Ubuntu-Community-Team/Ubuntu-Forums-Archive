---
title: "Karmic update -now no sound"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lindsay7 on 2009-10-12
I installed Karmic update and now I have no sound. What should I try to do?

---

### Post by qwerty800 on 2009-10-12
> **lindsay7 said:**
> I installed Karmic update and now I have no sound. What should I try to do?

I don't know, I don't have sound, Michael Terry don't have sound, the guy over there don't have sound...

Do you expect any kind of help if you don't give any information?

```
lspci|grep -i audio
```

---

### Post by lindsay7 on 2009-10-12
Results of entering code...

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by Rich_Roast on 2009-10-12
Personal experience has repeatedly shown searching around in volume control for muted devices can fix sound problems. There seem to be a variety of bugs which cause volume meters to set themselves to zero, including after updates.

---

### Post by emarkay on 2009-10-12
Yes, but if they go to "System > Preferences > Sound> Hardware" and fin there is nothing, and "output" is "Dummy"...

I just noticed this, too.  For my ATI machine I just dowmloaded the AC97 driver - this PC uses Realtek/Intel "HD Audio" drivers and if I can't figure it out natively, I will grab that driver set.

---

### Post by lindsay7 on 2009-10-12
yup, this is what I have too,

[ATTACH]131732[/ATTACH]

[ATTACH]131733[/ATTACH]

---

### Post by Ulsak on 2009-10-16
I find this output when grep:ed on my audio device. 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

But that does only appear on alsamixer command at terminal. However nothing show when trying the graphical tools ( as the volume control and the sound manager at System->Preferences->Sound.

Is there a modprobe workaround I could try?

---

### Post by PiotrekS on 2009-10-16
I have no sound too :( Sound modules are loaded but I hear only silence. Sound isn't muted in mixer.
I have tried to play some mp3s in Audacious and Rhytmbox but progress indicator show up for one second and then disappear and music isn't played.

---

### Post by dino99 on 2009-10-16
this happen to me a few days ago: i've deleted ~/.pulse and then sound come back again.

---

### Post by imaca on 2009-10-16
The Gnome Alsa mixer is no longer installed by default, instead there is a "sound preferences" panel which is pretty much useless.
I installed the gnome-alsa mixer and discovered everything is muted. Un-mute, wind up the volume and there is suddenly sound.

---

### Post by Ulsak on 2009-10-16
yes, I tried the removing of pulseaudio trick and I also found att that 
the command ```
alsamixer
``` had the correct soundcard detected. Nevertheless, no sound. 

This happened after I updated to the latest kernel. I also tried see what was going on in alsa.conf but I couldn't see anything obvious to do...

---

### Post by Ulsak on 2009-10-16
I found a solution ( can't recall where, maybe launchpad..:-k )

```
sudo alsa force-reload
```

---

### Post by rajeev1204 on 2009-10-16
Try using amixer instead of alsamixer.

---

### Post by Dernhelm on 2009-10-16
Yes! Thank you!

"sudo alsa force-reload" worked great for me. :) The sound is working beautifully.

---

### Post by qwerty800 on 2009-10-16
I know that there are some problems with the "AD Analog Devices" codec rigth now.

Check if it's not your case...

```
grep Codec /proc/asound/card0/codec*
```

If so, you may join us on [this bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/449665").

---

### Post by VMC on 2009-10-16
> **lindsay7 said:**
> Results of entering code...

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

There is a topic with [VIA]("http://ubuntuforums.org/showthread.php?t=1291507&highlight=sound") sound card trouble. Also search resulted with many hits. Try it.

Also on the hardware section Sound Preferences, you have nothing in there. You might want to check out why.

---

