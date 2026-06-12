---
title: "ext4 uses 22gb overhead on new HDD"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by mchlor on 2010-06-21
searched to no avail.

Brandnew 1.5tb hard drive was formatted using gparted in ext4. But something is using 22gb of the hard drive right off the bat.

why?

---

### Post by wilee-nilee on 2010-06-21
> **mchlor said:**
> searched to no avail.

Brandnew 1.5tb hard drive was formatted using gparted in ext4. But something is using 22gb of the hard drive right off the bat.

why?

It's the math what is called 1.5 terrabytes is measured differently. I forget the exact explanation, but my 320 gig external is only 310 gigs or something around that. I'm sure somebody will break it down correctly for you.

---

### Post by mchlor on 2010-06-21
thanks for the quick reply.

I'm well aware of the hard drive size difference from advertised capacity vs actual.

I'm perfectly fine with it showing up as having 1.34 TB but I'm not ok with it using 22gb right off the bat leaving me with 1.31TB of space.

Or,

Let me explain it this way.  It formats fine with 1.34 TB of capacity.  But something/some_file/overhead/whatever is already on there right after the format using up 22gb of space.

Is this 22gb of ext4 journaling  overhead?

---

### Post by wilee-nilee on 2010-06-21
> **mchlor said:**
> thanks for the quick reply.

I'm well aware of the hard drive size difference from advertised capacity vs actual.

I'm perfectly fine with it showing up as having 1.34 TB but I'm not ok with it using 22gb right off the bat leaving me with 1.31TB of space.

Or,

Let me explain it this way.  It formats fine with 1.34 TB of capacity.  But something/some_file/overhead/whatever is already on there right after the format using up 22gb of space.

Is this 22gb of ext4 journaling  overhead?

Sorry I don't know there is always a little space taken but I don't know how or if it breaks down with the larger the partitioning is. Somebody else though will know thou I suspect I see people with large HD on the forum a lot.

---

### Post by User Abuser on 2010-07-14
So is it the journal or what?? Just took 5gib of my new 300gib drive. Just want to know if it can shrink like MFT

---

