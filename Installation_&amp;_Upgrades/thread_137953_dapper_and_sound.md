---
title: "dapper and sound"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by mavr on 2006-03-01
I wanted to try out the dapper beta. I've installed gstreamer.mad but amarok still i can't play any mp3. Neither kaffeine is working.
I am Italian and noob. If anybody can help me with a couple of test to see what i am missing or what i've stuffed.
Thank u for your help guys.

---

### Post by RAOF on 2006-03-01
You need to install all the gstreamer0.10 packages - the Dapper programs use the new gstreamer, so the old 0.8 plugins no longer work with them.

---

### Post by mavr on 2006-03-01
I've done it, but still amarok doesn't want to play it. If i check the engine it is using it says Xine. Do i have to tell him to use gstreamer somehow? But is not on the list.

---

### Post by RAOF on 2006-03-01
Do you need to install the amarok-gstreamer package?

Actually, looking at "aptitude search amarok", there doesn't seem to be any amarok-gstreamer package at the moment.  You're probably after the libxine-extracodecs package, then :)

---

