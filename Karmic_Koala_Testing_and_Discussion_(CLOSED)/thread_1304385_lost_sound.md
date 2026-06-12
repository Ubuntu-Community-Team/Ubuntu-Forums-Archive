---
title: "lost sound?"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lazy-buntu on 2009-10-29
I upgraded from Jaunty and I've got no sound. Lspci shows a sound device in there. I don't even have sound at login.

Any ideas?

---

### Post by froggyswamp on 2009-10-29
What does the sound applet say

---

### Post by Lazy-buntu on 2009-10-29
I don't have a sound applet in my panel, but the volume keys on my keyboard work for mute unmute vol+ vol-

What's weird is if I go to preferences > sound > hardware, there's no hardware in there.

---

### Post by grandtoubab on 2009-10-29
test your level with
alsamixer

maybe they are all at bottom

---

### Post by Lazy-buntu on 2009-10-29
Alsamixer won't even launch from terminal so I did:

```
aplay -l
```

I get: no soundcards found...

---

### Post by grandtoubab on 2009-10-29
maybe  this
[URL="https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500"]
https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500[/URL]

Pulseaudio can't find working alsa sound cards on bootup.
"alsa force-reload" after login remedies the problems until next reboot.
Comments 40,41,42 propose a workaround - disabling sl-modem.

lot of sound problems in Karmic
[https://bugs.launchpad.net/ubuntu/karmic/+bugs?field.searchtext=alsa&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=]("https://bugs.launchpad.net/ubuntu/karmic/+bugs?field.searchtext=alsa&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")



General information
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

