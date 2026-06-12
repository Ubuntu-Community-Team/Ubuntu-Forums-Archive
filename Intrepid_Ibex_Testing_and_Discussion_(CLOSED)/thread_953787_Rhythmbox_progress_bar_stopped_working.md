---
title: "Rhythmbox progress bar stopped working"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2008-10-20
For some time (~ a week) the progressbar stops working after a while, videos don't play anymore and rhythmbox inserts big pauses at the end of each song. The thing is, music preview in nautilus works flawlessly and flash in firefox too. Does anyone know where I can start searching for this problem?

---

### Post by saceirdoth on 2008-10-20
I had same problem with a fedora-10 beta. Have to kill pulseaudio.

---

### Post by jfernyhough on 2008-10-20
Is this a problem with Pulseaudio 0.9.10? I thought it was just me as I'm using 0.9.13 from PPA. :D

---

### Post by mc4100 on 2008-10-20
> **jfernyhough said:**
> Is this a problem with Pulseaudio 0.9.10? I thought it was just me as I'm using 0.9.13 from PPA. :D

I too am using 0.9.13: it's funny, I don't see this is Rhythmbox ... but I do in Totem. The workaround is like saceirdoth said, kill and restart PulseAudio.

---

### Post by Benjamin_Lebsanft on 2008-10-21
> **mc4100 said:**
> I too am using 0.9.13: it's funny, I don't see this is Rhythmbox ... but I do in Totem. The workaround is like saceirdoth said, kill and restart PulseAudio.
me too, using pulseaudio 0.9.13 from ppa, is there a chance for this to get fixed?

---

### Post by jfernyhough on 2008-10-21
I wouldn't count on it, at least for a while. 0.9.10 is the version going into Intrepid, and all the dev effort will be going into that at the moment.

This is the risk you take using development PPAs. Fun, though. :D

---

