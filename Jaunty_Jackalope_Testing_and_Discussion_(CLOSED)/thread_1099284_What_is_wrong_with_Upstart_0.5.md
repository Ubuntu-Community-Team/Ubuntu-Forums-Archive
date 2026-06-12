---
title: "What is wrong with Upstart 0.5?"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yookoala on 2009-03-18
Upstart 0.5 is out for a while.
But it is not even on Ubuntu 9.04 (jaunty).

Just want to know what is the problem?

---

### Post by taavikko on 2009-03-18
Just wondering myself, since it's originally developed by ubuntu
seems funny that newest stable release isn't included

[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

---

### Post by tahina on 2009-03-18
You can find a video of a talk given by Scott James Remnant, the author of upstart here: [http://fosdem.unixheads.org/2009/maintracks/](http://fosdem.unixheads.org/2009/maintracks/) (it's the file named upstart.xvid.avi (and it's 597 megs)).

If I recall correctly, he basically says 0.5 is not as stable as 0.3. But it's an interesting talk for other reasons too.

The descrition of the talk, at [http://www.fosdem.org/2009/schedule/events/upstart](http://www.fosdem.org/2009/schedule/events/upstart) :

> This talk takes a trip along the Roadmap for Upstart 1.0, introducing what features will be available.

Linux has always traditionally lacked good service management facilities, so much so that the typical daemon doesn't use what ones we have and instead relies on hokey shell scripts.

Upstart is being developed to not only solve this problem but also how it, through integration with D-Bus, DeviceKit and similar frameworks, allows service lifecycles to be tied to hardware and system state.


---

### Post by ghindo on 2009-03-18
Interesting.  I would think that Upstart 0.5 would be stable, considering how long it's been out.  I mean, they've moved onto 0.5.1, so I would think that it would be worth including.

---

### Post by keybuk on 2009-03-19
0.5 isn't much of an improvement over 0.3 in basic terms, a lot of new things were tried but they didn't work out so well.

0.5's userland tools are notably worse than 0.3's and were never really finished.

I'm preferring to put all my effort into the next version (0.10) which will end up in Ubuntu

---

### Post by int on 2009-03-19
So in 9.10 we will have Plymouth that replace USplash 
And the new upstart...
And possibly grub 2.. 
And kernel 2.6.29+

So the Ubuntu boot will be reformulated..

---

