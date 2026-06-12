---
title: "gstreamer problems after 11.10 upgrade"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by powerclam on 2011-10-14
After allowing the update manager to upgrade me to 11.10, I'm having the following trouble with gstreamer:

1 - when running a java program using gstreamer and the java bindings, I am now getting the following error:[INDENT]Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: Unable to load library 'gstreamer-0.10': libgstreamer-0.10.so: cannot open shared object file: No such file or directory
[/INDENT]This is a 64 bit system. The "libgstreamer-0.10.so" exists in /usr/lib32
What do I need to do to make the /usr/lib32 visible/callable to the system?

2 - The webcam video is now all horked up. The command[INDENT]gst-launch-0.10 autovideosrc ! autovideosink
[/INDENT]now produces a horribly messed up image, with banding, ghosting, and over-amped red.
This problem seems to be with the camera driver, since[INDENT]gst-launch-0.10 videotestsrc ! autovideosink 
[/INDENT]produces a proper test-image.

Can anyone help me resolve these problems?
(kinda important, in a job-related sort of way)

---

### Post by gnush on 2011-10-14
I'm not sure how the libraries are placed in Ubuntu, have you tried to copy libgstreamer-0.10.so to /usr/lib? Are there any alternative packages in the repositories that is specifically made for 64bit systems?

---

### Post by powerclam on 2011-10-15
Thanks for your reply!
> **gnush said:**
> I'm not sure how the libraries are placed in Ubuntu, have you tried to copy libgstreamer-0.10.so to /usr/lib? Are there any alternative packages in the repositories that is specifically made for 64bit systems?

As for alternative packages specifically for 64bit - not so far as I can tell from the Software Center. (Which started yesterday, but doesn't seem to want to start at all for me this morning :[ )

Copying the lib/link to /usr/lib was the first thing I tried.
Predictably, I then encountered another "missing link" error on the gstinterfaces, which leads me to believe that _all_ gst-related libs would need to be copied to /usr/lib, which is not really practical, especially for an application that will be distributed. Even if it worked on my machine, it would result in a majorly abnormal installation, and an application that would not work on any machine that had not been similarly "modified."

Furthermore. copying the libs would do nothing to address the problem with video-capture.

I was sort of hoping that this morning I would find a slew of updates ready and waiting to be applied. No such luck.

Looks like for now my "solution" is to reinstall 11.04, with all the grief that entails, and hope that Ocelot gets fixed in the near future.
Too bad; judging from this message board it looks like the Canonical folks _really_ dropped the ball on the Ocelot release.

---

### Post by sudhakarRedi on 2013-03-05
hi powercalm...
have you installed gstreamer-0.10 and it's plugin base..?
check it once

---

### Post by sudhakarRedi on 2013-03-05
hi every one...

I am using gstreamer for media applications. 
I want to use my own decoder in gstreamer pipeline.

can any one help me...?

---

