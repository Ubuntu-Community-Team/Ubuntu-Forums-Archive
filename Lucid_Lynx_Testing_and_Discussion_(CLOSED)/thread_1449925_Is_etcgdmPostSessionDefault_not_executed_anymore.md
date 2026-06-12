---
title: "Is /etc/gdm/PostSession/Default not executed anymore?"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by night-wing on 2010-04-08
Hi.

In Lucid, I think, this script is not executed anymore.
Why?
I wrote a command for a shutdown sound in it, which plays, when I copy/type in at console - but not even when I shutdown.

Is this a bug?

Nightwing

---

### Post by dcstar on 2010-04-09
> **night-wing said:**
> Hi.

In Lucid, I think, this script is not executed anymore.
Why?
I wrote a command for a shutdown sound in it, which plays, when I copy/type in at console - but not even when I shutdown.

Is this a bug?

Nightwing

Shutdown closes everything so quickly the sound player stops before it gets a chance to play anything. If you Logout you should hear the sound play.

The "bug" is not forcing the system to wait until this script is completed, I don't know if the developers will want to change this as quick shutdowns are an obvious goal.

Personally, if a user wants to slow down their shutdown by playing a sound then that's the user's deliberate decision and the system should respect it and play the whole sound before shutting down.

---

### Post by night-wing on 2010-04-12
Is there any possibility to slow down the shutdown process till the sound is played?

---

