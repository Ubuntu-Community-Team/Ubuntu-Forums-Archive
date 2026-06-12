---
title: "Kubuntu alpha 3 no sound?"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autumnraine on 2010-02-28
I just did a fresh install of the Kubuntu Lynx third alpha and I'm having no luck getting the audio working. I know the system works fine because it plays audio in Ubuntu 9.10 fine and at least potentially worked in Kubuntu 9.10 (before I reinstalled I was able to get either the music apps or the video apps to work, depending on whether pulseaudio was installed). However I'm getting no sound in any applications. I've tried all the obvious steps and the ones I've found elsewhere, like making sure it's not muted, downloading the alsa-gnome gui to enable the relevant ports since I'm outputting audio over HDMI, and making sure all the seemingly necessary Phonon packages are installed, including libxine1-ffmpeg. Currently I have alsa but no pulseaudio installed (except the pulse library which is included as a part of Kubuntu). I read somewhere on these forums that Phonon doesn't need pulseaudio to work and is supposed to be a KDE alternative to it, not sure whether that's true. I've already updated everything via sudo apt-get upgrade.

For anyone else running Kubuntu, is your audio working and if so did it work to begin with? If not what needs to be installed to get it working? 

I'd really appreciate whatever help I can get. 

(BTW I'm using 10.04 because on my system it seemed to be as stable as Karmic Kubuntu, and includes the packages I need like Nouveau. Other than the audio problem I'm VERY pleased with it!)

---

### Post by autumnraine on 2010-02-28
So I've established that the sound plays alright (though scratchy) over analog output, but not HDMI. Why? Also, I seem to only have libasound 1.0.22.-0ubuntu4 - how do I get the most recent version? Enable different repositories?

---

### Post by alexandari on 2010-02-28
Removing Pulseaudio always does the trick. You might try that and also,install alsa.

---

### Post by autumnraine on 2010-02-28
pulseaudio's not installed, alsa is. I'm going to download the ubuntu-desktop to see if the problem persists in Gnome.

---

### Post by autumnraine on 2010-02-28
Well the HDMI audio doesn't work in Gnome either, so there must be something wrong with the basic setup in 10.04. I hope this gets fixed soon, because otherwise everythings working pretty great! 

Anyone have any suggestions? Do other people have audio working over HDMI?

---

### Post by Yeeha on 2010-03-01
Have you tryed messing with sound options? I couldnt hear flash movies in browser before raising pcm lever and couldnt use microfon in teamspeak 3 before raising digital lever in alsamixer.

---

### Post by autumnraine on 2010-03-01
Yes I've tried that. All the volume dials in alsamixer and gnome-alsamixer are as high as they go and none are muted.

---

