---
title: "Rhythmbox automatically pauses for Skype calls"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Flimm on 2009-10-06
I've just upgraded my system to Karmic beta, and I've noticed a nifty features: start playing some music in Rhythmbox, it will automatically pause the music whenever you receive a Skype call and resume as soon as the call is finished.

Unfortunately, it also pauses for every chat message I receive, because of the sound it emits.

Who's to praise for this? Rhythmbox? Pulseaudio? Skype? I'm impressed, in any case.

---

### Post by adam-red on 2009-10-06
I noticed it with skype but I have sounds disabled in messenger.

---

### Post by dalonso on 2009-10-06
> **Flimm said:**
> I've just upgraded my system to Karmic beta, and I've noticed a nifty features: start playing some music in Rhythmbox, it will automatically pause the music whenever you receive a Skype call and resume as soon as the call is finished.

Unfortunately, it also pauses for every chat message I receive, because of the sound it emits.

Who's to praise for this? Rhythmbox? Pulseaudio? Skype? I'm impressed, in any case.

Humm, I think this could be a bug in empathy. There's one commit on March, 8th that sets their pulseaudio role to "phone". This would be true when doing a voip call, but not when notifying about just received messages:

[http://mail.gnome.org/archives/svn-commits-list/2009-March/msg02455.html](http://mail.gnome.org/archives/svn-commits-list/2009-March/msg02455.html)

I have reported a bug: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/444880](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/444880)

---

### Post by FuturePilot on 2009-10-06
> **Flimm said:**
> 

Who's to praise for this? Rhythmbox? Pulseaudio? Skype? I'm impressed, in any case.

Pulseaudio and Skype. Pulseaudio has support for tagging audio streams and the Skype Beta does this tagging with its streams. This allows for an audio stream with a certain tag to pause other streams.

---

### Post by terryroe on 2009-10-08
Does anyone know a fix or workaround for this?  It's really annoying.  I like to be notified when I get a new skype message, but I also like to listen to music uninterrupted.  Hopefully, someone will take notice and revert this "feature"?

TR

---

### Post by Flimm on 2009-10-08
You can just turn off the noises Skype makes when you receive chat messages and stuff. Open Skype, open its options, click notifications, select the notifications ("Chat message received", etc) and untick "Play sound file". Obviously, this is a workaround, not a fix.

---

