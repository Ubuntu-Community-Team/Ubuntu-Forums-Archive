---
title: "upgrade from breezy to dapper: totem-xine playback looks like crap"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by stanwebber on 2006-07-25
something happened because playback of divx/xvid files now looks blocky (especially noticable with text or cartoons) where under breezy the image was smooth & flawless.  the dist-upgrade completed successfully without any issues whatsoever.  all formats are still recognized by totem & play fine--the image just looks like crap (even more so full screen)

prior to upgrade the following packages were installed

totem-xine
w32codecs
gnomebaker (gstreamer0.8 dependancy both breezy/dapper)

since upgrading i have performed the following to fix the issue

sudo apt-get remove w32codecs
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

how can i fix this short of switching back to a working os like windows?

---

### Post by stanwebber on 2006-07-25
this issue was resolved by applying the workaround from this seemingly unrelated bug here,

[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)

i resized totem_logo.png to 800x600 & all is back to the way it was

---

