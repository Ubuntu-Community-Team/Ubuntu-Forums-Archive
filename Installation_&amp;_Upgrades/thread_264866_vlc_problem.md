---
title: "vlc problem"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by czk101 on 2006-09-25
I've just installed vlc 0.7.2 (i want this version and not the latest) but when i play an .avi file i get the message

stream_out_transcode private error: cannot find decoder (avcodec)
stream_out_transcode private error: cannot create audio chain
main packetizer error: cannot create packetizer output
vop not coded

any ideas on how i can fix this?

thanks?

---

### Post by Henry Rayker on 2006-09-25
I believe the problem is that you don't have a divx codec. They aren't installed by default because they don't fit in with Ubuntu's philosophy on free software. The codec in question has some legal restrictions on where it can be distributed and stuff like that, so they leave it out.
[this]("https://help.ubuntu.com/community/RestrictedFormats") provides more information

---

### Post by czk101 on 2006-09-25
I thought i'd solved this by installing ffmpeg and including xvid. Is it possible i need to link this install to vlc or something?

---

