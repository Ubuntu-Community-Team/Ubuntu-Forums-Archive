---
title: "Totem's YouTube plugin broken?"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tpg on 2010-04-11
I've got a fresh install of Lucid Beta 2 in a VM, and have found that the YouTube plugin for totem (installed by default) appears to be broken. Walkthrough of what happened:

1) First time I searched for a youtube video and try to play it (searched for "cat" and tried first result), Totem tells me I need to install codecs. I go ahead and install all the codecs it suggests.

2) I then restart Totem, and try to play the same video. Totem fails with error message: "GStreamer encountered a general supporting library error"

3) Restart the VM to no avail. Run totem from terminal, get following error output:

** Message: Error: GStreamer encountered a general supporting library error.
gstffmpegdemux.c(1243): gst_ffmpegdemux_open (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/ffdemux_swf:ffdemux_swf0:
Input/output error

Anyone know what's going on here?

---

### Post by amano on 2010-04-11
Youtube changed some details and most players are broken ATM. Just wait. The fix is already coded and will probably hit Totem 2.30.1 and will even be backported to 2.28.

---

### Post by tpg on 2010-04-12
Glad to hear it's in the works! Do you know if the fix will be included with Lucid at release?

---

### Post by xerosis on 2010-04-12
> **tpg said:**
> Glad to hear it's in the works! Do you know if the fix will be included with Lucid at release?

It landed in Lucid a few days ago, works fine here.

---

