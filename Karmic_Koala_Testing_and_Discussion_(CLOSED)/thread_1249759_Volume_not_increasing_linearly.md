---
title: "Volume not increasing linearly"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-08-25
Try as I might, I've played with all the volume controls and can't get my volume control working properly following an upgrade to 9.10. It seems that it cuts out and I get silence at 25-30%, and then it increases from there to 100%. It should first cut out at 0%, not 30%...

---

### Post by crimsun on 2009-08-25
> **Enigmatic said:**
> Try as I might, I've played with all the volume controls and can't get my volume control working properly following an upgrade to 9.10. It seems that it cuts out and I get silence at 25-30%, and then it increases from there to 100%. It should first cut out at 0%, not 30%...

Please use "ubuntu-bug linux". Title your bug report appropriately with respect to the expected behaviour of your volume adjustment, please.

---

### Post by BwackNinja on 2009-08-25
I'd consider that part of: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948) because its the new mixer logic doing that.

---

### Post by crimsun on 2009-08-25
> **BwackNinja said:**
> I'd consider that part of: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948) because its the new mixer logic doing that.

No, the symptom points to the driver (linux).

---

### Post by BwackNinja on 2009-08-26
> **crimsun said:**
> No, the symptom points to the driver (linux).

I'd have to disagree with that, unless that bug would be blamed on driver issues as well. The new mixer logic in pulseaudio will not move the master volume slider until pcm, lfe, center, surround/rear are all up to 0 dB (if they exist), and this can easily occur at ~30% depending on your multichannel setup. Its easy to see while increasing the volume and watching the changes in alsamixer.

---

### Post by crimsun on 2009-08-26
> **BwackNinja said:**
> I'd have to disagree with that, unless that bug would be blamed on driver issues as well. The new mixer logic in pulseaudio will not move the master volume slider until pcm, lfe, center, surround/rear are all up to 0 dB (if they exist), and this can easily occur at ~30% depending on your multichannel setup. Its easy to see while increasing the volume and watching the changes in alsamixer.

PA can exacerbate driver issues. It's part of the joy of debugging audio in Linux.

---

### Post by Enigmatic on 2009-08-26
So, what should I do then? :) That bug doesn't completely describe my issue, as I'm not getting sound until 30% volume, then it ramps linearly to 100% as expected. I've tried playing with the volume controls in alsamixer but it doesn't seem to help. I have an Audigy 2 ZS card.

---

### Post by BwackNinja on 2009-08-26
> **Enigmatic said:**
> So, what should I do then? :) That bug doesn't completely describe my issue, as I'm not getting sound until 30% volume, then it ramps linearly to 100% as expected. I've tried playing with the volume controls in alsamixer but it doesn't seem to help. I have an Audigy 2 ZS card.

You should follow crimsun's suggestion and file a bug, but if you really need a workaround and have a 2 channel setup, backup and edit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf and /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common.

===================================
EDIT:

First I'd suggest checking in alsamixer if when you start getting sound is when the Master control starts going up
===================================


In analog-output.conf in each element after [Element Front] change "volume = merge" to "volume = ignore" and in analog-output.conf.common for [Element PCM] change "volume = merge" to "volume = zero".

And then have pulseaudio restart by running "pulseaudio -k" in a terminal.

If there is still a gap between 0% and when you get sound then you probably have a Front control in your alsamixer. In that case replace "volume = merge" in analog-output.conf under [Element Front] to "volume = zero" and then run "pulseaudio -k" again. If this doesn't work for you, just revert to the backups you've made.

As it says in the directions in analog-output.conf.common, "volume = merge" makes the element controlled by pulseaudio with the new mixer logic, "volume = ignore" makes it ignored by pulseaudio's mixer logic, and "volume = zero" puts the volume at 0 dB which is the highest all my volume controls go except for PCM, in which case it is the highest volume without distortion.

---

### Post by BwackNinja on 2009-08-26
> **crimsun said:**
> PA can exacerbate driver issues. It's part of the joy of debugging audio in Linux.

I generally agree with that sentiment, however in [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/016992.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/016992.html) before lennart decides to handle multichannel audio controls like is done now in pulseaudio, he was contemplating having changes made to alsa, and one of the key questions asked was:

"First of all, on some cards 'Master' seems not to have any effect on the actual analog output, only 'Front' and friends do. Is this a bug or intended behaviour? Can I assume that 'Master' and 'Front' are always independant?"

with the response being:

"It's an old feature.  AC97 spec gives the "master" volume control only for front channels.  Thus, old boards with AC97 may inherit this policy.  (The problem of emu10k1 is partly this.)"

and clarification saying:

"If both [front and master] exist, then they should be dependent, and Master should be really Master. If Front doesn't exist but only Master, the surrounds could be independent from master."

And that gave rise to the configuration files in /usr/share/pulseaudio/alsa-mixer/ and the new mixer logic to read those files and go with it. The inconsistency between the role of 'Master' depending on hardware and drivers and how it is set as controlling all in analog-output.conf coupled with how the new mixer logic only controls one element at a time causes this kind of weird behavior, as well as how the channel configuration does not change which elements are controlled unless another configuration file is specified in /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf for that specific output.

I hope I don't just seem argumentative, I've looked through every source of information I could find about this especially because I have a 4.0 multichannel setup with an AC97 card that I can't get pulseaudio to handle correctly and I've tested through all settings I could come up with to get an understanding of how this works, but its a bit over my head to work around this one.

---

### Post by BwackNinja on 2009-08-28
Badump bump

Assuming this issue is how I think it is, I want this resolved before I won't be using a surround sound setup for a few days - actually listening and using alsamixer is more reliable than only using alsamixer because pulseaudio will scale the stream's audio.

---

### Post by Enigmatic on 2009-09-05
> **BwackNinja said:**
> 

===================================
EDIT:

First I'd suggest checking in alsamixer if when you start getting sound is when the Master control starts going up
===================================



I checked alsamixer and although the volume in the notification window shows 30% or 50% etc, if I move below that point the master volume goes to zero in alsamixer. Also, if I move to the point where sound actually starts playing (past 0% on the master channel per alsamixer) the surround sound channels automatically peg to 100%.

---

### Post by BwackNinja on 2009-09-07
> **Enigmatic said:**
> I checked alsamixer and although the volume in the notification window shows 30% or 50% etc, if I move below that point the master volume goes to zero in alsamixer. Also, if I move to the point where sound actually starts playing (past 0% on the master channel per alsamixer) the surround sound channels automatically peg to 100%.

Yup, just follow the instructions and everything should be fine. It'd also be nice if you added to the bug report I mentioned.

Here's hoping that you get this soon and that this problem isn't just overlooked because it is affecting a lot of people.

---

### Post by Enigmatic on 2009-09-09
> **BwackNinja said:**
> Yup, just follow the instructions and everything should be fine. It'd also be nice if you added to the bug report I mentioned.

Here's hoping that you get this soon and that this problem isn't just overlooked because it is affecting a lot of people.


I added my comments to the bug report. I'm assuming you're referring to following the steps here? ([http://ubuntuforums.org/showpost.php?p=7849753&postcount=8](http://ubuntuforums.org/showpost.php?p=7849753&postcount=8)) I have also noticed that for Flash audio, I need about 50% of volume to get any output, compared to 30% for an audio app. Not sure how this relates.

---

### Post by BwackNinja on 2009-09-10
> **Enigmatic said:**
> I added my comments to the bug report. I'm assuming you're referring to following the steps here? ([http://ubuntuforums.org/showpost.php?p=7849753&postcount=8](http://ubuntuforums.org/showpost.php?p=7849753&postcount=8)) I have also noticed that for Flash audio, I need about 50% of volume to get any output, compared to 30% for an audio app. Not sure how this relates.

Yup, those instructions. It being different with flash may be because flash uses the alsa plugin for pulseaudio which might scales the audio extra or differently than native pulseaudio streams. That's my best guess. It might be fixed in alsa 1.0.21.

---

