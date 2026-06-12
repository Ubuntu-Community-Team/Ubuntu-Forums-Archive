---
title: "Mp3 Plugin For GnomeBaker"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by carltonx on 2006-09-06
"The plugin to handle a file of type audio/mpeg is not installed".
I have just installed GnomeBaker on Ubuntu 6.06 and I tried to burn some mp3 audio files and the above message appeared. Can anyone help me; how do I get these plugins and how do I install them?

---

### Post by croak77 on 2006-09-06
You'll need gstreamer0.8-mad and gstreamer0.8-misc. Follow this guide;

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by carltonx on 2006-09-06
Thank you Croak 77 it worked. Can you suggest a decent media player to play cds?

---

### Post by ngdias on 2006-09-12
According to Synaptic, I have a number of gstreamer packages installed, but they're version 0.10, not 0.08 as croak77 suggested. For example, gstreamer0.10-plugins-base.

Further down the list I can also see packges for 0.80, but those are not installed.

I get an error with MP3 and OGG in GnomeBaker. Are there equivalent packages of version 0.10 for gstreamer0.8-mad and gstreamer0.8-misc, or do I have to install the 0.80 ones?

---

### Post by acascianelli on 2006-10-24
Cool, I was looking for this also.

---

### Post by altonbr on 2007-01-30
Um... I installed everything that was under "gstreamer mp3" in a search in Synaptic... and I still can't burn audio CDs... Any ideas?

---

