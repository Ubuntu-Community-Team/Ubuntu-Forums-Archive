---
title: "Issues after upgrading Linux headers"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by nightwolf2k5 on 2009-12-20
Hi,

I have Ubuntu installed on my external hard drive. The boot loader is also installed on my external hard drive.
I have a very peculiar problem. As soon as I installed Ubuntu, I decided to upgrade. I downloaded and installed the linux headers version 2.6.31-17.
I was asked to restart the machine. After the restart, I selected the 2.6.31-17 option in the boot menu.
After that.. I get the ubuntu symbol for a while and then... nothing.. just a blank screen.

I am able to log into ubuntu if I select the 2.6.31-14 version. But now, empathy and the software centre dont work.
Is it possible to fix or remove the 2.6.31-17 version? I am guessing that everything else will work then.

I would appreciate some help on this issue.

edit: Somehow the new version worked!
here is what happens when I try to load the movie player or empathy..
> (totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcdio.so': /usr/lib/gstreamer-0.10/libgstcdio.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegaudioparse.so': /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegstream.so': /usr/lib/gstreamer-0.10/libgstmpegstream.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdvdlpcmdec.so': /usr/lib/gstreamer-0.10/libgstdvdlpcmdec.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstiec958.so': /usr/lib/gstreamer-0.10/libgstiec958.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmad.so': /usr/lib/gstreamer-0.10/libgstmad.so: file too short

(totem:2152): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsta52dec.so': /usr/lib/gstreamer-0.10/libgsta52dec.so: file too short
Error re-scanning registry , child terminated by signal
Run 'totem --help' to see a full list of available command line options.

Thanks.

---

