---
title: "Gstreamer Updates?"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-04-07
Anyone know the story with gstreamer updates? Were behind the stable releases as per:

	
GStreamer Bad 0.10.11, Ugly 0.10.11 & FFmpeg 0.10.7 stable releases
	2009-03-20 00:00

The GStreamer team is pleased to present new releases of the Bad, Ugly and FFmpeg Plugins modules in the 0.10 GStreamer stable release series.

Check out release notes for gst-plugins-bad, gst-plugins-ugly and gst-ffmpeg or download tarballs for gst-plugins-bad and gst-plugins-ugly and gst-ffmpeg

---

### Post by pferraro on 2009-04-08
If you want stay current with the latest stable releases, use this PPA:
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by pferraro on 2009-04-08
> **pferraro said:**
> If you want stay current with the latest stable releases, use this PPA:
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Actually, even that PPA is a little behind - debian unstable is current though.

---

### Post by pferraro on 2009-04-08
oh - and occasionally, patience pays off ;):
[http://launchpad.net/distros/ubuntu/jaunty/+source/gst-plugins-bad0.10/0.10.11-2ubuntu1](http://launchpad.net/distros/ubuntu/jaunty/+source/gst-plugins-bad0.10/0.10.11-2ubuntu1)
I expect the ugly plugins package will follow soon...

---

### Post by Nullack on 2009-04-08
So now its ugly. ugly multiverse and ffmpeg plugins that are out of date.

---

### Post by Nullack on 2009-04-10
Hmmmm with the archive freeze looming I sent an email to the motu list on this. No activity yet, but I can help with testing any plugin updates. These are stable gstreamer plugin updates that would otherwise result in bugs already resolved upstream for ubuntu users.

---

