---
title: "PulseAudio can't see mic2?"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-09-26
Hi

I have a web cam with an integral mic. My stable Jaunty system sees it as mic2 and it all works nicely.

In Karmic I can't seem to select mic2 and hence the web cam mic is not working. In fact no input devices are shown to select from in the 'Volume Control' window, 'Input Devices' tab.

Am I missing something really simple here?

---

### Post by andresmh on 2009-09-26
I've had the same problem since Alpha 1. I submitted it as a bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819)

---

### Post by bwallum on 2009-09-26
Done some more work and discovered that under 'Sound Preferences' and the Hardware tab you need to select an appropriate Profile with the drop down menu. I went for Analog Stereo Duplex (it had defaulted to Analog Stereo Output) and then both mic1 and mic2 appeared in the Input tab. I choose Analog Microphone/Microphone 2 for my web cam mic and it worked.

I did a reboot upon finding Sound Recorder playing up and all now behaves as expected. This is for Karmic and it all looks a lot different from Jaunty.

If you have the Sound Preferences window open and then start Sound Recorder you get this false error message:

"Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu"

Close the Sound Preferences window and Sound Recorder opens up ok.

Choosing the Profile is also available in PulseAudio 'Volume Control' window under the Configuration tab.  

So we still have some adverse 'features' but at least I could get it working. Sound has always been tricky with Ubuntu and I have never really understood why... inconsistency?

---

### Post by andresmh on 2009-09-26
Mine already had Analog Stereo Duplex as default and it still only shows one of the microphones :(

---

### Post by dadedo123 on 2009-09-26
The audio manager didn't detect the internal mic in my netbook.

---

### Post by jonick on 2009-10-02
> **dadedo123 said:**
> The audio manager didn't detect the internal mic in my netbook.

Same here, It used to be detected in Jaunty, but in Apha 5 & 6 the internal mic was not available in sound preferences, or by changing the hardware options. It was, however available by selecting it in Alsamixer,but I couldn't make the changes persistant.

My work around was to install gnome alsamixer, and run that every boot up to select the internal mic.

Something has changed in the Beta, Alsamixer no longer detects the internal mic at all. the sound card is an intel 8280 ??

Regards,

Jonick.

---

