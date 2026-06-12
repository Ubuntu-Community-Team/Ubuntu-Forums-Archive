---
title: "Another sound problem (volume and balance)"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-08
Once the volume goes below about 15%, it goes silent. Not muted, just silent. Also, balance doesn't seem graduated. It's either left, center, or right. Pretty useless like that.

Work in progress?

---

### Post by phenest on 2009-08-08
I'm also finding the login window sound (the one before you select the user), seems rather loud. In fact, very loud considering that the volume is only set to about 15% once the desktop loads.

---

### Post by phenest on 2009-08-10
Bump

---

### Post by cheleb on 2009-08-10
Same problem here. And i think you have the same machine as i do. A DELL Precision M90, right?

I guess we should wait for the next pulseaudio update and see if that changes anything.

---

### Post by phenest on 2009-08-11
I'm still finding the sound muted after boot. And I can't play anything through the laptop speakers because, even at 15% volume, it's blaring out. I can use headphones ok.

I've just had a look at alsamixer, and it looks the the volume control wants PCM at 100% first, followed by LFE, followed by Master. This means that my LFE channel is at 100% before the master has started increasing. So, starting at 0% volume, the first increase in volume sets PCM at 98% and LFE at 48%, and Master at 0%. The second increase in volume sets PCM to 99%, LFE to 84%, and Master to 0%, the 3rd increase has PCM at 99%, LFE at 100% and Master at 6%. This is using a volume step of 5. So by the time the Master has started increasing, my LFE is already at 100%!

---

### Post by phenest on 2009-08-13
Interesting to note, that my observation of alsamixer does not happen with a fresh install of alpha 3. Alsamixer in alpha 3 behaves as expected.

---

### Post by BwackNinja on 2009-08-13
> **phenest said:**
> Interesting to note, that my observation of alsamixer does not happen with a fresh install of alpha 3. Alsamixer in alpha 3 behaves as expected.

I'm having the same sort of problems, are you saying that a fresh install works correctly but the upgraded one for some reason doesn't? If so, I might feel like doing a fresh install.

---

### Post by phenest on 2009-08-14
> **BwackNinja said:**
> I'm having the same sort of problems, are you saying that a fresh install works correctly but the upgraded one for some reason doesn't? If so, I might feel like doing a fresh install.

With a fresh install of alpha 3 is fine. An upgraded alpha 3 exhibits the weird behaviour. I've haven't tried alpha 4 although I'm expecting that to be the same as alpha 3 plus upgrade.

---

### Post by ghindo on 2009-08-15
I am experiencing similar behavior with my Dell Inspiron 1420n.  I've been running Karmic all the way since Jaunty, so I couldn't pin down when it started, exactly.  Is there a bug report open for this?

---

### Post by phenest on 2009-08-15
No bug report as yet. I can't decide whether this is an alsa or pulse problem.

---

### Post by phenest on 2009-08-15
[Bug 410948]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948") seems to fit the bill.

---

### Post by BwackNinja on 2009-08-15
Sorry in advance, long post ahead! Its a good read though and goes through everything involving Bug 410948.

H'okay, so...

Using Karmic Alpha 4 and have used pulseaudio packages from both the repos and the ubuntu-audio-dev ppa

This problem stems from a discussion on a limitation of alsa:
" * Multichannel mixer controls are not exposed properly: [http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011830.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011830.html) " as seen on [http://pulseaudio.org/wiki/AlsaIssues](http://pulseaudio.org/wiki/AlsaIssues)

Discussion took place on the alsa mailing list with:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/016992.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/016992.html)
and then the next month:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-June/018710.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-June/018710.html)

Summed up (because it takes a long time to read it all) Lennart complains that ALSA doesn't expose multichannel mixer controls which makes volume control a pain, hence why it has been half-broken forever unless you've managed to fix yourself a decent setup and asks if it can be fixed. Lennart also inquires about any assumptions that can be made about how to control Master, Front, and PCM channels. A resounding "no" came for valid reasons including it'll break stuff and even if it can be considered the right way then regressions (which only happen when stuff is using ALSA directly or possibly the OSS compatibility layer) are still considered ALSA's fault, which is a bad thing. There's the possibility of adding new functions to the api to maintain compatibility but that's a huge pain to do right as well as choosing how different elements should interact, etc. Also - Master, Front, and PCM channels aren't quite used the same in each driver. Next up, Lennart says that he basically did the whole thing, but in PulseAudio and has the configuration files (the files in /usr/share/pulseaudio/alsa-mixer/paths/ /usr/share/pulseaudio/alsa-mixer/profile-sets/ if you want to try messing with them).

Problems as shown in this report stem from Master being set to be thought of as increasing the volume of all channels (which is true for some but not all) and PCM being thought as increasing the volume of all channels (which is true for some but not all). Changing these to be what you'd consider right for your audio card in /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf and /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common and moving the channels individually in pavucontrol and watching them change in alsamixer will show that only the channels that you change in pavucontrol will affect the corresponding channels in alsamixer.

Changing these globally will adversely affect hardware that was working properly to begin with, but the framework that Lennart has allows for udev rules to choose a specific configuration file based on the hardware/drivers. A good example is the AC97 cards, which, according to the mailing list, all operate in this same fashion that is broken with the current analog-output.conf and analog-output.conf.common because Master and PCM do not control more than the front. To truly fix this, we would need large scale testing of surround sound setups with different cards and facilitate the correct working of all hardware.

This, while slightly better than the current situation, has one more problem. Currently for me and others subscribed to this bug only one ALSA volume slider is moving at a time so you would simultaneously have output blasting on your rear speakers but nothing coming out of your front speakers. The intended behavior of the new mixer logic in PulseAudio is to move only one at a time and multiply the dB values to achieve a greate level of granularity in volume control without just resorting to doing that fully in hardware. The problem as I see it is that it seems not to be doing this per channel (as you can see when increasing the volume each ALSA volume control will take longer to reach its maximum than the  previous one so I'd call this mixer logic mostly-working) but instead is multiplying ALL the dB values of controls that have the "merge" option set.

Finally, there is the problem of whether the dB values are accurate, which is something that Lennart looked at and made a tool for. On my hardware, though the Master and Surround have the same reported dB range (0 to -46.40dB) and PCM has the range 0 to -34.50dB, for the Master (front) to match the loudness of the Surround (rear), I have to set PCM to about 85%, which I don't think makes sense when multiplying the dB values.

I hope this is fixed soon, I like my surround sound :D

~BwackNinja

---

### Post by BwackNinja on 2009-08-17
Any updates on this? I haven't seen anyone complaining about this anywhere other than the forums and that bug report. Probably because everything is working fine in stereo (which I'm resorting to right now).

---

### Post by phenest on 2009-08-17
> **BwackNinja said:**
> Any updates on this? I haven't seen anyone complaining about this anywhere other than the forums and that bug report. Probably because everything is working fine in stereo (which I'm resorting to right now).

The problem exists in stereo, but it's simply not noticeable. For example, I can plug in my headphones, and everything seems fine. But I can't disable the LFE channel on my laptop, and even if I could, it doesn't solve the problem. The lack of complaints or bug reports simply suggest that the majority of users only use stereo output.

---

### Post by ma2k1 on 2009-08-21
Same here :(
Inspiron 9400, karmic koala alpha 4.
Volume is too loud, if i try to regulate with alsamixer I see that PCM, LFE and MASTER work together... only when PCM and LFE are at 100% Master start to increase...

Any news?

---

### Post by BwackNinja on 2009-08-21
Someone should really post on the pulseaudio mailing list. Stuff would definitely be done or at least clarified.

---

### Post by ma2k1 on 2009-08-22
Waiting for an improvements in the alsa interface or pulseaudio manage of it, I have for the moment disabled my LFE (subwoofer).

[SIZE="3"]I've opened the file
*vi /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf*
and then I changed
**volume = ignore**
in the LFE section --> [Element LFE][/SIZE]

Now the volume work right (also from the pulseaudio volume control or directly with buttons control of inspiron) and isn't so loud...

If you try to see in alsamixer (just open the shell and digit alsamixer) you see that LFE is setted to zero and that isn't related to PCM and MASTER as before.
Now only Master and PCM work together and for the moment it's a reasonably solution.
See the attached picture


Have a fun ;)

---

### Post by phenest on 2009-09-07
> **ma2k1 said:**
> Waiting for an improvements in the alsa interface or pulseaudio manage of it, I have for the moment disabled my LFE (subwoofer).

Now only Master and PCM work together and for the moment it's a reasonably solution.

Yes, a reasonable solution, but will there be a fix?

---

### Post by phenest on 2009-09-07
The balance is working now. It graduates nicely between left and right.

---

### Post by phenest on 2009-10-03
Does anyone know the state of affairs regarding this issue? I've upgraded my Karmic test partition to the beta, and this is still a problem. In fact, it's a show stopper for me. I really want to use Karmic when it's released but only if the volume works properly with LFE channels.

---

### Post by phenest on 2009-10-05
Bump

---

### Post by mac.ryan on 2009-10-27
The bug that some other user linked above is progressing. There is an assignee and it "sounds" (ahah!) like the ppa package works better now.

That said, I am also stunned by the fact canonical is coming out with a version of ubuntu with such a massive bug and that they marked it as "medium priority"... :(

---

### Post by jezjones on 2009-10-27
Sound bugs are a low priority AFAIAK, they have been present in this form for years.. every upgrade requires a re-hack of ths sound on my system du jour, whether config files, changing the setting in the mixer or downloading a newer better ALSA / Pulse.

I would love sound to be addressed properly but apparently cloud computing is more important to more people.


Sorry to sound so negative about this, but i have posted and contributed to almost all of the "getting sound working in Hardy/Jaunty/gutsy etc etc" threads

---

### Post by SeanBlader on 2009-10-27
Well you know, sound in computers is so 15 years ago, cloud computing however is the current buzzword. What's most ironic is that sound back in the days of DOS was pretty easy, it was Sound Blaster compatible or you didn't bother. Personally, I'd rather have solid sound than a way to back up 2 gigs of data so I can get to them anywhere. If I want to get to my data somewhere else, I'll sneakernet it, it's more reliable than the cloud, and unfortunately more reliable than ALSA. Besides, USB is more ubiquitous than the network.

Moral of the story: sound is better than servers.

---

### Post by BwackNinja on 2009-10-27
> **jezjones said:**
> Sound bugs are a low priority AFAIAK, they have been present in this form for years.. every upgrade requires a re-hack of ths sound on my system du jour, whether config files, changing the setting in the mixer or downloading a newer better ALSA / Pulse.

I would love sound to be addressed properly but apparently cloud computing is more important to more people.


Sorry to sound so negative about this, but i have posted and contributed to almost all of the "getting sound working in Hardy/Jaunty/gutsy etc etc" threads

I hate to say that everything here is true, and at worst at the beginning of this thread we could still call the existence of this bug progress from the previous situation.

---

### Post by SveinT on 2009-10-27
Related bug report I filed some days ago:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/456564](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/456564)

---

### Post by BwackNinja on 2009-10-28
@SveinT Is it set to Analog Output / No Amplifier in the Output tab of gnome-volume-control? If not, try that.

---

