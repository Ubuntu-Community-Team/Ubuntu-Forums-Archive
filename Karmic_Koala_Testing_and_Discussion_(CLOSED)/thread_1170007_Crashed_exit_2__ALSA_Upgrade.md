---
title: "Crashed exit 2 : ALSA Upgrade"
date: 2009-05-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-25
Hmmmm

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/380426](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/380426)

---

### Post by Nullack on 2009-05-25
The dev is working on a fix already, nice!

---

### Post by super.rad on 2009-05-25
I used apport-collect to upload all the relevant logs to the bug, is it supposed to add each log as a seperate comment or is there some way I can get it to submit all the logs in one comment?
Just got about 20 emails through at once saying I had commented on the bug lol

---

### Post by autocrosser on 2009-05-25
Is it fixed yet?

---

### Post by super.rad on 2009-05-25
not for me

---

### Post by autocrosser on 2009-05-25
OK--thanks for the heads up--I'll wait for this one---hope the Alsa (fixed) will take care of my UT2004 sound problems--sound has been spotty after the last couple of Alsa updates...

---

### Post by alphacrucis2 on 2009-05-25
> **autocrosser said:**
> OK--thanks for the heads up--I'll wait for this one---hope the Alsa (fixed) will take care of my UT2004 sound problems--sound has been spotty after the last couple of Alsa updates...


A new version of alsa-base just downloaded for me but failed to install with error code (1)

---

### Post by inportb on 2009-05-25
Yep... saw this one too, figured I'd wait. It's good that a fix is in progress.

---

### Post by Nullack on 2009-05-25
Note to bug spammers - instead of spamming the bug comments, simply click on the effects me too link. This informs people your also effected.

---

### Post by inportb on 2009-05-25
> **Nullack said:**
> Note to bug spammers - instead of spamming the bug comments, simply click on the effects me too link. This informs people your also effected.

Oh yeah, and if you want to unsubscribe, don't message everyone saying so :P

---

### Post by ronacc on 2009-05-26
yes thanks for the headsup , I installed all updates but alsa and survived the reboot :P

---

### Post by paul_in_london on 2009-05-26
Still not fixed for me with alsa-base_1.0.20+dfsg-1ubuntu2.

Added details to Bug #380426.

---

### Post by taavikko on 2009-05-26
> **paul_in_london said:**
> Still not fixed for me with alsa-base_1.0.20+dfsg-1ubuntu2.

fix released as in alsa-base_1.0.20+dfsg-1ubuntu3

---

### Post by paul_in_london on 2009-05-26
Yep, sorted now with alsa-base_1.0.20+dfsg-1ubuntu3...

---

### Post by ranch hand on 2009-05-26
Installed the update this morning just fine but the volume is still about half what it was before updating to 2.6.30-6.

Have to see what happens.

---

### Post by seeker5528 on 2009-05-27
This alsa update must be what nuked my sound, nuked is probably not the right term, but that was the perception initially.

Running the alsa mixer from the command line showed, in addition to the normally expected sliders, 3 sliders with the label of DMX. Can't remember seeing DMX on any other mixer.

What is DMX you may ask? Good question, I don't know either. :p

But one of these while sliding it up did bring my sound up to a normal level. My suspicion is these would be front, center, and rear.

This is with some variant of VIA audio hardware.

Alsa has been updated since then with no repeat of the drop in sound.

Later, Seeker

---

### Post by ranch hand on 2009-05-27
The only dmx I can find reference to os DMXteratec 6fire usb.

---

### Post by seeker5528 on 2009-05-28
Oops, that should have been DXS and there are four sliders, sorry about that. :oops: 

If I open the full mixer view of the volume applet and click preferences it does give an option to display these sliders.

There is a reference in the alsa wiki:

[http://alsa.opensrc.org/index.php/Via](http://alsa.opensrc.org/index.php/Via)

Ok, that helps, but still doesn't give a clue as to what DXS actually is.

OK, found this:

[http://perso.netplus.ch/FCorthay/InstallGentoo/install_ALSA.html](http://perso.netplus.ch/FCorthay/InstallGentoo/install_ALSA.html)

> Here an information about dxs support:

    * 0: (default value) no DXS support, used for VIA8233A chips.
    * 1: enable full DXS support (at any supported sample rate).
    * 2: no DXS support: the hardware mixing ability of the chip is not used.
    * 3: DXS support at 48000 Hz only.
    * 4: DXS support at any supported sample rate with the codec set to 48000 Hz.

Hmmm, hardware mixing, my respect for some VIA audio chipsets just went up a notch. ;)

So if nothing else it looks like this hardware is another example of how it's a broken assumption to assume it is a good thing to grab exclusive access to the sound card outside of usage cases that require a higher precision of control over latency, timing, and synchronization (music production in particular). If I can have the hardware do the mixing, why would I want some software to come along and decide it should be doing the mixing?

Later, Seeker

---

### Post by ranch hand on 2009-05-28
I am not sure why you would want to do that but it looked like they may have been your answer.

I don't have the sound card or the hardware and do not use KDE so I just don't know.  Looks like a pretty piece of hardware though if you look it up.

---

