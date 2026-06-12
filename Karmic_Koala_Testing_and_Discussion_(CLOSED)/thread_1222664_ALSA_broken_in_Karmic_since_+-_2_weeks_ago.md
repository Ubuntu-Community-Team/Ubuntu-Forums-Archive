---
title: "ALSA broken in Karmic since +/- 2 weeks ago"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nIRV on 2009-07-25
Since more or less 2 weeks now, audio on my dell latitude d830 has stopped working. Sound has been replaced by weak noises during playback.

The sound card on my laptop is a HDA Intel Sound Card (STAC92xx). The problem appears to be linked to ALSA. I found several bugs opened in launchpad referring to lost of audio but none are actively pursued by programmers. (400545, 399182, 398080, 397400, 397890)

Is anybody on the forum facing a similar issue?

---

### Post by taavikko on 2009-07-25
I have similar chip on my laptop and it is working correctly.

Please test via new user ("sudo adduser test") and login to see if it works with the user: test.

If so, I would advice removing ~/.pulse* files/folders in recovery mode so no pulseaudio is running with chance to corrupt those files again.

---

### Post by nIRV on 2009-07-25
Bug 400682 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400682](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400682)) appears to be the most active bug on STAC92xx users who lost sound upgrading to Karmic.

taavikko, will try this and get back to you, thanks.

---

### Post by nIRV on 2009-07-25
> **taavikko said:**
> I have similar chip on my laptop and it is working correctly.

Please test via new user ("sudo adduser test") and login to see if it works with the user: test.

If so, I would advice removing ~/.pulse* files/folders in recovery mode so no pulseaudio is running with chance to corrupt those files again.

Both methods listed above didn't work here.

---

### Post by taavikko on 2009-07-25
> **nIRV said:**
> Both methods listed above didn't work here.

The other method was just to test with a new user.

Have you tried "alsamixer" and "alsamixer -Dhw" to see if any channel is muted?

---

### Post by papangul on 2009-07-25
Someone else is facing a similar problem and has filed a bug with the alsaproject:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4642](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4642)

I have a similar problem with sound in karmic, but with a diffent sound card, and have also filed a bug report:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646)

---

### Post by nIRV on 2009-07-25
> **taavikko said:**
> The other method was just to test with a new user.

Have you tried "alsamixer" and "alsamixer -Dhw" to see if any channel is muted?

Yep, the new user test didn't work.

None of the channels are muted in alsamixer.

---

### Post by nIRV on 2009-07-25
> **papangul said:**
> Someone else is facing a similar problem and has filed a bug with the alsaproject:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4642](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4642)

I have a similar problem with sound in karmic, but with a diffent sound card, and have also filed a bug report:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4646)

The description of both bugs listed in your post refer to losing sound after a short period of time. The problem I have is no sound at all.

---

