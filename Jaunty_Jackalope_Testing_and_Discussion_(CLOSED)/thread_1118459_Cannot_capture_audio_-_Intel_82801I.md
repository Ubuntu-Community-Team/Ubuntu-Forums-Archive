---
title: "Cannot capture audio - Intel 82801I"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by me13221 on 2009-04-07
Hey everyone-

Upgraded to 9.04 via 'update-manager -d' and everything went smoothly.  very sleek.  nice job.  several problems fixed.

One remains however: I cannot record sounds through the external mic.  I don't know exactly how to test this but I tried both Gnome Sound Recorder and Audacity.  I used a cassette tape player (really!) as the source, and it sounds fine in headphones.  But sound recorder just produces static, and audacity behaves very strangely (a bug in itself, perhaps) but doesn't record audio.

I want to narrow it down to hardware vs. software vs. Alsa / Jack / PulseAudio mumbo jumbo.  Any suggestions?  The hardware is an Intel 82801I HD Audio controller on a Lenovo x200.

---

### Post by macogw on 2009-04-07
Almost all of the Intel HDA stuff says that in the lspci line.  That's basically no information at all.  Can you download this [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) and run it in bash (*not* sh)?

Also, to clarify...you mean a mic that you plug in right?  Because we know the built-into-screen ones are almost universally broken.

---

### Post by me13221 on 2009-04-07
> **macogw said:**
> Almost all of the Intel HDA stuff says that in the lspci line.  That's basically no information at all.  Can you download this [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) and run it in bash (*not* sh)?

Sure- here's the output (attached)

> **macogw said:**
> Also, to clarify...you mean a mic that you plug in right?  Because we know the built-into-screen ones are almost universally broken.

That's right.  I'm using a double-ended 1/8" headphone cable to connect the headphone-out of the tape player to the red-tipped mic-in jack on the notebook.

---

