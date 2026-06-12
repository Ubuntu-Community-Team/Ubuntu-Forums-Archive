---
title: "Going to Fullscreen in Totem crashes X"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by notoriousdbp on 2009-04-12
Got Jaunty up and running and have a major problem with DVD playback in Totem-gstreamer.  Basically the playback is really slow and jerky if I get any visual at all and maximising or going to full screen crashes X.  I'm using an ATI card and have desktop effects enabled.  Using Totem Xine is still jerky but allows  the transition to maximised and full screen

I logged a bug on launchpad (#352741) over a fortnight ago and nobody has looked at it yet and we're only 10 days from release which concerns me to say the least.

---

### Post by Nullack on 2009-04-12
Look at the ubuntu wiki for tips on how to debug this yourself some more.

You wont always get help with your bug reports. It happens to me and many others.

First thing I would do is turn off compiz.

---

### Post by notoriousdbp on 2009-04-13
Thanks for the reply.  Switching off compiz does sort things out but it's just a question of why should I have to? It's a shame as it means we're no further forward from 8.10 although we don't have the flickering video issue anymore.

I've filed bug reports using the ubuntu-bug method for totem-gstreamer compiz and xserver-xorg-video-ati

---

### Post by Nullack on 2009-04-13
It fixes it because linux has a broken video architecture. Fixing it is ongoing but it isnt being fixed in a rapid manner.

---

