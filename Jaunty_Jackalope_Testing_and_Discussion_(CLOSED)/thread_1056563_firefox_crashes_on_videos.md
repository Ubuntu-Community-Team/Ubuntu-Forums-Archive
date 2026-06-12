---
title: "firefox crashes on videos"
date: 2009-01-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-01-31
When I try to view a video (e.g. from msn.com or msnbc.com) using firefox in Jaunty it crashes soon after beginning to open up the video window.

Starting in a terminal gives the uninformative error message 
"Illegal instruction: core dump"

I'm guessing Flash, but no-one else seems to be complaining in this forum.

Any ideas what might be amiss? Apart from running alpha software and expecting standard stuff to work, I mean...

---

### Post by cariboo on 2009-01-31
I had a couple of random crashes while using 180.22 drivers, but once I upgraded to 180.25, I haven't had any crashes so far.

Jim

---

### Post by scradock on 2009-01-31
> **cariboo907 said:**
> I had a couple of random crashes while using 180.22 drivers, but once I upgraded to 180.25, I haven't had any crashes so far.

Jim

Well, that's not what's wrong here, using the OS ati/radeon drivers. 

I remembered that I had installed libflashplayer.so without nspluginwrapper some weeks ago, instead of using flashplugin-nonfree from the repos. So I tried installing fp-nf (which brings in nspluginwrapper again) and the crash doesn't happen any more. So it looks like a regression - we once had a dream of getting beyond nspluginwrapper, but it died - at least for now.

Anyone else had the same experience?

---

