---
title: "Karmic after boot sometimes is  mute"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by makro on 2009-10-16
Hello!
I've eepc 900ha with karmic netbook updated daily.
Since last kernel update from yesterday sometimes after boot the volume in gnome is mute and the slider is set to 0. It doesn't happen every time,
Any ideas?

Thanks in advance

---

### Post by josteinaj on 2009-10-16
I have a similar problem after installing a fresh install of Karmic Beta, upgraded to the latest packages.

The volume mutes/unmutes seemingly at random. It often happens when I adjust the volume, especially when I lower the volume.

The laptop in question is a HP EliteBook 8530w.

---

### Post by makro on 2009-10-17
Upgrade this morning didn't solve the problem

I opened a bug [https://bugs.launchpad.net/ubuntu/+bug/453776](https://bugs.launchpad.net/ubuntu/+bug/453776)
(hope I did it in the right way!:))

---

### Post by VMC on 2009-10-17
Thanks for filing the bug report. I added yes, it affects me too.

---

### Post by makro on 2009-10-17
Thank you too!
Hope they have enough informations to provide a fix

---

### Post by null_pointer_us on 2009-10-17
Certain sound-related updates reset the volume to zero for some reason.

IMO this is still undesirable because it makes the system look flaky and can confuse new users.

I often get family/friend support calls from people whose "sound stopped working" because they hit the mute key or some app's volume slider is tied into main/global volume in a dumb way.

---

