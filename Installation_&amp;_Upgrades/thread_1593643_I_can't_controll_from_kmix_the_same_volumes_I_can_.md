---
title: "I can't controll from kmix the same volumes I can controll with Alasamixer"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by danlo8600 on 2010-10-11
Hello to all, after the intallation of Kubuntu 10.10 I'have a problem with kmix, this is the immages of my kmix and my alsamixer:

**Kmix:**
[IMG]http://img510.imageshack.us/img510/9191/mixu.jpg[/IMG]

**Alsa:**
[IMG]http://img176.imageshack.us/img176/1766/alsa.jpg[/IMG]

I can't controll from kmix the same volumes I can controll with Alasamixer.

This is a new installation. I'have a Dell Studio 1555 in this is my audio card:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

This problem start during the RC period, when kubuntu 10.10 was in beta I don't have this issue.

What can I do?

Sorry for my bad english

Thank you all

---

### Post by seeker5528 on 2010-10-11
You have to uninstall or disable pulseaudio, if you want kmix to show the alsa stuff.

I have not actually poked around to find out how you would disable pulseaudio without uninstalling it, but it's been said elsewhere there is a way. If you want to uninstall, just uninstall any pulseaudio* packages, the libpulse* packages you want to keep. You might have to turn off the option to treat recommends as depends while uninstalling if it seems like an excessive number of packages will be removed. 

Later, Seeker

---

### Post by danlo8600 on 2010-10-11
Thanks for your reply.
This problem is generate from a bad packaging of the Kubuntu team, or some new version of pulse?

The strange thing is that until three weeks ago it worked perfectly without eliminating pulse.

---

### Post by Zorael on 2010-10-12
I'm not sure I understand.

Pulse, per design, hides the multitude of ALSA channels (and their volume sliders) and instead imposes its own single volume slider, and also one per application. This is primarily done to reduce confusion, as there's little point in most usecases to have one Master, one PCM and one Front all affecting the same volume. So I'd think that what you're seeing is by design.

For some more fine-grained control of Pulse, you can install the GTK Pulse volume manager, **pavucontrol**. KMix only seems to have barebone Pulse support so far, so the GTK tools make a nice complement. There's also **paprefs** for changing advanced settings.

---

### Post by danlo8600 on 2010-10-12
I'm not entirely sure that kmix is working well, for example, now I can not adjust the volume for individual headphone outputs, or disable the internal microphone to use the external one. Both in the Beta, which in Kubuntu 10.04, kmix showed me everything.
I also installed Ubuntu on a secondary partition and there are no problems, I can adjust many more volumes.
The thing I noticed is that, on kubuntu xine basic use the ATI HDMI audio rather than integrated into the motherboard. On first start, I had no output in the speakers so I had to increase as the priority. What's even more strange is that in the list (see photo) is not pulseaudio:


[IMG]http://img63.imageshack.us/img63/332/kmix4.jpg[/IMG]

---

### Post by Zorael on 2010-10-12
> **danlo8600 said:**
> I'm not entirely sure that kmix is working well, for example, now I can not adjust the volume for individual headphone outputs, or disable the internal microphone to use the external one.

I think this is expected behavior. KMix still doesn't allow for as deep management of Pulse as the real Pulse GTK tools do. KMix is currently supposed to look like the screenshot you posted in the top post. It only allows for very basic volume changes. PulseAudio integration still needs work. I'm not sure how it could have looked any different in 10.10 beta.

Install **pavucontrol** and use it to set your microphone settings.

[img]http://ubuntuforums.org/attachment.php?attachmentid=172062&d=1286876084[/img]

---

### Post by danlo8600 on 2010-10-12
My old kmix is most similar to this:

[IMG]http://janbartspang.net/wp-content/uploads/2010/07/kmix.jpg[/IMG]

I have this in Kubuntu 10.04 with KDE 4.5.1 and with Kubuntu 10.10 beta. The problem began after the arrival of some updates.

---

### Post by Zorael on 2010-10-12
That is the volume channels that ALSA makes available using your soundcard driver.

Again, PulseAudio acts as an abstracting layer ontop of ALSA, imposing a single output and input volume slider per soundcard, as well as the ability to change the volumes of individual applications playing or recording sound. It hides the rest.

So the screenshot in your original post shows expected behavior. Something likely went wrong with your PulseAudio installation in 10.10 beta, and it never actually established itself as default. It wasn't default in 10.04.

KMix will look like that again if you remove PulseAudio.

---

### Post by danlo8600 on 2010-10-12
Ok thank you so much, now i try to remove pulse :D but i'm not realy happy for this solution ;)

---

